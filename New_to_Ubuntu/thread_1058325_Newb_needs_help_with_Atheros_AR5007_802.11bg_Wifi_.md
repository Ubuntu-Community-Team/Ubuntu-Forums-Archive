---
title: "Newb needs help with Atheros AR5007 802.11b/g Wifi Adapter"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by fortinbras22 on 2009-02-02
Hey Everyone! 
I'm really new to Linux and Ubuntu. I just installed the 32-bt Ubuntu 8.10 on my laptop and for whatever reason I cannot get my Atheros AR5007 802.11b/g Wifi Adapter to so much as even turn on (generally automatic upon Windows login, but there is a button for it, too). Likewise, I cannot detect the wireless network my condo association provides gratis, nor can I get online with firefox...

I really appreciate any help I can get, and although I am reasonably intelligent, please assume that I know nothing. 

Thank you!

---

### Post by shifty_powers on 2009-02-02
you need the linux-backports-module package, bhut for that you need an internet connection.

do you have access to a ethernet based connection?

---

### Post by fortinbras22 on 2009-02-02
Thank you for your reply, shifty_powers. 

Unfortunately I do not have access to an ethernet connection. 

Would it be possible to same the needed files to my flash drive and access it within ubuntu?

Thank you for your help,


F

---

### Post by Crafty Kisses on 2009-02-02
Read this and see if it doesn't help: [http://ubuntuforums.org/showthread.php?t=766529](http://ubuntuforums.org/showthread.php?t=766529).

---

### Post by shifty_powers on 2009-02-02
well you can start with [http://packages.ubuntu.com/intrepid/linux-backports-modules-intrepid](http://packages.ubuntu.com/intrepid/linux-backports-modules-intrepid)

but you would need to satisfy dependecies.... that is a nasty road to go down, seriously. If there is ANY way of getting a temporary internet connection to that pc i would...

---

### Post by benerivo on 2009-02-02
shifty_powers is right, although there shouldn't be many dependancies, so it could be as simple as downloading the correct version for your current kernel version. I don't think trying the generic version would work, as it may just try to download the current version and therefore would require internet access. Check your kernel version with```
uname -r
```and if it is 2.6.27-11 then try [this link]("http://security.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-2.6.27/linux-backports-modules-2.6.27-11-generic_2.6.27-11.12_i386.deb") for a .deb file.

---

### Post by fortinbras22 on 2009-02-02
ok...I will look into these... thank you both

---

### Post by pstrbrc on 2009-02-02
> **shifty_powers said:**
> you need the linux-backports-module package, bhut for that you need an internet connection.

do you have access to a ethernet based connection?

OK, not to hijack, but I do have a broadband connection here in my office, so what do I do to get my atheros ar5007 working on 8.04?

---

### Post by theApokalypsis on 2009-02-02
the backports have spotty support however, the thread CodeName mentioned talks about creating the lastest MadWifi drivers from the lastest is the way to go.

for a simple short Tut to save some reading on the thread check out...

[https://help.ubuntu.com/community/AspireOne#Install%20Ubuntu%20Intrepid%20Ibex%208.10%20on%20the%20Acer%20Aspire%20One](https://help.ubuntu.com/community/AspireOne#Install%20Ubuntu%20Intrepid%20Ibex%208.10%20on%20the%20Acer%20Aspire%20One) 

under the heading "Wireless module" just a little bit down, you can see a short Tut on how to compile and install for 8.10. the aspire one uses the same or very close chipset i believe.

good luck.



EDIT:

pstrbrc: check out that link as well, keep scrolling and their is also a 8.04 install for madwifi and atheros cards as well.

---

