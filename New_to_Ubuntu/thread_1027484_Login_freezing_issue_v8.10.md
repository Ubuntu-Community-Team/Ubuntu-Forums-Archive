---
title: "Login freezing issue v8.10"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by bartz118 on 2009-01-01
Hello,

I am new to Ubuntu / linux in general.  Every time I login through the graphical interface it locks up.  I still have the mouse, but the background stays a peach color.  I can login in through the command line.  

I just bought the computer and don't know much about the specs.  It had windows xp on it and it was working fine.  I downloaded Ubuntu off of it and burned the cd.

It is a Intel p4 2.532 ghz with an onboard intel video card (not sure what model).

I just tried memtest86 and it keeps locking up on test #3.

Any suggestions?

Thanks

---

### Post by abn91c on 2009-01-01
> **bartz118 said:**
> Hello,

I am new to Ubuntu / linux in general.  Every time I login through the graphical interface it locks up.  I still have the mouse, but the background stays a peach color.  I can login in through the command line.  

I just bought the computer and don't know much about the specs.  It had windows xp on it and it was working fine.  I downloaded Ubuntu off of it and burned the cd.

It is a Intel p4 2.532 ghz with an onboard intel video card (not sure what model).

I just tried memtest86 and it keeps locking up on test #3.

Any suggestions?

Thanks
press ctrl+alt+f1, at the prompt type these commands one at a time, the problem it the desktop effect that ubuntu loads by default
 sudo apt-get remove compiz
 sudo apt-get remove compiz core
 after they are done sudo reboot

---

### Post by bartz118 on 2009-01-01
Thanks for helping.  

I still have the issue.  

I was able to remove the compiz, but I was not able to remove compiz core. It told me that it couldn't find package core.

Thanks
Justin

P.S the memtest lockup was my dumb fault for not turning off the usb legacy in the Bios.

---

### Post by Coder543 on 2009-01-01
have a flash drive in hand
make sure you know the name of this flash drive.
insert said flash drive into usb
turn on the computer
press ctrl + alt + f1
login
ls /media/
the above command will list the devices plugged in. replace USBDRIVE with the name listed above
sudo killall gdm
enter your password
sudo gdm > "/media/USBDRIVE/gdmout.txt"
you will now be presented with the login window
login
if after three minutes you still haven't logged in, just go ahead and turn off the computer.
now, upload the gdmout.txt file that should be on your flash drive, if there is anything in it.

---

### Post by abn91c on 2009-01-01
> **bartz118 said:**
> Thanks for helping.  

I still have the issue.  

I was able to remove the compiz, but I was not able to remove compiz core. It told me that it couldn't find package core.

Thanks
Justin

P.S the memtest lockup was my dumb fault for not turning off the usb legacy in the Bios.

oops sorry my bad its **[COLOR="Red"]sudo apt-get remove compiz-core[/COLOR]**
i forgot the **[COLOR="Red"]-[/COLOR]**

---

### Post by bartz118 on 2009-01-01
Thanks.  I thought it was missing something. That fixed my issue.

---

### Post by prshah on 2009-01-01
> **abn91c said:**
> 
 sudo apt-get remove compiz
 sudo apt-get remove compiz core


> **Coder543 said:**
> 
sudo killall gdm


Ouch, talk about using a sledgehammer where a flyswatter will suffice...

You can achieve each of the above effects with less system invasive techniques```
sudo /etc/init.d/gdm stop
sudo chmod a-x /usr/bin/compiz.real
sudo chmod a-x /usr/bin/compiz

```

The above commands are more "graceful"; gdm stop will properly shutdown the desktop manager, not forcefully terminate it. And the other commands will remove execute permissions on Compiz, so that in the future (probably after applying updates) if you want to re-enable it, all you have to do is turn the execute permission back on (a+x) instead of reinstalling it.

---

