---
title: "How do I boot in safe mode?"
date: 2010-05-27
forum: New to Ubuntu
---

### Post by Hex99 on 2010-05-27
Hi there,
I was messing with the xorg.conf file trying to hack my sis m672 graphics card but to no avail. Instead I now get a screen that is completely unreadable/usable.

I know there is a safe mode that ignores the video-settings i can boot into but I am not sure what keys to press to get it.
Anyone have any advice please, as until i sort this I have an expensive paperweight with some colour on the screen.

Thanks.

---

### Post by Ozymandias_117 on 2010-05-27
Hold shift during Boot and it will pull up GRUB boot loader. Select the one closest to the top that has (Recovery Mode) on the end. It will boot to a list, There is something there about repair VGA or safe VGA, something like that. Try it out.

---

### Post by Hex99 on 2010-05-27
> **Ozymandias_117 said:**
> Hold shift during Boot and it will pull up GRUB boot loader. Select the one closest to the top that has (Recovery Mode) on the end. It will boot to a list, There is something there about repair VGA or safe VGA, something like that. Try it out.
 
THANK you!
It worked even though the thing is very hard to use because my screen flickers at boot-up so you just see stuff scrolling at high speed, luckily I managed to select the right option even in this way and got my system back.
No wonder you kicked butt in the Watchmen kind sir!
 
Now if only someone could tell me how to get my F&H laptop to display in its full 1366x768 range instead of only 1024x768 Best I could manage so far even using cvt and xandr commands to try and add the newmode...
If you can help I would really appreciate it...need...to...get...rid...of..windows forever!!
Thanks again.
G.

---

### Post by Ozymandias_117 on 2010-05-27
What type of graphics card?
Have you installed proprietary drivers?

edit: Now that you've told me there is a character named Ozymandias in Watchmen I'ma have to go rent it >.< :P

---

### Post by Hex99 on 2010-05-27
I have an Sis m672 graphics card or chip on an F&H laptop that came with no operating system. originally it was just limited to 800x600 but then I copied a xorg.conf file that was provided on a review of the computer and after learning how to create a xorg.conf file I used this text and it brought the screen resolution up to 1024x768 which is a bit better but not much because the screen apparently is 1366x768 (from the e-buyer overview of the product) which would explain why at 1024x768 the real estate looks a little stretched and people and fonts are warped to a more "fat" look.
 
I tried to use "tweaked" versions of the drivers I found on some ubuntu related site but it made things worse so I uninstalled them again. I then tried to use cvt and xandr to create the new mode but failed miserably...I actually got an error on the terminal about it being unable to create the new mode I could probably re-create that error and post it if it would be helpful.
 
One thing I noticed is that when using cvt to get info on the 1366x768 mode it actually returns values for 1368x768 and I think that two-pixel difference might be the reason? I dunno...I really have only about 48 hours of ubuntu under my belt but they are consecutive and I really would like to get this laptop up and running so i can dump my windows addiction forever.
 
As for the watchmen...the movie kind of sucked but the graphic novel is too cool and you definitely must read it given that you are literate enough to have such a classic nickname.
I was even contemplating to pay the advanced ubuntu support fee just to see if I could get a nice code-guy to reverse hack the driver required for this card....but not sure they would go that far...if they will...I'll spend the cash but by the end of 6 months I will be a monster on ubuntu :)
 
In any case, really thanks for the prompt response, it's really cool how these forums work.

---

### Post by Ozymandias_117 on 2010-05-27
I'm not exactly sure how CVT works, I've never used it... But did you change your graphics driver to Vesa before trying it? I'm pretty sure it only works with Vesa drivers.

Next, what did xrandr -q list?

---

### Post by Hex99 on 2010-05-27
all I know I learnt from one of the ubuntu libraries...the way i figure it cvt gives you info on what a proposed new screen mode would need to look like, You then use this info with xandr and --newmode to create the new mode. In theory.
I'm not sure what "changing the graphics driver to VESA" entails but in the xorg.conf file the display is set as default not VESA or VDSL or one of those. Cvt returns values but when you try to use them in the newmode they don't work. I have found out enough to know the Sis m672 chipset is upsetting many people....would have been nice to know before I bough tthis machine though....

---

### Post by Ozymandias_117 on 2010-05-27
Post the output of ```
xrandr -q
```
Also, post the output of ```
cat /etc/X11/xorg.conf | grep Driver
```

---

### Post by Hex99 on 2010-05-27
aratan@Stitch:~$ xrandr -q
Screen 0: minimum 640 x 480, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       61.0* 
   800x600        61.0  
   640x480        61.0  
aratan@Stitch:~$ cat /etc/X11/xorg.conf | grep Driver
    Driver "kbd"
    Driver "mouse"
    Driver "synaptics"
    Driver "vesa"
    Driver "vesa"


there it is. 
Really man, I feel so grateful you're helping. I was on the verge of going all John Connor on the machines....

---

### Post by Ozymandias_117 on 2010-05-27
Try ```
xrandr --fb 1366x768
```

---

### Post by Hex99 on 2010-05-27
it gives an error code. says:
 
xrandr: screen cannot be larger than 1024x768 (desired size 1366x768)
 
the way I understood it from [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)
 
is that if the mode does not exist you have to create it using the command newmode but that didn't work either as I tried to explain above....would me posting the xorg.conf file I have help? in the xorg.conf there is also a modeline for 1280x768 but it seems to be useless since for some reason the limit seems to be 1024x768.
 
anyway...I will check any suggestions you may have later today I've been up all night again trying to fix this and failing...thanks though. I feel a bit like a prisoner in count of montecristo who now hears a knocking on the stone wall from a nearby cell....maybe one day it will allow me freedom! :)

---

### Post by Ozymandias_117 on 2010-05-28
Sorry, I misunderstood part of your previous post...

Try using cvt to get the resolution again.

```
cvt 1366 768
```

Then try to make the newmode and post back the error it gives you.

---

### Post by Hex99 on 2010-05-30
here is the terminal prompts:

aratan@Stitch:~$ cvt 1366 768
# 1368x768 59.88 Hz (CVT) hsync: 47.79 kHz; pclk: 85.25 MHz
Modeline "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync
aratan@Stitch:~$ xrandr --newmode "1366x768_60.00" 85.25 1368 1440 1576 1784 768 771 781 798 -hsync +vsync
aratan@Stitch:~$ 


as you can see it doesn't specifically give me an error code. It just doesn't do anything. Resolution remains the same.

HOWEVER: After I tried to do some addmodes and THEN repeated the newmode command itdid give me an error code. Here is the full list of commands I used and responses again:



aratan@Stitch:~$ cvt 1366 768
# 1368x768 59.88 Hz (CVT) hsync: 47.79 kHz; pclk: 85.25 MHz
Modeline "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync
aratan@Stitch:~$ xrandr --newmode "1366x768_60.00" 85.25 1368 1440 1576 1784 768 771 781 798 -hsync +vsync
aratan@Stitch:~$ xrandr --addmode VESA 1366x768
xrandr: cannot find output "VESA"
aratan@Stitch:~$ xrandr --addmode default 1366x768
xrandr: cannot find mode "1366x768"
aratan@Stitch:~$ xrandr--newmode "1366x768_60.00" 85.25 1368 1440 1576 1784 768 771 781 798 -hsync +vsync
xrandr--newmode: command not found
aratan@Stitch:~$ xrandr --newmode "1366x768_60.00" 85.25 1368 1440 1576 1784 768 771 781 798 -hsync +vsync
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  18
  Current serial number in output stream:  18
aratan@Stitch:~$ 


I hope this makes some sense to you.
Sorry for the two days off but I had a serious case of food poisoning from apparently dodgy prawns. I could barely lie stand and reading or doing anything was impossible.

As for the Ubuntu priests....they do not chant loud enough! I already have a dell laptop that has ubuntu on it and I loveit...the only problem is in the UK they only sell the 10" netbookversion with Ubuntu on it, so I can't get a PROPER laptop with Ubuntu pre-loaded. 
Take back this silly Island and get rid of the King I say...no taxation without representation and all that!

G.

---

### Post by Hex99 on 2010-05-30
Another point...I do have some propriety drivers for this Sis video system on a cd that came with the laptop but as it explains in the manual, these are apparently only for use with Windows (XP, Vista or 7) and even then you have to install them in a specific order depending on which model of this laptop you have. FUrthermore, I also have discovered that this Sis m672 video chipset apparently uses RAM "dynamically" from the memory (up to 256MB of it)according to the manual. Meaning (if my limited experience with computers from 15 years ago is still relevant) that in all likelyhood this Sis m672 is a crappy little chipset embedded somewhere on the motherboard, or maybe tacked on to the underside of the laptop like old gum. Persistent one though as in the list of upgrade options apparently there is no video upgrade option.

---

### Post by Hex99 on 2010-05-30
And lastly...some stuff here 

[http://ubuntuforums.org/showthread.php?t=927219&highlight=sis+video+chipsets&page=2](http://ubuntuforums.org/showthread.php?t=927219&highlight=sis+video+chipsets&page=2)

looks a little hopeful except I see nowhere the chipset I seem to have which I am told is SiS m672 from the manual. Is there a way I can get a definitive answer as to exactly what chipset I have in this laptop? The problem is there are about 8 models of this laptop, I have it narroweddown to either model G or model H and I am 99% sure it's model G which has the Sis chipset, but it's hard to tell from the information you get on the manual. The Sis chipset is cheaper though so I am sure it's the one I have, also because the other is an NVIDIA GeForce G 105m GSdiscrete Video (External board) and I am sure that would work better.

Just wondering if there is some simple command I can use that returns the guts of the video BIOS?

and if the link above is the way to go...can you hold my hand through it, because there are some private messages that went on obviously as some of the steps are missing and I can't make full sense of it on my own.

Thanks again bud. Like I said the first time...Ozy was the smartest one of the watchmen for a reason!

---

### Post by Ozymandias_117 on 2010-05-30
> **Hex99 said:**
> here is the terminal prompts:

aratan@Stitch:~$ cvt 1366 768
# 1368x768 59.88 Hz (CVT) hsync: 47.79 kHz; pclk: 85.25 MHz
Modeline "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync
aratan@Stitch:~$ xrandr --newmode "1366x768_60.00" 85.25 1368 1440 1576 1784 768 771 781 798 -hsync +vsync
aratan@Stitch:~$ 


as you can see it doesn't specifically give me an error code. It just doesn't do anything. Resolution remains the same.

HOWEVER: After I tried to do some addmodes and THEN repeated the newmode command itdid give me an error code. Here is the full list of commands I used and responses again:



aratan@Stitch:~$ cvt 1366 768
# 1368x768 59.88 Hz (CVT) hsync: 47.79 kHz; pclk: 85.25 MHz
Modeline "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync
aratan@Stitch:~$ xrandr --newmode "1366x768_60.00" 85.25 1368 1440 1576 1784 768 771 781 798 -hsync +vsync
aratan@Stitch:~$ xrandr --addmode VESA 1366x768
xrandr: cannot find output "VESA"
aratan@Stitch:~$ xrandr --addmode default 1366x768
xrandr: cannot find mode "1366x768"
aratan@Stitch:~$ xrandr--newmode "1366x768_60.00" 85.25 1368 1440 1576 1784 768 771 781 798 -hsync +vsync
xrandr--newmode: command not found
aratan@Stitch:~$ xrandr --newmode "1366x768_60.00" 85.25 1368 1440 1576 1784 768 771 781 798 -hsync +vsync
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  18
  Current serial number in output stream:  18
aratan@Stitch:~$ 


I hope this makes some sense to you.
Sorry for the two days off but I had a serious case of food poisoning from apparently dodgy prawns. I could barely lie stand and reading or doing anything was impossible.

As for the Ubuntu priests....they do not chant loud enough! I already have a dell laptop that has ubuntu on it and I loveit...the only problem is in the UK they only sell the 10" netbookversion with Ubuntu on it, so I can't get a PROPER laptop with Ubuntu pre-loaded. 
Take back this silly Island and get rid of the King I say...no taxation without representation and all that!

G.

Try this:

```
xrandr --newmode 1366x768 85.25 1368 1440 1576 1784 768 771 781 798 -hsync +vsync
xrandr --addmode default 1366x768
xrandr --output default --mode 1366x768
```

The first problem was you tried to add it to "VESA" which isn't an output :P It's a driver.

The second problem was you named the mode > "1366x768_60.00" then tried to call it with 1366x768

I'm guessing the third problem came from trying to create multiple modes with the same name

Side Note: What about System76?

---

### Post by Ozymandias_117 on 2010-05-30
> **Hex99 said:**
> Another point...I do have some propriety drivers for this Sis video system on a cd that came with the laptop but as it explains in the manual, these are apparently only for use with Windows (XP, Vista or 7) and even then you have to install them in a specific order depending on which model of this laptop you have. FUrthermore, I also have discovered that this Sis m672 video chipset apparently uses RAM "dynamically" from the memory (up to 256MB of it)according to the manual. Meaning (if my limited experience with computers from 15 years ago is still relevant) that in all likelyhood this Sis m672 is a crappy little chipset embedded somewhere on the motherboard, or maybe tacked on to the underside of the laptop like old gum. Persistent one though as in the list of upgrade options apparently there is no video upgrade option.

I don't know of any wrappers for graphics drivers.

Well, all laptops are embedded graphics, but yeah, sounds like it's a crappy one. :D

---

### Post by Ozymandias_117 on 2010-05-30
> **Hex99 said:**
> And lastly...some stuff here 

[http://ubuntuforums.org/showthread.php?t=927219&highlight=sis+video+chipsets&page=2](http://ubuntuforums.org/showthread.php?t=927219&highlight=sis+video+chipsets&page=2)

looks a little hopeful except I see nowhere the chipset I seem to have which I am told is SiS m672 from the manual. Is there a way I can get a definitive answer as to exactly what chipset I have in this laptop? The problem is there are about 8 models of this laptop, I have it narroweddown to either model G or model H and I am 99% sure it's model G which has the Sis chipset, but it's hard to tell from the information you get on the manual. The Sis chipset is cheaper though so I am sure it's the one I have, also because the other is an NVIDIA GeForce G 105m GSdiscrete Video (External board) and I am sure that would work better.

Just wondering if there is some simple command I can use that returns the guts of the video BIOS?

and if the link above is the way to go...can you hold my hand through it, because there are some private messages that went on obviously as some of the steps are missing and I can't make full sense of it on my own.

Thanks again bud. Like I said the first time...Ozy was the smartest one of the watchmen for a reason!

```
sudo lspci | grep VGA
```

---

### Post by Hex99 on 2010-05-30
On the previous post...my defence is as follows:
1) I am stupid
2) I haven't coded in BASIC in 25 years so I forgot how to spell long ago
3) I don't really want to learn. I want to be entitled and have many slaves just get my work done for me. Sadly I am not emperor.

apart from that...I did as you said but the last command was not recognised by the terminal (the --output default --mode 1366x768 xandr command).

On system 76...as far as I can tell they only operate in the USA and not UK as my (admittedly cursory googling seemed to return only US based stuff...but see point 1 above....I may be wrong)

ON the up side...I do have Ubuntu working rather well on my Samsung NC20 which is a minor victory. The only problem there is I have a huge windows partition on it and apparently GParted has some bugs in it and Gnome PArtition Editor doesn't even see the Ubuntu partition....I'd really like to get rid of Windows alltogether from this Samsung laptop but...it took me ages to install it on here because the NC20 does not have a CD drive so I hat to copy the ISO of ubuntu 10.04 onto a usb stick and then with genial inspiration I also copied the wubi file onto it and ran it and it worked...I got Ubuntu 10.04 to work on the NC20.
The problem is the drive was partitioned so that Windows hogs most of it so I now have a ubuntu laptop with no space on it.

Is there a safe way I can kill the windows partition off here? (I don't care about the data on it at all as it has little on it). 

This would not fix my SiS problem but I could then give THAT brand new laptop to the girlfriend who can install windows 7 on it and that way she get a new PC and I get a working Ubuntu one on the NC20.

As for your last message...I have not tried it yet as I was busy setting up the NC20 for a few hours. But I will give it a shot tomorrow and see if it changes anything.

Again...I salute your perseverance with this nooob!
G.

---

### Post by Ozymandias_117 on 2010-05-30
> **Hex99 said:**
> On the previous post...my defence is as follows:
1) I am stupid
2) I haven't coded in BASIC in 25 years so I forgot how to spell long ago
3) I don't really want to learn. I want to be entitled and have many slaves just get my work done for me. Sadly I am not emperor.

apart from that...I did as you said but the last command was not recognised by the terminal (the --output default --mode 1366x768 xandr command).

On system 76...as far as I can tell they only operate in the USA and not UK as my (admittedly cursory googling seemed to return only US based stuff...but see point 1 above....I may be wrong)

ON the up side...I do have Ubuntu working rather well on my Samsung NC20 which is a minor victory. The only problem there is I have a huge windows partition on it and apparently GParted has some bugs in it and Gnome PArtition Editor doesn't even see the Ubuntu partition....I'd really like to get rid of Windows alltogether from this Samsung laptop but...it took me ages to install it on here because the NC20 does not have a CD drive so I hat to copy the ISO of ubuntu 10.04 onto a usb stick and then with genial inspiration I also copied the wubi file onto it and ran it and it worked...I got Ubuntu 10.04 to work on the NC20.
The problem is the drive was partitioned so that Windows hogs most of it so I now have a ubuntu laptop with no space on it.

Is there a safe way I can kill the windows partition off here? (I don't care about the data on it at all as it has little on it). 

This would not fix my SiS problem but I could then give THAT brand new laptop to the girlfriend who can install windows 7 on it and that way she get a new PC and I get a working Ubuntu one on the NC20.

As for your last message...I have not tried it yet as I was busy setting up the NC20 for a few hours. But I will give it a shot tomorrow and see if it changes anything.

Again...I salute your perseverance with this nooob!
G.

Just to test... try the ```
xrandr --fb 1366x768
``` again. (Note, from what I understand, if you've rebooted, you'll have to redo the newmode and addmode parts)

After checking that it IS SiS, make a backup of, and post your, xorg.conf file and we can try to get it running the SiS drivers. That may fix everything :P
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo cat /etc/X11/xorg.conf
```

One thing I don't understand on your post, On the other laptop you were referring to, the one you wanted Windows off of, did you install Ubuntu via Wubi?

---

### Post by Hex99 on 2010-06-01
Hello brother!
I have now officially given up at trying to get Ubuntu to work on that F&H machine. It would have been nice but it was not to be. Like with some pretty girls that were really great in bed too but their crazy didn't suit my needs, I had to let them go....but fear not...because I have found my happy bride in the pristine white samsung NC20 which is now running Ubuntu beautifully with more fonts installed than I can shake a stick at and I am happy. My gf is happy too as she has now got a brand new laptop she can install windows 7 on and replace her old crappy machine. So all is well.

I truly thank you for your friendship. It has been a bonding experience. And I'm serious. You made me like the Ubuntu community, which I haven't even really met yet, so you achieved a lot. 
If you'd like to keep in touch you can find me here: [www.gfilotto.com](www.gfilotto.com) it's about to be launched officially in a couple or three weeks, but it's my spot in the web-world.

On Ubuntu-related stuff, I still have some niggling newbie questions so feel free to keep helping me there too.

This week's issues:
1. In both Chrome and Firefox when I click on the address bar it does not highlight the whole thing making for easy deletion of the existing address as soon as I type something, which means I waste precious seconds having to manually highlight the address bar and then deleting it with the delete key before typing a new address or search query etc.

2. It seems if I run firefox and Chrome together sometimes they affect each other, one browser shutting the other off spontaneously sometimes...can i fix this...

3. Most important of all. On installing Ubuntu 10.04 for the second time (wiping out my old windows partition) I got an error message saying the admin directory could not be locked. I didn't know what to do, so ignored the message. But my primary reason for moving to Ubuntu was security as I had been hacked in windows with a trojan that could not be removed as it resided in the DMIO.sys file (which apparently controls all access to the hard-disk and therefore all data). Given the type of virus apparently also recorded keystrokes it made me quite paranoid.
I would like to be safe from the spying eyes of intruders as I have some confidential client files in my laptop since I work as a hypnotist and sometimes have to deal with people that have some pretty serious issues.

Can you send me to a good ubuntu-security for idiots school where I can just push two buttons and be SAFE you know like...forever...from all the bad people on the 'net...:) :) :) I will be quite happy to defend myself with my bare hands from marauding orcs...but net attacks are like magic for us mild mannered monks...

Again. Thanks for all your help.

---

### Post by Ozymandias_117 on 2010-06-01
> **Hex99 said:**
> Hello brother!
I have now officially given up at trying to get Ubuntu to work on that F&H machine. It would have been nice but it was not to be. Like with some pretty girls that were really great in bed too but their crazy didn't suit my needs, I had to let them go....but fear not...because I have found my happy bride in the pristine white samsung NC20 which is now running Ubuntu beautifully with more fonts installed than I can shake a stick at and I am happy. My gf is happy too as she has now got a brand new laptop she can install windows 7 on and replace her old crappy machine. So all is well.

I truly thank you for your friendship. It has been a bonding experience. And I'm serious. You made me like the Ubuntu community, which I haven't even really met yet, so you achieved a lot. 
If you'd like to keep in touch you can find me here: [www.gfilotto.com](www.gfilotto.com) it's about to be launched officially in a couple or three weeks, but it's my spot in the web-world.

On Ubuntu-related stuff, I still have some niggling newbie questions so feel free to keep helping me there too.

This week's issues:
1. In both Chrome and Firefox when I click on the address bar it does not highlight the whole thing making for easy deletion of the existing address as soon as I type something, which means I waste precious seconds having to manually highlight the address bar and then deleting it with the delete key before typing a new address or search query etc.

2. It seems if I run firefox and Chrome together sometimes they affect each other, one browser shutting the other off spontaneously sometimes...can i fix this...

3. Most important of all. On installing Ubuntu 10.04 for the second time (wiping out my old windows partition) I got an error message saying the admin directory could not be locked. I didn't know what to do, so ignored the message. But my primary reason for moving to Ubuntu was security as I had been hacked in windows with a trojan that could not be removed as it resided in the DMIO.sys file (which apparently controls all access to the hard-disk and therefore all data). Given the type of virus apparently also recorded keystrokes it made me quite paranoid.
I would like to be safe from the spying eyes of intruders as I have some confidential client files in my laptop since I work as a hypnotist and sometimes have to deal with people that have some pretty serious issues.

Can you send me to a good ubuntu-security for idiots school where I can just push two buttons and be SAFE you know like...forever...from all the bad people on the 'net...:) :) :) I will be quite happy to defend myself with my bare hands from marauding orcs...but net attacks are like magic for us mild mannered monks...

Again. Thanks for all your help.

1. Triple-clicking does it, I don't know if there is a way to make it highlight all with a single click.

2. The only thing I can wonder is if they're trying to access the same plugins at the same time? Right after it happens you can try ```
dmesg | tail
``` It may give you some useful information.

3. Security doesn't really have an easy 1 click fix-all. Mostly because it's a moving target... If you want to learn more about security, check this thread out. (The apparmor link is REALLY good btw) [http://ubuntuforums.org/showthread.php?t=510812]("http://ubuntuforums.org/showthread.php?t=510812")

---

