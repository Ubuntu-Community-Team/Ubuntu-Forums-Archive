---
title: "Having Issues Setting up External Monitor"
date: 2010-02-25
forum: New to Ubuntu
---

### Post by -memetic- on 2010-02-25
I cannot get the monitor to display at the correct resolution. I can only get the monitor to run in 600x800. And, when I try to turn off mirror displays it doesn't work -- the monitor goes black (except sometimes I can see the cursor/pointer on the left side of the display, but it doesn't move). I have searched, but cannot find any help getting this setup right. 

I hope someone can please help me because all my son's educational videos are on an external drive and he cannot view them on the laptop. Any help would be much appreciated.

I am running 9.10
The monitor is a 52" Sharp Aquos (current model)
The laptop is an Eee 1005HA (video out through VGA)

If any other info is needed I will gladly provide it. Oh, and hi everyone. Thank you

---

### Post by smmalmansoori on 2010-02-25
I think when you mirror displays it chooses the lower resolution of the two monitors and use it on both, so try either to extend the display or set the Sharp monitor as main monitor then choose single display.

---

### Post by sandyd on 2010-02-25
I havent used intel cards before, but its likely that the video card (or its drivers) doesnt support plugging that kind of monitor .
This type of configuration is called a dual screen configuration.
have you tried using a smaller monitor and seeing if it works?

---

### Post by wangsuda on 2010-02-25
One thing I have noticed is that the resolution of the first and second monitors must be matched for a successful mirroring. Before you mirror the device, make sure the resolution setting matches one available for your computer monitor.

---

### Post by -memetic- on 2010-02-25
Thanks for the replies.

I don't want to mirror at all, I want to use the aquos as the primary (and only) display. So far, I cannot turn off mirror. If I turn it off, I get blank screens.

I know the laptop can work with the tv because when I had win7 installed I could use the tv just fine. This is specific to me not knowing how to do it in ubuntu. I thought this was going to be easy seeing how far linux has come since I used it last some ten years ago. 

I did find a tutorial at the eeeuser forum that never came up using searches. I stumbled upon it coincidentally after I posted this thread. I am going to have at it and see what happens. Unfortunately, it is more time consuming than I would prefer. If anyone has a quick solution please let me know.

Thanks again.

---

### Post by wangsuda on 2010-02-25
> **-memetic- said:**
> Thanks for the replies.

I don't want to mirror at all,You should be able to turn off the computer monitor while leaving the other set on. See attached screen shot.

---

### Post by -memetic- on 2010-02-25
Where is the attachment?

---

### Post by wangsuda on 2010-02-25
> **-memetic- said:**
> Where is the attachment?

Sorry, hit post too quick. It's there now.

---

### Post by -memetic- on 2010-02-25
Yes, that is what I did. Didn't work.

---

### Post by wangsuda on 2010-02-25
Sorry. I am out of ideas. I hope someone else can give you the advice you need. Good luck!

---

### Post by 23dornot23d on 2010-02-25
Have a look at this thread ..... go to where tjc has posted ...... Posted: Wed Sep 30, 2009 10:00 pm 
its an old post ..... but best I can do ......
 
[http://mysettopbox.tv/phpBB2/viewtopic.php?p=125953&sid=adb9ca96de6e5d317f56c6ccf01ab943](http://mysettopbox.tv/phpBB2/viewtopic.php?p=125953&sid=adb9ca96de6e5d317f56c6ccf01ab943)


Check your xorg.conf file see if it has similar settings ..... to these ...... these are just for the 52"
you will have to check for running dual mode ...... as I could not find much information on this TV
being used as a monitor .....

But ...... 

I would expect to see something similar to below ..... to sort the resolution out
(  You say you ran it from windows on vga before - can you say what resolution it was at  ?  )

Section "Screen" 
        Identifier "Screen0" 
        Device     "Card0" 
        Monitor    "Monitor0" 
        DefaultColorDepth 24 
        SubSection "Display" 
                Depth     1 
                Modes "1920x1080_60i" "1280x720_60_0" "720x480_60" 
        EndSubSection 
        SubSection "Display" 
                Depth     4 
                Modes "1920x1080_60i" "1280x720_60_0" "720x480_60" 
        EndSubSection 
        SubSection "Display" 
                Depth     8 
                Modes "1920x1080_60i" "1280x720_60_0" "720x480_60" 
        EndSubSection 
        SubSection "Display" 
                Depth     15 
                Modes "1920x1080_60i" "1280x720_60_0" "720x480_60" 
        EndSubSection 
        SubSection "Display" 
                Depth     16 
                Modes "1920x1080_60i" "1280x720_60_0" "720x480_60" 
        EndSubSection 
        SubSection "Display" 
                Depth     24 
                Modes "1920x1080_60i" "1280x720_60_0" "720x480_60" 
        EndSubSection 
        SubSection "Display" 
                Depth     32 
                Modes "1920x1080_60i" "1280x720_60_0" "720x480_60" 
        EndSubSection 
EndSection




Its not the simple fix you might be looking for ..... but it might help point you in the right direction

/etc/X11/xorg.cong 

was where all the settings for the monitor used to be stored ..... and if the settings are in there the system
should still use them ...... unless anybody else knows different ...... things change so quickly ......

( grub2 setting the display up then stopping it - then it being restarted again .... in gdm ...... ( xorg ? ) then Hal ..... )

( all ..... getting rather complex for this old man ...... soon it will be all automatic ......)

But I hope at least that this is a lead into how to sort it out ......

If you could run the screen ok at these resolutions above from Windows ..... 

Then I would expect the possibility is good for linux to do the same too .....


This may be too much information .... for the Absolute Beginner thread ...... but this is possibly the only
way to answer this question on what to search for as a problem cause ........ [B]
for the resolution not being set up properly[/B].



If you want to know more about xorg.conf look here .... [http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html](http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html)

---

### Post by -memetic- on 2010-02-26
I followed the tutorial with no luck.

The problem is if I try to set the resolution to the external monitor higher than the 1824x600 default, both screens go blank and I have to power down using the power button. Anyone experience this before?

---

### Post by -memetic- on 2010-02-26
The resolutions are all there I just can't get them to work. Anytime I try to change from the default resolution (the resolution that is automatically selected when I plug an external monitor in) I loose both monitors -- they go black. 

I can't find a single thing about this anywhere.

---

### Post by 23dornot23d on 2010-02-27
Can you post the contents of the following file here please xorg,conf

do this comand in a terminal window .....

gedit /etc/X11/xorg.conf

save it to your desktop by just doing save as ...... xorg.conf ...... choosing the Desktop as the place
to save it ......


Then post it here ......... so we can see it ...... ty

---

### Post by hobo14 on 2010-02-27
Here's a guide I wrote detailing my experience with what might(?) be a similar situation.

[http://ubuntuforums.org/showthread.php?t=1346125]("http://ubuntuforums.org/showthread.php?t=1346125")

---

### Post by -memetic- on 2010-02-27
> **23dornot23d said:**
> Can you post the contents of the following file here please xorg,conf

do this comand in a terminal window .....

gedit /etc/X11/xorg.conf

save it to your desktop by just doing save as ...... xorg.conf ...... choosing the Desktop as the place
to save it ......


Then post it here ......... so we can see it ...... ty

The file appears blank.

---

### Post by -memetic- on 2010-02-27
> **hobo14 said:**
> Here's a guide I wrote detailing my experience with what might(?) be a similar situation.

[http://ubuntuforums.org/showthread.php?t=1346125](http://ubuntuforums.org/showthread.php?t=1346125)


Working on that now. I'll let you know the results. rThank you.

---

