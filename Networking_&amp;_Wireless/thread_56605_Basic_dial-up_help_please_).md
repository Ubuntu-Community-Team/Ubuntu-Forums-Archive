---
title: "Basic dial-up help please :)"
date: 2005-08-13
forum: Networking &amp; Wireless
---

### Post by Monika on 2005-08-13
Uptil now my net connection has been through an adsl router. But I'm forced to use a dial-up connection for a while (though will hopefully be back to the adsl router in a few weeks) and I have no idea how to set it up in my linux (ubuntu).
The modem I have is a Pentagram Predator faks modem 56USB and there are linux drivers on the CD. There is a ReadMe file there and I've started reading it, but I need help to even be able to follow those instructions ;)
I've never touched a linux kernel before and it seems like I'm going to have to do something with modules this time. The make file needs to have some sort of 'kernel_includes" path changed. And I've no idea what to write there. I do not have any kernel source downloaded and I'm running the basic 386 ubuntu kernel. Is there any way to download the kernel sources via windows?

What should I do? Have I given enough information for somebody to be able to help?

---

### Post by cwaldbieser on 2005-08-13
You might not have to actually compile anything into the kernel if the modem isn't a WinModem.  "pppconfig" is a menu driven program that should help you set up the connection info, and "wvdial" could establish the connection.  If you use kubuntu, I would recommend using "kppp".

---

### Post by az on 2005-08-13
[QUOTE=Monika]Uptil now my net connection has been through an adsl router. But I'm forced to use a dial-up connection for a while (though will hopefully be back to the adsl router in a few weeks) and I have no idea how to set it up in my linux (ubuntu).
The modem I have is a Pentagram Predator faks modem 56USB and there are linux drivers on the CD. There is a ReadMe file there and I've started reading it, but I need help to even be able to follow those instructions ;)
I've never touched a linux kernel before and it seems like I'm going to have to do something with modules this time. The make file needs to have some sort of 'kernel_includes" path changed. And I've no idea what to write there. I do not have any kernel source downloaded and I'm running the basic 386 ubuntu kernel. Is there any way to download the kernel sources via windows?

What should I do? Have I given enough information for somebody to be able to help?[/QUOTE]


Right off the bat, install build-essential and linux-headers-2.6.10-5-386

Then in the README, when it says anything about kernel sources or kernel_includes, you are covered.  It should automagically detect the linux-headers and use that.

Post the README if you want, that would be the most helpful.

---

### Post by Monika on 2005-08-14
[QUOTE=azz]Right off the bat, install build-essential and linux-headers-2.6.10-5-386[/QUOTE]

Can't do it cause I don't have net access in linux which is my main problem :( And I've no idea how to do it via windows. Unless these packages are on the Ubuntu (hoary) CD?

Thanks for the replies, I will try and post the readme later maybe, but it does say it needs the kernel source, so I think I definitely need those packages installed.

Oh, and I'm on gnome based Ubuntu.

---

### Post by az on 2005-08-14
Those packages are on the cd.  That is the point of providing them -  Users who cannot get on the net need them to build drivers.  No, you will not need to full kernel source - just the headers.  I promise.

---

### Post by blastus on 2005-08-14
To install the necessary stuff to compile drivers for your kernel you need to insert the Ubuntu Hoary CD into the drive and at a terminal prompt enter:

sudo apt-get install build-essential linux-headers-2.6.10-5-386

You may be prompted for a password. Enter your password at this point and the packages will get installed. 

You can also install these packages with the "Synaptic Package Manager" program from the System -> Administration menu. To use Synaptic instead of typing in an apt-get command, open Synaptic and scroll down and find the build-essential and linux-headers-2.6.10-5-386 packages. Then check them off and press the "Apply" button.

---

