---
title: "xorg.conf How to (simple Qs)"
date: 2010-12-29
forum: New to Ubuntu
---

### Post by hollowtd on 2010-12-29
Hi

I'm trying to simply add and edit text in "etc/X11/xorg.conf" When I type this in a terminal I get the gedit document. Where in the world is the "device" section or any other section for that matter? How do I "open" xorg.conf and work within it? Thanks so much!

---

### Post by wojox on 2010-12-29
It looks like this ( I'm on Fedora right now)

```
# RPM Fusion - nvidia-xorg.conf
# 
Section "Device"
	Identifier  "Videocard0"
	Driver      "nvidia"
EndSection
```

Post yours up here.

---

### Post by hollowtd on 2010-12-29
Sorry, what did you type to get that to show up? I'm in 10.10 Ubuntu now. I'm trying to do this: [https://wiki.ubuntu.com/PowerPCFAQ#3D%20video%20drivers,%20Beryl,%20Compiz](https://wiki.ubuntu.com/PowerPCFAQ#3D%20video%20drivers,%20Beryl,%20Compiz) (see 3D, Beryl, Compiz section about half way down).

---

### Post by wojox on 2010-12-29
If you want to edit it then 

```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by hollowtd on 2010-12-29
Thanks for that. I've got the gedit file open. (It's blank and is/looks like a text edit document). Now, where is all the sections? Like the "device" section?

---

### Post by bkratz on 2010-12-29
> **hollowtd said:**
> Thanks for that. I've got the gedit file open. (It's blank and is/looks like a text edit document). Now, where is all the sections? Like the "device" section?

Xorg isn't used in newer Ubuntu versions, that is why you see a blank-- you are creating one. It will use it if done correctly. You might want to look at this.

[http://www.grenage.com/xorg.html](http://www.grenage.com/xorg.html)

and here is a thread about a lot of user doing the same thing

[http://ubuntuforums.org/showthread.php?t=1611769](http://ubuntuforums.org/showthread.php?t=1611769)

---

### Post by hollowtd on 2010-12-29
I'm trying to do this: 3D performance tweak for ATI Radeon cards section of [https://wiki.ubuntu.com/PowerPCFAQ#3D%20video%20drivers,%20Beryl,%20Compiz](https://wiki.ubuntu.com/PowerPCFAQ#3D%20video%20drivers,%20Beryl,%20Compiz)

Seems simple but how can I do it now without xorg?

---

### Post by wojox on 2010-12-29
```
sudo Xorg -configure
```

May still generate a new file. What Video Card/Chip are you using?

```
lspci | grep VGA
```

---

### Post by hollowtd on 2010-12-29
I'm using Radeon Mobility M7 (7500)

When I try to type in compiz --replace I get  

Fatal: software rendering detected
Error: failed to manage screen: 0
Fatal: no manageable screens found on display :0.0

---

