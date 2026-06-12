---
title: "Changing dual boot order in 9.10"
date: 2010-04-15
forum: New to Ubuntu
---

### Post by archkidd on 2010-04-15
I have installed ubuntu 9.1 wirh XP Pro and when the dual boot menu comes up XP is first and highlighted and ubuntu second.  I want to reverse that but everything I find about how to do it uses the menu.lst file and my installation does not have a menu.lst file!   Is 9.10 different or am I doing something wrong?

---

### Post by ed-koala on 2010-04-15
The file you need to edit is /etc/default/grub.

Don;t forget to run sudo update-grub (or is it grub2?) once done editing.

---

### Post by archkidd on 2010-04-15
Thanks but that is the Grub2 menu.  That is not the one I have trouble with.  When my computer starts it shows a choice of 2 OS, XP and Ubuntu.  When I select ubuntu THEN I get the Grub2 menu. (I am assuming that because it is the same as I see in grub.cfg file) Ubuntu 9.10 is at the top of that one and so is no trouble.
What I don't understand is where the first menu comes from and how I change that. Because it has XP first it automatically boots into that unless I sit there and manually change it into ubuntu.  I can do that but it is a pain :(

---

### Post by ed-koala on 2010-04-15
Hmmmm.  I'm not sure where the first menu you are talking about is coming from.  9.10 uses grub2, menu.lst is from grub legacy and also would appear after your first menu same as grub2.

There is a bootscript program you can download and run to get info on your system.  I'd recommend getting that, run it and post the results here.  That'll tell us all we should need to know to see what's going on.

---

### Post by archkidd on 2010-04-15
So from what you say, and other reading I have been doing in the meantime, I think the first menu must be coming from my hardware.  Because when I think about it ubuntu doesn't start until I select it from the first menu so it can't be creating it!
So I will look for the bootscript program as you suggest and see what it tells me. Thanks

---

### Post by skompier on 2010-04-15
If you just want Ubuntu to be the default OS, you can install startupmanager and choose which one you want. The order will be the same. Open System>Administration>Synaptic and search for startupmanager.

---

### Post by archkidd on 2010-04-16
I found startupmanager but don't think that solves my problem as it does not run until ubuntu runs and I am trying to make that selection before it does. The main ubuntu that I want is the first selection in what I now know is my Grub menu so that is ok.
Investigating the startup scripts shows me that the menu I want to change is in the computer flash memory and that is too much hassle for me to change.
I am only using dual boot until I am comfortable with ubuntu and have fould the apps that replace the ones I use in Windows, and I have gone through the printing and other functions and am happy with how to operate. Then I intend to do a clean install and operate ubuntu only.  S o there will be no problem then.  I will live with the menu choice for the month or two that it takes.
Thanks for all the help.  I know I will be back with more things I can't do and really appreciate how quickly people give help.

---

### Post by oldfred on 2010-04-16
Are you using wubi, where the install is in a NTFS windows partition? You then still boot with windows and in XP it is boot.ini that is the first menu.
I do not know if there is an offical way to edit it. I think someone saw instructions on the wubi site.

---

### Post by KirbySmith on 2010-04-16
It is possible that you are booting from the windows multi-boot file that lives in the root of the C:  drive.  I think it is called something like boot.ini in NT5.0, so it likely is the same in NT5.1.  I believe that the order of listings in this file determines the order of display.  In simple one-OS installations, the options don't appear during boot.

kirby

---

### Post by spydeyrch on 2010-04-16
From what you are mentioning, it sounds to me that you installed ubuntu via Wubi. This installs ubuntu from within windows. then when you boot up your computer, you get the windows boot list (all black and white text), where windows is first and ubuntu  is second and those are the only options, right? If you choose ubuntu, then it goes to the grub menu where ubuntu is first, then you have the prior kernels, rescue mode, and then at the bottom windows xp. Does that sound right?

Let me know if that is right and I think that I have a solution for you. :popcorn: I have done it this way it the solution has worked for me 100% every time.

---

### Post by archkidd on 2010-04-17
Spyderych, you are right, I did install using  wubi and the first screen is b&w and the sequence is as you describe.  I would be interested in your solution.  Thanks

---

### Post by oldfred on 2010-04-17
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20make%20Ubuntu%20the%20default%20boot%20option?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20make%20Ubuntu%20the%20default%20boot%20option?)

But if you are to the point of liking Ubuntu it may be time to create a new partition(s) and install Ubuntu to the partition. Wubi is for testing in a windows environment without having to create new partitions or modify windows partition sizes. But it still is running on the windows NTFS partition which is not the native Ubuntu install.

---

### Post by archkidd on 2010-04-17
Fantastic!  Thank Oldfred that is how it is done and so easily by using the Windows control panel!  So now I have an automatic start into Ubuntu.
Thank you for the advice re partitions.  I will look into that.
I have only been using ubuntu for a week and have some things still to sort out.  I have not tried to print yet.  I cannot open my CD drive.  I need to install addons to see videos in firefox etc

---

### Post by RJ12 on 2010-04-17
For the video addon have you ever ran
```
sudo apt-get install ubuntu-restricted-extras
```

If not, run that. Also just to let you know (you may already know this), when you enter your password on the Terminal it looks like it isn't typing. Just keep going and press enter and all should continue :)

---

### Post by IndyGunFreak on 2010-04-17
> **oldfred said:**
> Are you using wubi, where the install is in a NTFS windows partition? You then still boot with windows and in XP it is boot.ini that is the first menu.
I do not know if there is an offical way to edit it. I think someone saw instructions on the wubi site.

This... Definitely sounds like something Wubi would do...

IGF

---

### Post by archkidd on 2010-04-18
to RJ12.  I had not yet run the restricted extras and having done so, from the synaptic package manager, I now have video in firefox. Thanks.  So many things to discover as a newbie!

---

### Post by charly17201 on 2010-06-16
> **oldfred said:**
> [https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20make%20Ubuntu%20the%20default%20boot%20option?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20make%20Ubuntu%20the%20default%20boot%20option?)

But if you are to the point of liking Ubuntu it may be time to create a new partition(s) and install Ubuntu to the partition. Wubi is for testing in a windows environment without having to create new partitions or modify windows partition sizes. But it still is running on the windows NTFS partition which is not the native Ubuntu install.

Thanks for this info and the link. I've been looking for the same answers. And the link also has info on dumping the Wubi for a true Ubuntu installation. I've had a number of issues getting my Eee 1005HA over to Linux..... and this should finally complete the move.

---

