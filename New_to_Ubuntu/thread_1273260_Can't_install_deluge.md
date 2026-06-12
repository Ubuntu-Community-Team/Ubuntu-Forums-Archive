---
title: "Can't install deluge"
date: 2009-09-23
forum: New to Ubuntu
---

### Post by Falc7 on 2009-09-23
I am trying to install deluge, i downloaded all 3 files from getdeb, i try to install them and i get the message "an unknown error occured". Is there a problem with my system?

I am aware i could get it other ways, i would just like to get this way working, because its the latest package, and to make sure nothing is wrong with my system, packages ect

---

### Post by Bachstelze on 2009-09-23
Try installing them from the command line:

```
sdo dpkg -i package.deb
```

and paste what you get.

---

### Post by nothingspecial on 2009-09-23
I ought to read the whole post before posting

---

### Post by halitech on 2009-09-23
> **Falc7 said:**
> I am trying to install deluge, i downloaded all 3 files from getdeb, i try to install them and i get the message "an unknown error occured". Is there a problem with my system?

I am aware i could get it other ways, i would just like to get this way working, because its the latest package ect

How are you trying to install it and what exact files did you download?


> **Bachstelze said:**
> Try installing them from the command line:

```
sdo dpkg -i package.deb
```

and paste what you get.

wouldn't it be sudo dpkg -i? ;)

---

### Post by Falc7 on 2009-09-23
> **Bachstelze said:**
> Try installing them from the command line:

```
sdo dpkg -i package.deb
```

and paste what you get.

```
jamie@jamie-kubuntu:~$ sudo dpkg -i package.deb
[sudo] password for jamie:
dpkg: error processing package.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 package.deb
jamie@jamie-kubuntu:~$


```

> **halitech said:**
> How are you trying to install it and what exact files did you download?

I am doubling clicking the 3 files here:
[http://www.getdeb.net/release/4466](http://www.getdeb.net/release/4466)
It asks me, would you like to install this package? I click yes, then it says an unknown error occurred, i could make screen shots if it would help.

---

### Post by halitech on 2009-09-23
> **Falc7 said:**
> ```
jamie@jamie-kubuntu:~$ sudo dpkg -i package.deb
[sudo] password for jamie:
dpkg: error processing package.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 package.deb
jamie@jamie-kubuntu:~$

```

I think Bachstelze forgot to mention that you need to change package.deb to the proper file name of the deb you are trying to install

do you have gdebi installed?

edit: just clicked in that you are trying to do this on Kubuntu, deluge is a GTK app so it might be missing some dependencies. try the command line and it should pull the dependencies in that it needs.

---

### Post by sisco311 on 2009-09-23
> **halitech said:**
> 
edit: just clicked in that you are trying to do this on Kubuntu, deluge is a GTK app so it might be missing some dependencies. try the command line and it should pull the dependencies in that it needs.
+1

The best way to deal with the dependencies and still get the latest version is to install it from the ppa repos.

---

### Post by Falc7 on 2009-09-23
Oh yes, silly me :p

```
jamie@jamie-kubuntu:~$ sudo dpkg -i deluge-core_1.1.9-1~getdeb1_all.deb
dpkg: error processing deluge-core_1.1.9-1~getdeb1_all.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 deluge-core_1.1.9-1~getdeb1_all.deb
jamie@jamie-kubuntu:~$

```

I have got gdebi installed through synaptic

---

### Post by kaivalagi on 2009-09-23
> **sisco311 said:**
> +1

The best way to deal with the dependencies and still get the latest version is to install it from the ppa repos.

+1

The ppa for deluge can be viewed here: [https://launchpad.net/~deluge-team/+archive/ppa](https://launchpad.net/~deluge-team/+archive/ppa)

---

### Post by Falc7 on 2009-09-23
Ah ok, i'll try that now, does this mean i won't be able to install debs easily in the future, or is it just deluge specific?

Edit: It installed, thanks guy :)

---

### Post by halitech on 2009-09-23
> **Falc7 said:**
> Oh yes, silly me :p

```
jamie@jamie-kubuntu:~$ sudo dpkg -i deluge-core_1.1.9-1~getdeb1_all.deb
dpkg: error processing deluge-core_1.1.9-1~getdeb1_all.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 deluge-core_1.1.9-1~getdeb1_all.deb
jamie@jamie-kubuntu:~$

```

I have got gdebi installed through synaptic

are the files you downloaded in your /home folder or are they on the desktop? you need to run dpkg in the directory where the files are

---

### Post by Falc7 on 2009-09-23
They were on the desktop, but i was able to add the repositories and install deluge that way, which is probably better because now deluge will stay up-to-date :)

---

### Post by halitech on 2009-09-23
> **Falc7 said:**
> They were on the desktop, but i was able to add the repositories and install deluge that way, which is probably better because now deluge will stay up-to-date :)

very true. thats why it was failing, if the files were on the desktop and you weren't in the same directory, it wouldn't find them and therefor would fail.

---

### Post by WaNaBePi on 2009-10-09
I had deluge 0.5.9 installed and working great. Then i wanted to update it, and i went to there site, and downloaded the .tar.gz file. Went through the read me, and copy and pasted all the dependencies in to a terminal, every thing seams to have worked just fine. Then attempted to "build and install" deluge...Only the scripts to do so in the read me just give me: error2 setup.py does not exist...and now deluge doesn't work at all(cause i did some command to get rid of old installs to try and fix the problem, per their web site) So i have once again screwed my self!

Just tell me what i need to do to get rid of anything that may be blocking my install. or what other info one needs in order to know the problem.

I'm going to need 1/2 step by 1/2 step instructions on how to do this right cause I'm a hard core newb.

Thanks in advance.

never mind wrong area SORRY. Im on ubuntu intrepid

---

### Post by kaivalagi on 2009-10-09
> **WaNaBePi said:**
> I had deluge 0.5.9 installed and working great. Then i wanted to update it, and i went to there site, and downloaded the .tar.gz file. Went through the read me, and copy and pasted all the dependencies in to a terminal, every thing seams to have worked just fine. Then attempted to "build and install" deluge...Only the scripts to do so in the read me just give me: error2 setup.py does not exist...and now deluge doesn't work at all(cause i did some command to get rid of old installs to try and fix the problem, per their web site) So i have once again screwed my self!

Just tell me what i need to do to get rid of anything that may be blocking my install. or what other info one needs in order to know the problem.

I'm going to need 1/2 step by 1/2 step instructions on how to do this right cause I'm a hard core newb.

Thanks in advance.

never mind wrong area SORRY. Im on ubuntu intrepid

Why don't you just install from the ppa here: [https://launchpad.net/~deluge-team/+archive/ppa](https://launchpad.net/~deluge-team/+archive/ppa)

You need to:

1) Add this to your /etc/apt/sources.list file:

deb [http://ppa.launchpad.net/deluge-team/ppa/ubuntu](http://ppa.launchpad.net/deluge-team/ppa/ubuntu) intrepid main 
deb-src [http://ppa.launchpad.net/deluge-team/ppa/ubuntu](http://ppa.launchpad.net/deluge-team/ppa/ubuntu) intrepid main 

2) Add the attached key txt file to your authenticated archives list (in synaptic is the easiest)

---

