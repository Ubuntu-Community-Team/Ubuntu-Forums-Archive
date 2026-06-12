---
title: "Desktop Missing after &quot;switch Desktop Mode&quot;"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by finippino on 2009-04-24
Hello all,

I installed 9.04 netbook remix today on my Asus eeepc 1000HA.  All is well until I "Switch Desktop Mode" to the classic desktop.  Then when I rebooted I lost the panels and really cant do anything.  I did a few reinstalls just to isolate the issue and I have confirmed that "Switch Desktop Mode" is causing the problem.  Has anyone had this same problem with their eee? 

Thanks

---

### Post by Peter09 on 2009-04-24
When you lose the panels try opening a terminal, (ALT-F2) will do, and run 

```
nautilus
```

It sounds like thats what is crashing.

---

### Post by GeorgeVita on 2009-04-24
Hi **finippino**,

above does NOT work (alt+F2)

after having the same problem I followed the following steps and succeed to turn it back:

1. right click on background
2. click on **create launcer**
3. type **xterm** to name
4. type **xterm** to command
5. click **ok**
6. double click on **xterm** (icon created above)
7. type **desktop-switcher** and press enter
8. choose **Ubuntu Netbook Desktop** and **Apply**

The above creates a shortcut to have access to a terminal window and then run the swither from terminal.

...and we must wait for the resolving update or... force ourselves to the new (mobile phone) style!

I personally prefer a little computer (standard desktop) than a big pda (without touchscreen).

Regards,
George

---

### Post by finippino on 2009-04-24
Thanks for your help!  I could not get nautilus to work so I tried the xterm way and it worked.  So needless to say, this is a bug right?

---

### Post by Tk0680 on 2009-04-26
Just thought I'd add my voice to this.

I suffered the same problem on my Dell Mini 9; switching to "normal" mode (more out of curiosity than a dislike for a the netbook launcher) gave me a half-formed taskbar (with a menu button that didn't work - my guess was it was still trying to send me to the "home" screen). Logging out and in gave me nothing but a blank desktop.

I'd got xterm up via a launcher, expecting to have some variable in my profile needing a reset - glad it was rather simpler than that! Thanks very much for the answer.

It's a big shame though that, even after all this time (I've been with Ubuntu since Hoary), something as basic as switching desktop mode can cause something as showstopping as this. It spoils my - otherwise very impressed - initial impression of Jaunty. As much as I hate to say it (and really, I do - I'm a huge fan of Linux and Ubuntu in particular) - a new edition of Windows wouldn't ship with a bug like this in it in a million years.

---

### Post by Tk0680 on 2009-04-26
Nope, it's not entirely fixed.

I've got my "netbook mode" desktop back, minus gnome-panel which has to be run manually.

Additionally, windows now launch anchored right to the top-left corner of the screen (over the top of the panel) with no option to close them short of their own File menu.

Grr.

---

### Post by y_garti on 2009-04-26
i just use the desktop-switcher command and chose ubuntu net-book desktop
and i suffer lots of errors 
1.The panel encountered a problem while loading "OAFIID:GNOME_GoHome". Do you want to delete the applet from your configuration? (when i chose delete or don't delete the result is the same nothing happed)
2. The panel encountered a problem while loading "OAFIID:GNOME_WindowPicker". Do you want to delete the applet from your configuration? (when i chose delete or don't delete the result is the same nothing happed)
3. i don't see my icons on desktop again

is there a way i can return to my previous configuration before i used the desktop-switcher

---

### Post by GeorgeVita on 2009-04-26
Hi **y_garti**,
I manage to solve all problems regarding Desktop & panels but working now only with the "old style" standard desktop with the following:

In my first try, I download the **.img** file, test it with **md5sum** and found it ok. Then "burn it" to the USB stick using a **windows** application. Booting from this USB stick (live mode) I made a "**check disk for defects**" and this found an **error in 1 file**. Searching internet I found a **bug report** telling that this is **not a major problem**, so as I had the m5dsum OK I did the installation. Many problems appeared...

I return to: [https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles)

For my second try, I used the **same .img file** which burned to the USB stick using the image burner via **ImageWriter** downloaded to the "problematic" UNR netbook. The stick was **formated in a windows pc** as **FAT-32**. I tried to md5sum test the USB stick but the checksum were not as the file (maybe this is OK because of extra files created or extracted). My result of this was:

[B]sudo md5sum /dev/sdb
c2c595e816935d7bda865fc0cd42f904  /dev/sdb
[/B]

The **/dev/sdb** was my USB stick as created after its attachment checked with the terminal command: **ls /dev/sd***
It could be **/dev/sdc** so needs testing. **The md5sum created after 7 or 8 minutes** with no indication in the terminal window for the progress.

After I did a **fresh install** and select "**use password at login**" (old style) when asked. After the installation I boot (Netbook Desktop look) and the first thing I do was to **change desktop to Standard** (old type). Then I **shut down**. **Boot** again. All panels in their position!

Then I attach my 3G modem, setup the connection, choose a closer repository (to be faster) and I made all upgrades suggested (most of them were Firefox, one was X... i do not remember). Reboot.

**Conclusion**:
I don't know what caused the faults or what action fix it. Possibly the USB disk did not work properly or the repositories have a patched version or ...?
Now I am using the standard desktop only because I fear to  test the Netbook one! Also I don't know how many people (and "debugging" hours or  how many posts) around the globe are tired with this!

Hope above will help a little or give some hope!

Regards,
George

---

### Post by y_garti on 2009-04-26
wow thanks a lot but to tell you the true i formated my hd (i want to test the new ext4) 
so i decided to make a clean installation

but thanks a lot  for trying to help

---

### Post by chaschev on 2009-05-28
[COLOR=Silver]What helps is

```
rm -r .gconf* .gnome*
```but all gnome-configuration data will be lost after running this command. You may want to backup these folders first and then to restore pieces of configuration manually. Also one may try creating a new user - the new user has a fully functional netbook desktop - and duplicating a bug there. 

Just to add. After running kdiff3 on the 'fielthy and healthy' species of folders mentioned above, you will notice that Ubuntu changes a lot. Now I don't have for further analysis, sorry. :)[/COLOR]  

UPDATE:

[https://bugs.launchpad.net/desktop-switcher/+bug/349519](https://bugs.launchpad.net/desktop-switcher/+bug/349519)

In short,

1. install attached deb package (version 0.4.6)
2. rm -r ~/.config/desktop-switcher
3. switch to preferred desktop (I think, this one is optional)
4. Execute configuration command

Netbook-mode should be: gconftool-2 --set /desktop/gnome/session/required_components_list --type list --list-type=string ["windowmanager","panel"]


 Classic mode:
 gconftool-2 --set /desktop/gnome/session/required_components_list --type list --list-type=string ["windowmanager","panel","filemanager"]


5. Log Out, Log In

 
Hope this helps!

---

