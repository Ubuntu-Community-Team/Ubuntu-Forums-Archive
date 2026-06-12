---
title: "after installation, black screen blinking mouse"
date: 2010-09-03
forum: New to Ubuntu
---

### Post by nublol on 2010-09-03
okay, so i have a boot-able usb (which i'm using right now) that works. i use it to do the full installation, it goes all the way through and says reboot, so then i do that, it says take out the usb or the thing i used to install it, so i do that. then when it reboots up it shows the Ubuntu loading screen with the dots underneath, it seems to finish doing that, then right after it goes to a black screen with my mouse in the middle of the screen. from there it proceeds to blink (staying on for about 4 seconds, i can move it) then it goes away, and repeats once or twice. after, it does not do anything and just stays at this black screen. 

[CENTER]i have a hp pavilion a705w and all of it's components from the factory.
i truly do not know what i did wrong.
i am very new to Linux.
any suggestions are greatly appreciated.


Thanks in advance,
Cody
[/CENTER]

---

### Post by nublol on 2010-09-03
also, i had an XP before, but i deleted my whole partition for Ubuntu, thinking it would work, and it obviously doesn't.
anything, and i mean anything is extremely helpful.

---

### Post by techningeer on 2010-09-03
Apparently, x.org doesn't recognize your display. Post your x.org log files here (/var/log/X.org.*n*log, where n is the number). Include them all.

---

### Post by nublol on 2010-09-03
and how would i go about doing that? sorry, but like i said i'm completely new at this.

Edit: i tried tryping that in the command prompt lol, to no avail.

---

### Post by techningeer on 2010-09-03
> **nublol said:**
> and how would i go about doing that? sorry, but like i said i'm completely new at this.

Edit: i tried tryping that in the command prompt lol, to no avail.

nublol, I'll have to catch you later. I'll get back as soon as I can!

---

### Post by llamabr on 2010-09-03
post the output of:

```
ls /var/log/X*
```

---

### Post by nublol on 2010-09-03
/var/log/Xorg.0.log

does that look about right?

---

### Post by nublol on 2010-09-03
does anyone know where they were going with this?

---

### Post by nublol on 2010-09-04
still need help... kind of need a use-able computer...

---

### Post by cariboo on 2010-09-04
It would have helped if you had told us what version you are using.

Can you start in recovery mode? To start in recovery mode if you are using Karmic and newer, press the shift key just after post is finished and you should see the grub menu. Use the arrow keys to navigate to recovery mode then press enter. You'll see a whole lot of text stream by and eventually you should see a menu. Use the arrow keys to select resume. you'll be taken to a login prompt. Enter your user name and password, you won't see anything when you enter your password, press enter when you've entered it.

Once you have entered your user name and password, at the prompt type:

```
startx
```

You should be taken directly to the desktop, if it goes back to a prompt, have a look at /var/log/Xorg.0.log. To do this at the prompt type:

```
cat /var/log/Xorg.0.log
```

A lot of text will stream by, the last 10 lines or so will tell you what has gone wrong. If you can copy or write the last 10 lines in your next post, it would be very helpful.

---

### Post by nublol on 2010-09-04
i'm using 10.04.1, sorry i thought i had mentioned that in my OP.
and i will be right back to go and try to start in recovery mode, give me a few mins.

---

### Post by nublol on 2010-09-04
> **cariboo907 said:**
> It would have helped if you had told us what version you are using.

Can you start in recovery mode? To start in recovery mode if you are using Karmic and newer, press the shift key just after post is finished and you should see the grub menu. Use the arrow keys to navigate to recovery mode then press enter. You'll see a whole lot of text stream by and eventually you should see a menu. Use the arrow keys to select resume. you'll be taken to a login prompt. Enter your user name and password, you won't see anything when you enter your password, press enter when you've entered it.

Once you have entered your user name and password, at the prompt type:

```
startx
```You should be taken directly to the desktop, if it goes back to a prompt, have a look at /var/log/Xorg.0.log. To do this at the prompt type:

```
cat /var/log/Xorg.0.log
```A lot of text will stream by, the last 10 lines or so will tell you what has gone wrong. If you can copy or write the last 10 lines in your next post, it would be very helpful.

i did everything to the [CODE]startx[CODE] and the username and pass, and i am now in. but in the case that my computer restarts, do i have to do all of this over again?

---

### Post by nublol on 2010-09-04
11: /usr/lib/xorg/modules/drivers/intel_drv.so (0x142000+0x13f61) [0x155f61]
12: /usr/lib/xorg/modules/drivers/intel_drv.so (0x142000+0x4527a) [0x18727a]
13: /usr/lib/xorg/modules/drivers/intel_drv.so (0x142000+0x5b6a4) [0x19d6a4]
14: /usr/lib/xorg/modules/drivers/intel_drv.so (0x142000+0x5b733) [0x19d733]
15: /usr/lib/xorg/modules/drivers/intel_drv.so (0x142000+0x5bb97) [0x19db97]
16: /usr/bin/X (0x8048000+0xa3c6d) [0x80ebc6d]
17: /usr/bin/X (ChangeWindowAttributes+0x2b9) [0x809a0d9]
18: /usr/bin/X (0x8048000+0x29e45) [0x8071e45]
19: /usr/bin/X (0x8048000+0x2a477) [0x8072477]
20: /usr/bin/X (0x8048000+0x1ed7a) [0x8066d7a]
21: /lib/tls/i686/cmov/libc.so.6 (__libc_start_main+0xe6) [0x364bd6]
22: /usr/bin/X (0x8048000+0x1e961) [0x8066961]

also, that's from running the command you gave me.

i restarted my computer to see if it would boot normally now, and i still have to go through the same process.
also, thank you for helping, to all of you.

---

### Post by nublol on 2010-09-04
it sometimes fails in rescue mode, and everything will go black, with only my mouse showing, but it cannot move.

---

### Post by techningeer on 2010-09-06
nublol, start in rescue mode. Run "aptitude upgrade", then run "apt-get update". This should take care of some problems. Also, don't use any Extra graphics features such as 2d, 3d, and so on.

---

