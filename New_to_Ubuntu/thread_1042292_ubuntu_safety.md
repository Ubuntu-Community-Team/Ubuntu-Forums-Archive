---
title: "ubuntu safety"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by downloadfreak on 2009-01-17
Hello,

I was just wondering. Is it treu that ubuntu (and linux in general) is very safe from virusses, spyware, hackers etc.?
And is there any way to increase the safety instead of doing nothing (that's what I'm doing now)

---

### Post by zzHanks on 2009-01-17
Hi 

[This]("http://www.psychocats.net/ubuntu/security") link might answer some of your questions.

---

### Post by earthpigg on 2009-01-17
> **downloadfreak said:**
> Hello,

I was just wondering. Is it treu that ubuntu (and linux in general) is very safe from virusses, spyware, hackers etc.?
And is there any way to increase the safety instead of doing nothing (that's what I'm doing now)

most people here dont bother with an antivirus or software firewall.

zero linux viruses exist 'in the wild'.

some browser-specific (firefox) or office specific malware (ms office malware scripts that work in openoffice.org) exists.... but can't ruin your system to the point that you cant simply boot, uninstall and --purge OO.o or firefox and reinstall:

```
sudo apt-get remove firefox --purge
```

if i am mistaken in any of that, someone please correct me ;)



also, many windows malware/viruses 'work' in WINE.... which means it can ruin your WINE install, but nothing else.

---

### Post by mjheagle8 on 2009-01-17
almost all viruses target windows, which as earthpigg said, can only damage your wine installation.  you need to take some security measures however bc no computer is completely safe from hackers. just exercise judgement when on the internet.

---

### Post by jrusso2 on 2009-01-17
One of the main ways Linux gets hacked is not by virus but by people getting into your SSH login.  So if your running a public facing SSH you need to make sure you use a secure login.

---

### Post by earthpigg on 2009-01-17
> **jrusso2 said:**
> One of the main ways Linux gets hacked is not by virus but by people getting into your SSH login.  So if your running a public facing SSH you need to make sure you use a secure login.

and if you dont know wtf SSH is and you installed ubuntu and manage the system yourself, then you are guaranteed not to be vulnerable to that.

---

### Post by perlluver on 2009-01-17
Have a look at this guide, it should take care of most of you concerns: [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812).

---

### Post by handydan918 on 2009-01-17
> **earthpigg said:**
> and if you dont know wtf SSH is and you installed ubuntu and manage the system yourself, then you are guaranteed not to be vulnerable to that.
This is quite accurate. Only the client side of the SSH package is installed by default, so if you don't know WTF SSH is, you probably haven't installed the server half. 
And it you are behind a router, it really wouldn't matter anyway, unless you arbitrarily opened up port 22 on the router...
 IOW, you have to take some actions to really put yourself at risk.

---

### Post by downloadfreak on 2009-01-17
Many thanks everybody, I have enough information now!

---

### Post by Hendrixski on 2009-01-17
> **downloadfreak said:**
> Many thanks everybody, I have enough information now!

Viruses? They can't hide in Linux because everything is open.  They only seek refuge in dark alleyways and places out of view of the public.

---

