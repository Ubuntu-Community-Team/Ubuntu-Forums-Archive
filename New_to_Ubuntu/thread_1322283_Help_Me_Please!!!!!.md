---
title: "Help Me Please!!!!!"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by sheed3036det@hotmail.com on 2009-11-10
i have ubuntu 9.04 and it will not boot up right. it boots up fine until it get to the screen where you enter user name. When it gets to that screen it comes up with the ubuntu logo with pink and purple lines through it at the top of the screen. I tried to boot up in the terminal. Once i reach the desktop in the terminal i tried to upgrade to ubuntu 9.10 it said it cant upgrade because it cant access locked files. any ideas to try and fix m problem thanks. ps i am new to linux i know at little but just basic commands

---

### Post by monton on 2009-11-10
Have you considered doing a fresh install instead of an upgrade? Do you have files on the drive you need?

---

### Post by doas777 on 2009-11-10
lets try resetting your video settings to default. hit ctrl + alt + F1. does the screen switch to a command line interface?
if so, login by providing username and password. 
then enter this command:
```

sudo service gdm stop
sudo dpkg-reconfigure -p high xserver-xorg
sudo reboot
 
```

---

### Post by theozzlives on 2009-11-10
About the upgrade and locked files, you may have to do:
```
sudo dpkg --configure -a
```

---

### Post by Jeramiah on 2009-11-10
Oh man! That sounds bad. Is a chipset problem maybe? My sisters old computer I rebuilt did the same thing, I thought I hooked something up wrong! But it looks like the Pro's above my post got the right idea! Go Pro Users! Ubuntu powers activate, form of:

TECH SUPPORT! Hahaha!

Nah seriously, Ubuntu's strong community is why it makes the learning curve for Linux so much easier. Cheers guys! :popcorn:

---

### Post by doas777 on 2009-11-10
I have to recommend a clean reinstall if you want to get 9.10. that should address your problem. or if you want to stick with 9.04 then we can work on that. i recomend however, that you get your issue worked out before upgrading, if you want to upgrade rather than reinstall. it can really amplify a problem.

it most likely has nothing to do with your chipset, but could theoretically be a failing vidcard or monitor. it's too early to call it a hardware problem.

the locked files thing isn;t really a problem. a lock just means that the file has been opened for writing. it woudl be bad if 6 programs tried to append the same file at (almost) exactly the same time, so the first app to get it open, locks it. since the files cannot be deleted or overwritten, the updater fails.

---

### Post by sheed3036det@hotmail.com on 2009-11-11
have ubuntu 9.04, Asus M3A78 Pro motherboard, ati chipset when i boot up and it comes up with the login in screen it show the ubuuntu logo at the top with pink and purple lines through it, i cant get to the terminal anymore even in recovery mode(i use to beable to get to the terminal), when i could get in the terminal i tried to do an upadate but it wouldnt let me it said that the files were locked any help is needed to fix this problem please thanks (btw im using a live cd now and i would like trying to avoiding reformatting if possible)

---

### Post by sandyd on 2009-11-11
> **sheed3036det@hotmail.com said:**
> have ubuntu 9.04, Asus M3A78 Pro motherboard, ati chipset when i boot up and it comes up with the login in screen it show the ubuuntu logo at the top with pink and purple lines through it, i cant get to the terminal anymore even in recovery mode(i use to beable to get to the terminal), when i could get in the terminal i tried to do an upadate but it wouldnt let me it said that the files were locked any help is needed to fix this problem please thanks (btw im using a live cd now and i would like trying to avoiding reformatting if possible)
the mesed up login screen is most likely due to a driver problem

when you get to the messed up login screen, press alt+f1

login with your username and password.
then run this (you **might** wanna write this down since its not gonna be in front of you when your doing this)
```

sudo apt-get update && sudo apt-get install envyng-core
sudo envyng -t

```
select the ATI driver and follow the rest of the instructions.

---

### Post by overdrank on 2009-11-11
Please do not create multiple threads on the same issue. Threads merged.

---

