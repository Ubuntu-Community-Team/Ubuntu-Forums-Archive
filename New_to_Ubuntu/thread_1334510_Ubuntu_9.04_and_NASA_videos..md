---
title: "Ubuntu 9.04 and NASA videos."
date: 2009-11-22
forum: New to Ubuntu
---

### Post by bob brazie on 2009-11-22
Ubuntu 9.04 and NASA videos.

I cannot view any videos at NASA.gov.

I am assuming this will happen at other sites too.

It searches for suitable plugin but finds none. MMS plugin needed?

How can I view these files in Firefox?

Thanks in advance. Bob.

---

### Post by qwerty2009 on 2009-11-22
> **bob brazie said:**
> Ubuntu 9.04 and NASA videos.

I cannot view any videos at NASA.gov.

I am assuming this will happen at other sites too.

It searches for suitable plugin but finds none. MMS plugin needed?

How can I view these files in Firefox?

Thanks in advance. Bob.
Have you installed ubuntu restricted extras? if not install from software center or add and remove if your still using jaunty :P

---

### Post by cariboo on 2009-11-22
I would also suggest installing the w32codecs or w64codecs and the non-free codecs, depending on what version you are using from the [Medibuntu]("http:///www.medibuntu.org/") repositories.

---

### Post by bob brazie on 2009-11-22
> **qwerty2009 said:**
> Have you installed ubuntu restricted extras? if not install from software center or add and remove if your still using jaunty :P


Not sure where the software center is. I did follow the instructions here: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) which added the right things I thought.

I am using 9.04 and don't understand what/where your suggestion to remove means. <g>

Remember this is the absolute beginer talk forum. <g>

Thnaks, Bob.

---

### Post by chaanakya_chiraag on 2009-11-22
He meant the "Add/Remove Software" Menu item under Applications in the top-left corner.

---

### Post by bob brazie on 2009-11-22
I did that but still can't view the NASA site videos in Firefox.

Should I do the steps again?

BTW: I was wondering in the line: sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs)

Should I change the "release" to Jaunty. Or is that thinking too much? <g>

---

### Post by bob brazie on 2009-11-22
> **chaanakya_chiraag said:**
> He meant the "Add/Remove Software" Menu item under Applications in the top-left corner.

I thought so but what do I look for and choose to install?

Thanks, Bob.

---

### Post by chaanakya_chiraag on 2009-11-22
Personally, I like to use the following command:
```
sudo aptitude install <package>
```
Open up a terminal (Applications->Accessories->Terminal) and enter the following command:
```
sudo aptitude install w32codecs
```
and see if it works.

---

### Post by bob brazie on 2009-11-22
Dose this output look correct? I am not sure about what/why things were removed and if anything was installed.


bob@bob-laptop:~$ sudo aptitude install w32codecs
[sudo] password for bob: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
The following packages will be REMOVED:
  linux-headers-2.6.28-11{u} linux-headers-2.6.28-11-generic{u} 
0 packages upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 74.7MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 137782 files and directories currently installed.)
Removing linux-headers-2.6.28-11-generic ...
Removing linux-headers-2.6.28-11 ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

---

### Post by oldos2er on 2009-11-22
The only way I've been able to view Nasa tv is with Realplayer. You'll need to first set up the Medibuntu repository to install it: [http://medibuntu.org/](http://medibuntu.org/)

---

### Post by bob brazie on 2009-11-22
And then what would the install command be for Realplayer?

---

### Post by asuastrophysics on 2009-11-22
> **bob brazie said:**
> And then what would the install command be for Realplayer?

Go to Applications -> Accessories -> Terminal

And type this in:

```
sudo apt-get install realplayer
```

*******make sure you have added the medibuntu repository in "software services" first, or you might get a message saying "couldn't find realplayer..."*****

---

### Post by bob brazie on 2009-11-22
Thanks, that worked but I still don't understand why it won't load and play in the Firefox window it is intended to be viewed in.

Can anyone explain why?

Thanks, Bob.

---

### Post by chaanakya_chiraag on 2009-11-22
Hmmmm...
That's strange, because it worked OOTB for me.  I'm at a loss...

---

### Post by asuastrophysics on 2009-11-22
> **bob brazie said:**
> Thanks, that worked but I still don't understand why it won't load and play in the Firefox window it is intended to be viewed in.

Can anyone explain why?

Thanks, Bob.

Because the video format being used by NASA is an exclusive realpayer format.
This means that unless realpayer an *embedded* plugin in your internet browser (like adobe flash), these video files will only launch in realplayer.

Try googling for "ubuntu - realplayer firefox plugin"
that might set you right. let me know how it goes. I'm sure you'll find something. firefox is perhaps the most customisable browser on Earth. 

-Cheers!

---

### Post by JohnnyVW on 2009-11-22
This may be of help:

[https://help.ubuntu.com/community/RealPlayerInstallationMethods?action=show&redirect=RealplayerInstallationMethods](https://help.ubuntu.com/community/RealPlayerInstallationMethods?action=show&redirect=RealplayerInstallationMethods)

---

### Post by bob brazie on 2009-11-23
Real player IS installed.

---

### Post by oldos2er on 2009-11-23
Here's an older thread on the same subject: [http://ubuntuforums.org/showthread.php?t=693945](http://ubuntuforums.org/showthread.php?t=693945)

---

