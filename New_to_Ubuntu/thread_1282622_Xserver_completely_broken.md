---
title: "Xserver completely broken"
date: 2009-10-04
forum: New to Ubuntu
---

### Post by iamjfarrell on 2009-10-04
I tried to download a new nVidia driver and when I ran and installed it. It messed up my xserver. I tried to go through the GUI to use the old driver but it doesn't seem to work. What should I do to fix the problem?

---

### Post by sandyd on 2009-10-04
```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by iamjfarrell on 2009-10-04
> **carlee said:**
> ```

sudo dpkg-reconfigure xserver-xorg

```

This seemed mostly concerned with my keyboard setup.

---

### Post by sandyd on 2009-10-04
that will completely reset your xserver config.

---

### Post by iamjfarrell on 2009-10-04
I did it and I am still on 800X600 resolution. I tried to apply the nVidia driver 180 through the GUI hardware drivers program, restarted and still no changes.

---

### Post by iamjfarrell on 2009-10-04
```
nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver
                  line.


ERROR: Unable to write to directory '/etc/X11'.
```

I don't know if that helps any but that is different from what it said before I did the dpkg reconfigure

---

### Post by bwallum on 2009-10-04
Try> gksudo gedit /etc/X11/xorg.confthen look for a section headed > Section "Device"
	Identifier	"Default Device"
	Driver	"nv"
	Option	"NoLogo"	"True"
EndSection

Change Driver to "nv" if not already there and see if that works

---

### Post by iamjfarrell on 2009-10-04
> **bwallum said:**
> Trythen look for a section headed 

Change Driver to "nv" if not already there and see if that works

I copy and pasted all that into place of the section that was there. it said something of the effect configured device or something like that.

---

### Post by bwallum on 2009-10-04
Try System>Preferences>Display

Can you change the resolution there?

---

### Post by iamjfarrell on 2009-10-04
> **bwallum said:**
> Try System>Preferences>Display

Can you change the resolution there?

I tried that and this is what I got. 

It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?

---

### Post by bwallum on 2009-10-04
Thats a pointer to the NVIDIA X Server Settings tool.

Click on yes and the second line down in the left panel should allow to reset the resolution. Then save the configuration when happy.

---

### Post by iamjfarrell on 2009-10-04
> **bwallum said:**
> Thats a pointer to the NVIDIA X Server Settings tool.

Click on yes and the second line down in the left panel should allow to reset the resolution. Then save the configuration when happy.

This is what I get when I try to run that. 

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

And when I run nvidia-xconfig this is what I get.

```
nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver
                  line.


ERROR: Unable to write to directory '/etc/X11'.

```

---

### Post by bwallum on 2009-10-04
It's really best to use System>Administration>Hardware Drivers to change your nVidia driver as it takes away a lot of the manual intervention away that we are doing now. The 185 driver is really nice and stable for me. Consider choosing the one recommended for your card if you need to change the driver again.

---

### Post by bwallum on 2009-10-04
Try to load the driver from Hardware Drivers

---

### Post by iamjfarrell on 2009-10-04
I have tried to use the Hardware Drivers program. When I use it it says a restart is required. I restart and I start ubuntu with no X-server. Is there a way I can uninstall the .run driver I tried to install

---

### Post by bwallum on 2009-10-04
I would fall back to carlee's advice running in recovery mode.```
sudo dpkg-reconfigure xserver-xorg
```

To enter recovery mode reboot and when the grub menu appears (you may have to press ESC when prompted if you don't normally have the grub menu showing) select recovery mode, usually the line below the top one with single os systems.

Then you type in the code above and follow the prompts. When you return to the command line prompt type[HTML]sudo reboot[/HTML]

That should take you back to a standard driver, you can then reload the accelerated driver from Hardware Drivers.

---

### Post by iamjfarrell on 2009-10-04
> **bwallum said:**
> I would fall back to carlee's advice running in recovery mode.```
sudo dpkg-reconfigure xserver-xorg
```

To enter recovery mode reboot and when the grub menu appears (you may have to press ESC when prompted if you don't normally have the grub menu showing) select recovery mode, usually the line below the top one with single os systems.

Then you type in the code above and follow the prompts. When you return to the command line prompt type[HTML]sudo reboot[/HTML]

That should take you back to a standard driver, you can then reload the accelerated driver from Hardware Drivers. 

I need to be in recover mode to do this? I have done it in normal. I will try it in recovery.

---

### Post by iamjfarrell on 2009-10-04
In recovery mode I couldn't find anywhere to put in code. I did xfix and dpkg. Am I just doomed for 800x600? Back to vista, it is.

---

### Post by bwallum on 2009-10-04
Yes the trouble with doing it in normal mode is that the X server is running. In recovery mode you are changing the system before the X server starts. It is possible to stop and start the xserver in normal mode but you lose the gui so it's just as easy to try the above.

---

### Post by bwallum on 2009-10-04
If you go back to vista you really are doomed :-) but fortunately Ubuntu is quite tolerant so please bear with us a little further.

When you enter recovery mode look for something that says 'consul'. However xfix should have sorted it. Can you try the command using a consul in recovery mode?

---

### Post by iamjfarrell on 2009-10-04
Vista is like breathing in carbon monoxide. haha I didn't see anything that said "consul". 

This whole problem started when I took the advice of someone to upgrade my nVidia driver. I installed the .run driver and it has been messed up ever since. Is there a way to uninstall that?

---

### Post by bwallum on 2009-10-04
I'm sure there must be but it means stopping the xserver and plucking out the files and putting in new ones. 

In recovery mode look for 

root   drop to root shell

You then get a command line. Use that to enter carlee's fix

---

### Post by bwallum on 2009-10-04
Something I overlooked if you still get problems. You said you tried the nvidia-xconfig command. It needs to be run as root. In Ubuntu we do this with the sudo command. So the command should be ```
sudo nvidia-xconfig
```If you still have no joy then try reinstalling your nvidia driver. Do this by following the how to in #19 above. Note that it is important to disable any accelerated driver through Hardware Drivers first, that is, if a green light shows, disable it.

I'm sorry I have to go now. If nobody jumps in to help on this thread then make a new post with something like 'How do I remove an nVidia driver installed with a .run file'

Good luck and I'm really sorry I have to leave at this time.

---

### Post by iamjfarrell on 2009-10-04
I finally got it solved! thank god! It was one little step. I had to go to properties on the .run file and make it an executable. At least that is what I think solved the problem. I just reinstalled the driver.

---

### Post by bwallum on 2009-10-05
Bravo, pleased to hear you got it sorted. I changed from Windows about two years ago, then converted the family (including my 84 year old Mother-in-law), then my friends. Not one has reverted although my son still runs XP in a dual boot box for playing network games. Way to go, good luck.

---

### Post by iamjfarrell on 2009-10-05
> **bwallum said:**
> Bravo, pleased to hear you got it sorted. I changed from Windows about two years ago, then converted the family (including my 84 year old Mother-in-law), then my friends. Not one has reverted although my son still runs XP in a dual boot box for playing network games. Way to go, good luck.

That is very cool. I haven't converted anyone. but I bought my computer and I dual boot with Vista. and loaded ubuntu on it right away. I only use vista when I have to do school work on blackboard. the discussion board doesn't work. I really like it, but I miss my compiz a lot. I have tried fixing it forever

---

### Post by bwallum on 2009-10-06
> **iamjfarrell said:**
> .... but I miss my compiz a lot. I have tried fixing it forever

New updates to compiz yesterday

---

### Post by iamjfarrell on 2009-10-06
> **bwallum said:**
> New updates to compiz yesterday

I am not sure if I got them. I can't remember. I just know that my compiz is completey screwed up. Fusion-icon doesn't open, CCSM doesn't open. It's a mess

---

