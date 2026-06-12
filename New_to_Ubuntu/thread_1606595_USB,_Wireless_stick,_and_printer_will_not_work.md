---
title: "USB, Wireless stick, and printer will not work"
date: 2010-10-26
forum: New to Ubuntu
---

### Post by Gregory37 on 2010-10-26
Hello everyone, I am a newbie to ubuntu 10.10. I installed it 2 weeks ago, and it's running fine, with the exception of any thumb drive or my rogers internet stick will not run.  when I plug it up to my usb port, it reads   Nokia data card cd-Rom. i tried right clicking-open, and nothing happens. This happens whith my thumb drive and my printer. please help!

---

### Post by Hippytaff on 2010-10-26
> **Gregory37 said:**
> Hello everyone, I am a newbie to ubuntu 10.10. I installed it 2 weeks ago, and it's running fine, with the exception of any thumb drive or my rogers internet stick will not run.  when I plug it up to my usb port, it reads   Nokia data card cd-Rom. i tried right clicking-open, and nothing happens. This happens whith my thumb drive and my printer. please help!

With the usb wireless thing plugged in enter into a terminal (open a terminal with CTRL~+ALT+T)

```

lsusb

```
 and post the result to help people help you :-)
does nothing work in any of your usb ports ? :-)

---

### Post by Gregory37 on 2010-10-26
thanks for responding hippytaff, I type lsusb into the terminal, and still nothing. nothing I plug into my USB port works

---

### Post by Hippytaff on 2010-10-26
> **Gregory37 said:**
> thanks for responding hippytaff, I type lsusb into the terminal, and still nothing. nothing I plug into my USB port works
Nothing at all?

Don't know why your not getting a result from that command, I would expect some kind of result - heres mine with nothing plugged in

> 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


---

### Post by Gregory37 on 2010-10-26
I'm sorry, this is what comes up in the terminal
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0421:0627 Nokia Mobile Phones 
Bus 001 Device 003: ID 046d:09b8 Logitech, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by Hippytaff on 2010-10-26
I would offer more but I'm just about to go to bed, but this is worth looking at
[http://manpages.ubuntu.com/manpages/lucid/man1/usb_modeswitch.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/usb_modeswitch.1.html)
modeswitch...if you get no luck with this then look into ndiswrapper, but I think your issue is to do with letting ubuntu know that the usb effort is wireless dongle :-)

---

### Post by Gregory37 on 2010-10-26
ok, i will give it a try, thanks for you help

---

### Post by Gregory37 on 2010-10-26
still need help! thanks

---

### Post by Hippytaff on 2010-10-26
Keep posting :-) 

I'm still here, but there are others (with more knowledge than me :-))

What do you need to know?

---

### Post by Gregory37 on 2010-10-26
I've tried 
[http://manpages.ubuntu.com/manpages/lucid/man1/usb_modeswitch.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/usb_modeswitch.1.html)

still nothing, my Internet stick and my thumb drive still will not open up or work

Thanks

---

