---
title: "VirtualBox installation problem on 8.10"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by frontiersman on 2008-12-08
I have installed Ubuntu Server edition 8.10 on my machine and have tried to install virtualbox with apt-get.  The installation produces an error "No suitable module for running kernel found."  
I tried reinstalling virtualbox with the same error.  Any help would be much appreciated.

-----------------
root@homer:~# apt-get --reinstall install virtualbox
Reading package lists... Done
Building dependency tree
Reading state information... Done
Note, selecting virtualbox-ose instead of virtualbox
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 26 not upgraded.
Need to get 0B/6285kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 36174 files and directories currently installed.)
Preparing to replace virtualbox-ose 2.0.4-dfsg-0ubuntu1 (using .../virtualbox-ose_2.0.4-dfsg-0ubuntu1_i386.deb) ...
Shutting down VirtualBox host networking ...done.
 * Stopping VirtualBox kernel module vboxdrv                             [ OK ]
Unpacking replacement virtualbox-ose ...
Setting up virtualbox-ose (2.0.4-dfsg-0ubuntu1) ...
Starting VirtualBox host networking * Starting VirtualBox kernel module vboxdrv 
 * No suitable module for running kernel found.

-----------------------------------

---

### Post by lovelyvik293 on 2008-12-08
You have to install the vboxdrv kernel from the synaptic.
Search vboxdrv in synaptic.

---

### Post by scorp123 on 2008-12-08
> **lovelyvik293 said:**
> You have to install the vboxdrv kernel from the synaptic.
Search vboxdrv in synaptic. This is not a guessing contest or a TV quiz, OK? ):P

---

### Post by scorp123 on 2008-12-08
> **frontiersman said:**
> "No suitable module for running kernel found." Can you please open a terminal:
[INDENT]Applications > Accessories > Terminal[/INDENT]

Normally the VirtualBox driver should have been activated automagically ... I wonder why it did not do it in your case?

As for manually getting the driver to work: Into that open terminal please type these commands exactly as shown (copy & paste): 
```
sudo /etc/init.d/vboxdrv setup
``` ... this should activate the driver. BTW: when it asks for a password ... that's your password! And there will not be any sorts of visual feedback. No stars. No question marks. No dots .... You have to type your password blindly and then just hit the enter key, OK?

Also ... just out of curiosity. Can you please give me the output of this command: ```
dpkg -l build-essential
``` .. Ideally the answer should look like this: ```
ii  build-essential  11.4 
``` ... "ii" means the package is installed. 

If my suspicion is right you didn't install that package and hence VirtualBox might have trouble to compile a driver appropriate for your kernel. If it is not installed and VirtualBox still complains, try these commands: 
```

sudo apt-get install build-essential
sudo /etc/init.d/vboxdrv setup
```  ... that should fix it.

---

### Post by frontiersman on 2008-12-08
Thanks for the info, but I don't have x11 or synaptic on this machine as I intend to run it headless.  I cannot find any packages matching vboxdrv in apt.

root@homer:~# apt-cache search vboxdrv
root@homer:~#

---

### Post by lovelyvik293 on 2008-12-08
@scorp123 Yes it's not a TV show but you told the same thing ..
vboxdrv is needed.

---

### Post by scorp123 on 2008-12-08
> **frontiersman said:**
> I cannot find any packages matching vboxdrv in apt.

root@homer:~# apt-cache search vboxdrv
root@homer:~# Of course not. Such a package doesn't exist. He posted his "helpful" suggestion without bothering to check if what he is posting is even right. Yes, he or she tried to help. OK. So far so good. But posting incorrect stuff isn't helping anyone. Hence my comment above ...

---

### Post by scorp123 on 2008-12-08
> **lovelyvik293 said:**
> @scorp123 Yes it's not a TV show but you told the same thing ..
vboxdrv is needed. There is a galaxy of a difference between saying "vboxdrv is needed" and between saying "go search in synaptic". ):P

You posted something and didn't even bother to check if what you are posting is even correct. tss tss tss ....

---

### Post by lovelyvik293 on 2008-12-08
> **scorp123 said:**
> Of course not. Such a package doesn't exist. He posted his "helpful" suggestion without bothering to check if what he is posting is even right. Yes, he or she tried to help. OK. So far so good. But posting incorrect stuff isn't helping anyone. Hence my comment above ...

Sorry for my "vboxdrv is needed".I am newbie here.
By searching in synaptic i got the package 
virtualbox-ose-modules--2.6.24
So i wrote that.

---

### Post by frontiersman on 2008-12-08
Thanks scorp123,
Build-essential was not installed.
```
root@homer:~# dpkg -l build-essential
No packages found matching build-essential.
```

I installed it.

```
root@homer:~# dpkg -l build-essential
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  build-essentia 11.4           Informational list of build-essential packag

```

However, vboxdrv setup is not an option.
```
root@homer:~# /etc/init.d/vboxdrv setup
 * Usage: /etc/init.d/vboxdrv {start|stop|restart|status}

```

I tired vboxdrv start, also to no avail.

```
root@homer:~# /etc/init.d/vboxdrv start
 * Starting VirtualBox kernel module vboxdrv
 * No suitable module for running kernel found.

```

any other suggestions?

---

### Post by scorp123 on 2008-12-08
> **lovelyvik293 said:**
> By searching in synaptic i got the package 
virtualbox-ose-modules--2.6.24 Yes, but please: Open a terminal and try your own suggestion: ```
apt-cache search vboxdrv
``` ... you will not get any results from that, unfortunately.

Correct it would have to be something like ... ```
apt-cache search virtualbox*
``` ... that would give plenty of results.

---

### Post by jimv on 2008-12-08
You can download it here:

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

The nice part of this version is that A) it support fake SATA and USB and B) if you update to a new kernel, it will give you a command to run that will recompile the VBox kernel modules.

EDIT

I just noticed that the site I posted has a repo listed.  Just follow the instructions to add the respository, then use apt-get to install "virtualbox-2.0".  This version will automatically update the kernel modules when you upgrade your kernel.

---

### Post by ajwak95 on 2008-12-08
do sudo apt-get update, then go to virtualbox.com and download the VirtualBox .DEB file. And that should solve your issues.

---

### Post by scorp123 on 2008-12-08
> **frontiersman said:**
> However, vboxdrv setup is not an option. OK .... now I am confused. Is that the "OSE" version? I would not have expected it to be so different from the "PUEL" version.

Try the package "lovely" found .... looks like that might do the job. .... I hope ...

---

### Post by lovelyvik293 on 2008-12-08
Now it's funny.
please use
```
 apt-get install virtualbox-ose-modules-2.6.24-21-generic
```
@scorp123 thanks for telling me new thing(to double check each thing prior to post)

---

### Post by scorp123 on 2008-12-08
> **jimv said:**
> You can download it here:

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) I'd go with the SUN repo ... this has the nice side effect that whenever there is a new version you will automatically be notified.

Open an editor and save what follows into this file:
** /etc/apt/sources.list.d/virtualbox.list **

Possible commands to do that:
```
Terminal:
sudo vim /etc/apt/sources.list.d/virtualbox.list

Gnome:
gksudo gedit /etc/apt/sources.list.d/virtualbox.list

KDE:
kdesu kate /etc/apt/sources.list.d/virtualbox.list
```

Put this into that file:
```
 deb http://download.virtualbox.org/virtualbox/debian intrepid non-free 
```

Then you have to get SUN's keys:
```
wget -q http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc -O- | sudo apt-key add -
```

Update your repos:
```
sudo apt-get update
```

Install VirtualBox 2.1 (exact version as of this writing: 2.1.0-41146):
```
sudo apt-get install virtualbox-2.1
```

... voila.

.
.
.
.

---

### Post by frontiersman on 2008-12-08
Thanks very much. That works.  
Adding the repository:

```
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) intrepid non-free
```

and, 

```
apt-get install virtualbox-2.0
```


fixed the problem.  Many thanks again to all who posted contributions to the problem.
The Open source community rules! :)

---

### Post by scorp123 on 2008-12-08
> **frontiersman said:**
>  Adding the repository ... fixed the problem. In case it breaks again (e.g. after a kernel update? could happen ...) you can execute the command that I posted earlier: ```
sudo /etc/init.d/vboxdrv setup 
```  ... the command does not work with the "OSE" version of VirtualBox, but it definitely works with SUN's "xVM VirtualBox" which you now have from the repos. Example from my own installation here:

```
 > /etc/init.d/vboxdrv help
Usage: /etc/init.d/vboxdrv {start|stop|stop_vms|restart|force-reload|status|**setup**} 
```  As you can see, the non-OSS version understands the "setup" command.

My apologies then regarding the previous misunderstanding ;)

):P

---

### Post by scorp123 on 2008-12-09
> **lovelyvik293 said:**
> ```
 apt-get install virtualbox-ose-modules-2.6.24-21-generic
``` Above package is obviously for Linux Kernel 2.6.24 ... and that was in Hardy (Ubuntu 8.04) .... Ubuntu 8.10 "Intrepid" uses  2.6.27!  And OP has already stated that he is running Ubuntu 8.10. So your instructions would again not function on "Intrepid".

> **lovelyvik293 said:**
>  @scorp123 thanks for telling me new thing(to double check each thing prior to post) Yes, please do that in the future. ):P

---

### Post by skajotde on 2008-12-15
> **frontiersman said:**
> 
```
apt-get install virtualbox-2.0
```


fixed the problem.  Many thanks again to all who posted contributions to the problem.
The Open source community rules! :)

Is there solution for *-ose version ? (free for developer at job which need a few Windows features ;) )

---

### Post by scorp123 on 2008-12-17
> **skajotde said:**
> Is there solution for *-ose version ? (free for developer at job which need a few Windows features ;) ) I never used that one, sorry.

But why not use Sun's xVM VirtualBox? It's free to for "personal evaluation", and according to Sun's own lax definitions (and intentionally so!) this may mean anything for as long as it means that one single human is using one single instance of VirtualBox on one single computer. I guess that "programming and testing software" is covered under "personal evaluation" too.

---

