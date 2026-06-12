---
title: "Waiting mouse cursor after installing Xfree86 on jaunty"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by MykalMunlight on 2009-05-08
Installed Ubuntu Jaunty on my Dell Optiplex GX240 1.8 ghz pentium 4, 256MB RAM, ATI Pro Rage 128 vid card, 80GB HD; from Ubuntu Live CD. Everything worked fine except I only had 800x600 Display or lesser in display options. I hunted down an xorg.conf file from someone that had the same card and their file info on here. Modified my xorg.conf to match using gedit. this gave me 1024x768!

     I tried enabling enhaced graphics or using compiz and no dice. Also my Video and flash video looked like they were running @ 10fps. So I read some more posts about my ATI graphics card and found (in the same post as the xorg.conf file) that someone had all these features and great video with xfree86 on Ubuntu Hardy(post is 2 or 3 years old). So I downloaded and installed xfree86 gl24 and installed it using "sh Xinstall.sh" per instructions on their site. 
     First I got a silly mouse error about input dev 0 not being installed after doing xf86config. I redirected it to /dev/input/mice driver. Now when I start my computer all I get is a blank screen with a mouse cursor doing it's thinking circle with the dots moving. I can move the mouse around the screen but after waiting for 10hrs The logon screen still hasn't loaded. I can access the Terminal with ctr+alt+F#1-6. 
     All I want is my Gnome back and I dont want to lose my data. Can someone help me either fix what xfree86 has done or reinstall xorg. (tried apt-get install xserver-xorg and it tells me it's already latest version). I am a newbie and have been learning linux for a week. Searched forums for the last two days and found nothing similar. So now I am writing this on my Moto Q. 
        Thanx in advance.:confused:

---

### Post by dvl300 on 2009-05-08
re-install Ubuntu with the live CD
then update via internet, that should sort out
your initial resolution problem by installing a
graphics driver

you may have to allow the driver as well to run

---

### Post by MykalMunlight on 2009-05-08
Wanted to avoid reinstall. using gprs modem cnnection and it would take forever to redownload the apps. Also I don't want to lose all the other stuff I have stored on there. Thank you for your speedy anwer. I switched to Ubuntu because I heard it was easy to recover from problems like this. Are there any other options. I don
t want to reinstall every time I encounter a problem.:(

---

### Post by dvl300 on 2009-05-08
there should be a repair option when you boot ubuntu
try that

---

### Post by MykalMunlight on 2009-05-08
> **dvl300 said:**
> there should be a repair option when you boot ubuntu
try that

It doesn't give me the recovery menu. Just says enter root password for maintenance or press ctrl+D to continue. Ctrl+D continues boot to thinking mouse cursor. This is after hitting esc in Grub and Choosing recovery mode.

---

### Post by dvl300 on 2009-05-08
then enter your password

---

### Post by achase79 on 2009-05-08
in recovery mode type "xfix"

---

### Post by MykalMunlight on 2009-05-08
That takes me to Terminal screen.

---

### Post by dvl300 on 2009-05-08
Remove fglrx packages
then reboot

---

### Post by MykalMunlight on 2009-05-08
> **achase79 said:**
> in recovery mode type "xfix"

bash: xfix: command not found

---

### Post by MykalMunlight on 2009-05-08
> **dvl300 said:**
> Remove fglrx packages
then reboot

apt-get remove xfree86-driver-fglrx
xfree86-driver-fglrx is not installed so not removed.
ditto for org.

---

### Post by MykalMunlight on 2009-05-09
I AM SUPERHUMAN!!! I fixed it. Deleted X11 and X11R6. Booted live CD and copied the files from live session to my desktop via terminal. Rebooted to maintenance terminal and copied files to appropriate directories from desktop. Rebuilt xorg.conf and rebooted. Houston we have Gnome!:popcorn::KS

---

### Post by Ptero-4 on 2009-05-09
BTW: If your card is the ATI Rage 128 (and not a Radeon with 128MB VRAM) it doesn't use propietary drivers and cannot do compiz.

---

### Post by MykalMunlight on 2009-05-09
Found a fix for compiz on ATI also. So my video card is no longer blacklisted. \\:D/

---

### Post by LilJohn!! on 2009-12-02
> **MykalMunlight said:**
> I AM SUPERHUMAN!!! I fixed it. Deleted X11 and X11R6. Booted live CD and copied the files from live session to my desktop via terminal. Rebooted to maintenance terminal and copied files to appropriate directories from desktop. Rebuilt xorg.conf and rebooted. Houston we have Gnome!:popcorn::KS
I'm having the same problem that you had in regards to the "Waiting mouse cursor after installing Xfree86 on jaunty", but I am not quite as capable with Terminal or knowledgable with Ubuntu as you appear to be, so could you please explain in a little greater detail how I go about repairing?

When I do a search for x11 and x11r6 there seem to be more than a dozen different folders with those names...  which do I copy and delete?

---

