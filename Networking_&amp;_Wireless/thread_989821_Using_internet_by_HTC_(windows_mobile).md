---
title: "Using internet by HTC (windows mobile)"
date: 2008-11-22
forum: Networking &amp; Wireless
---

### Post by brotin on 2008-11-22
Hello everybody,

I'm using HTC P3400, Windows Mobile 6.1. I want to use internet in Ubuntu by this PDA Phone. Please help me out, how i'll use internet by windows mobile?:confused:

PLz plz plz help me

---

### Post by superprash2003 on 2008-11-22
do you have a wifi router?

---

### Post by brotin on 2008-11-26
> **superprash2003 said:**
> do you have a wifi router?

I dont have wifi router

---

### Post by Daulat on 2010-02-13
I too have HTC p3400i and thought to have internet on my desktop through it.

Is there anyway for this one?

---

### Post by Sylslay on 2010-02-13
HTC Touch had builid in wifi router.
Is need only whean he want connect more than one komputer.

1st connect with cable that Htc, and check for it by 
lsub.
2nd if you will able to copy picture form yours phone by F-Spot, that meant that proper drivers for phone are in linux kernel.

Now
Setup Internet connection:
For phones has to use dialer like ppp-gnome dialaer or wvdial or kppp

code: sudo apt-get install gnome-ppp

and get setings from gsm network and wrote them in config file , like 

[http://ubuntuforums.org/showthread.php?t=1027453](http://ubuntuforums.org/showthread.php?t=1027453)

---

### Post by saidinesh5 on 2010-02-13
i did use internet like that using a HTC S710, hope the same thing works for you.

1)simply connect the phone to pc via. the usb cable
2)on phone, goto "internet connection sharing" , in that, simply select the access point you use to browse the internet on your phone, and select the usb and simply press connect

thats it. your PC will be connected to a new network, which is by default connected to internet. your phone will give your PC the IP address too. 

hope this works for you,
good luck :)

---

### Post by Laxman_prodigy on 2010-02-13
I will try this things and report here the results. Thanks as always.:D

---

