---
title: "Dual Widescreen Issues"
date: 2009-10-26
forum: New to Ubuntu
---

### Post by BarePaw on 2009-10-26
I used to run one widescreen and one standard size monitor with my 9.04 desktop. Now I have a second widescreen and I'm having trouble setting it up. I'm running an nvidia 5200 dual vga card. When I go into the nvidia xserver settings, it still sees the second monitor as a standard size and only gives me the option of 640x480 or 320x240. When I click <Detect Displays> nothing changes. I tried reformatting and that didn't work either. It still shows up as one widescreen and one standard. What do I need to do to get it to work? Thanks.

---

### Post by tomBorgia on 2009-10-28
Hi,

It's a pain but you'll probably need to manually edit the /etc/X11/xorg.conf file...

[https://help.ubuntu.com/community/XORGHardy]("https://help.ubuntu.com/community/XORGHardy")

MAKE A BACKUP OF THE FILE FIRST!!!

And good luck ;-)

---

### Post by BarePaw on 2009-10-28
I've edited xorg.conf trying several different resolutions and aspect ratios. The monitors in the Xserver Settings always maintain their (incorrect) aspect ratios. When I use a larger resolution like 2048 (which should be fine for these two monitors) they don't cover the whole virtual monitor and moving the mouse off the side moves it back and forth.

---

### Post by tomBorgia on 2009-10-30
Can you post your Xorg.conf file... I've had to mess around a fair bit with it in the past but these days linux is a lot better at doing these things automagically... it's the more non-standard setups that require a bit more messing around!

---

