---
title: "I think I screwed EVERYTHING up. Help?"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by RogueS on 2009-01-06
Ok so I've been using Ubuntu for a while now and so I like it and I'm getting really used to using it.

I have a few major issues however that are making it hard for me to do everything that I need to do on Ubuntu. This is also my only working computer right now.

First issue. I messed up the bar that has the "System" and "Applications" part on it.

I opened firefox by right clicking on a photo on my desk top and opening it in firefox!
I accidentally made the part of the bar that has my short cuts to applications on it a little too big so I could not see the other parts of the bar, it was just white with a firefox button on it so I wanted to remove the part with the shortcuts and just get my system and applications stuff back BUT I deleted the whole bar!

I can't even tell what time it is now!

So... I need to get that bar back.

Next issue. I think my video card driver is out of date. 
I can't get resolution other than 800x600 or something so I can't use a lot of my applications that have buttons that I can't actually even reach because they extend past the bottom of my screen. 
I really need to fix this and make my resolution a LOT smaller.

Next issue. I want to install Veoh so I can watch free movies - they require that you download and install their little program to watch any full length content.

Next issue. I don't think everything is up to date because when I use Imeem or other flash related sites the content does not display.
Also when I use plentyoffish the IM program does not work.

Also when I use tripod in firefox I can't type in the text fields I had to download seamonkey to do that but seamonkey does not allow plentyoffish IM or imeem video content either. 

Ok other than that I think I'm ok but if someone could start by slowly, like I'm really stupid, explaining to me step by step how to get my bar back it would be much appreciated.

Thanks!

R.S.

---

### Post by JoshuaRL on 2009-01-06
First off, welcome to Ubuntu!  Sorry for the problems you're having, but good job on keeping a positive attitude.
Now, let's get to solving some of your issues.

> **RogueS said:**
> 
First issue. I messed up the bar that has the "System" and "Applications" part on it.

I opened firefox by right clicking on a photo on my desk top and opening it in firefox!
I accidentally made the part of the bar that has my short cuts to applications on it a little too big so I could not see the other parts of the bar, it was just white with a firefox button on it so I wanted to remove the part with the shortcuts and just get my system and applications stuff back BUT I deleted the whole bar!

I can't even tell what time it is now!

So... I need to get that bar back.

What you want to do is add that bar back, right?  Now, I'm at work right now so I'm going off of memory.  If I say to do anything a little wrong, hopefully someone will correct me.

Go to the bar at the bottom and right click.  You'll get one of two menus.  Either one with something about the Application bar, which lists open applications.  Go a little farther to the right, and try again until you find something different.  It will have an option to add a panel.  That's what you want.  Make sure it's at the top, and then right click it to add panel items.  Then just read the description and add what you want there.  Should be pretty simple.

Post back here if you have any issues, and once that's fixed we'll move on to the other stuff.

---

### Post by bump_ on 2009-01-06
For the panel problem:

Right Click on your bottom panel and choose "New Panel". Move the new panel to the top of your screen. Right click on this new panel and select "Add to Panel". From the list of applets choose "Menu Bar", "Clock", "Volume Control" and whatever else you had on your bar.

As for the video problem: After you get you menu back, go to System->Administration->Restricted Driver Manager and make sure everything is checked (if there is anything)

---

### Post by northern lights on 2009-01-06
> **RogueS said:**
> I messed up the bar that has the "System" and "Applications" part on it.If both panels are gone, press Alt+F2, type```
gnome-panel
```
and hit Enter. If that solves the issue, which it should, navigate to "System > Preferences > Sessions" and add *gnome-panel* to the "Startup Programs". If only the top panel is gone, right-click on the bottom panel and choose "New Panel". Subsequently right-click the new top panel and add "Clock", "Main Menu", "Notification Area", "Network Monitor", "Log Out..." and whatever else you want.

> **RogueS said:**
> Next issue. I think my video card driver is out of date. 
I can't get resolution other than 800x600 or something so I can't use a lot of my applications that have buttons that I can't actually even reach because they extend past the bottom of my screen. 
I really need to fix this and make my resolution a LOT smaller.
What graphics device do you use? Rather than telling us from memory, please open a terminal (Applications > Accessories > Terminal or Alt+F2 > *gnome-terminal*) and post the output of```
sudo lshw -C display
```For a quick solution, run```
sudo dpkg-reconfigure -phigh xserver-xorg
```

> **RogueS said:**
> Next issue. I want to install Veoh so I can watch free movies - they require that you download and install their little program to watch any full length content.
This is going to be the toughest, as Veoh does not offer a Linux client. You need to attempt to run it through Wine. Wine is in the repositories. Check whether others have experience with running Veoh through Wine [here]("http://appdb.winehq.org/").

> **RogueS said:**
> Next issue. I don't think everything is up to dateWhat is the output of```
sudo apt-get update && sudo apt-get upgrade
```

> **RogueS said:**
> when I use Imeem or other flash related sites the content does not display.Again, open a terminal and run```
sudo apt-get update && sudo aptitude purge totem-mozilla && sudo apt-get install flashplugin-nonfree mozilla-mplayer ubuntu-restricted-extras
```

> **RogueS said:**
> Also when I use tripod in firefox I can't type in the text fieldsNo idea what's happening here.

---

### Post by theinnercityhippy on 2009-01-06
> **bump_ said:**
> For the panel problem:

Right Click on your bottom panel and choose "New Panel". Move the new panel to the top of your screen. Right click on this new panel and select "Add to Panel". From the list of applets choose "Menu Bar", "Clock", "Volume Control" and whatever else you had on your bar.

As for the video problem: After you get you menu back, go to System->Administration->Restricted Driver Manager and make sure everything is checked (if there is anything)

If you don't have a panel at the bottom either go to 

Accessories > Terminal

and at the prompt type

    $> gnome-panel

Which should start a new instance

---

### Post by RogueS on 2009-01-06
OK Got the panel back!!! THANKS! (even have some new stuff on there that I didnt have before so we're real good, awesome, thanks guys)

Here is my video card


[sudo] password for rogues: 
  *-display               
       description: VGA compatible controller
       product: NV44 [GeForce 6200 LE]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: driver=nvidia latency=0 module=nvidia
rogues@rogues-desktop:~$

---

### Post by RogueS on 2009-01-06
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Updates are well...up to date :) trying the flash thing now

---

### Post by JoshuaRL on 2009-01-06
For your graphics card, go to System->Administration->Hardware Drivers.  See if it can find any proprietary drivers for your 6200.

---

### Post by RogueS on 2009-01-06
I have 'nividia accelerated graphics driver' (latest cards) 

checked and activated.

On my screen resolution screen the options I have are: 

Resolution 640x480 Or 320X240 (it goes that low eww)

and the Refresh Rate can only be set to 50hz

Maybe it's my monitor? I mean I did switch with my room mate?

---

### Post by JoshuaRL on 2009-01-06
Well, my brother has that card in XP and it goes to a higher resolution than that.  So maybe try restarting and see if the graphics driver is better.

---

### Post by RogueS on 2009-01-06
Just for the record the Monitor is an old Sony Trinitron Multiscan 220GS that I got for free when I built my friend's tower (and gave her the good monitor to be nice lol)

---

### Post by JoshuaRL on 2009-01-06
Hmm, do you know if it can go any higher than that resolution?  It may not be able to.  But kudos for finding out the exact name and model of your monitor.

---

### Post by RogueS on 2009-01-06
So I restarted it. I'm going to ask the roommate to switch back and figure out if its just this monitor or what.

It was fine when I built her windows tower using this one, and it was find on ubuntu with the previous owner who used ubuntu on the tower I rebuilt to use windows for her. 

So hmmm she's going to kill me but I dont care LOL

---

### Post by RogueS on 2009-01-06
It was the monitor!!!!!!!!!!!!!!

I switched it for an old Dell we had and now the resolution is fine. the old Sony works on windows, we tested it. :KS

---

### Post by JoshuaRL on 2009-01-06
> **RogueS said:**
> It was the monitor!!!!!!!!!!!!!!

I switched it for an old Dell we had and now the resolution is fine. the old Sony works on windows, we tested it. :KS

Well, huh.  That's kind of weird that it doesn't work in Ubuntu.  Can you force the right resolution and refresh rate in?

---

### Post by northern lights on 2009-01-07
Flash fixed? Veoh working in Wine?

---

### Post by RogueS on 2009-01-10
No Veoh yet havent tried im too emmmm yeah not ambitious enough but I lost my sound so what does it matter anyway LOL!

---

### Post by northern lights on 2009-01-11
> **RogueS said:**
> but I lost my sound so what does it matter anyway LOL!
How exactly did you "loose your sound"?
This shouldn't happen at all.

Please post the output of```
sudo lshw -C multimedia
```

---

