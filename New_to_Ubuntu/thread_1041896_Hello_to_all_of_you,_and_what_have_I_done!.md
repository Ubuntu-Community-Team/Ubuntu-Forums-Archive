---
title: "Hello to all of you, and what have I done!"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by Lee Denault on 2009-01-17
Let me start off by saying that I have looked for the solution to my problem, but  right now all the lingo and codes are french to me. I simply do not understand, but I want to.

I will point form my steps and put my problem in bold (easier to comprehend)[I have no idea what my sound/video cards are, I don't even know how to find out that information..]

- I am dual booting Vista and Ubuntu for about 14 hours now

- I have installed it correctly, downloaded and installed 219 packages (time consuming!)

- I like the alertness of Ubuntu and the speedy start-ups

- I disliked the screen resolution 800x600 I believe it was.

- I started something called 'Orca' I think?

- took me through all of these steps, and like a fool I said yes or 'y' to everything.

- **Now after I type in my user name and password(during this stage it has my desired resolution)but after this stage my monitor goes completely black, and says 'input not recognized'**

I have an Acer machine, Acer monitor....I'm not sure how to give you other information which I am positive is necessary. 

HELP! I want to be a Linux person.

---

### Post by melojo on 2009-01-17
boot into recovery and type the code below.

```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by Bucky Ball on 2009-01-17
[http://live.gnome.org/Orca](http://live.gnome.org/Orca)

That might be of some help. Yea, doesn't sound like orca was the way to go. What kind of graphics card have you got? You need the correct linux drivers for that. I have never used orca but am presuming the magnification is set to high (bigger than your screen).

---

### Post by Lee Denault on 2009-01-17
Ok I'm going to do what you said, I'm going to get my laptop. So hopefully we can have a speedy conversation, while I do all the surgery on the home computer!

---

### Post by Lee Denault on 2009-01-17
> **melojo said:**
> boot into recovery and type the code below.

```

sudo dpkg-reconfigure xserver-xorg

```

I have the choices of

resume
clean
dpkg
fsck
root
xfix

Where do I type in the code?

---

### Post by Lee Denault on 2009-01-17
> **Bucky Ball said:**
> [http://live.gnome.org/Orca](http://live.gnome.org/Orca)

That might be of some help. Yea, doesn't sound like orca was the way to go. What kind of graphics card have you got? You need the correct linux drivers for that. I have never used orca but am presuming the magnification is set to high (bigger than your screen).

Nvidia GEForce 6100nforce 405?

Does that sound right?

---

### Post by melojo on 2009-01-17
choose xfix

you won't need to type in the code

---

### Post by cariboo on 2009-01-17
You don't have to type in any commands (the code tags are a misnomer) just select xfix at the menu and it will do the same thing as typing:

```
sudo dpkg-reconfigure xserver-xorg
```

The xfix command creates a new /etc/X11/xorg.conf with  the default settings.

Jim

---

### Post by Lee Denault on 2009-01-17
> **melojo said:**
> choose xfix

you won't need to type in the code

Thank you very much, worked perfect.



can you send me in the right direction of how to get the resolution I want?

My monitor is an acer AL1716

---

### Post by Lee Denault on 2009-01-17
I hope I don't piss you guys off, I'm just really intrigued by Linux and would love to learn how to get around on my own.

---

### Post by cariboo on 2009-01-17
Go to System-->Administration-->Hardware Drivers, this should pop a window that allows you to enable the restricted drivers fo your video card. The restricted drivers are closed source, that are maintained by the respective manufacturers. I have a Nvidia 8400GS video card and an Acer AL1714 monitor and I get 1280X1024 resolution.

Jim

---

### Post by Lee Denault on 2009-01-17
I went to

System>Admin>Hardware Drivers

Activated Nvidia (Version 177)

Restarted, and the same thing happened, the black screen upon start-up.

I'm back to the hardware driver screen again. 

Should I try the other 2 options?

---

### Post by Lee Denault on 2009-01-17
All 3 options in the hardware drivers window inevitably end up with the same black screen on start-up

---

### Post by Lee Denault on 2009-01-17
I found this site for me Graphics Card.

[http://hardware4linux.info/component/28118/](http://hardware4linux.info/component/28118/)

So it is compatible. She just needs some tweaking, I just don't know what or how do to the tweaking.

---

### Post by minsf on 2009-01-17
i think if you use ctrl+alt+f1 you'll get from the black screen to the command line interface (you'll probably need to enter your password).

now the problem seems to be that the drivers have been installed, but the configuration file /etc/X11/xorg.conf is not configured correctly.
you'll have to edit this file. if you have to edit it manually, use ```
sudo nano /etc/X11/xorg.conf
```(use ctrl+o to save and ctrl+x to exit this editor). but there may be some tools that will edit this file for you, like the "dpkg-reconfigure" command that was suggested to you in post #2. 

I am not so sure how exactly to edit this file, but after editing has been done, you should restart the desktop manager with ```
sudo /etc/init.d/gdm restart
```

before editing, you may want to back up these xorg.conf files, so that if something goes wrong you can go back to your backup version. you can do it with ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```with the idea that we copied the file to the file xorg.conf.old 
if you need to back it up again you can copy it to xorg.conf.old2 and so on. 
if you ever want to replace your backup file with the current xorg.conf, you use:```
sudo mv /etc/X11/xorg.conf.old /etc/X11/xorg.conf
```

some help with editing be found with the "man xorg.conf" command, though i hope some people can suggest something here :)

---

### Post by sayabis on 2009-01-17
Same thing happended here. I'm also new to ubuntu. After changing the resolution, my old crt AOC 14" monitor went nuts and went blank. All the LED lights in my old crt monitor lit up like crazy. I tried rebooting and after loging in, my crt again went blank.

I tried ctrl+alt+f1 and entered the command "sudo dpkg-reconfigure xserver-xorg" and nothing happened.

I also tried booting in recovery and selecting xfix and still nothing happend.

I also tried editing the xorg.conf using crtl+alt+f1 to get into the command line and entered "sudo nano /etc/x11/xorg.conf". The xorg.conf opened but turned out empty. I was hoping to edit the xorg.conf. 

Is there another way to edit the screen resolution via recovery mode or ctrl+alt+f1?

This is drving me nuts.

---

### Post by minsf on 2009-01-17
sayabis, capital X in "X11"! it is important! dont forget to back up the file before editing it.

---

### Post by redseventyseven on 2009-01-17
Lee, I have an NVidia graphics card in my desktop machine, and it took me an age to get it set up correctly when I first started! Don't panic though, it should be possible.

There's a useful tool called "Envy" which is designed to help set up NVidia and ATI drivers. Look for it in the Synaptic Package Manager.

Also, consider Linux Mint - it's a distro which is based on Ubuntu with a few extra tools to help complete beginners get everything set up straight away.

---

### Post by Bucky Ball on 2009-01-17
Envy won't be required. The 177 is correct for this card pretty sure. 

You probably need to manually edit the xorg.conf file. Could you boot to recovery kernel, drop to root then type:

```
sudo nano /etc/X11/xorg.conf 
```Look for a section that is headed 'device', and the identifier is 'configured video device' and try changing it to this:

```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "nvidia"
        Option          "NoLogo"        "True"
```Hit control/x to exit, agree to save etc. then type 'exit' and that will take you back to the options. Choose the first one, resume booting.

If you're keeping up, well done and stick with it. Any different?

---

### Post by Lee Denault on 2009-01-17
> **Bucky Ball said:**
> Envy won't be required. The 177 is correct for this card pretty sure. 

You probably need to manually edit the xorg.conf file. Could you boot to recovery kernel, drop to root then type:

```
sudo nano /etc/X11/xorg.conf 
```Look for a section that is headed 'device', and the identifier is 'configured video device' and try changing it to this:

```
Section "Device"
        Identifier      "Configured Video Device"
        **[B]Driver          "nvidia"**[/B]
        Option          "NoLogo"        "True"
```Hit control/x to exit, agree to save etc. then type 'exit' and that will take you back to the options. Choose the first one, resume booting.

If you're keeping up, well done and stick with it.Any different?

No different:(

But when I looked for the section "device" for the first time.

There was no Driver line (the part I bolded)

So I created it...didn't work

---

### Post by minsf on 2009-01-17
> **Lee Denault said:**
> No different:(

But when I looked for the section "device" for the first time.

There was no Driver line (the part I bolded)

So I created it...didn't work

before you started editing, did you boot to recovery kernel or did you use alt+ctrl+f1 or did you use the live cd to get to the command line interface? 
dont get to the command line via the live cd. if you use the live cd you need to mount the hard drive and look for the xorg.conf file through the mounted root.
i like to do this editing by a regular boot, then alt-ctrl+F1 when you get the black screen. after the editing suggested by bucky in post #18, dont forget the "sudo /etc/init.d/gdm restart" command.

---

### Post by Lee Denault on 2009-01-17
> **minsf said:**
> before you started editing, did you boot to recovery kernel or did you use alt+ctrl+f1 or did you use the live cd to get to the command line interface? 
dont get to the command line via the live cd. if you use the live cd you need to mount the hard drive and look for the xorg.conf file through the mounted root.
i like to do this editing by a regular boot, then alt-ctrl+F1 when you get the black screen. after the editing suggested by bucky in post #18, dont forget the "sudo /etc/init.d/gdm restart" command.


I booted to recovery. I then did the editing, didnt work.

I then pressed alt+ctrl+f1 during the black screen, did the editing...BUT there was a line there this time that wasn't there before.

Option      "useFBDev"              "True"

But I seem to be having a lot of trouble lol

---

### Post by albinootje on 2009-01-17
> **Lee Denault said:**
> Thank you very much, worked perfect.
So.. you have a higher resolution than 800x600 now ?

> 
can you send me in the right direction of how to get the resolution I want?

My monitor is an acer AL1716

-> System -> Preferences -> Screen Resolution

---

### Post by Lee Denault on 2009-01-17
> **albinootje said:**
> -> System -> Preferences -> Screen Resolution

Turns out I have bigger problems:(

---

### Post by Lee Denault on 2009-01-17
Will this help?

[http://www.nvidia.com/object/linux_display_ia32_1.0-8174.html](http://www.nvidia.com/object/linux_display_ia32_1.0-8174.html)

---

### Post by chriscross93 on 2009-01-17
> **Lee Denault said:**
> Turns out I have bigger problems:(

I could be wrong, but I was having similar problems until I install the ATI drivers for my card:KS.  Goto
System->administration->Hardware Drivers
and see if you have the proprietary drivers enabled.  Whatever open source driver ubuntu may be using may not really work with your graphics card.  Once thats done (reboot) and then try to change your resolution.

READ: I didn't read the entire thread, I could be totally off the mark, but this is my best guess:confused: after reading the first and last page.

*good luck*:)

---

### Post by albinootje on 2009-01-17
> **Lee Denault said:**
> Will this help?

[http://www.nvidia.com/object/linux_display_ia32_1.0-8174.html](http://www.nvidia.com/object/linux_display_ia32_1.0-8174.html)

The restricted Nvidia driver that you already tried, probably has that driver (or similar) bundled already.

Another option for you is to go back to the original state where you had the 800x600 screen, and then generate a ModeLine for your graphics configuration based on the monitor specifications from the manual of your monitor.

Here's an online ModeLine generator :
[http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)

---

### Post by Lee Denault on 2009-01-17
> **chriscross93 said:**
> I could be wrong, but I was having similar problems until I install the ATI drivers for my card:KS.  Goto
System->administration->Hardware Drivers
and see if you have the proprietary drivers enabled.  Whatever open source driver ubuntu may be using may not really work with your graphics card.  Once thats done (reboot) and then try to change your resolution.

READ: I didn't read the entire thread, I could be totally off the mark, but this is my best guess:confused: after reading the first and last page.

*good luck*:)

Once I enable a proprietary driver, it will tell me to restart, so i do, but then the black screen comes following the reboot.

---

### Post by lakersforce on 2009-01-17
> **Lee Denault said:**
> 
- **Now after I type in my user name and password(during this stage it has my desired resolution)but after this stage my monitor goes completely black, and says 'input not recognized'**


Easy/cumbersome solution (depends on the way you look at it): Connect your pc to a different monitor and change the refresh rate and/or resolution, and plug it back in to your Acer.

---

### Post by Lee Denault on 2009-01-17
I guess this damn thing isn't going to work eh?

---

### Post by Lee Denault on 2009-01-17
Will this work?


This person has all the problems I have with the same graphic card

[http://ubuntuswitch.blogspot.com/2008/12/ubuntu-810intrepid-change-default.html](http://ubuntuswitch.blogspot.com/2008/12/ubuntu-810intrepid-change-default.html)

---

### Post by Lee Denault on 2009-01-17
```
Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```



Doesn't even look like it knows I have a monitor.

I have an ACER  AL1706

---

### Post by Bucky Ball on 2009-01-17
Now add the changes I mentioned before. Make sure you do it from recovery kernel, drop to root shell at the options; that way you haven't started X, back to normal boot and see how you go.

```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "nvidia"
        Option          "NoLogo"        "True"
```

... making sure you have Hardware Drivers->Nvidia driver enabled first.

---

### Post by chriscross93 on 2009-01-17
> **Lee Denault said:**
> Once I enable a proprietary driver, it will tell me to restart, so i do, but then the black screen comes following the reboot.

Hmmm....So it appears that your monitor does not support the native resolution of your video card.  Do you have another monitor that you can hook up?  If you hook another one up that works, you can use it to set the resolution that you need and then hook your first one back up. 


...That seems like the easiest solution, assuming you have another one.

---

### Post by Bucky Ball on 2009-01-17
You could also go to Synaptics and install:

nvidia-xconf

... see if that gives you any joy ...

---

### Post by Lee Denault on 2009-01-17
> **Bucky Ball said:**
> Now add the changes I mentioned before. Make sure you do it from recovery kernel, drop to root shell at the options; that way you haven't started X, back to normal boot and see how you go.

```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "nvidia"
        Option          "NoLogo"        "True"
```

... making sure you have Hardware Drivers->Nvidia driver enabled first.

No I don't, the screen goes black after the reboot.

when the screen goes black should I press ALT+CTRL+F1 then... sudo nano /etc/X11/xorg.conf 

Than tell you what it says?

---

### Post by Bucky Ball on 2009-01-17
Nope, boot from the recovery kernel. Choose 'Root shell' from the options then make the changes. When you have, type 'exit' in the shell and you will get back to the options. Proceed with the first selection, resume normal boot. :)

You can also keep an eye out during the boot process for any errors that might come up in the screen text before it gets to the options. Does it hang anywhere else?

But you really need to enable the restricted driver first if you can get back to a low res boot. Order should be.

Enable driver
Reboot to recovery kernel
Drop to root and make changes
Resume normal boot

... and see what happens.

---

### Post by chriscross93 on 2009-01-17
> **Lee Denault said:**
> No I don't, the screen goes black after the reboot.

when the screen goes black should I press ALT+CTRL+F1 then... sudo nano /etc/X11/xorg.conf 

Than tell you what it says?

yes.:)

---

### Post by Lee Denault on 2009-01-17
Ok, be right back.

---

### Post by Leo Dragonheart on 2009-01-17
Do an advanced search and tpye in Nvidia in the key words and Leo Dragonheart in the user thingy... there is a thread I posted a couple days ago and a guy showed me step by step how to fix it...

---

### Post by Leo Dragonheart on 2009-01-17
Here is what he told me to do...



I've had the exact same problem with NVIDIA cards and the restricted driver. I searched for months to find an answer and I must tell you it was a painful runaround. The good news is I was able to fix it easily, simply by manually editing my xorg.conf file. In my case the problem was not with the NVIDIA driver at all. The problem was that my monitor was not correctly recognized by the X-server system. Once I identified my monitor specs in the xorg.conf file, everything worked perfectly. This is how I did it.

First you need to open your xorg.conf file in Gedit, like this:

Code:

**sudo gedit /etc/X11/xorg.conf**

You'll have to enter your password to gain editing privileges.

Some say you should back up the file first, but I found gedit does this automaticaliy, and right now your original file isn't doing you much good anyway.

Next, you have to add a few lines to specific sections of your xorg.conf file. BUT DO NOT CHANGE ANYTHING ELSE!

In the Monitor section add the lines that appear in bold:
Code:

Section "Monitor"
    Identifier     "Configured Monitor"
   [B] HorizSync       31.0 - 65.0
    VertRefresh     51.0 - 90.0	[/B]
EndSection

Note that these are the specs that fit my particular monitor. They'll probably work for yours also - but if you want to you can replace the VertRefresh and HorizSync values with your monitor's actual data if you know what they are.

Next, in the Screen section add the lines that appear in bold, right before the EndSection line.

Code:

  [B]  SubSection     "Display"
        Depth       24
        Modes      "1280x1024_60"
    EndSubSection[/B]

This set my monitor to my desired resolution which is 1280X1024. You can substitute the resolution data to suit your needs. Reboot your computer and you should have a high resolution display. Next, you should run the NVIDIA settings program to fine tune your system.

If this doesn't work, then you can boot in recovery mode and select the fix x-server option. This will give you a high resolution display but no special effects, etc.

I hope this helps.

---

### Post by Lee Denault on 2009-01-18
Ok, I'm going to try this Leo,

Do I go to Add/Remove to get Gedit?

---

### Post by Leo Dragonheart on 2009-01-18
No go to accesories then terminal

---

### Post by Lee Denault on 2009-01-18
> **Leo Dragonheart said:**
> No go to accesories then terminal

Ok, Wish me luck!

---

### Post by Leo Dragonheart on 2009-01-18
Good luck...

---

### Post by Lee Denault on 2009-01-18
Ok, I press 'Save' After?

---

### Post by Leo Dragonheart on 2009-01-18
yep...

---

### Post by Lee Denault on 2009-01-18
IT WORKED!!!!!!!

YES!!!

Thank you so much everybody!!!!

Especially you Leo!!


Finally I can see!!!

Time to celebrate with a nice cold adult beverage!:guitar:

---

### Post by minsf on 2009-01-18
glad to hear it worked!
enjoy!

---

### Post by Leo Dragonheart on 2009-01-18
Fantastic glad it worked...This forum is flooded with Nvidia problems they should put a seperate section for it... Glad I could help but I just passed on the info...

---

### Post by Lee Denault on 2009-01-18
Now, I am going to dink around with Compiz

---

### Post by Bucky Ball on 2009-01-18
Hoorah, they exclaimed! Leo Dragonheart, knew there was something to be done with those sections of the xconf but wasn't sure what. Good fix. 

Have fun exploring and playing with Compiz.

---

