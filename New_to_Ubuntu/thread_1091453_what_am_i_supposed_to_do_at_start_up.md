---
title: "what am i supposed to do at start up?"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by DElliottJr on 2009-03-09
this may or met not be the forum to discuss this but what is supposed to happen when i log into ubuntu? i dont think it supposed to be a blank screen(nice beige color!) if it is then hey im in luck! in the lower left corner at log in it gives options am i supposed to start from there? or i dont evn know

---

### Post by llamabr on 2009-03-09
Do you get a chance to log in with your username password?  or do you even get that far?

If the former, try adjusting some of the settings at the bottom before logging in.  Make sure you've chosen Gnome, english, etc.

If the latter, what exactly do you see at the bottom?

---

### Post by DElliottJr on 2009-03-09
yea ican put in my username password and then nothin... i've chosen gnomeandnothing from there either. the only thing i can do is failsafe terminal. and as a super green newbie i have no idea what to with it! this how i'm going to learn though! so any and all advise is very greatly appreciated!!

---

### Post by Temposs on 2009-03-09
Please tell as much as you can about the specs of the computer you're running, so we can determine if there are any issues with your hardware.

---

### Post by DElliottJr on 2009-03-09
dell inspiron 1100
celeron 2.3GHz
20.gb hdd
320.gb external hdd
1152Mb ddr pc2700 ram
i845gl chipset

6 yrold p.o.s. :o
;) thank you!!

---

### Post by ajgreeny on 2009-03-09
Are you certain the CD you used to install the system is OK?  Boot to that and choose the option to check the CD.  You could also run ```
md5sum ubuntu-8.10-desktop-i386.iso
```on the file you used to burn the CD and check it is correct.

That assumes you used that iso file. of course; if it was another, change the name in that command.  You will need to do that using the live CD with the iso on a usb flash drive or disk, as you will probably find it easier than using the command line in your installed ubuntu, assuming you can get to that.

Any more info needed, come back again.

---

### Post by DElliottJr on 2009-03-09
yea i've checked the md5 sum and ran disk check everything was fine.. i've made so many of these! for 8.04,8.10 desktop.. 8.10 alternate and even linux mint 6 desk top and nonoe of them work! and now grub has decicec it doesn't want to boot xp! so my laptop is just about useless!

---

### Post by avtolle on 2009-03-09
Wondering if the OP has run into this "known problem": [http://www.ubuntu.com/getubuntu/releasenotes/810#Hangs%20with%20desktop%20effects%20on%20Intel%20830MG%20and%20845G%20video%20cards](http://www.ubuntu.com/getubuntu/releasenotes/810#Hangs%20with%20desktop%20effects%20on%20Intel%20830MG%20and%20845G%20video%20cards)

---

### Post by avtolle on 2009-03-09
You have tried to log in using "safe graphics mode" chosen from Session at the bottom of that page (as I understand your initial post)? 

At the failsafe terminal, have you typed "xfix" (I believe this is the command) or "startx" (without the quote marks, of course)? I'd try the first one and see what occurs, post error messages here.

---

### Post by DElliottJr on 2009-03-09
well im going to re-instell in safe graphicd mode i found a bug with my graphics card on that page you posted. good loo:Dkin out!! you have no idea how long i scoured the internet looking for that!! thank you!!

---

### Post by avtolle on 2009-03-09
You are welcome. Good luck, and post back with any questions, and (of course) if it worked.

---

