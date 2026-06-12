---
title: "Monitor unknown, can not change resolution"
date: 2011-02-26
forum: New to Ubuntu
---

### Post by VTT Alps on 2011-02-26
Just loaded 10.10 on my Dell Inspiron mini.  When I try to adjust the screen resolution, it says my monitor is unknown, and I can't change anything.   This computer came pre-configured with Linux from Dell and was loaded with version 8.04.   I don't understand how it worked in 8.04 and in 10.10 it can't find the drivers, or know what the monitor is.  

Thanks

---

### Post by vivek.pandey on 2011-02-26
have you tried this system->monitors ?
what type of laptop is it showing their i mean in monitor prefernces window ? also you can try detecting monitor

---

### Post by VTT Alps on 2011-02-26
I have been to System / Preferences / Monitor.   I tried to detect monitor and nothing happens.

---

### Post by realzippy on 2011-02-26
Does the working 8.04 system still exist?

---

### Post by VTT Alps on 2011-02-26
No, I loaded 10.10 and 8.04 is gone.  I still have the 8.04 disk they sent me

---

### Post by realzippy on 2011-02-26
> **VTT Alps said:**
> No, I loaded 10.10 and 8.04 is gone.  I still have the 8.04 disk they sent me

is it a Live CD?
Anyway,your 8.04 contains a file:
 /etc/X11/xorg.conf

which might help when copied to 10.10...

---

### Post by vivek.pandey on 2011-02-26
on terminal type command
 xrandr

without parameters it gives you the supported resolutions, and you can set the resolution using:

xrandr -s <resolution index from the resolutions list>
or
xrandr -s <x_res>*<y_res>

for more help see the manual page of xrandr

---

### Post by realzippy on 2011-02-26
There won't be higher resolutions available in xrandr....
btw,we are in Absolute Beginner Talk


@ OP

assuming you want a higher resoluion,sorry.
You did not say what you want to set.....

---

### Post by VTT Alps on 2011-02-26
I searched the 8.04 disk.  Did not find a file called xorg.conf

I think it is a live CD that will book Ubuntu.  It might be in there, but it is compressed into a larger file.

Is there an other place I can get the file.

Thanks.

---

### Post by realzippy on 2011-02-26
If it is a liveCD,the file will be there when running.

I am sure the DELL Ubuntu stuff is out there,google for it.
Even think there used to be an own DELL thread here in the forum...



Due to soccer time in Europe right now  --sorry  ;-)  
I am out for 120 minutes...

---

### Post by VTT Alps on 2011-02-27
I have searched everywhere for the xorg.conf  file on the net.  I am not finding it.   Dells site has a drive for a  Matrox G200ew.   Not sure if that is what I need.  It is also a .tar file.   Tried to load it, but not sure how to unpack it and make it work.  

In regard the the 8.04 disk I have.  I dont have a cd drive for my mini.  Can I just copy the files from the live disk on to a USB drive and boot my mini that way.   Then get the xorg.conf file I need

---

### Post by realzippy on 2011-02-27
... open a terminal (Applications menu -> Accessories -> Terminal),paste in:

```
lspci | grep VGA
```

and post the output,so we know which graphics device you are running.

---

### Post by VTT Alps on 2011-02-27
This is what I get

cwa@cwa-Inspiron-1010:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller (rev 07)

---

### Post by realzippy on 2011-02-28
googling
"Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller (rev 07) ubuntu"
gives this:
[http://ubuntuforums.org/showthread.php?t=1229345](http://ubuntuforums.org/showthread.php?t=1229345)
which should be helpful.

...feel free to ask.

Edit: replace "aptitude" in the commands with "apt-get"

---

### Post by VTT Alps on 2011-03-01
That's, too much for me to understand.  And there are 337 pages to that thread.  It's overwhelming to me.   

OK, new plan.  I will pick up a external CD drive for my netbook,  then boot 8.04.   Then copy the xorg.conf.   then copy the file to the /etc/X11 in 10.10 like you originally suggested.   

If that doesn't work, OK, at least I have a CD drive to reload 8.04  

I will post the results once my external CD drive arrives. 

Cheers for now.

---

### Post by realzippy on 2011-03-02
*That's, too much for me to understand.*

...it looks harder than it is.
Could reduce it to a few commands you only had to paste into terminal.
Problem is:
There is a special driver for your graphics device,only pasting
it's xorg.conf won't do it,if you want compiz to work.
Recommend to test the instructions from that link,let me know if you want this.

---

### Post by VTT Alps on 2011-03-02
If I understand correcly.  Even if I get my xorg.conf from 8.04 it won't work.  I have to upload a driver and do to something with "compiz" ??

OK, I will follow steps 1-14 on the first post of the link you sent me and keep my fingers crossed.

Question:  Step 3 mentions to do something different if I have 1 or 2 gig of ram.  How do I determine how much ram I have.  

I will post the results.  

Thanks.

---

### Post by realzippy on 2011-03-02
Should only go to step 8,after reboot your resolution should be available.
If this has worked,go on ...
Compiz is that desktop effects thingy you might have heard of....

```
cat /proc/meminfo
```
shows your RAM.

---

### Post by VTT Alps on 2011-03-02
That worked.  I can now control my resolution.   Did not load compiz.  I have no idea what it is, and the description after a few google searches didn't help.   

Note:  when I added the lines to my xorg.conf file in step 7,  I commented out the other lines.  That was a mistake.  That made the screen go blank.  Had to run off the USB live disk and un-comment the lines.   Then everything worked fine.

Thanks a lot for your help.  I really appreciate it.

---

### Post by realzippy on 2011-03-03
You are welcome.

Don't bother with the missing desktop effects (compiz),
in another dell mini thread it was mentioned that it does not
work flawlessly with that driver....
Have fun.

---

