---
title: "Server version 8.04 - monitor says &quot;out of range&quot;"
date: 2010-07-08
forum: New to Ubuntu
---

### Post by etlarue on 2010-07-08
I am just getting in to ubuntu, so I downloaded the server version to see what it could do.  I installed everything and it seemed to work fine, but when I boot up ubuntu, my monitor says "out of range."  I discovered that this usually means that the monitor I have can't handle either the refresh rate or the screen resolution.  I've searched and found some "possible" solutions on how to change the resolution/refresh rate - none of which have worked.  Here are the commands I've tried:

> 
xrandr --output VGA --mode 1024x768

sudo dpkg-reconfigure xserver-xorg

$ sudo dpkg-reconfigure xserver-xorg

rm~/.config/monitors.xml

xrandr --addmode VGA 1280x760

cat /etc/X11/xorg.conf


Again, I don't know anything about the commands you can give to ubuntu, so I was just typing things in that I found on forums and on the internet.

All of the above commands told me either "Invalid file name (or something like that)" or "Command Not Recognized"

If anyone can help me out, that'd be great!

Thanks,
LaRue

---

### Post by cariboo on 2010-07-08
We need more information.

[list=1]
[*] Are you running a gui?
[*] What make and model of video adapter does your system have?
[*] What type of monitor are you using crt/lcd?
[/list]

---

### Post by etlarue on 2010-07-08
1. No gui - I was told that this was a command-line based interface only.  I turn on the computer and in the boot menu, I select the Ubuntu server and it starts loading up.  Then the screen goes blank and says "out of range"

2. I don't know much about hardware, but I opened up my computer and looked at the video card.  It said this: Reality 334 SGRam 4MB AGP - I found out that a video card called "Number Nine Reality 334" does exist, so that may be it.  This is a computer that's about 11 years old if that helps.

3. LCD monitor

---

