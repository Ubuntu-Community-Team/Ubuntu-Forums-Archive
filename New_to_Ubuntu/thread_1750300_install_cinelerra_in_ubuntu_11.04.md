---
title: "install cinelerra in ubuntu 11.04"
date: 2011-05-05
forum: New to Ubuntu
---

### Post by ifar on 2011-05-05
Hi everibody

I had installed cinelerra in ubuntu 11.04.

that is de way:

add the repo

**sudo add-apt-repository ppa:cinelerra-ppa/ppa**

update

**sudo apt-get update**

and install

[B]sudo apt-get install cinelerra

[/B]and have fan!


(more info in [https://launchpad.net/~cinelerra-ppa/+archive/ppa]("https://launchpad.net/%7Ecinelerra-ppa/+archive/ppa"))

---

### Post by Weepleman on 2011-05-12
When I tried this, it cinelerra says that I need libx.so.98, and that isn't in the repositories.

---

### Post by ifar on 2011-05-16
It worked perfectly for me. I have been working in a 16min. long movie clip with no problems.

Anyway i checked my repos. I have also another repo called cinelerra-exp activated. I thought it was invalid but could be necesary!  

check this:

[https://launchpad.net/~cinelerra-ppa/+archive/cinelerra-exp](https://launchpad.net/~cinelerra-ppa/+archive/cinelerra-exp)

active this new repo and try to install again, and please reply!

---

### Post by bijeeshvs on 2011-05-29
I was also stumbled upon the same lib, adding the repos and installing didnt solved my problem. My cinelerra was working just fine until i upgraded ubuntu.

My cinelerra was compiled from git, so I used make -autoremove, uninstalled using synaptic and then installed from synaptic and now it WORKS!!!!!!!!!!!

---

### Post by rojaasensei on 2011-08-20
I tried the synaptic route as mentioned by bijeeshvs, but still ended with failure due to dependency issues.:(

---

### Post by sarang031705 on 2011-10-02
Thank you so much ifar....it worked fine with the installation

---

### Post by ErikSlinger on 2012-02-04
Thanks a lot! Spend an evening to get it working before finding this post.

---

