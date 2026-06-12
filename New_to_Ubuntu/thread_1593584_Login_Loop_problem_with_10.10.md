---
title: "Login Loop problem with 10.10"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by mistypotato on 2010-10-11
Hi,
I just installed 10.10 on my mom's Presario and for some reason, it will get to the point where I log in, but then it flashes the desktop for about a 1/2 second then seems to log me out and loop back to the login screen.

I cannot get out of this loop.

Any idea what I could try?

Thx

---

### Post by Slarty Bardfast on 2010-10-12
I'm having a similar issue.  I log in, screen goes black for a sec, then goes right back to the login screen.  I can log into the cli no problem and I've tried renaming my xorg.conf.  At that point I just get a black screen at login.  I can ssh to my box but even after I kill gdm it stays black and I've had to reboot.  I've also tried re-installing my NVIDIA drivers a bunch of times but no go.  I created a new user to see if it was maybe a profile issue but the same thing happened.  I'm going to try a dpkg repair from the recovery console when I get home from work.  I guess I can try pulling the video card but I can't remember if the motherboard on that machine has onboard video or not.  I had a look at syslog and xorg.0.log but couldn't see anything too weird except for some mouse errors.  Any suggestions?

---

### Post by mistypotato on 2010-10-13
The only way I've been able to get past the problem is to change to SAFE GRAPHICS MODE using the SESSION box on the task bar at the bottom of the screen.

You'll only see it after choosing the User.

At the bottom of the screen on the taskbar (or status line) you should see something near the middle about SESSION.

There should be an option to change to SAFE graphics mode.

Then I get in ok...but in safe graphics ode of course.

---

### Post by Gorban on 2010-10-13
I have the same problem.

I managed to login by doing this:

Start the computer
Enter grub
Choose recovery mode
Choose root
Enter root password
Run "startx"

---

### Post by PPPilot on 2010-10-13
I've run into this problem. Ubuntu has problems with video after login. As near as I can tell Ubuntu displays the login screen at the highest resolution your video card can produce. In my case that is 1600x1200. I am running Ubuntu Video Drivers. As long as I leave it at that setting I can login most of the time. I say most of the time because from time to time I have to login a couple of times to get in. If I set the resolution lower once I'm in and then logout or reboot, I am in the login loop. This is loging into a Gnome Session. If I login to a KDE Session, I do not have the problem because any change I make to the desktop resolution makes no difference when I logout or reboot. It does not loop the desktop just comes up at 1600x1200 no matter what. I've been experiencing this on all versions starting with 9.04 through 10.04. Time will tell how 10.10 will respond.

---

### Post by moonguide on 2010-10-16
> **Gorban said:**
> I have the same problem.

I managed to login by doing this:

Start the computer
Enter grub
Choose recovery mode
Choose root
Enter root password
Run "startx"
I have the same problem. Here's what I get following your procedure, mostly:

Power up.
Grub comes up (I'm dual booting with Ubuntu 9)
Select Ubuntu, with Linux 2.6.35-22-generic (recovery mode)
Recovery Menu presented:
  resume      Resume normal boot
  clean       Try to make free space
  dpkg        Repair broken packages
  failsafeX   Run in failsafe graphic mode
  grub        Update grub bootloader
  netroot     Drop to root shell prompt with networking
  root        Drop to root shell prompt

Choosing "netroot" gives me a shell with a prompt:

root@Frodo:~#

Typing "startx" takes me to a screen with the new background graphic, but nothing else. No response to the keyboard or mouse. Power cycling needed to try again.

Choosing "root" produces that same results as "netroot" (not surprising).

Choosing "FailsafeX" starts to do something, but then fails with a message that disappeared before I could read it. I did see that I should look at /var/logs/Xorg.failsafe.log. That showed me a lot of stuff I don't really understand, but it eventually got to a line that says

Fatal server error: 
[    24.448] no screens found

Choosing "dpkg" told me:

The following packages will be upgraded:
  libvte-common libvte9 linux-headers-2.6.35-22
  linux-headers-2.6.35-22-generic linux-image-2.6.35-22-generic linux-libc-dev
  python-vte update-manager update-manager-core
9 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 47.3MB of archives.
After this operation, 4096B of additional disk space will be used.
Do you want to continue [Y/n]?

Answering "Y" started a few minutes of upgrading, followed by a request that I hit <ENTER>, which led back to the Recovery Menu.

I tried "resume" and was prompted for a loging in text mode. After logging in I ran startx. I got the purple background screen, but nothing else.

Any recommendations on where to go from here?

---

### Post by moonguide on 2010-10-17
RESOLVED

(For each of the following I chose to boot into recovery mode from GRUB.)

Alas, I did not keep notes on where I got the answer (it was on this forum, I think in one of the 10.04 threads), but here's the steps I took to get my 10.10 install working:

I renamed ~.ICEauthority and ~.Xauthority, prefixing them with "old" so I could change them back if I needed to. I did them one at a time. Neither change made any difference -- I still had the login loop.

One recommendation said to add the following to /etc/X11/xorg.conf:

Section "ServerFlags"
Option "AIGLX" "off"
EndSection

I rebooted, letting GRUB make the default choice, and successfully logged in to 10.10.

I didn't have an xorg.conf file, so I created one with nano. (If you are like me you might not know about nano. It's a text file editor like vi or vim.)

---

