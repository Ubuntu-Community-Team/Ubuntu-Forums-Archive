---
title: "Only provides 600x400 screen resolution"
date: 2009-05-27
forum: New to Ubuntu
---

### Post by Chalfont on 2009-05-27
Originally tacked on teh end of someone else's post but now Bumping it.

I have loaded 9.04 Ubuntu onto a 3 yr old eMachines desktop (2.16Ghz intel chip) with VIA graphics chipset, and now it gives me two resolutions... 800x600 or 800x480. Now this isn't good enough, XP gave me up to 1280x... 

Followed the Wikis and guides, I did the System > Adminstration > Display menu selection.  It showed the dialogue box, but it was empty with the message 'no proprietary drivers installed'. No button or function at all to get a list (which apparently there should be). Yes I am on the internet as i am typing this!  Where do I get a list of drivers to choose from?  Is my install broken?

So if I cannot get a decent display then it has to be goodbye Linux and back to being a Micro$oft dupe. ALSO: In another thread someone suggested checking the 'Screens and Graphics menu' you refer to above? I didn't see one, please be totally specific about what things to clisk in 9.04 to reach it.

Now I also looked at downloading a VIA driver and installing it. Did the download, but cannot find where it went, could not at first find the command line, and cannot work out the syntax of the Linux DOS language or where to put the file that is 'run'.  The help screens and documentation I have found here so far do the thing of using terms and language that means you have to know what you are doing before you can start to learn about how to do things.  Very Lewis Caroll 'Alice in Wonderland' stuff and I am beginning to feel like the Red Queen's people running as fast as possible just to try and keep up.

I wasn't expecting so many problems, beginning to think some of the posts I read in ZD Net are correct, Linux is for geeks only with Computing Science backgrounds or hundreds of hours to waste.

---

### Post by overdrank on 2009-05-27
Hi and welcome, sorry to hear you are having some issues with the graphics. VIA graphics are not well support in linux so you may have some issues but you can try and boot into recovery mode and use the xfix option to correct.
Best of luck. :)

---

### Post by Chalfont on 2009-05-27
Oh well, sounds like that's that then.  
So much for the brave new world, more like the damp overhyped squib.

---

### Post by CatKiller on 2009-05-27
Normally, resolution problems are caused by one of the monitor, the graphics card, or the graphics driver not passing the EDID information to X that lets it automatically set the correct refresh rate, and so it defaults to really low values that won't damage any monitors. You can manually set the values for your monitor by putting the VertRefresh and HorizSync ranges in your xorg.conf. You should be able to get these numbers from the manual or specifications for your monitor. These values go in the "Monitor" Section of xorg.conf.

You can edit xorg.conf with ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf
``````
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       aa-bb
        VertRefresh     cc-dd
EndSection

```You'll need to replace aa-dd with the values for **your** monitor.

---

### Post by Chalfont on 2009-05-28
Thanks CatKiller

I tried that and it came back and said I didn't have permission to save the edit!  Even after I had entered the password (and only one user registered so I thought this should have root level admin rights from what I have been reading).

So I decided that this suggested a more serious issue, and given that I have done no work since loading it, I am now in process of reloading it again over the top of the old load.  Perhaps this time it will take properly.

---

### Post by paul_anders on 2009-05-28
i have 3 options for  you of which 1 will work.

1, install and try envy-ng
2, run xrandr in cli. Can you see the resolution you want ? 
3, lastly but most likely to work 99.9% download and install Suse. If you can manage rpm's then go for it.

I have always had problems with graph cards and ubuntu every release  has the same problem. Im in that same pickle now.... To over come it im using xrandr in auto start to adjust the correct the screen resolution.

---

### Post by Chalfont on 2009-05-28
Thanks Paul
Unfortunately, as I said, i am a newbie.
Sorry to sound pathetic but I have no idea what "1, install and try envy-ng" actually requires me to do.  Similarly for "run xrandr in cli." or "If you can manage rpm's" in regards to SUSE

I'm still reloading so I don't know if I have a problem or not at the end of it.

If I do then I might look up those terms and see if there's some help about how to do them.

Thanks

---

### Post by Chalfont on 2009-05-28
And also. of course, as per the recommendations in the stickies at the top of each forum, I'll wait to see if anyone else reads  and/or comments to ensure these are valid and safe activities for me to do, thanks.

---

### Post by paul_anders on 2009-05-28
im sorry ioverlooked something in your first post... You are using via card.... Envy-ng will not work with that card.

When you done installing.... Make sure you get the latest up dates..... Then open your terminal..... And type xrandr the result should see a few different resolutions hopefully u will see 1024x786. If so you will be ok. If not then dowload and install Suse.... I find that suse always gets graphics card working on first contact..... suse is linux too. its all worth a try. You have nothing to loose but everything to learn

And no you are not pathetic

---

### Post by Chalfont on 2009-05-28
OK, issue resolved, reloading Ubuntu 9.04 from scratch worked, now have lots of nice screen display sizes to choose from.

Thanks for the help from everyone.

---

### Post by paul_anders on 2009-05-28
im sorry ioverlooked something in your first post... You are using via card.... Envy-ng will not work with that card.

When you done installing.... Make sure you get the latest up dates..... Then open your terminal..... And type xrandr the result should see a few different resolutions hopefully u will see 1024x786. If so you will be ok. If not then dowload and install Suse.... I find that suse always gets graphics card working on first contact..... suse is linux too. its all worth a try. You have nothing to loose but everything to learn

And no you are not pathetic

---

