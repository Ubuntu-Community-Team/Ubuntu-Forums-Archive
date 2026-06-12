---
title: "How to make the beep beep?"
date: 2009-06-08
forum: New to Ubuntu
---

### Post by resander on 2009-06-08
on Ubuntu 8.10 on a desktop Compac PC.

I have tried from program:    
printf ( "\007\007\007\n" ) ;
putchar ( '\a' ) ;
putchar ( '\007' ) ;

and from command line:
ken@ken-desktop:~$ echo -e '\a'
ken@ken-desktop:~$ echo -e '\G'
ken@ken-desktop:~$ echo -e '\007'

but no beep to be heard. 

On startup there is a ping just before login user and password dialog appears. 

Some sound info:

ken@ken-desktop:~$ xset q | grep bell
  bell percent:  50    bell pitch:  400    bell duration:  100

ken@ken-desktop:~$ lsmod | grep pcspkr
pcspkr                 10624  0 

There is no inbuilt speaker, but there are two external that work for music and video. I don't know if there is a sound device for a system beep.
There is a volume control called alsa mixer on Applications->Sound and Video menu.

How do I enable the beep?

---

### Post by durand on 2009-06-08
Not working here either. Try the [beep]("apt://beep") program, it's what I use.

---

### Post by resander on 2009-06-10
Installed beep program, but it did not beep when I tried it from the command line.

Q1.  Is the beep hardware (assuming there is such) disabled by Ubuntu?

Q2.  How can I prove or disprove there is a beep device in the PC? Via BIOS? How? Don't know what to expect, so opening PC not an option.

---

### Post by durand on 2009-06-10
Does your computer beep on startup? It shouldn't be disabled in ubuntu..
Maybe you just don't have a device.

---

### Post by Bios Element on 2009-06-10
echo -e '\a' worked for me.

---

### Post by resander on 2009-06-11
My computer pings (sonar radar quality) exactly at the point when the startup sequence prompts for login name and password.

Is there a (dull) beep earlier during startup, for example when power is turned on?

---

### Post by durand on 2009-06-11
Not necessarilly but it doesn't seem to be working for you.

Oh, try sudo beep.

---

### Post by Sockerdrickan on 2009-06-11
> **durand said:**
> Not necessarilly but it doesn't seem to be working for you.

Oh, try sudo beep.
Why the heck would that help?

---

### Post by durand on 2009-06-11
Thats what I had to do, I just remembered. As for why beep needs root access, I have no idea.

---

### Post by llamabr on 2009-06-11
> **Tux0r said:**
> Why the heck would that help?

depending on the way it was installed, you may have limited access to the module that controls the beep.

You might also not have the module installed.  The module is called pcspkr.  it may be blacklisted in /etc/modprobe.d/blacklist or you may not have the hardware.

---

### Post by resander on 2009-06-12
The last post in

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1041329](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1041329)

says the old-fashioned, inbuilt PC speaker is disabled by default in the Linux kernel. To enable it you need to recompile the kernel.

Source:
[http://howto.wikia.com/wiki/Howto_en...e_Linux_kernel](http://howto.wikia.com/wiki/Howto_en...e_Linux_kernel)

I assume an old-fashioned inbuilt speaker would produce poor quality tones useful for beeps and not much else, I do not mean a real speaker (like an external) sitting inside the box, which I have on another PC.

The ping on startup comes from the external speakers.

Don't want to take the risk recompiling the kernel.

pcskr is not on the blacklist in /etc/modprobe.d, but snd_pcsp is.
Don't know if the following is relevant. 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/263747](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/263747)

How can I generate a beep by software using the sound system and play it through the external speakers?

---

### Post by apmcd47 on 2009-06-12
Gnome-terminal:
Edit your current preferences and tick (enable) the terminal bell box in the General tab.

Konsole: 
Ensure the "Play a Sound" action is enabled for "Bell emitted ..." events in the Notification Settings dialog.

XFCE Terminal:
Sorry, don't know.

Andrew

---

### Post by resander on 2009-06-12
Terminal Bell is already ticked in Gnome Terminal.

---

