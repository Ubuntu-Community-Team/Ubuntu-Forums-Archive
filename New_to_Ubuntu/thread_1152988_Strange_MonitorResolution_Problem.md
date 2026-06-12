---
title: "Strange Monitor/Resolution Problem"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by Meetloaf13 on 2009-05-08
So, it would be easiest for me to show you a picture of this, but my camera is broken and my phone's media card is going bonkers, however, I think i can explain it well enough.

If I were to split my monitor vertically into 5 regions like so:
AAA|BBB|CCC|DDD|EEE

normally you would see things on screen in proper order.  However, when I installed Ubuntu this morning on an older laptop, anything ubuntu renders shows up like this:

AAA|DDD|EEE|A|DDEEE

So that part of what I should see is mirrored, and part is missing.

I'm not savvy enough with ubuntu to get to the correct monitor settings, I don't know if it's a resolution problem or graphic driver problem.

I had Windows XP loaded and showing just fine last night, so I don't think it's the monitor.

The machine is a Dell Lattitude C80 (ANCIENT I know)  It has a dedicated 32mb graphics card. 

Thanks


EDIT:
Just got an image:
[http://picasaweb.google.com/meetloaf13/Misc02?feat=directlink](http://picasaweb.google.com/meetloaf13/Misc02?feat=directlink)

---

### Post by ptt49er on 2009-05-08
That sounds kind of like the problem I'm having, except it's more like the five regions are overlapping each other. If I don't change the resolution from the initial set up it looks good, except I cannot see the bottom or far right of the desktop. Then when I change the resolution to 1280x800 it overlaps and I can't see anything. I'm going to try using OpenChrome drivers tonight and see if that helps.

---

### Post by NightwishFan on 2009-05-08
If you go to recovery mode (ubuntu) in the bootloader, then you should be able to reconfigure the graphics. I do not think that would solve anything. Perhaps someone can tell you how to get to the one graphics recovery thing, it might allow you to use the vesa driver.

---

### Post by Meetloaf13 on 2009-05-08
Not sure if anyone saw my link to the picture, b/c I just did an edit.

Here it is:
[http://picasaweb.google.com/meetloaf13/Misc02?feat=directlink](http://picasaweb.google.com/meetloaf13/Misc02?feat=directlink)

---

### Post by unutbu on 2009-05-08
Open a terminal (Applications>Accessories>Terminal) and type
```

sudo lspci -nn > ~/Desktop/lspci.txt
cp /var/log/Xorg.0.log ~/Desktop/Xorg.0.log.txt
cp ~/.xsession-errors ~/Desktop/xsession-errors.txt
cp /etc/X11/xorg.conf ~/Desktop/xorg.conf.txt
```

This will create 4 files in ~/Desktop:
lspci.txt, 
Xorg.0.log.txt, 
xsession-errors.txt and 
xorg.conf.txt

Please post them as attachments here.

---

### Post by Meetloaf13 on 2009-05-08
Hah, quite exciting shifting windows around and "guess clicking" around to procure these puppies.  =]

Nonetheless, here they are:

EDIT:
Bah, didn't work.  Be right back...actually, you know what the 3 last files are all blank, I got this error when entering the last 3:

"cp: missing destination file operand after '/etc/X11/xorg.conf' " respectively for each command, what am I doing wrong?

---

### Post by unutbu on 2009-05-08
Sorry, my mistake. The commands should have been:

```
sudo lspci -nn > ~/Desktop/lspci.txt
cp /var/log/Xorg.0.log ~/Desktop/Xorg.0.log.txt
cp ~/.xsession-errors ~/Desktop/xsession-errors.txt
cp /etc/X11/xorg.conf ~/Desktop/xorg.conf.txt
```

---

### Post by Meetloaf13 on 2009-05-09
> **unutbu said:**
> Sorry, my mistake. The commands should have been:

```
sudo lspci -nn > ~/Desktop/lspci.txt
cp /var/log/Xorg.0.log ~/Desktop/Xorg.0.log.txt
cp ~/.xsession-errors ~/Desktop/xsession-errors.txt
cp /etc/X11/xorg.conf ~/Desktop/xorg.conf.txt
```

I'm having trouble seeing how that set of commands differs from the first.

---

### Post by Scunnered on 2009-05-09
You dont say what you are using it is Jaunty or what?  If Jaunty there are problems with Intel graphics which causes me problems with my display.

Current info indicates that it will not be fixed until 9.10 although there is a fix posted which claims to work.

---

### Post by Meetloaf13 on 2009-05-09
It is Jaunty, however, it is not an intel integrated graphics card, like I said, it's a dedicated card (ATI Mobility 4 32MB to be specific)

---

### Post by unutbu on 2009-05-09
The first time I posted, I included a ">" sign by mistake:
```

cp /var/log/Xorg.0.log **>** ~/Desktop/Xorg.0.log.txt  # WRONG
```

The correct command has no ">" sign:
```

cp /var/log/Xorg.0.log ~/Desktop/Xorg.0.log.txt
```

---

### Post by Meetloaf13 on 2009-05-09
Hah, don't I feel like an idiot :oops: ...thanks for being patient with me. =]

Here are the files, I had to split one of them because it was too large.

Also, I don't plan on running emerald, or compiz, or anything crazy. So if there's a vanilla graphics driver that would make things easier, let's go that route.

In fact, I was thinking of turning this computer into a little SSH tunneling server so I can learn how to do all that jazz.

Thanks!

---

### Post by unutbu on 2009-05-09
I noticed this in your /var/log/Xorg.0.log:

```
(II) R128(0): Configured Monitor: Using default hsync range of 31.50-37.90 kHz

```
Normally, the hsync for a monitor is in the range of 30-85 kHz.
Having a restricted hsync range could cause X to behave badly.

What is the make/model of your monitor? If you have a manual or specs for your monitor, please post the valid Horizontal Sync range and Vertical Refresh rate. Otherwise, we shall try to find out using google.

---

### Post by Meetloaf13 on 2009-05-09
It is a laptop monitor.  I cannot be sure of the make/model since it is rather old.  Like I said before, it is a Dell Latitude C800 (we're talking '90s baby).  Back in the day, the monitor was top of the line with a Max Resolution of 1680.

Here is the Dell OEM packing list re: the monitor:
1	7E889	SUB-ASSEMBLY..., LIQUID CRYSTAL DISPLAY..., THIN FILM TRANSISTOR..., ULTRA EXTENDED GRAPHICS ARRAY..., IBM..., MALAYSIA DIRECT SHIP...

---

### Post by unutbu on 2009-05-09
In a terminal type
```

gksu gedit /etc/X11/xorg.conf
```

This will pull up an editor with root privileges, so we can modify xorg.conf.

Change 
```

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection
```

to

```
Section "Monitor"
	Identifier "Configured Monitor"
	HorizSync 30-80
	VertRefresh 50-65
EndSection

```
Save and exit gedit.
Logout. Restart the X server by one of these methods:

[list]
[*] If using a pre-Jaunty release of Ubuntu, press Ctrl-Alt-Backspace to restart the the X server. 

[*]If using Jaunty, press Ctrl-Alt-F1. This should take you to a text console. Login, and type
```

sudo /etc/init.d/gdm restart

```
Then press Ctrl-Alt-F7 to get back to the (graphical) gdm login window.
[/list]

Log back in. 
If this does not fix the problem, please attach```


cp /var/log/Xorg.0.log ~/Desktop/Xorg.0.log.txt
cp ~/.xsession-errors ~/Desktop/xsession-errors.txt
cp /etc/X11/xorg.conf ~/Desktop/xorg.conf.txt

```
again.

---

### Post by Meetloaf13 on 2009-05-09
Unutbu, you are truly a genious.  That did the trick.  I running a full 1600x1200 pixels of uncombobulated glory.

Thanks!

=]

---

### Post by ptt49er on 2009-05-10
Okay...so I tried installing the OpenChrome display drivers and they didn't work. I've tried all of the advice here and on several other threads.

I've attached 3 of 4 files requested earlier in this thread. I'm working on splitting up the Xorg.O.log.txt file. It's too large to post.

---

### Post by unutbu on 2009-05-10
What resolution do you currently have? Is the screen messed up like Meetloaf13's was? What resolution are you looking for?

What happened when you added 
```

Section "Monitor"
	Identifier "Configured Monitor"
	HorizSync 30-80
	VertRefresh 50-65
EndSection
```

to your xorg.conf? Perhaps edit xorg.conf as described in post #15, and then repost xorg.conf.txt, xsession-erros.txt, Xorg.0.log.doc

---

### Post by ptt49er on 2009-05-10
I added that to my xorg.conf file before I posted. My screen looks just like Meetloaf13's.

The resolution is set at 1600x1200 from install. I need 1280x800 for my laptop.

---

### Post by unutbu on 2009-05-10
The xorg.conf.txt that you attached to post #17 suggests that you have not 
yet edited your /etc/X11/xorg.conf.

Make sure you run 
```

gksu gedit /etc/X11/xorg.conf 
```

to get root privileges. Otherwise, you will not be able to save the changes.

---

### Post by ptt49er on 2009-05-10
That's the command I'm running and it's bringing up the text file in the editor with those changes showing up.

I think I forgot to run the restart command. Which I ran and it changed the output file.

The display manager showed 61 hz, which it hadn't shown before. But when I change the resolution it got all garbled again.

Now it's garbled again and I can't get it to change back. Guess I'll have to reinstall  Ubuntu.

---

### Post by ptt49er on 2009-05-10
unutbu...thanks for your help! I figured it out. Your questioning about my xorg.conf file got me to thinking.

I found this post on Friday and didn't realize I could just copy and past his xorg.conf file into my own.
[http://ubuntuforums.org/showthread.php?t=1069323&highlight=nm3500w](http://ubuntuforums.org/showthread.php?t=1069323&highlight=nm3500w)

So I did that, reloaded the file and it works perfectly.

Thanks again!!

---

### Post by unutbu on 2009-05-10
Fantastic. Congratulations! :)

---

