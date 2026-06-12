---
title: "Confused about nvidia drivers and updates"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by bledsoe on 2009-01-20
I recently installed Ubuntu version 8.10, though I ended up having to do a complete reinstall before I got it to work.  Everything was going fine on the first install until the box popped up listing the nvidia graphics drivers that I could install.  Even though the graphics looked fine to me, since one of the nvidia drivers was labeled "Recommended" I selected that one and clicked the activate button.  I also told the Update Manager to install all the recommended software updates (over a hundred as I recall).

When I rebooted, the screen quickly displayed a series of black and white boxes rather than the orange Ubuntu screens, all the video output was completely messed up.  I searched online for help (via my Windows system), but I couldn't figure out how to undo whatever I had done.  I finally just reinstalled Ubuntu, though since I suspected that I had previously messed up the nvidia hardware driver, I did not activate any of the nvidia drivers after the second install and instead just kept whatever driver it was using with a vanilla install.  I did go ahead and install most of the software updates, but two of them had "nvidia" in their title (nvidia-177-modaliases and nvidia-96-modaliases) so I did not install those.

Everything's been running fine, and I have absolutely no complaints so far, but I'm really curious about the nvidia drivers.  In particular, I'd like to know:

1. Why does the Hardware Drivers configuration tool say that one of the nvidia drivers is "Recommended" (version 177) if activating it screws up my system?
2. How do I know which nvidia driver I "should" be using (I have an nvidia e-GeForce 6200 graphics card)?  As I said, the graphics look fine to me, but I'm not a gamer or power user; am I missing out on some fancy graphics features because I don't have the best driver installed?
3. Is there an easy way to undo a driver install that screws up my system (i.e., a way that doesn't involve a complete reinstall)?
4. While I suspect that it was the installation of the "recommended" nvidia driver that messed up my first install, I've still been reluctant to install those two nvidia software updates; can I go ahead and install those?

(Note that while I'm a reasonably experienced computer user, I'm still new to Linux and Ubuntu so try not to get too technical on me.)

Thanks for any help,

---

### Post by gettinoriginal on 2009-01-20
First, go to System, Administration, Software Sources and make sure the first four boxes are checked, then to third party tab and make sure that all boxes are checked but uncheck the CD.  Then run Update manager. Next try to activate your driver from System, Administration, Hardware Drivers.  :p

---

### Post by bledsoe on 2009-01-20
Hi, and thanks for the response.  I made the changes you suggested in Software Sources and then ran Update Manager; it just displayed the 2 nvidia updates I mentioned in my original post, plus an adobe-flashplugin "Distribution update."

I'm not sure what you mean by "Next try to activate your driver from System, Administration, Hardware Drivers."  I can bring up the Hardware Drivers dialog box, but it just displays the same 3 "NVIDIA accelerated graphics driver" options I had before, including the one labeled "Recommended."  I still don't know which of these, if any, I should activate, or why one of those should work any better than whatever nvidia driver my system is using now.  (And I sure don't want to activate the Recommended one since that appears to be what messed up my video output the first time.)

---

### Post by gettinoriginal on 2009-01-20
I doubt seriously that with the updates applied that it will "mess up".  After you activate the driver, go to System, Preferences, Appearance, Visual Effects, and mark "Extra" or "Custom" and you will have all the 3D effects and eye candy enabled.

---

### Post by bledsoe on 2009-01-20
Ah, interesting.  I notice that when I go to System, Preferences, Appearance, Visual Effects, and mark "Extra," I get a dialog box that says "Enable driver? NVIDIA accelerated graphics driver (version 173)."  Perhaps this is a hint that the version 173 is the correct graphics driver for my system?

While I'm glad that you don't think that enabling this driver will mess up my system, I'm sure you'll understand if I'm a little hesitant after my last experience enabling what I assume was the wrong driver (the "Recommended" version 177).  So just in case enabling version 173 does something weird to my video output, is there a way to revert back to my current settings if something goes wrong?  I'd hate to have to reinstall the whole system again.

---

### Post by gettinoriginal on 2009-01-20
Oh, there are ways, so don't fear :p

---

### Post by AliTabuger7 on 2009-01-21
1- If you are experiencing problems, Envy is a good application to fix them.

2- Legacy support, I believe. 177 sounds right to me, but the previous one would probably work just as well. CUDA is the main improvement in 177, which is not available for your card. Nevertheless, the driver should still work.

3- When the x server fails to startup, it will go through prompts to choose a different driver (in 8.10).

---

### Post by jerome1232 on 2009-01-21
--edit-- and yes xorg should be asking you to reconfigure anyways I forgot about that (I always bypassed it and reconfigured myself if things went wrong)

In the event that x crashes after you install the driver you would do this (from a terminal, so hit ctrl+alt+f1 and login)

Of course change the last part 173 or whatever version it was you installed
```
sudo apt-get autoremove nvida-glx-177
sudo dpkg-reconfigure -phigh xserver-xorg
sudo reboot
```

---

### Post by yther on 2009-01-21
Since you want to know how to revert things if a new driver messes up your X display, remember this:  If your graphical screen is garbled you can usually get to a text login by pushing Alt+F1, or Ctrl+Alt+F1.  From there, log in, and you can use **dpkg** to configure your X environment from scratch if necessary.  The command "sudo dpkg-reconfigure -phigh xserver-xorg" will ask you a bunch of questions and redo your configuration.  During the process you can choose a more generic video driver and hopefully recover.

Also, Envy is a good tool, and if *that* leaves you with an unusable display, you can log in to a text console and run "sudo envy --uninstall-all" and it will revert you to whatever you had before.

The text-mode tool "aptitude" is also useful in these situations.  I'd suggest you read the basic documentation for it ("man aptitude") and learn how to search, install, and purge packages.  It can be your friend if (like me) you manage to break your graphical environment from time to time!

(Hm, cross-posted with someone else giving you similar advice in fewer words...  ;) )

---

### Post by bledsoe on 2009-01-21
Many thanks for all the suggestions.  I read thru some of the stickies in the Absolute Beginner Talk forum to find out a little more about the dpkg-reconfigure command, and then I went ahead and activated the nvidia version 173 driver thru the System-> Preferences -> Appearance menus (as described earlier by gettinoriginal).  As soon as it was finished installing, I rebooted, and after the orange "Ubuntu loading" bar finished, my screen immediately displayed the dreaded black/white/gray boxes just like I described in my first post.

This time I got to a terminal login via Ctrl+Alt+F1, logged in and entered the command "sudo dpkg-reconfigure -phigh xserver-xorg" (as suggested by yther and jerome1232), and after some text jibberish that I didn't really understand, I rebooted again (actually, I had to turn the machine off and back on) and it booted just fine.  (No reinstall needed!  Woo-hoo!)

Of course, I'm still confused as to why these nvidia drivers are messing up my video display, especially when Ubuntu is recommending that I install them, so it would be great if someone could explain that.

[One additional piece of info: after executing the dpkg-reconfigure command and rebooting, when I go to System-> Preferences -> Appearance again and select the Visual Effects tab and click on the Extra button, I now get a message that says "Desktop effects could not be enabled."]

---

### Post by jerome1232 on 2009-01-21
A couple things, instead of doing a hard shutdown, just issue the reboot command
```
sudo reboot
# or to shutdown and halt the system
sudo shutdown -h now
```

The reason the visual effects is giving a different error I think is because you never removed the driver, just configured xorg to not use the driver. To actually remove the driver:
(Of course you can do this from a gui, just use synaptic package manager.)
```
sudo apt-get autoremvoe nvidia-glx-173
```

I suggest trying envyng, it seems to get alot of people working when the first method fails.
```
sudo apt-get install envyng-gtk
sudo envyng -t
```
tell it to install the nvidia driver and select 173 or 177.

If it fails and destroys x as did the previous attempt, to undo it you would log in to your trusty terminal and run
```
sudo envyng --uninstall-all
sudo reboot
```

---

### Post by bledsoe on 2009-01-21
Thanks for that info.  And one of the other posters recommended Envy as well; I think that will be next on my list of things to try, but I may not get around to it for a while, so I think I'm going to declare this thread resolved and post again if I have trouble with Envy.

Thanks again to everyone for all the help.

---

### Post by dawynn on 2009-01-22
1) Note that the Hardware Drivers tool *only* looks at your card -- and makes video driver suggestions *strictly* based on your video card.

Personally, I have a nVidia FX 5700LE -- which is supported by the 173 series driver, so the Hardware Drivers tool recommends it.  But I'm using it in a rig with an Athlon Classic CPU.  The Athlon Classic did not fully support SSE instructions -- and the 173 and 180 drivers use SSE instructions.  In my case, this only really comes into play when 3D graphics are used (gaming, compiz).  For 2D, and basic functionality, the 173 driver worked for me.

So, you may need to consider using the 96 driver instead of the 173.

2) In your Software Sources tool, make sure to go to the Updates tab and verify that Intrepid-Updates is selected.  If memory serves correctly, Intrepid came with many of the nVidia drivers broken -- they were only fixed *after* install (I know this applies to the 96, 173 and 180 may have been fixed prior to release).

3) In the end, if you're not worried about 3D graphics, you may be trying to fix something that you're not even worried about.  You say you're not a gamer, but do you want to use compiz?  If so, you need functional 3D capabilities.  If not, go into Synaptic and remove all packages with "compiz" in the name, and go ahead and use the nv driver.  I believe that the 2D graphics should be enough, even for most video players (please, someone correct me if I'm wrong).

---

### Post by dawynn on 2009-01-22
Something I saw in another thread reminded me of something.  My own computer got pretty messed up because my xorg.conf had two screen declarations, two monitors, pretty much two of everything.  But I have a very basic computer with only one video card and one monitor.  Once I simplified the configuration, everything works well.  I'm wondering if that's the case here.

If you post your /etc/X11/xorg.conf file here, we can help you look for any such problems that might be caused by your configuration file.

---

### Post by bledsoe on 2009-01-28
I finally got around to looking at the Synaptic Package Manager and, via a little trial and error, finally got my system back to what I believe is its initial "vanilla" state with regard to the video drivers.  At least, my system now boots without the long string of text messages, including the one line that said something like "nvidia 71.86.04" with a red text [fail] message next to it.

The Synaptic Package Manager lists a number of packages that start with "nvidia-" and the critical ones seem to be nvidia-glx-xxx, nvidia-xxx-kernel-source, and nvidia-xxx-modaliases, where xxx is either 71, 96, 173, 177, or 180.  The trick seems to be to uninstall all of the nvidia-glx-xx packages, as well as all of the nvidia-xxx-kernel-source packages.  It doesn't seem to matter whether the nvidia-xxx-modaliases packages are installed or not (I left all of mine installed).

Now my system boots with no long string of text messages or errors.  Of course, I am apparently not fully utilizing the 3D potential of my nvidia graphics card, or certain desktop visual effects, but it appears that for whatever reason, the Ubuntu nvidia drivers don't work with my system.  I'd love to know why that is, and to be able to install and activate the appropriate driver, but for now I'm happy that my system is running fine, and since I'm not a gamer or power video user, the graphics I have now are acceptable.

---

