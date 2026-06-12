---
title: "Gnome-Do looks kinda funny...=/"
date: 2010-01-25
forum: New to Ubuntu
---

### Post by kamitsukai on 2010-01-25
For some reason I get oblong shadows appearing on all four sides of gnome-do (screenshot included below) anyone tell me how I can get rid of them?

  I installed Gnome-Do from the stable ppa and I'm currently running Kubuntu 9.10 (well Linux Mint 8 KDE Community Edition...)

thanks in advance!

---

### Post by clive littlewood on 2010-01-25
Hi

Maybe because Gnome-Do is a GNOME app !!!!

Pehaps somebody running KDE can help.

Clive

---

### Post by SuperSonic4 on 2010-01-25
Why would you want gnome-do? From the screenshot it looks like KRunner (Alt+F2 krunner)

Although I've no idea what it's meant to do. Perhaps someone more familiar with gnome can tell me XD

---

### Post by lykwydchykyn on 2010-01-25
I just tried installing gnome-do on my Kubuntu box and I don't see anything like that.

Is compositing enabled in KDE?
Do you have an old gnome-do configuration in your home directory that might have incompatible settings?
Have you tried running Gnome-do under other window managers or desktop environments on this machine to see if it does it there?

---

### Post by kamitsukai on 2010-01-25
> **clive littlewood said:**
> Hi

Maybe because Gnome-Do is a GNOME app !!!!

Pehaps somebody running KDE can help.

Clive

just because it's a app which has gnome dependencies doesent mean it won't run properly in a KDE desktop;)

and yes kwin is enabled i'll disable it and see how it goes...

---

### Post by kamitsukai on 2010-01-25
turned of kwin and it told me that certain features wre incompatible because compositing was off...

---

### Post by lykwydchykyn on 2010-01-25
> **kamitsukai said:**
> turned of kwin and it told me that certain features wre incompatible because compositing was off...

Naturally, but did it fix the gnome-do issue?

What about the other things I asked about?

---

### Post by kamitsukai on 2010-01-25
> **lykwydchykyn said:**
> Naturally, but did it fix the gnome-do issue?

What about the other things I asked about?

sorry yer the problem was fixed I'll see if I can post a bug report on gnome-do

and there's no old config files and I have previously run gnome-do on ubuntu 9.10 on the same laptop =]

---

### Post by KhaaL on 2010-02-22
Hi

this looks like this bug: [https://bugs.launchpad.net/do/+bug/351324](https://bugs.launchpad.net/do/+bug/351324)

I'm running KDE 4.4 and am experiencing this bug with gnome do aswell. if you find any remedy please write it in the bugs comments

---

### Post by HalfEmptyHero on 2010-02-22
if you disable shadows in kwin, it will fix it.

---

