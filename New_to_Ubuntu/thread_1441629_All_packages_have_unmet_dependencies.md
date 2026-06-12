---
title: "All packages have unmet dependencies"
date: 2010-03-29
forum: New to Ubuntu
---

### Post by drfurly on 2010-03-29
Howdy all. I'm a software engineering major, previous Windows usr4lyfe, but now academia requires that I lrn2linux, so here I am. Forgive me if I seem a little jaded regarding Linux. I've tried it in the past, and I honestly want to learn to use it, but every time I try I hit about 50 brick walls before I start moving.

I'm running Ubuntu 9.10 on a Dell Inspiron 1420.

My problems all stem from my apparent inability to install anything at all. I've used the Software Center and the apt-get install command on a number of programs, including VLC, Wine and Java Runtime Environment and all give me the same error: "The following packages have unmet dependencies".

For example:

```
jon@lappy-j86:~$ sudo apt-get install sun-java6-bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  sun-java6-bin: Depends: sun-java6-jre (= 6-15-1) but it is not going to be installed
                 Depends: unixodbc but it is not installable
E: Broken packages
```So, naturally, I should install sun-java6-jre, amarite?

```
jon@lappy-j86:~$ sudo apt-get install sun-java6-jre
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  sun-java6-jre: Depends: java-common (>= 0.24) but it is not installable
                 Depends: sun-java6-bin (= 6-15-1) but it is not going to be installed or
                          ia32-sun-java6-bin (= 6-15-1) but it is not installable
                 Recommends: gsfonts-x11 but it is not installable
E: Broken packages
```Right. So at this point I'm assuming that I'm missing some sort of obvious knowledge about the innards of Linux, but I can't figure it out.

Please, is there any sort of basic explanation as to what is going on? Maybe other users experience this as well? I'm currently reading the little Ubuntu Pocket Guide PDF linked elsewhere on the website, but classes start tomorrow and I'm gonna have a real hard time if I can't run basic things like Wine or JRE.

---

### Post by mick222 on 2010-03-29
You can't install bin files with apt-get use synaptic or
```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```
To install the bin file see here [ http://sites.google.com/site/easylin...IT-UBUNTU-9.10 ]( http://sites.google.com/site/easylin...IT-UBUNTU-9.10 )

---

### Post by drfurly on 2010-03-29
Same gridlock when I use synaptic.

I click the checkbox of *X* and it says there's an unresolved dependency and it requires *Y* so I click on *Y* and it says there's an unresolved dependency and it requires *X*. Even when I select both and once and then click the check box it just lists them one after the other.

```
sun-java6-fonts:
 Depends: sun-java6-jre but it is not going to be installed

sun-java6-bin:
 Depends: sun-java6-jre but it is not going to be installed
 Depends: unixodbc  but it is not installable

sun-java6-jre:
 Depends: java-common (>=0.24) but it is not installable
 Depends: sun-java6-bin but it is not going to be installed or
     ia32-sun-java6-bin (=6-15-1) but it is not installable
 Recommends: gsfonts-x11  but it is not installable
```

I assume I must be doing something wrong, but I'm doing what every guide tells me to do.

---

### Post by Perfect Storm on 2010-03-29
Try first;
```
sudo apt-get update && sudo apt-get upgrade
```

If it doesn't help, we'll need to see your repositories if something is disabled.

---

### Post by garvinrick4 on 2010-03-29
Just try running Code: sudo apt-get install ubuntu-restricted-extras


It has a lot of packages you will need including java, codecs,flash and so on. If some is already installed it will just tell you latest version is installed.

First make sure you do a Code:

sudo apt-get install -f  (to fix any broken packages)

sudo apt-get clean   ( to remove your cache of programs in case you got a bad one or you just keep installing same dud package.)

Now run the ubuntu-restricted-extras

---

### Post by mick222 on 2010-03-29
sry posted in wrong place

---

### Post by drfurly on 2010-03-29
Well, the whole restricted extras thing was pretty entertaining, but didn't solve my problem. Checking the software sources, though, I realized that the box next to Canonical (which is the main package hub, from what I hear) was unchecked. I checked that box, closed the sources and my update manager came up with about 250 updates.

I'mma hit the sack right now while the manager does it's thing, hopefully that's the reason none of this stuff was working, but I'll see in the morning.

---

### Post by garvinrick4 on 2010-03-29
> **drfurly said:**
> Well, the whole restricted extras thing was pretty entertaining, but didn't solve my problem. Checking the software sources, though, I realized that the box next to Canonical (which is the main package hub, from what I hear) was unchecked. I checked that box, closed the sources and my update manager came up with about 250 updates.

I'mma hit the sack right now while the manager does it's thing, hopefully that's the reason none of this stuff was working, but I'll see in the morning. You have to have partners repository installed also to install.

---

### Post by garvinrick4 on 2010-03-29
Looking at it, it just seems you do not have all your repositories installed.

Every 9.10 I have installed, and after loading repositories.

When I sudo apt-get update && sudo apt-get upgrade it would install java.

as artificial intelligence stated in post.

---

### Post by mkvnmtr on 2010-03-29
I found that once I understood software sources and synaptic this linux stuff is kind of easy. You will get used to it and find the same I am sure.

---

