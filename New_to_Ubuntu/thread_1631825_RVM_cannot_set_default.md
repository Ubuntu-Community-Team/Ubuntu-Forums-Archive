---
title: "RVM cannot set default"
date: 2010-11-27
forum: New to Ubuntu
---

### Post by flebber on 2010-11-27
I am trying to get rvm to set ruby 1.9.2 as default but it doesn seem to want to work.

I have even removed the default ruby 1.8.7 install and then reinstalled via rvm so that now I have both ruby 1.9.2 and 1.8.7 installed via rvm.

However when setting rvm to use 1.9.2 as default it isnt ¨sticking¨

```
sayth@sayth-homee:~$ rvm use 1.9.2
Using /home/sayth/.rvm/gems/ruby-1.9.2-p0
sayth@sayth-homee:~$ rvm --default use 1.9.2
Using /home/sayth/.rvm/gems/ruby-1.9.2-p0
sayth@sayth-homee:~$ ruby -v
ruby 1.8.7 (2010-06-23 patchlevel 299) [i686-linux]
sayth@sayth-homee:~$ 

```

---

### Post by karthikeyhegde on 2010-11-27
You need add below line to ./profile file
[[ -s "$HOME/.rvm/scripts/rvm" ]] && . "$HOME/.rvm/scripts/rvm"

 Go through .. 

[http://rvm.beginrescueend.com/rvm/basics/](http://rvm.beginrescueend.com/rvm/basics/)
[http://marcgrabanski.com/articles/gem-management-with-rvm-and-bundler](http://marcgrabanski.com/articles/gem-management-with-rvm-and-bundler)

---

