---
title: "HP Touchpad Laptop mouse right click not working"
date: 2010-10-02
forum: New to Ubuntu
---

### Post by kmas on 2010-10-02
my touchpad right click doesn't work. Meaning, nothing happens when I right click. I have a button on my key board for right click, but doesn't right click on items where mouse pointer is hovering, I usually right clicks, on different spots, except if it is a clickable item like a file in nautilus, but it wont't work for highlighting. I also went into ubuntu mouse settings and found an annoying work around, i enable right click with long click, so basically after 2 seconds left clicking right click menu context shows up, only problem with that is, it doesn't work well for certain things like links for example, any one on what to do to troubleshoot this?

here's a complete report of my hard info: [http://dl.dropbox.com/u/1567633/hardinfo_report.html](http://dl.dropbox.com/u/1567633/hardinfo_report.html) I'm giving all out, just in case i forget to mention anything, by the ways, i'm on maverick RC AMD 64, HP dv7, synaptic touchpad integrated, not a plug and play. 

ruling out the possibility of it failing because of something i installed, this is a fresh install, ruling out hardware issue, mouse works well under windows. for troubleshooting sake, switched from right handed to left handed, the right click (select) works fine, but the left click (menu) wouldn't bring menu up. I know it has to do with the touchpad configuration on my laptop because USB mouse works. 

[http://ubuntuforums.org/showthread.php?t=1574015](http://ubuntuforums.org/showthread.php?t=1574015)
[http://ubuntuforums.org/showthread.php?t=1572412](http://ubuntuforums.org/showthread.php?t=1572412) 
are the threads that might be related, but they are about physical keyboards and mouse and not touch pads.. 

also found this [bug]("https://bugs.launchpad.net/udev/+bug/637208"), but not quite what i'm looking for. 

I also tried using easy strokes  to set my right click as ctrl clik, but it doesn't work well.

[https://help.ubuntu.com/community/SynapticsTouchpad]("https://help.ubuntu.com/community/SynapticsTouchpad")
the instruction here are useless, maverick doesn't support hal. SMHConfig doesn't work either. My XORG file has nothing on synaptic touchpad. synclient makes mouse freeze instead and doesn't solve issue, makes it even worse because it freezes the USB Mouse too. syndaemon only starts and restart touch pad nothing else.

---

### Post by mörgæs on 2010-10-02
Have you tried 10.04 and 9.10?

---

### Post by kmas on 2010-10-02
yeah i'm just coming from 10.04, it works there..

---

### Post by laithbsoul on 2010-10-02
Then it seems to be a bug with 10.10 RC and your Touchpad

---

### Post by mörgæs on 2010-10-02
It would be great to open a bug report in Launchpad for 10.10 (or confirm it, if there is already one).

---

### Post by Vbitz on 2010-10-03
> **Sabot said:**
> To get the trackpad working correctly you need to use the terminal and enter in the below commands. Make sure you press enter after each command:

    ```
sudo su
```

    ```
echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe
```

    ```
reboot
```


Once the computer reboots your trackpad will be able to do left click and drag and right clicking.

[http://ubuntuforums.org/showthread.php?t=1388164&page=6](http://ubuntuforums.org/showthread.php?t=1388164&page=6)
This fixed it on mine

---

### Post by kmas on 2010-10-04
your solution fixed the right click and left click but it broke everything else... mouse is now very laggy, even if i lower sensitivity it takes forever to take cursor from one end of the screen to the other.. also broke, middle click, edge scrolling, horizontal scrolling and dragging..

also noticed after that, one tab for the mouse option disappeared. I'm navigating through that thread and will report if i fix the other issues..

took a shot at filing a bug.. [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/654716](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/654716)

---

### Post by kmas on 2010-10-13
found a temporary solution. filed a bug. @ [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/654716]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/654716") then my bug was linked to [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/582809]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/582809"), and the solution for this bug, is [POST 61 ]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/582809/comments/61")Under the bug.. 

in case link doesnt work in furture, here is the content.. 
```
It's possible to use dkms to build the psmouse module for the buttonless synaptics touchpad on some newer netbooks.

First make sure dkms package is installed.

Next download this patched source archive for the psmouse module from kernel 2.6.35-22-generic on maverick. I just posted it to this bug, it's called: psmouse-2.6.35-22-generic-patched.tar.bz2

In a terminal, unpack the source archive in /usr/src

Next, in a terminal, enter these commands:

sudo dkms add -m psmouse -v 2.6.35-22-generic
sudo dkms build -m psmouse -v 2.6.35-22-generic
sudo dkms install -m psmouse -v 2.6.35-22-generic

This should install the psmouse.ko module in /lib/modules/<kernel version>/updates/dkms. Reboot to load it.

If the mouse doesn't function properly, use this command to check if it's installed.

sudo dkms status -m psmouse -v 2.6.35-22-generic

If it's not, then try rebuilding it with

sudo dkms build -m psmouse -v 2.6.35-22-generic
sudo dkms install -m psmouse -v 2.6.35-22-generic

Once a new kernel is issued with a fix, then you can remove it with:

sudo dkms uninstall -m psmouse -v 2.6.35-22-generic
sudo dkms remove -m psmouse -v 2.6.35-22-generic --all

I also believe that dkms will automatically build and install it on any kernel upgrade, but haven't tested that yet.

After installing any kernel update, you can test with

sudo dkms status -m psmouse -v 2.6.35-22-generic

and if it's not built, use the above commands to build and install it.

Reboot to make it effective.

For more info, see man dkms for the official documents.
```

*PS use at your own risk.. i don't recommend messing with dkms unless you absolutely either feel that courageous or know what you're doing...

---

### Post by ailharry81b on 2010-10-14
This worked beautifully - genius! Thanks!

---

### Post by rezashamdani on 2010-10-16
thanks :)

---

### Post by radkin on 2010-10-21
That worked great, thank you very much. 
The only problem I have with the touchpad now is:
When trying to move a window to another place it moves in a jerky & unpredictable way.
HP Pavilion dv7

---

### Post by look4reality on 2010-10-31
> **Vbitz said:**
> [http://ubuntuforums.org/showthread.php?t=1388164&page=6](http://ubuntuforums.org/showthread.php?t=1388164&page=6)
This fixed it on mine

Wow..
Thanks buddy
It worked for me...

I am using HP-ProBook 4520s, right click wasn't working for ubuntu 10.10.

Now its alright.
thanks for ya help.

-Arun

---

### Post by jascha on 2010-11-09
I have a ProBook 4520s with 10.10 on it and when I tried the fix in link I saw there was no /usr/lib/X11/xorg.conf.d directory. Looking to get this touchpad working any insights?

---

### Post by KdotJ on 2010-11-09
This has been the most annoying thing for me regarding ubuntu... It has been ages now. Other distros have a package for the so called "clickpad" which work great. As for maverick, I'm using the same work-around as described in this thread, which works for now albeit not 100% smoothly. I hope this gets addressed in Natty...

---

### Post by vale_ron on 2010-12-01
Many thanks, it worked for me!

---

### Post by enfantduchatmort on 2010-12-06
> **radkin said:**
> That worked great, thank you very much. 
The only problem I have with the touchpad now is:
When trying to move a window to another place it moves in a jerky & unpredictable way.
HP Pavilion dv7
it works if you run > synclient JumpyCursorThreshold=200 not sure how to make this permanent though

---

### Post by kishanbhat on 2011-01-30
[I]I could make the change permanent by adding:
[/I]
Option "JumpyCursorThreshold" "100"[I]

to /usr/share/X11/xorg.conf.d/50-synaptics.conf and restarting X.

Ofcourse, I had to apply the mouse patch using dkms ;)
[/I]

---

### Post by HPA on 2011-03-09
> **Vbitz said:**
> [http://ubuntuforums.org/showthread.php?t=1388164&page=6](http://ubuntuforums.org/showthread.php?t=1388164&page=6)
This fixed it on mineThis fixed the problem with the right-click button on mine, but this: _[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/582809/comments/61](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/582809/comments/61)_ didn't fix the problem with the edge scrolling.
When I went to System->Preferences->Mouse, I saw that the third  tab titled "Touchpad" has disappeared, so now I cannot enable/disable  edge (or horizontal) scrolling with a "tick"...
Any suggestion?
Thanks.

---

### Post by akimbo_joe on 2011-03-21
Thankyou, works perfectly:)

---

### Post by HPA on 2011-03-24
After a new attempt, I've managed to solve the problem with edge scrolling in my laptop:
I opened the /etc/modprobe.d folder and deleted the psmouse.modeprobe file which was created after giving these commands in the teminal:[URL="http://forum.ubuntu-gr.org/viewtopic.php?f=4&t=17131&start=20#"]
[/URL]```
sudo su
echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe
reboot
```Now, edge scrolling is activated and the "Touchpad" tab in System->Preferences->Mouse appeared again.
Thank you very much.

---

### Post by lennyp on 2011-04-22
that didn't work for me.  The right-click works now and the terminal says that psmouse is installed when I check for it but the touchpad tab still doesn't appear.

---

### Post by xape on 2011-05-03
It works, tnx :-)

Andrea

---

### Post by Allec on 2011-05-09
thank you man, you are a genius. God bless you !

---

### Post by luberfly on 2011-07-21
And what's about Ubuntu 11.04?

Best Regards

Luca

---

### Post by lubart on 2011-09-11
It works excellent for 10.04 as well!
Thank you!!!

---

### Post by rockvilla on 2011-11-22
This solution worked for my kernel 2.6.35-22-generic
but few days back i updated the kernel to 2.6.32-35-generic-pae to access ram more than 3 gb now the above solution don't work for me can any one help ?


Error I am getting : 


rockvilla@rockvilla-laptop:~$ sudo dkms add -m psmouse -v 2.6.35-22-generic

Error! DKMS tree already contains: psmouse-2.6.35-22-generic
You cannot add the same module/version combo more than once.
rockvilla@rockvilla-laptop:~$ sudo dkms build -m psmouse -v 2.6.35-22-generic

Error! Your kernel headers for kernel 2.6.32-35-generic-pae cannot be found at
/lib/modules/2.6.32-35-generic-pae/build or /lib/modules/2.6.32-35-generic-pae/source.
You can use the --kernelsourcedir option to tell DKMS where it's located, or you could install the linux-headers-2.6.32-35-generic-pae package.

---

