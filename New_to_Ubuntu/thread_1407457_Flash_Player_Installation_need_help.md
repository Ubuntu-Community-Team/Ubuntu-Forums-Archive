---
title: "Flash Player Installation need help"
date: 2010-02-15
forum: New to Ubuntu
---

### Post by nk212 on 2010-02-15
hello.

I am a new user of Ubuntu, I am trying to install flash player for mozilla by 
sudo apt-get install adobe-flashplugin

but i am getting the following error;
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package adobe-flashplugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package adobe-flashplugin has no installation candidate

What should i do?

---

### Post by luckydeveloper on 2010-02-15
Why dont you go to the adobe site directly and install the flash plugin for your mozilla firefox. Here is the link, give it a try [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

---

### Post by nk212 on 2010-02-15
Thank you for your reply, I tried from the website firefox prompted me that were some missing plugins including flash player when i clicked on it to install it said it is already installed but i still cant use it.

thankyou.

---

### Post by luckydeveloper on 2010-02-15
try restarting your firefox and then see. 

If you still get problems, download the flash player deb file from the link I gave earlier and install it. It will work

---

### Post by nk212 on 2010-02-15
How do i Run the .deb file?

---

### Post by luckydeveloper on 2010-02-15
double click it :) simple. Please close firefox before you double click that deb file. And please make this thread 'Solved' after your problem is solved :):popcorn:

---

### Post by nk212 on 2010-02-15
i double clicked the file and it says that 
Error: Conflicts with the installed package 'flashplugin-installer'

---

### Post by luckydeveloper on 2010-02-15
ok, Go to Application -> Accessories -> Terminal


And type

sudo apt-get remove adobe-flashplugin


then
close Firefox
double click the deb file

---

### Post by nk212 on 2010-02-15
this time it says:

Reading package lists... Done Building dependency tree        Reading state information... Done Package adobe-flashplugin is not installed, so not removed 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by buster2 on 2010-02-15
have you tried the software centre ?

---

### Post by luckydeveloper on 2010-02-15
> **nk212 said:**
> this time it says:

Reading package lists... Done Building dependency tree        Reading state information... Done Package adobe-flashplugin is not installed, so not removed 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Flash plugin installation in ubuntu is so damn easy and I don't know why this is a problem in your case. Anyways we can sort that out.

Open a terminal and type

sudo apt-get remove flashplugin-installer  

and Press Enter

then type

sudo apt-get install flashplugin-nonfree  

and press Enter

---

### Post by nk212 on 2010-02-15
No i didnt thankyou i think i can make it work now
Thanks buster

---

### Post by nk212 on 2010-02-15
on the other hand it didnt work

---

### Post by Soul-Sing on 2010-02-15
Not running a 64bit version of ubuntu?

---

### Post by linuxadore on 2010-02-15
flashplayer 10 don't work 4 me, flashplayer 9 from Synaptic also. I find solution to migrate to flashplayer9. [B]Here is step-by-step tutorial on my blog. 
[http://my.opera.com/linuxadore/blog/old-flashplayer9-installing-from-source-in-ubuntu-hardy-8-04](http://my.opera.com/linuxadore/blog/old-flashplayer9-installing-from-source-in-ubuntu-hardy-8-04)[/B]

NOTE: Open Synaptic first, click Search, type flash, hit enter, mark 4 completely removal flash packages. flash-installer not exist in repos, just flashplugin-nonfree!

---

### Post by lovinglinux on 2010-02-15
For 32bit see [this](http://lovinglinux.megabyet.net/?page_id=220#Removing-Conflicting-Plugins-2).

For 64bit see [this](http://ubuntuforums.org/showthread.php?t=1358591).

---

