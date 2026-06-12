---
title: "web browser problems"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by hellyea on 2009-04-25
I just installed ubuntu 8.10 and am having problems with firefox.  It has problems loading any web page with the exception of google. I have tried disabling IPv6 with no result.  Also I have tried to install epiphany, opera, and iceweasel but have the same problem with all of them.  When using the command sudo apt-get install epiphany it gives me an error that says "E: Package epiphany has no installation candidate" 

what am I doing wrong?!!? please be specific in any resolutions and commands to be used as I am very new to ubuntu. Thanks!

---

### Post by Sef on 2009-04-25
Applications > Accessories > Terminal

Type a browser name in there and what errors does it give you?

---

### Post by Seks on 2009-04-25
that won't install epiphany because the package is actually called "epiphany-browser" (epiphany must be something else)

the other thing sounds like a DNS issue, you could try using [openDNS]("https://www.opendns.com/start/device/ubuntu")

---

### Post by s.fox on 2009-04-25
> **hellyea said:**
> Also I have tried to install epiphany, opera, and iceweasel but have the same problem with all of them.  When using the command sudo apt-get install epiphany it gives me an error that says "E: Package epiphany has no installation candidate" 

what am I doing wrong?!!? please be specific in any resolutions and commands to be used as I am very new to ubuntu. Thanks!

Hi, 

It sounds like a problem with your sources list.  Can you run this command in Terminal:

```
gedit /etc/apt/sources.list
```

Please post the content of the file :) 

-Ash R

---

### Post by hellyea on 2009-04-25
hi thanks for everybody replying so quickly I am trying these things but as I cannot use firefox right now I am switching between ubuntu and windows so it is taking some time.  I tried typing epiphany and here is what it gave me:

The program 'epiphany' is currently not installed. You can install it by typing: sudo apt-get install epiphany-browser
bash:epiphany: command not found.

however when I try that command I get the same result:
E: package epiphany-browser has no installation candidate

ASH R I will be trying your suggestion next and will be replying momentarily

---

### Post by hellyea on 2009-04-25
this is what I get when I run gedit /etc/apt/sources.list

	 	 #deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted  
 # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to  
 # newer versions of the distribution.  
 

 deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid main restricted  
 deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid main restricted  
 

 ## Major bug fix updates produced after the final release of the  
 ## distribution.  
 deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted 
 deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted 
 

 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu  
 ## team. Also, please note that software in universe WILL NOT receive any  
 ## review or updates from the Ubuntu security team.  
 deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid universe  
 deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid universe  
 deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-updates universe  
 deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-updates universe  
 

 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu  
 ## team, and may not be under a free licence. Please satisfy yourself as to  
 ## your rights to use the software. Also, please note that software in  
 ## multiverse WILL NOT receive any review or updates from the Ubuntu  
 ## security team.  
 deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid multiverse  
 deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid multiverse  
 deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse  
 deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse  
 

 ## Uncomment the following two lines to add software from the 'backports'  
 ## repository.  
 ## N.B. software from this repository may not have been tested as  
 ## extensively as that contained in the main release, although it includes  
 ## newer versions of some applications which may provide useful features.  
 ## Also, please note that software in backports WILL NOT receive any review  
 ## or updates from the Ubuntu security team.  
 # deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse  
 # deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse  
 

 ## Uncomment the following two lines to add software from Canonical's  
 ## 'partner' repository. This software is not part of Ubuntu, but is  
 ## offered by Canonical and the respective vendors as a service to Ubuntu  
 ## users.  
 # deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner  
 # deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner  
   
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted  
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted  
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe  
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe  
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse  
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse

---

### Post by kansasnoob on 2009-04-25
> **Ash R said:**
> Hi, 

It sounds like a problem with your sources list.  Can you run this command in Terminal:

```
gedit /etc/apt/sources.list
```

Please post the content of the file :) 

-Ash R

You mean:

```
cat /etc/apt/sources.list
```

You would run "sudo gedit /etc/apt/sources.list" only if you intended to edit the list.

---

### Post by kansasnoob on 2009-04-25
Well, it would be advisable to uncomment the partner repos:

> ## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner 

Which is to say change the last two lines so they look like this:

> deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

You simply remove the # from in front of the line .......... or just go to System > Administration > Software Sources and "tick" on the third Party tab then check the Partner Repo.

But that's not going to solve your problem.

edit: Oops, meant to add refer to Sef's post!

---

### Post by hellyea on 2009-04-25
I tried to run the opendns deal but when I opened gksudo gedit /etc/dhcp3/dhclient.conf it opened a blank page and then would not allow me to save the document. Also I ticked the options in the the third party tab and it still will not allow me to run sudo apt-get install epiphany-browser

---

### Post by Noel96 on 2009-04-25
Have you tried uninstalling Firefox using synaptic package manager and then reinstalling it? (I don't think I read any reference to this in the above posts, but if I'm suggesting something that has already been stated/done, please ignore me.)

---

### Post by hellyea on 2009-04-25
if I uninstall do I need a disc to reinstall it or do I use the sudo command?

---

