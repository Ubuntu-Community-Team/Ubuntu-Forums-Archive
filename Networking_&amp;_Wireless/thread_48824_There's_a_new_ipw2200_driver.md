---
title: "There's a new ipw2200 driver"
date: 2005-07-14
forum: Networking &amp; Wireless
---

### Post by matthew on 2005-07-14
Anyone tried it yet? I have 1.0.4 installed and it's working beautifully, but [this site](http://ipw2200.sourceforge.net/)  says there is now a 1.0.6 driver out. Has anyone given it a test drive yet? Is it worth the upgrade?

---

### Post by matthew on 2005-07-14
**bump**

Anyone??

---

### Post by ape on 2005-07-15
After I saw your initial post last night, I downloaded and installed them.  Seem to work just fine here.  I'm not doing WPA or anything, but basic WEP works.

---

### Post by matthew on 2005-07-15
Thanks, ape.

I am using wpa with the 1.0.4 driver and wpa_supplicant and all is good with the world...I don't want to make any change unless there is some new functionality involved. 

Have you (or anyone else) noticed any new bells or whistles?

---

### Post by ape on 2005-07-15
I had looked through the changelog for 1.0.6 and although all of the fixes sound great, I really wasn't experiencing any of the problems listed. :)   So, not anything new that I notice.

I still plan on getting WPA set up sometime.  Any gotchas?

---

### Post by matthew on 2005-07-15
I set it up using the howto detailed [here](http://www.ubuntuforums.org/showthread.php?t=26623). Follow the steps carefully and you should have no problem getting wpa to work. Luca is really the wpa/ipw2200 guru around here. I was hoping he had a chance to play with the new driver and would comment if he had time.

---

### Post by jaac on 2005-07-16
I tried to compiled the new drivers but it says that can't find ieee*.h :(

Any ideias?

---

### Post by ape on 2005-07-17
Jaac,

  You also need to download the new ieee* subsystem from the link shown on the page where you got the 1.0.6 drivers from.  It is no longer packaged with the ipw2200 drivers.  Once you've downloaded these ieee* drivers, built them and followed the instructions in the INSTALL file explicitly, the new 1.0.6 ipw2200 drivers will build and run fine.

---

### Post by odin on 2005-07-18
I downloaded the ieee* subsytem and follow the instructions but ones i deleted the old versions of the modules and i try the make command then it says that i dont have the build directory.In the installations instructions says that if you dont have that directory or it is empty then I need to install the kernel source packages for my distribution.

Can anyone tell what that is and how should I do it?

Thank's

---

### Post by luca_linux on 2005-07-18
Sorry but I've been very busy in these last days. But now I'm here.
I'll update my HowTo soon, probably by tomorrow.
Yeah, there're great and many improvements (especially about hwcrypto, packet fragmentation, monitor mode, bug fixes and so on) in the new version (1.0.6) and as said, ieee80211 is not built in anymore.

---

### Post by matthew on 2005-07-18
I just used luca's updated [HowTo](http://ubuntuforums.org/showthread.php?t=26623&page=1&pp=10)  and the new drivers work great.

---

### Post by odin on 2005-07-19
I also followed that HowTo but it doesnt work and dont know exactly why because everything is where it should be(I think)

For example when execute make for ieee80211-1.0.3 i get this warning:
 
"could not find versions for .tmp_versions/ieee80211.mod"
of course trying make install I get the same warning.And the same when execute the make for ipw2200-1.0.6.I get a warning saying that it couldn find versions for .tmp_versions/ieee80211.mod and for .tmp_versions/ipw2200.mod

I really dont have any idea of what this may be so If anyone can help explain it slowly  ;-)

thank's

---

### Post by luca_linux on 2005-07-19
Have you run the remove-old scripts?

---

### Post by odin on 2005-07-19
Yes I did and about some of the files it said something like the system cuoldnt find them or couldnt delete them.But i was trying it with warty and i dont know if it has something to do with that but now I just update the system to hoary and I gonna try again with the whole process and i'll post the result later,just in case anyone has time to see it.

Thank's

---

### Post by luca_linux on 2005-07-19
Ok, I'll wait for your post. Let me know.

---

### Post by odin on 2005-07-19
ok now everything is working perfectly.The problem was that I dont know why the remove-old didnt remove one of the old files and i did manually and later when i execute make in ipw2200 didnt work because it couldnt find ieee80211.h

I just type make IEEE80211_INC=the/path/where/ieee80211.h/was (I dont know exactly what this is and why I needed to do this) and now everything is working perfectly.




thank u very much for your attention.

ciao

---

### Post by luca_linux on 2005-07-19
Ok, I'm happy you've solved.

Cheers,
Luca

---

