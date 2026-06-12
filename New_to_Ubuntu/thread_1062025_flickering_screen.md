---
title: "flickering screen"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by stefdnk on 2009-02-06
I just managed to install Xubuntu 8.10 on my old Powerbook 533, overcoming the missing deection of cd drive.

Now when I boot I get only a flickering screen.
If I use Ctrl + Alt + F1 I can log into Ubuntu but only with a text screen. I can se it says  there's an error using the card pbbuttonsd  "default" as it doesn't exist.
Is that a videocard filure?

And how do I manage the video card if it is?

Completely new to Ubuntu, so please be patient;)

---

### Post by taseedorf on 2009-02-06
at the command prompt type

sudo /etc/init.d/xdm stop    (or replace xdm with gdm)

than try

sudo /etc/init.d/xdm start (or gdm)

see if it gives you errors.

or try this

sudo dpkg-reconfigure xserver-xorg

and that will reconfigure your xserver so you can see a gui

than type

startx

---

### Post by stefdnk on 2009-02-07
Thanks for the input.
I tried the reconfigure and it all worked until the last keyboard ok.
Then I type  startx and it say:
Fatal server error: Server is already active for display 0
If this server is no longer running , remove /tmp/.XO-lock

Invalid MIT-MAGIC-Cookie - 11 keygiving up.
Xinit:Interrupted system call (errno 4) unable to connect to X server
xinit: No such process (errno 3) server error.


Sorry, I don't know how to remove the tmd/.XO-lock
Beginner in linux commands

Thanks so far :)

---

### Post by stefdnk on 2009-02-07
Oh, I tried the stop and start. 
The stop gave me the unreadable lines and typing the start command afterwards gaev me a scren looking like an Xray of an infected tooth :(

I believe that's the eqv to a kernel panic?

---

### Post by stefdnk on 2009-02-07
Ok, So I have been looking around and probably haven't understood much, but  I am using aRadeon Mobiliy M6 LY VGA controller.

I have tried typing glxinfo and it saysError:unable to open display.

dmesg  shows a long list ( how do I scroll in such a list,BTW?) and I can see it says agpgart:  putting AGP V2 device at 0000:00:0b:0 into 4x mode
and the same for 000:00:10:0


modprobe agpart  says  FATAL: module agpart not found.


does that make any sense to anybody  ?

---

### Post by stefdnk on 2009-02-08
I think I have pinned it down to a missing driver for M6 Ly card.
Anyone know how to get around it? or Is there a driver somewhere ?
I haven't found it:(

---

### Post by stefdnk on 2009-02-10
Well, nobody seems to know :confused:

I thought these forums were filled with nerds dreaming in sudo commands ;)

It was fun trying, but I never got past the console.  ](*,)
):P    :---)

---

### Post by taseedorf on 2009-02-27
reinstall drivers.  when updating xorg you never shutdown the x screen, it was already running
on a different terminal

alt f7

---

### Post by 3rdalbum on 2009-02-27
I know this thread has been bumped from 2 weeks ago, but you might want to try asking in the Apple Users forum on Ubuntu Forums.

I don't know the specs of that Powerbook but you'd want to make sure it's got enough memory to run Xubuntu from CD. If Xorg is just giving you a bizarre image, it might not have enough memory available for AGP.

---

