---
title: "installing packages like java6, ant, apache from 8.04 LTS"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by hosdes on 2009-01-05
we have ubuntu 8.04 LTS hardy heron minimal system server edition installed and through the terminal I did "sudo apt-get update" to get the latest list of packages to install.

the following I would like to install apache, mysql, php, java, apache-ant.

I tried "apt-get install sun-java6-jdk" and does not work. did "apt-cache -s | java" and show me a list of 

The program 'java' can be found in the following packages:
 * java-gcj-compat-headless
 * openjdk-6-jre-headless
 * cacao
 * j2re1.4
 * kaffe
 * jamvm
 * gij-4.1
 * gij-4.2
 * sablevm

---

### Post by hosdes on 2009-01-05
found somewhat answer.  I did apt-get update but at first still could not find certain repos.  after awhile they did show up.

---

