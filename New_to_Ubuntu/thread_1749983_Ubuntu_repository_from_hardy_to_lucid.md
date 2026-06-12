---
title: "Ubuntu repository from hardy to lucid"
date: 2011-05-05
forum: New to Ubuntu
---

### Post by Naqib on 2011-05-05
Hi everyone, 
I am sorry if I selected the wrong forum, since, I am new in Linux.

I have a local repository in Hardy, which has got some general packages also some exclusive packages. This local repository provides packages for Boxes using apt-get update/apt-get upgrade commands. 

Now I want to replace this repository with the lucid for which I have already upgraded my local repository operating system to UBUNTU 10.4.  

hardy repository has got these folders: main non-free freedit and contrib.

I did copy the main folder for 10.4 UBUNTU CD and replace it with the and did dpkg-scanpackages for it, it do apt-get update successfully, but when I do  apt-get upgrade it generates error something like impossible to fetch http:/7...../ HASH SUM MISMATCH.

then I learnt a bit from internet that I should use reprepro for creating a new repository but in this point, I am confiused, I dont know how to integrate the packages of hardy with lucid.

Thanks in advance

---

