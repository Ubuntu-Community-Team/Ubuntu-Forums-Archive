---
title: "Can not log into 9.04 now"
date: 2009-08-23
forum: New to Ubuntu
---

### Post by pme 72 on 2009-08-23
Yesterday afternoon I removed and reinstalled my video card driver, fglrx. All seemed well. This morning on boot I saw the Ubuntu logo and the loading line underneath. The logo disappeared as usual. Then some unfamiliar script moved past the top of the screen. I did see what appeared to be my log in prompt in regular script. The script flashed off and on and then I was presented with a mostly black screen. There are a couple of faint colored specs just at the top of the screen. Nothing else happens.

I tried again and attempted to enter my login info but the scripts go by too quickly. I tried to use my Pause button to freeze the scripts but that did not work. 

I tried to boot into an earlier kernel but the same thing happened. 

I tried cntl-alt-F1 from the black screen to get to a terminal but nothing happens. 

I have a 9.04 32bit installation where I am writing this now. It loaded fine. I am able to mount the inaccessible distribution from here.

Is it possible to resurrect the ailing partition?

---

### Post by jimmy the saint on 2009-08-23
hit ctr-alt-f3 (or f4 or f5..) and type "startx" without the quotes.  If that fails, try to reinstall the driver, then try a different driver.  ctr-alt-f3 will get you to another terminal.  ctr-alt-f7 will get you back to the default.

---

### Post by pme 72 on 2009-08-23
Thank you for the reply. I can not seem to gain access to a terminal at any point in the login/boot process or after the screen turns black. I have tried cntr-alt-F1 (through -F11) nothing.

---

### Post by bresdog on 2009-08-23
I've actually just done something very stupid and left myself with pretty much the exact same problem. Where you installed your video card i was trying to find a fix for a problem i've been having, when playing video my laptop would crash. Entered this command -

sudo dpkg-reconfigure -phigh xserver-xorg

Is there anyway of undoing this command? Bear in mind, like above i've got a black screen, with red characters along the top. I tried loading earlier kernels and thats not worked, and there was also an option to auto-fix graphics problem, that ddn't work but it did bring up this-

/etc/x11/xorg.conf.20090823182035

Im assuming this is the location of the original config i just changed?

---

### Post by SuaSwe on 2009-08-23
Sounds like a backup, yes.

Open /etc/X11/xorg.conf and /etc/x11/xorg.conf.20090823182035 side by side and see if they are mostly the same file, and if so, what's changed. I couldn't swear but I should think that if it looks like /etc/x11/xorg.conf.20090823182035 is a backup, you should be able to just rename it to xorg.conf and replace the new one with it.

---

### Post by pme 72 on 2009-08-24
Thank you jimmy the saint. I booted into Recovery Mode. Choosing xfix did not solve the issue but removing the fglrx driver and rebooting allowed me to log in. Many thanks.

---

