---
title: "Blank screen on boot, following display driver insteall"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by abo999 on 2008-12-16
Hi! I'm brand new to Ubuntu, and have a bit of a problem...

I've installed 8.04 on my laptop without a hitch :D My desktop has not been so straightforward. At first I had problems getting it to boot at all (it was seeing my HDDs as SCSI devices instead of IDE, fixed now). 

Anyway, got it installed and working last night, added some applications and then installed the ATI display driver for my card.

This was a bit of a mare but appeared to get there in the end, and asked to restart the machine. It was past midnight so I switched off and went to bed.

This morning, the machine starts to boot, with the Ubuntu logo appearing in nice hi res but after a short while the display goes black; the monitor is not going to standby, it is just displaying a blank black screen. I *think* this happens when it should go peach(what is that colour lol), and ask for my username.

The machine boots fine from the live DVD. Is there a way to repair it? I guess I could just reinstall seeing as I have nothing important on there at the moment, but I'd rather learn how to fix it if possible instead of copping out with a reinstall.

Cheers

---

### Post by cdtech on 2008-12-16
Boot into the recovery mode (this puts you into a command line only screen) log in (normal user account) then type:
```
sudo dpkg-reconfigure xserver-xorg
```
This will reconfigure your xserver.

Hope this helps ya......

---

### Post by abo999 on 2008-12-16
Well,I get to enter my username and password now! Unfortunately the screen now goes white instead of seeing the heron, and there are no toolbars or icons to click.

---

### Post by abo999 on 2008-12-16
Sorted it. It seems there is some sort of conflict between the driver and a couple of the Ubuntu updates. I'll start a thread on that...

---

