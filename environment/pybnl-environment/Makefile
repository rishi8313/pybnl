

TAG_DATE=201806040450_

# docker run -it --rm continuumio/anaconda /bin/bash
# docker run -it --rm jupyter/r-notebook:0f73f7488fa0 /bin/bash
# docker run -it --rm -e HTTP_PROXY=${HTTP_PROXY} -e HTTPS_PROXY=${HTTPS_PROXY} -e http_proxy=${HTTP_PROXY} -e https_proxy=${HTTPS_PROXY} -w /home/jovyan/work jupyter/r-notebook:0f73f7488fa0 /bin/sh

# docker run -it --rm -w /home/jovyan/work/pybnl --user root pybnl-test-image:latest /bin/bash
# docker run -it --rm -w /home/jovyan/work/pybnl             pybnl-test-image:latest /bin/bash


pybnl-test-image: clean
	cp -r ../pybnl . &&	docker build --build-arg HTTP_PROXY=${HTTP_PROXY} --build-arg HTTPS_PROXY=${HTTPS_PROXY} --build-arg http_proxy=${HTTP_PROXY} --build-arg https_proxy=${HTTPS_PROXY} --tag pybnl-test-image:${TAG_DATE} -f Dockerfile .

test:
	docker run -it --rm -e HTTP_PROXY=${HTTP_PROXY} -e HTTPS_PROXY=${HTTPS_PROXY} -e http_proxy=${HTTP_PROXY} -e https_proxy=${HTTPS_PROXY} -w /home/jovyan/work/pybnl/tests pybnl-test-image:${TAG_DATE} pytest

clean:
	rm -rf pybnl

sync: clean
	cp ./* ../pybnl/environment/pybnl-environment/
