---
title: "Really like ubuntu but whats up with wine?"
date: 2010-01-15
forum: New to Ubuntu
---

### Post by grandamn on 2010-01-15
Ive been using ubuntu and switching back and forth between 8.10 and windows 7. Then windows 7 won and I stayed away from ubuntu for a while. Then I downloaded 9.10 and it is a single boot because I finally got used to all the software and music player and just wanted to say that ubuntu has finally grew on me. It really is great software, not as shinny as windows 7 but it works great.  My question is, i look on-line and some programs a platnium or gold with wine, some dont work at all on the web-page, but when i install wine i have not found a single program that works properly with it. what's up with that? 

I also use virtualbox with windows 7. I have Magic the gathering on-line working through that but the graphics are crappy looking. I tried to install Heroes of Might and Magic V in VB but it dosent work. Is it because of the Direct X 9.0?

---

### Post by Grenage on 2010-01-15
Regardless of WINE rating, it's hit and miss.  Top ratings usually mean it will work, often with fiddling.  I've never had luck with games on a VM, the performance has always been dire.

If you have a Windows license, I would really recommend a dual boot config - you'll save yourself a lot of pain.

---

### Post by marshmallow1304 on 2010-01-15
Try [PlayOnLinux]("apt://playonlinux").  It simplifies installation and tweaking for a decent number of games and applications.

---

### Post by Sir Jasper on 2010-01-15
Hi,

Just in case you may have any wrong setting(s) have a look at the Application settings in your Wine Configuration. Also, especially with Platignum or Gold classifications you might note the version of Wine that was used and compare your version.

My regards

---

### Post by sandyd on 2010-01-15
most of the ratings on the WINEHQ site are done using developmental versions of WINE. (although, to this day, i still dont understand why they dont have the dev versions in the repos with a different name). search on google for "wine deb repository" and youll find it.

---

### Post by Paqman on 2010-01-15
Wine is a bit of a kludge IMO. Very little stuff works well on it, and it just requires more messing about with than I can be bothered with.

Wine is an awesome project and I have huge respect for the people behind it, but the sheer complexity of the task means they're probably never going to get it working 100%.

---

### Post by DarinB on 2010-01-15
i agree wine is a pain and if you like tinkering until you pull your hair out use it.
i say if you have a license for win use it as a dual boot or get another machine just for win. 
when i can i will buy a second box. they are really not that expensive any more for what i need. 
trying to get wine to work is like making a purse out of a sows ear. Not that i have any idea where that saying came from.

---

### Post by jennielf on 2010-01-15
I actually tried to install WoW via Crossover and Wine and preferred Wine. After a bit of fiddling I was able to get WoW to install with full graphics support and sound and everything - The fiddling had less to do with Wine and more to do with my horrible knowledge of Windows file systems.

This is the sole reason I am running Ubuntu at all. I am actually a mac girl and Just wanted a better graphics card system that didn't have Windows that I could play WoW on. (my 24" iMac with 128VRAM was getting a bit long in the tooth) :D

I am very happy with it so far.

---

### Post by scratman on 2010-01-15
Purse out of a sows ear is a biblical quote.

---

### Post by wavery on 2010-01-15
I hate to add to the chorus of dual-booters, but from my limited experience with Wine, you'll save yourself a lot of headaches with a dual-boot system if you have the license.

---

### Post by Sir Jasper on 2010-01-15
Hi,

I use some 25 Windows programs (no games) that work perfectly using Wine.

I just abandoned any Windows programs that did not work immediately.

Portable Windows programs tend to work perfectly, but Wine HQ will rarely mention any of them.

I have a pragmatic view and I am pro ´buntu, but I am not anti Windows. 
Portable Windows programs are easily deleted (or first tried from a USB stick).

My regards 

PS I gave up the Wine Graphics setting ¨Emulate a virtual desktop¨ in favour of Full Screen (though not so listed) which [for me] is significantly better.

---

### Post by DarinB on 2010-01-15
what do you people think of vmware type app to set up win in an ubuntu environment? i don't know enough about it but i wonder if it would solve many problems...can you run win programs in a virtual windows install

---

### Post by JimInLakeland on 2010-01-15
> **grenage said:**
> regardless of wine rating, it's hit and miss.  Top ratings usually mean it will work, often with fiddling.  I've never had luck with games on a vm, the performance has always been dire.

If you have a windows license, i would really recommend a dual boot config - you'll save yourself a lot of pain.

+1

---

### Post by Paqman on 2010-01-16
> **DarinB said:**
> what do you people think of vmware type app to set up win in an ubuntu environment? i don't know enough about it but i wonder if it would solve many problems...can you run win programs in a virtual windows install

Absolutely. You're talking about virtualisation. The open source virtual machine package Virtualbox is available in the repos (although the non-open source version direct from Sun is very popular).

VMs are good for desktop apps, and you can use VBox's "seamless mode" to have them integrate nicely into your Ubuntu desktop. What VMs are _not_ good for is anything requiring 3D graphics acceleration like gaming, or any hefty number crunching. For both of those you'll want to run Windows natively on your actual hardware (ie: dual boot).

---

