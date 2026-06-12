---
title: "Assistance is requested to set the correct dial command in Gnome-ppp"
date: 2006-12-13
forum: Networking &amp; Wireless
---

### Post by fefniir on 2006-12-13
I have a Verizon XV6700 that I am using as my modem. So far I have been able to configure wvdial to connect without a problem. However, I would like to use gnome-ppp to manage the connection. I have managed to (so far) narrow the problem down to the following line in $HOME/.wvdial.conf

Dial Command = ATM1L3DT

My modem, apparently, does not recognize this as the command to dial out, and simply returns an OK. Of course, this leaves gnome-ppp waiting for a CONNECT that will never happen.

Manually editing the line doesn't work because gnome-ppp rewrites the line every time it is started. 

Does anyone know of a way to permanently change this to the correct command?

---

### Post by ciscosurfer on 2006-12-13
> **fefniir said:**
> I have a Verizon XV6700 that I am using as my modem. So far I have been able to configure wvdial to connect without a problem. However, I would like to use gnome-ppp to manage the connection. I have managed to (so far) narrow the problem down to the following line in $HOME/.wvdial.conf

Dial Command = ATM1L3DT

My modem, apparently, does not recognize this as the command to dial out, and simply returns an OK. Of course, this leaves gnome-ppp waiting for a CONNECT that will never happen.

Manually editing the line doesn't work because gnome-ppp rewrites the line every time it is started. 

Does anyone know of a way to permanently change this to the correct command?The dial command is correct.  It's basically saying, "Attention modem, here's a dial-tone, ready for the number to dial".  It's a standard dial command that modem's understand.

Are you using a analog, usb, or isdn modem?  Making sure those settings are correct are important.

Make sure you go over all of your settings in gnome-ppp (you shouldn't edit your ~/.wvdial.conf file--it gets written by wvdial).

Here are few links to follow up on: 
[http://andrewtv.org/fedora-ppc6700/](http://andrewtv.org/fedora-ppc6700/)
[http://ubuntuforums.org/showthread.php?t=315760&highlight=wvdial](http://ubuntuforums.org/showthread.php?t=315760&highlight=wvdial)
[http://www.penlug.org/twiki/bin/view/Main/LinuxHardwareInfoToshibaTecra9000](http://www.penlug.org/twiki/bin/view/Main/LinuxHardwareInfoToshibaTecra9000) (the modem section)
[http://ubuntuforums.org/showthread.php?t=346](http://ubuntuforums.org/showthread.php?t=346)
[http://ubuntuforums.org/showthread.php?t=7566](http://ubuntuforums.org/showthread.php?t=7566)
[http://wiki.linuxquestions.org/wiki/Set_up_modem](http://wiki.linuxquestions.org/wiki/Set_up_modem)

---

### Post by fefniir on 2006-12-18
> **ciscosurfer said:**
> The dial command is correct.  It's basically saying, "Attention modem, here's a dial-tone, ready for the number to dial".  It's a standard dial command that modem's understand.

Are you using a analog, usb, or isdn modem?  Making sure those settings are correct are important.

Make sure you go over all of your settings in gnome-ppp (you shouldn't edit your ~/.wvdial.conf file--it gets written by wvdial).

Here are few links to follow up on: 
[http://andrewtv.org/fedora-ppc6700/](http://andrewtv.org/fedora-ppc6700/)
[http://ubuntuforums.org/showthread.php?t=315760&highlight=wvdial](http://ubuntuforums.org/showthread.php?t=315760&highlight=wvdial)
[http://www.penlug.org/twiki/bin/view/Main/LinuxHardwareInfoToshibaTecra9000](http://www.penlug.org/twiki/bin/view/Main/LinuxHardwareInfoToshibaTecra9000) (the modem section)
[http://ubuntuforums.org/showthread.php?t=346](http://ubuntuforums.org/showthread.php?t=346)
[http://ubuntuforums.org/showthread.php?t=7566](http://ubuntuforums.org/showthread.php?t=7566)
[http://wiki.linuxquestions.org/wiki/Set_up_modem](http://wiki.linuxquestions.org/wiki/Set_up_modem)
Sorry this reply has taking so long, been without power for almost 3 days....

Hmmm...perhaps I chould have chosen my words better....

It's not that the command "ATM1L3DT" is incorrect, it's that my modem ,which is a verizon xv6700 mobile phone running in usb tethered mode, dosen't recognize any command other than "ATDT" as the command to dial out. 

I have tried all three modes listed in gnome-ppp, but none of the default dial commands will work. 

What I am looking for is a way to permently override the default dial command set by gnome-ppp or if there is any known init string that might set my modem to accept "ATM1L3DT" as a dial out command.

---

### Post by fefniir on 2006-12-28
WOOT!! Got it working!
In retrospect the solution is so incredibly simple I can't believe it took me this long to figure it out.

At any rate the solution:
1. Set the modem type to ISDN, which sets the dial command to AT
2. Set the phone number to DT#777
Can you guess what happens when the program adds those two together?

Yep, you get "ATDT#777"

---

