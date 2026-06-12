---
title: "[SOLVED] Broadcom wireless card problems"
date: 2008-11-13
forum: Networking &amp; Wireless
---

### Post by Marius Derekus on 2008-11-13
Hello,

I have installed Ubuntu 8.04 on an acer extensa 4420-5963 laptop with windows vista installed. For some reason i cant get wireless internet to work on ubuntu at all. I don't know if it is because my driver is not compatibe. It seems as if perhaps ubuntu does not recognize my Broadcom wireless card, but i don't even know how to check if it recognizes it or not. **ANY help will do.**

p.s. I don't have any internet on Ubuntu so please do NOT have me do any **sudo apt-get install** commands. However, i do have internet on vista, so if there are any packages i must install i can still install them via **packages.ubuntu.com** or any other repository i am directed to.  Forgive me for the hassle.



Note:If there is another thread that answers my questions, please direct me to it.

---

### Post by buccaneere on 2008-11-13
Can you get Ubuntu on wired connection?

[http://ubuntuforums.org/archive/index.php/t-879296.html](http://ubuntuforums.org/archive/index.php/t-879296.html)

Looks like a BCM 4310 card (or 4312).

Try this:

Load Ubuntu, go to system/administration/hardware drivers

See if your proprietary drivers are listed for BCM card, and enable them.

---

### Post by Marius Derekus on 2008-11-14
Thanx for the help, I'll check that out immediately.

---

### Post by Marius Derekus on 2008-11-14
Oh by the way, before i check that out, you are right. It is a bcm4312. now i'll check out the rest of what you said.
I probably could get wired connection on ubuntu if i had the acces to a wired connection which i don't.
I also (be prepared, your jaws may drop) don't have Make. I am trying to see if make will work through the version they give me via **packages.ubuntu.com**, though i recall having errors on another computer.
What you have shown appears as if it would probably solve the problem (On the forum you directed me to was another link to another forum which led to certain drivers that would probably solve the problem), but as metioned earlier, i need to somehow install Make. **Thank you very much and please continue to help.** ****

---

### Post by Marius Derekus on 2008-11-14
**YES! YES! YES! YES! YES! YES!** You are a life saver buccaneere. I looked, and Make was already installed. When i tried what was said on the forum you gave me, it worked! I could never thank you enough, i've tried making this work for months and no attempt worked, i almost gave up on ubuntu and uninstalled it. Once again. **THANK YOU!**

---

### Post by Marius Derekus on 2008-11-14
:)

---

### Post by Marius Derekus on 2008-11-14
if you are having the same problem then download this driver (make sure to get the README as well.) [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

I had to add these commands to the file /etc/rb.local. Here are the commands:

**sudo modprobe ieee80211_crypt_tkip** *You may not need to add this one. Add this command if the one below doesn't* work. 
**sudo insmod *pathname*/wl.ko** *This is the important command. If you add the above command, don't delete this one.* 

Yes, these are the commands on the README. I had to add these to rb.local because everytime I booted ubuntu up, I would always have to retype those commands on console in order for wireless internet to work. When i add these commands to rc.local, it automatically runs these commands when i boot up ubuntu, making wireless internet up and running without needing to touch console.

**note: If you need help just ask, i will continue to keep an eye on this post.**

Also, the website says it is made for BCM4311-, BCM4312-, BCM4321-, and BCM4322-based hardware. If you have a wireless card such as the BCM4318, I do not know if it will work. You can always try it out but i wouldn't edit rc.local unless your sure the driver works.

---

