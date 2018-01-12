# Ruby on Rails on Docker on CentOS

## Docker on CentOS
- http://docs.docker.jp/engine/installation/centos.html

``` sudo yum update ```

``` curl -sSL https://get.docker.com/ | sh ```

``` sudo service docker start ```

``` sudo docker run hello-world ```

``` sudo usermod -aG docker ubuntu ```

- do exit & login

``` docker run hello-world ```

``` sudo chkconfig docker on ```


## Ruby on Rails
- https://hub.docker.com/_/rails/

``` docker pull rails ```

``` docker run -it --rm --user "$(id -u):$(id -g)" -v "$PWD":/usr/src/app -w /usr/src/app rails rails new --skip-bundle webapp ```

``` cd webapp ```

``` docker run --rm -v "$PWD":/usr/src/app -w /usr/src/app ruby:2.4 bundle install ```

``` echo "FROM rails:onbuild" > Dockerfile ```

``` docker build -t rails-onbuild . ```

``` docker run --name rails01 -p 80:3000 -d rails-onbuild ```



## Check
- http://192.168.99.100:8080/