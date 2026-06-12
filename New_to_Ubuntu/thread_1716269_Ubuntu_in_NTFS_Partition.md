---
title: "Ubuntu in NTFS Partition?"
date: 2011-03-28
forum: New to Ubuntu
---

### Post by rez182 on 2011-03-28
i am about to install Ubuntu trough Wubi. In C: im using windows 7 and in D: i want to use Ubuntu. Is it possible to use Ubuntu in NTFS file system?

IMPORTANT: i already have files in my D: will installing Ubuntu in D: using Wubi delete the files?

---

### Post by Nickjpost on 2011-03-28
> **rez182 said:**
> i am about to install Ubuntu trough Wubi. In C: im using windows 7 and in D: i want to use Ubuntu. Is it possible to use Ubuntu in NTFS file system?

IMPORTANT: i already have files in my D: will installing Ubuntu in D: using Wubi delete the files?

Wubi allows Ubuntu to install an an application, albeit a very large one, but an application nonetheless. It does not harm windows and only allows up to 30G of space and the hibernate function is not available. If you want to install ubuntu on a physical partition, check this out:

Wubi install details: [https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

Partitioning windows to install Ubuntu as an additional operating system:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

PLEASE NOTE THAT WHATEVER YOU CHOOSE TO DO IS AT YOUR OWN RISK. MAKE A BACKUP OF ALL OF YOUR IMPORTANT DATA AND HAVE A RECOVERY DISK FOR WINDOWS AVAILABLE.

---

### Post by zpliang on 2011-03-28
Wubi will not hurt the partition nor the windows file system. 
It consists of just a few large files and a boot option, that you can edit with bcdedit.

---

### Post by rez182 on 2011-03-28
thanks guys...

so this is basically to try Ubuntu.
Wubi by default has 5gb for Ubuntu installation. is it enough?

EDIT: can you guys suggest any security software for Ubuntu which has firewall and antivirus? and is it possible to use ZoneAlarm and Avast in Ubuntu?

---

### Post by cmcanulty on 2011-03-28
I believe firewall is automatic in Ubuntu antivirus not needed so far in Linux.I have installed bleach bit which cleans up things a bit I run every few days

---

### Post by Matt__ on 2011-03-28
avast have a linux version if you really want it

[http://www.avast.com/linux-home-edition](http://www.avast.com/linux-home-edition)

personally i think you should just run from a live usb disk install for trying out ubuntu or go the whole hog and make a dual boot machine.

---

### Post by bodhi.zazen on 2011-03-28
> **rez182 said:**
> EDIT: can you guys suggest any security software for Ubuntu which has firewall and antivirus? and is it possible to use ZoneAlarm and Avast in Ubuntu?

Linux is not Windows and you do not need any of that stuff (firewall, antivirus, or ZoneAlarm) in Ubuntu to be secure.

See the security sticky:

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by rez182 on 2011-03-28
thanks for the info everyone.

@Matt__ i think a proper fresh Ubuntu installation is a good idea. is there a step by step guide for that? please suggest a minimum size for the new partition.

thanks everyone...great Ubuntu community...

---

### Post by Nickjpost on 2011-03-28
> **rez182 said:**
> thanks for the info everyone.

@Matt__ i think a proper fresh Ubuntu installation is a good idea. is there a step by step guide for that? please suggest a minimum size for the new partition.

thanks everyone...great Ubuntu community...
Partitioning windows to install Ubuntu as an additional operating system:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

If you have Vista/Win7 here's how to shrink your partition:
[https://help.ubuntu.com/community/HowtoResizeWindowsPartitions#Resize%20the%20Windows%20partition]("https://help.ubuntu.com/community/HowtoResizeWindowsPartitions#Resize%20the%20Windows%20partition")

Here's a guide to partitioning

[http://techpp.com/2010/01/19/how-to-partition-a-hdd-hard-disk-in-windows-7/](http://techpp.com/2010/01/19/how-to-partition-a-hdd-hard-disk-in-windows-7/)


The size of Ubuntu is dependent on what you plan to use it for. If you want to learn Ubuntu's full potential, I might suggest around 40-60G, but that is just a suggestion. I encourage you to learn about Ubuntu's vast capabilities and then use your own judgement from there.

---

### Post by pcwiz11 on 2011-03-28
> **rez182 said:**
> thanks guys...

so this is basically to try Ubuntu.
Wubi by default has 5gb for Ubuntu installation. is it enough?

5GB will do just fine however I'd recommend using 8GB if you can afford to.

---

### Post by rez182 on 2011-03-29
thanks nick and everyone else...

i was unable to burn Ubuntu in a CD nor do i have a pen drive. (my CD/DVD writer burns 100% but later when re-inserted, says the disk is empty. tried many times with different burning softs. any idea how i can get it fixed or wat the problem is?)

i found a few problems with Ubuntu installation through Wubi.

the most important problem is, Ubuntu does not restart, it gets hanged. same problem even after uninstalling and reinstalling with Wubi.

other problems:

1) the touch pad does not work
2) after login to Ubuntu the sound keeps looping and gets hanged (happened once)
3) sometimes when i install an app, after i put in the authentication code, it does nothing until i close the window. then it starts installing.

i have one question, why are some apps simple as a download manager so huge in size above 200mb after installation in Ubuntu?

thanks everyone. ill have a lot more questions soon :)

---

### Post by Elfy on 2011-03-29
> i have one question, why are some apps simple as a download manager so huge in size above 200mb after installation in Ubuntu?What makes you say that?

Where are you getting the information from?

---

### Post by rez182 on 2011-03-29
in the software center there is a download manager app called Kgde or something i dont remember, which said the setup size was about 60mb and the after installation size was 200mb. some other apps were really big too.

---

### Post by Elfy on 2011-03-29
> **rez182 said:**
> in the software center there is a download manager app called Kgde or something i dont remember, which said the setup size was about 60mb and the after installation size was 200mb. some other apps were really big too.

Aah - if you have ubuntu installed and want to install a kde app then you'll also need to install some of the libs the app needs to work. If you then need to install another kde app the chances are that the installed size will be much smaller as you could already have the 'extra' libs.

More or less if the package's name is ksomething it'll need extra packages on ubuntu.

I almost posted as well to say that "5GB will do just fine" might be a bit hopeful, if you intend to install kde packages on ubuntu you might find it runnning out sooner than anticipated.

That said wubi _is_ just a try it and see app and not supposed to be used forever.

Have fun

---

### Post by rez182 on 2011-03-29
[QUOTE=forestpiskie;That said wubi _is_ just a try it and see app and not supposed to be used forever.[/QUOTE]

do you know any way i can install Ubuntu in a separate raw partition from win7 without using a CD or a pen drive?

---

### Post by Elfy on 2011-03-29
> **rez182 said:**
> do you know any way i can install Ubuntu in a separate raw partition from win7 without using a CD or a pen drive?

I don't no, at least I know you could try a net install but would need to be able to access the necessary files - for that I would know you could do so from grub but until you install any linux you'll not have grub.

I'd try and sort your burner issue personally. 

[https://help.ubuntu.com/community/Installation/NetbootInstallFromInternet](https://help.ubuntu.com/community/Installation/NetbootInstallFromInternet)

---

### Post by rez182 on 2011-03-29
finally i installed ubuntu in a separate ext4 partition (was a problem with the blank CD). feels kinda good. although there still seems to be the problem with restarting. gets hanged. 

i am a little curious if its safe to use the "Empathy Internet Messaging" for facebook and msn chat. is it safe to use them?

thanks everyone for the support. always wanted to be a linux user.

---

### Post by rez182 on 2011-03-29
there are some major problems with my Ubuntu 10.10

i cannot use it without A/C power. it gets hanged. i then have to manuallly shutdown my pc with the power button. please need help

---

### Post by cmcanulty on 2011-03-29
Check system-preferences-power options in case something there is causing it

---

### Post by rez182 on 2011-03-29
> **cmcanulty said:**
> Check system-preferences-power options in case something there is causing it

the power manager was at its default... i later changed it to not spin down HDD in battery mode and it seems to be working in battery mode now. but i cannot pin point the reason behind it. i should close this thread and open a new one. anyidea how to close tihs thread?

thanks alot everyone...

---

### Post by Elfy on 2011-03-29
You can't actually close it - only staff can do that.

You can though mark it as solved - Thread Tools at the top of the thread.

---

### Post by rez182 on 2011-03-29
thanks

---

### Post by Learning Linux 2011 on 2011-03-29
> **rez182 said:**
> thanks guys...

so this is basically to try Ubuntu.
Wubi by default has 5gb for Ubuntu installation. is it enough?

EDIT: can you guys suggest any security software for Ubuntu which has firewall and antivirus? and is it possible to use ZoneAlarm and Avast in Ubuntu?


Amazingly, you don't need a firewall or anti-virus for Linux, as it is far more secure than Windows due to the way it is designed.

You wouldn't need ZoneAlarm or Avast.

the program 'ufw' is used for the firewall command line.  You can also use Ubuntu Software center to download programs that interact with ufw in a graphical way.

---

### Post by rez182 on 2011-03-29
thanks @learning linux...i did a fresh install in a separate partition for linux..

linux is pretty amazing in its own way...

can anyone tell me how i can replace the default evolution mail icon in the top panel to thunderbird?
i installed thunderbird and when i click add to panel, i dont see thunderbird... help plz...

---

### Post by Learning Linux 2011 on 2011-03-31
> **rez182 said:**
> thanks @learning linux...i did a fresh install in a separate partition for linux..

linux is pretty amazing in its own way...

can anyone tell me how i can replace the default evolution mail icon in the top panel to thunderbird?
i installed thunderbird and when i click add to panel, i dont see thunderbird... help plz...


You might want to start a new thread for this one.

---

