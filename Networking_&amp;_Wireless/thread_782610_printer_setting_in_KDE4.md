---
title: "printer setting in KDE4?"
date: 2008-05-05
forum: Networking &amp; Wireless
---

### Post by one_ro on 2008-05-05
Dear listers,

I'm trying to use a network printer, probably through samba but I cannot find any icon for printers in the System Settings.

I am using Kubuntu Hardy with KDE4; I know it's not stable yet, but in conjunction with compiz I just like it. So what would be the easiest way to set up a printer in KDE4?

Alternatively, how can I start CUPS?
Thanks in advance,
Adrian

---

### Post by robertsaron on 2008-05-25
I am having the same question. My printer is not even seen in KDE4 Hardy. It is an hp deskjet 720c, This is the first time my printer is not recognized by any distro of linux. How do I even set up a printer in KDE4 hardy?

---

### Post by one_ro on 2008-05-26
Well, I found an answer by my own, happy to help if I can. Just type:

sudo kcmshell printers

and you'll get that specific windows that's missing in the System Setting.

If you don't have the direct door, just use the window ;)
There are many more you can set (like the clock), see all possibilities with:

kcmshell --list

I hope it helps,
Adrian

---

### Post by robertsaron on 2008-05-29
thanks so much i will try that when i get home. Where the heck did you find this?

---

### Post by one_ro on 2008-05-29
> **robertsaron said:**
> thanks so much i will try that when i get home. Where the heck did you find this?

Oh, that gets back to old Kubuntu 5.04, when a bug prevented the user from clicking the "Administrator" button (it didn't fit in the window), so I remembered I got this solution on ubuntuforums, opening not the System Settings but only a specific one using kcmshell.
Useful memories, huh?
Cheers,
Adrian

---

### Post by robertsaron on 2008-05-29
kcmshell did not work. the output of what i get is below, how to fix?



bob@bob-desktop:~$ sudo kcmshell printers
[sudo] password for aaron:
Error: "/var/tmp/kdecache-bob" is owned by uid 1000 instead of uid 0.
kcmshell (kdelibs): WARNING: Could not find module 'printers'.

---

### Post by syyid on 2008-05-29
Exact same issue, seems like a pretty glaring omission for the printers icon to be missing :|

---

### Post by syyid on 2008-05-29
I did an install of KDE3 as well , thought I'd check that out (KDE4 seems um very incomplete at the moment) but in any case the install itself fixed the could not find module printers issue

---

### Post by syyid on 2008-05-29
Another interesting thing - apparently there's something hp has that does the install too - called HP lip (Linux Imaging and Printing System)
Not sure if it was originally installed or was installed with kde3 but it can be invoked from the shell with 
sudo hp-setup

Also you can check if you have it by 
dpkg -l hplip
if there's a ii hplip then you have it.

---

### Post by robertsaron on 2008-05-30
I did try HP lip, and it did not work, it says it finds the printers, but unable to print a test page, and it freezes on me a lot.

---

### Post by one_ro on 2008-06-02
Hi there,

> **robertsaron said:**
> kcmshell did not work. the output of what i get is below, how to fix?



bob@bob-desktop:~$ sudo kcmshell printers
[sudo] password for aaron:
Error: "/var/tmp/kdecache-bob" is owned by uid 1000 instead of uid 0.
kcmshell (kdelibs): WARNING: Could not find module 'printers'.

Sorry it didn't work, on my computer it does. My best bet is you don't have some packages installed or something needs to be updated/upgraded.
I remember at first "kcmshell --list" did not return anything (except for printers), but later on I had the full list. Unfortunately, I have no idea which packages (if any) you need for that, maybe other people reading this will guide you.

But I can assure you it does work, once you have it installed...
Adrian

---

### Post by robertsaron on 2008-06-05
Thanks for the update, I will wait for KDE4.1 and see if that resolves anything. I am also looking into getting a new printer, one that does, lan and usb. So that will problably resolve the issue.

---

### Post by syyid on 2008-06-05
Robert, did you get a chance to try to install the kde3 packages (kde from the package manager). You could do the KDE3 install and try it again (this worked for me within kde4). If it doesn't you could also try to do it via KDE3
after the install logout
click on menu (I think, the other button besides the login/cancel)
switch ur session to KDE3
install the printer 
logout / switch to kde4 / log back in

---

### Post by robertsaron on 2008-06-09
Do i install just certain KDE3 libraries? or all of KDE 3? If so, for both, how to install?

---

### Post by syyid on 2008-06-09
I'm a newbie too so not a 100% sure but I figured it was easier to do the full install then figure out which specific libraries were needed. To do the full install I went to the Adept Package Manager and selected KDE for install (which automatically selected all of its relevant libraries) and applied the change.

---

### Post by robertsaron on 2008-06-12
I was also thinking about installing some of the Gnome stuff for printing to see if that would work. KDE4.1 is not that far out, and neither is the next release. So I may just Wait, by then I may have a new printer so it may not really matter.

---

### Post by harak on 2008-06-24
or you can also open a browser and enter [http://localhost:631](http://localhost:631)

note in the end it will ask for login name password. just enter the login name and password (sudo?) that is required to login into your computer.

---

