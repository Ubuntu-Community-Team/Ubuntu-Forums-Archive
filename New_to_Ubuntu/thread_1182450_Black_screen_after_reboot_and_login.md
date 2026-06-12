---
title: "Black screen after reboot and login"
date: 2009-06-09
forum: New to Ubuntu
---

### Post by ozzyprv on 2009-06-09
What?: Black screen after booting, entering username and password at welcome screen

Sequence of event:
1. I left my laptop running on battery for what now I think was too long (see #2)
2. Pressed power button to re-start system
3. Got a message (from BIOS) saying that battery was critically low
4. Immediately connected to AC
5. Booted as per usual
6. At welcome screen entered username and password
7. Black screen, nothing else happened
8. Ctrl+Alt+F1
9. See this message:
> Boot from (hd0,1) ext3  8688268c-ef2a-439d-bfe9-9ea51bc79180
Starting up ...
Loading, please wait...
19+0 records in
19+0 records out
kinit: name_to_dev_t(/dev/disk/by-uuid/98dd6622-a4df-4a7e-95a1-1a6872e81758 ) = dev(8,6)
kinit: No resume image, doing normal boot...

Not sure what to do. Please help. Thanks.

---

### Post by ozzyprv on 2009-06-09
After spending hours last night reading the posts, I realized I forgot to mention something that is different from previous posts: 

after login + password, I can see the mouse pointer (arrow).

I can actually move it around. That is a black screen with a mouse pointer.


What I have tried so far:

1. > "sudo nvidia-xconfig"

--> Same black screen and mouse pointer.

2. > Booting in to safe mode + xfix

--> Same black screen and mouse pointer.

3. > from terminal (tty1) "sudo etc/init.d/gdm restart" 

--> Same black screen and mouse pointer.

4. > 
a - "sudo blkid" and
b - Checked that swap line UUID from /etc/fstab matches swap UUID from step a
c - Check that the UUID in /etc/initramfs-tools/conf.d/resume matches the swap UUID from step a

--> Same black screen and mouse pointer.



I am running out of ideas. Again, for some reason I think what is happening has to do  with resuming after depleting the battery (see post#1).

---

### Post by OffAxis on 2009-06-09
does the Rescue Mode (terminal) work as expected?
It's just the x-server that's not working?

when you used 
```

sudo etc/init.d/gdm restart
```

what happened? Did you get the 
```
 sudo /etc/init.d/gdm restart
 * Stopping GNOME Display Manager...                                     [ OK ]
 * Starting GNOME Display Manager...                                     [ OK ]

```
output?

Can you boot successfully off a LiveCD?

---

### Post by ozzyprv on 2009-06-09
> **OffAxis said:**
> does the Rescue Mode (terminal) work as expected?
It's just the x-server that's not working? 
Yes, rescue mode works okay.


> **OffAxis said:**
> 
when you used 
```

sudo etc/init.d/gdm restart
```

what happened? Did you get the 
```
 sudo /etc/init.d/gdm restart
 * Stopping GNOME Display Manager...                                     [ OK ]
 * Starting GNOME Display Manager...                                     [ OK ]

```
output?

Yes, I got that output. Then when I "see" Ctrl+Alt+F7 --> Black screen.


> **OffAxis said:**
> 
Can you boot successfully off a LiveCD?

I will try that (different version since I am running 9.04 kernes, i.e. no LiveCD) when I get home.
What would that tell you?

Thank you.

---

### Post by OffAxis on 2009-06-09
A liveCD would be the 'Is it a hardware problem?' litmus test, by not using the installed software / gnome setup. If the liveCD works fine, then you know it's probably a software configuration problem.
 (And, since you had something funny happen with your power that could have impacted your thermal management, it's a good place to start.)

---

### Post by ozzyprv on 2009-06-09
Thank you OffAxis,

Just loaded 9.04 with NO problem via LiveCD (ubuntu-9.04-desktop-i386). It must be a software problem then.


Rebooted right after, just for the sake of it, and ended up at the same black screen + mouse pointer....

What would you suggest I do next?

---

### Post by ozzyprv on 2009-06-09
Another update of my trials:

I tried "sudo dpkg-reconfigure xerver-xorg"
the "sudo /etc/init.d/gdm restart"

Same thing, black screen with mouse pointer.

Something I think I (and you) may have overlooked is this:

Different from the many, many posts I have read, I am able to get to the login/password screens (GUI). It is only after I enter the password that I get the black screen with only the mouse pointer showing.

Does that help?

---

### Post by anewguy on 2009-06-09
I would suggest using the command line and reinstalling your video driver - it may have gotten "bitten" in your power problem.  I made the mistake (while testing another PC) of plugging mine straight into the wall since the power strip was being used for testing, and wouldn't you know it - a car hit a power pole, power spiked, then fluctuated, then died.  PC had similar problem - in my case I ended up having to reinstall Ubuntu.

Dave :)

---

### Post by ozzyprv on 2009-06-10
> **anewguy said:**
> I would suggest using the command line and reinstalling your video driver -
Dave :)

Thanks Dave, I tried that too with no success.

---

### Post by ozzyprv on 2009-06-10
> **anewguy said:**
> ...in my case I ended up having to reinstall Ubuntu.
Dave :)


I gave myself 24 hours to solve the problem. I still know there was a fix, but I did not know it.

I am doing a fresh-install now, not happy about it, but that is life.

Thanks to all who helped me.

---

