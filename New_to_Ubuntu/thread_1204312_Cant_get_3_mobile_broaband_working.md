---
title: "Cant get 3 mobile broaband working"
date: 2009-07-04
forum: New to Ubuntu
---

### Post by richie1913 on 2009-07-04
Hi all again,still cant get my 3 dongle working,vodafone yes no problem but 3 nothing.If I boot up with the dongle In nothing,If I plug the dongle In while Ubuntu Is running nothing,I have already looked at some threads but the Instructions are way beyond me,If any one has the patients to do a step by step guide In newbie language I would be so grateful.Here's hoping thanks Richard.

---

### Post by t0p on 2009-07-04
> **richie1913 said:**
> Hi all again,still cant get my 3 dongle working,vodafone yes no problem but 3 nothing.If I boot up with the dongle In nothing,If I plug the dongle In while Ubuntu Is running nothing,I have already looked at some threads but the Instructions are way beyond me,If any one has the patients to do a step by step guide In newbie language I would be so grateful.Here's hoping thanks Richard.

So ubuntu isn't detecting your dongle?  Or at least, network manager isn't launching the mobile network wizard when the dongle is plugged in.

Plug in the dongle, wait for a bit for the dongle to be detected, then right-click on the network manager icon (picture of 2 monitors in the top right of your display).  Is there a new entry there?

If not: 

Take out the dongle.

Now, open a terminal (**Applications > Accessories > Terminal**)  Type in the command

```
tail -f /var/log/messages
```

Re-insert the dongle again.  Is new output printed to the monitor?  Cut-and-paste it here for us to look at.
  
Wait a moment then plug it back in.

---

### Post by richie1913 on 2009-07-04
Hi t0p,I ran that command for you and here are the results,just the new output that came up when I inserted the dongle.
Jul  5 02:33:34 richard-desktop kernel: [ 6439.381966] usb 1-2.1: new full speed USB device using uhci_hcd and address 9
Jul  5 02:33:34 richard-desktop kernel: [ 6439.555883] usb 1-2.1: configuration #1 chosen from 1 choice
Jul  5 02:33:34 richard-desktop kernel: [ 6439.564157] usb-storage: device ignored
Hope that Is what you wanted,Thank-you Richard

---

### Post by jarrah-95 on 2009-07-04
what is the model and brand of your modem (might say it on the back or box)
thanks

---

### Post by richie1913 on 2009-07-04
Hi all I can find out Is the model which Is a ZTE MF627 Pay as you go

---

### Post by jarrah-95 on 2009-07-04
witch version of ubuntu are you using

---

### Post by jarrah-95 on 2009-07-04
try this thread if you havent alredy
[http://newyork.ubuntuforums.org/showthread.php?t=1017630](http://newyork.ubuntuforums.org/showthread.php?t=1017630)

---

### Post by richie1913 on 2009-07-04
Its Ubuntu 9.04 Desktop Edition

---

### Post by richie1913 on 2009-07-05
Thanks for the links to them threads but I am no closer to getting this to run.The thread says to edit usb_modeswitch.conf I have tried but when I try to save the edited version Ubuntu will not let me because of lack of permission how do I get permission to do this

---

### Post by Ji Ruo on 2009-07-05
> **richie1913 said:**
> Thanks for the links to them threads but I am no closer to getting this to run.The thread says to edit usb_modeswitch.conf I have tried but when I try to save the edited version Ubuntu will not let me because of lack of permission how do I get permission to do this

Your problem here is just that you aren't using the sudo command. If you want to run anything that requires administrator privileges you have to put sudo in front of it. In this case you actually want to use gksudo, because you are opening a desktop application (and not one using a terminal/command line). Press <Alt> + <F2> and try typing this:

> gksudo gedit /etc/usb_modeswitch.conf 

Then enter your password. This will open the usb_modeswitch.conf with the gedit text editor that comes with ubuntu, with administrator privileges. You will be able to save it. 

Whenever you're changing .conf files, it's a good idea to save it first so you can get back to it later if you need to, so save it (in the /etc directory) as usb_modeswitch.conf.backup or something like that. If it's a new (blank) file of course you don't need to bother with this.

---

