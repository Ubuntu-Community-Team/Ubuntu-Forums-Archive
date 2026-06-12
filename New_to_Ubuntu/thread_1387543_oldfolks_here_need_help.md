---
title: "oldfolks here need help"
date: 2010-01-22
forum: New to Ubuntu
---

### Post by oldfolks on 2010-01-22
I am new like just started and need some help.
I have live cd of 9.10 and the only way I can run it is in safe mode but then it runs fine I do system test under live cd and it tells me [I]I need to download driver for my Video card. I do that then it tells me to restart, but I'm in live cd so it doesnt work.
 So I do a install of Ubuntu hoping it will work but cannot get on.
I have a ATI radeon 3650 video card. What can I do before I try to install to get it to work.
Please if you answer Be very clear and dumb it down for me, I'm not very computer savvy. It took me 3 days to get this far,and Grub is Greek to me.
Thanks
[/I]

---

### Post by candtalan on 2010-01-22
Welcome!

> **oldfolks said:**
> I am new like just started and need some help.
I have live cd of 9.10 and the only way I can run it is in safe mode but then it runs fine 

This is safe graphics mode, it is not the same as Windows full 'Safe mode'. Using safe graphics mode in Ubuntu is no problem, it just chooses a sutable video driver system which is hopefully going to work but is not the very latest bells and whistles. It is perfectly valid to use.

>  I do system test under live cd and it tells me I need to download driver for my Video card. I do that then it tells me to restart, but I'm in live cd so it doesnt work 

Quite so. Live CD is a full running version, not a cut down version. Some things can be installed normally,  however, for the very few things which would normally need a complete re start, as you have seen, it is difficult or maybe impossible to do things with video drivers. It is good news that you can get video drivers, hopefully they will be ok after a full install.

>  So I do a install of Ubuntu hoping it will work but cannot get on. 

Did you install? Please tell what you did to install. there are a number of different ways to install and it is useful to know more to offer some comments. 

> 
I have a ATI radeon 3650 video card. What can I do before I try to install to get it to work 

If it works in safe graphics mode then continue that way. An install should pick that up. If you later need fancy drivers, come back to here or maybe choose the multimedia and video  part of these forums
[http://ubuntuforums.org/forumdisplay.php?f=334](http://ubuntuforums.org/forumdisplay.php?f=334)

Ah, just remembered. Sometimes, other versions of Ubuntu, such as 9.04 and 8.10, even the long term support version 8.04.3, may have better graphics on your particular system. Just a thought.

---

### Post by JiuJitsu500 on 2010-01-22
Quick info: The 3650 + Karmic Koala don't completely jive...

You can get it fully operational and cool as beanz, but you can only have 2GB of RAM. I done googled and googled and asked and asked, and on three seperate computers (Toshiba sattelites with ATI 3650) it would only boot into safe graphics.
Until I found the launchpad Bug site where it said the only fix for now is to remove a 2GB chip (these guys and mine had 4GB), and no one as far as I have found has any workarounds for this.

So if you have more than 2GB of RAM... you have to unfortunately downgrade :( At least until Lucid comes out perhaps.... Or find a 3rd party driver that encompasses all ATI cards up to date somehwere in Launchpad.

The good thing is however, 2GB is still more than you'll ever really need unless performing some pretty advanced stuff... Linux is great at preserving RAM :)

---

### Post by robert shearer on 2010-01-22
> I do system test under live cd and it tells me I need to download driver for my Video card. I do that then it tells me to restart, but I'm in live cd so it doesnt work 

Sometimes the instruction is to "restart x" or "the x-server" so after downloading and installing the driver click on the red button at the top right and you should get a menu that has several options including "shut down" and "log out".
Select log out and this may restart the desktop using the downloaded driver without restarting the whole system from scratch.

Of course the downloaded driver will be lost when you eventually close the cd but it should let you try out the driver meantime to see if it works ok.

It would help if you could post the specs of the computer you are trying to install on.

Well done to have got so far already!!:D

Keep asking and you will find people here only too willing to help.

---

### Post by oldfolks on 2010-01-22
Thanks to all of you who answered, but in the meantime I disconnected the Radeon 3650 and went with the onboard video. It installed just fine with that so now I have it installed with Windows. 
 In my 70 years I haven't learned too much but keep on trying.
Next thing is I would like to add PCLinux but don't know how to do the Grub thing so I can have all 3 on my system. When your retired a person needs things to occupy your time. Ha.
Thanks again
Oldfolks

---

### Post by lisati on 2010-01-22
> **oldfolks said:**
> Thanks to all of you who answered, but in the meantime I disconnected the Radeon 3650 and went with the onboard video. It installed just fine with that so now I have it installed with Windows. 
 In my 70 years I haven't learned too much but keep on trying.
Next thing is I would like to add PCLinux but don't know how to do the Grub thing so I can have all 3 on my system. When your retired a person needs things to occupy your time. Ha.
Thanks again
Oldfolks

70? That's still young! My mum is over 80 and still going strong!

Anyway, welcome to the world of Ubuntu Linux!

---

### Post by Bartender on 2010-01-22
> **oldfolks said:**
> Next thing is I would like to add PCLinux ... a person needs things to occupy your time.

I have a feeling you could stay plenty busy with one Linux OS if you tried...

---

### Post by ubunterooster on 2010-01-22
I've disconnected my graapics card, too. But I did this after I saw how much power it used.

---

