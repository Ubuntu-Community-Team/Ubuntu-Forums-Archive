---
title: "dpkg-reconfigure -phigh xserver-xorg does NOTHING in karmic!!!"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by humphreybc on 2009-10-30
This command won't work in karmic, so I can't bloody well reconfigure my Xorg.conf file to boot again.

I tried writing it from scratch but I obviously got it wrong and can't boot. I'm typing this from the liveCD.

So, what's the new command to reconfigure the Xorg.conf file with a NEW default one????

---

### Post by wilburthemexican on 2009-10-31
wow, i have the same issue. does nothing at all. Did you figure this out?

---

### Post by u007 on 2009-11-01
same here...:(

---

### Post by zefiriss01 on 2009-11-02
same

---

### Post by kansasnoob on 2009-11-02
I've been lucky. The default options give me what I need.

But yeah there is no longer that option if needed!

I'm feeling that with a lot of changes, like it's my way or the highway!

I need to run the reconfigure X option from recovery mode and see if I can parse what it does. Documentation needs to be improved!

---

### Post by phpcitizen on 2009-11-04
Same here. Is there an alternative method now? 

Developers please?

---

### Post by starcannon on 2009-11-04
I have not had reason to see if this will work or not, but perhaps [try out these]("http://wiki.archlinux.org/index.php/Xorg#Xorg_-configure") commands.


GL 

Starcannon

[http://wiki.archlinux.org/index.php/Xorg#Xorg_-configure](http://wiki.archlinux.org/index.php/Xorg#Xorg_-configure)

---

### Post by LarryJ2 on 2009-11-04
Does
***gksudo dpkg-reconfigure -phigh xserver-xorg***
or
[I][B]sudo  dpkg-reconfigure -phigh xserver-xorg
[/B][/I]
result in a revised  /etc/X11/xorg.conf file?

I use the nvidia driver and  you can  start nvidia-settings from the menu (System->Admin->Nvidia Settings) all day but nothing is written to the xorg.conf until you start nvidia-settings from a terminal (Applications->Accessorites->Terminal)  like this:

***sudo nvidia-setting***s

/etc/X11/xorg.conf  has these permissions (using the comand ls -al)
ls -al /etc/X11/xorg.conf
-rw-r--r-- 1 root root 1982 2009-11-04 08:21 /etc/X11/xorg.conf

so your default unprivileged user that you normally logon with doesn't have the rights to modify  xorg.conf.  Only by assumming administrator's rights with the command  "sudo" will xorg.conf be modified.

Or that's my current theory...until it's shown I don't know what I'm talking about...:)

---

### Post by bkratz on 2009-11-04
> **LarryJ2 said:**
> Does
***gksudo dpkg-reconfigure -phigh xserver-xorg***
or
[I][B]sudo  dpkg-reconfigure -phigh xserver-xorg
[/B][/I]
result in a revised  /etc/X11/xorg.conf file?

I use the nvidia driver and  you can  start nvidia-settings from the menu (System->Admin->Nvidia Settings) all day but nothing is written to the xorg.conf until you start nvidia-settings from a terminal (Applications->Accessorites->Terminal)  like this:

***sudo nvidia-setting***s

/etc/X11/xorg.conf  has these permissions (using the comand ls -al)
ls -al /etc/X11/xorg.conf
-rw-r--r-- 1 root root 1982 2009-11-04 08:21 /etc/X11/xorg.conf

so your default unprivileged user that you normally logon with doesn't have the rights to modify  xorg.conf.  Only by assumming administrator's rights with the command  "sudo" will xorg.conf be modified.

Or that's my current theory...until it's shown I don't know what I'm talking about...:)



None of the commands in this thread ( and mentioned sources) allowed me to do what the OP was asking for (create a new  xorg.conf file) , even if they were proceeded by either sudo or gksudo.

My computer has a DVI output and my monitor has only VGA so the automode could not determine the monitor EID.

The way I did this was to put my xorg.conf file from my old 904 system on a thumbdrive (it was VERY minimal). With gksudo I COULD create a blank file with the correct name in /etc/X11 and saved the blank file. I then re-entered  " gksudo gedit /etc/X11/xorg.conf  "  and was able to copy the contents of the thumbdrive to the newly created file. Here I could edit it to my hearts content. Power down then up gave me all kinds of display options then.  Of course the monitor was known as "unknown" but so what.

---

### Post by OffAxis on 2009-11-04
> Is there an alternative method now? 
I believe the alternative method is:
1. Boot into 'Recovery Mode' from grub
2. Choose 'Fix Graphics problems'

---

### Post by Mooble on 2009-11-05
I do not have this "fix graphics problems" option in my recovery mode.  The options I have are:

resume
clean
dpkg
grub
netroot
root

I tried dpkg, but it didn't fix it.  What else can I try?

---

### Post by Arup on 2009-11-05
After install of nvidia via hardware applet, tried doing gksudo nvidia-settings to change resolution etc. When I go to save it, it would give me a message that unable to parse xorg. Seems like in Karmic, new xorg isn't created so had to do a gksudo nvidia-xconfig and then do a gksudo nvidia-settings and save, all worked out well.

---

### Post by humphreybc on 2009-11-05
I saw "Xorg -reconfigure" as a commnand to replace it somewhere, and it seems to work, but it places a new Xorg in your root folder, and it's completely different to what we want...

---

### Post by Mooble on 2009-11-05
> **Arup said:**
> After install of nvidia via hardware applet, tried doing gksudo nvidia-settings to change resolution etc. When I go to save it, it would give me a message that unable to parse xorg. Seems like in Karmic, new xorg isn't created so had to do a gksudo nvidia-xconfig and then do a gksudo nvidia-settings and save, all worked out well.
Tried this.  And well, I can log in graphically now, but the highest resolutions it lets me use is 640x480.  Which is...interesting.

---

### Post by Arup on 2009-11-05
> **Mooble said:**
> Tried this.  And well, I can log in graphically now, but the highest resolutions it lets me use is 640x480.  Which is...interesting.

If you are using drivers from Ubuntu repos, try the dpkg-reconfigure xserver-xorg

---

### Post by Mooble on 2009-11-05
> **Arup said:**
> If you are using drivers from Ubuntu repos, try the dpkg-reconfigure xserver-xorg
That didn't seem to change anything.  It pauses for a bit after I send the command, but no messages come up, and whent I startx, I still only have resolutions of 640x480 and below.

---

### Post by kansasnoob on 2009-11-05
> **Mooble said:**
> I do not have this "fix graphics problems" option in my recovery mode.  The options I have are:

resume
clean
dpkg
grub
netroot
root

I tried dpkg, but it didn't fix it.  What else can I try?


That's odd. I get:

resume
clean
dpkg
fsck
grub
netroot
root
xfix

I have to use the arrow keys to get all the way from one end of the list to the other.

---

### Post by Mooble on 2009-11-05
That's...very strange.  Are you using 9.10?  Though, I suppose this would have more to do with the version of Grub I'm using?  Is there perhaps a way for me to check?

---

### Post by humphreybc on 2009-11-05
I don't have a graphical recovery option in 9.10, GRUB2.

I'm pretty sure it has nothing to do with the bootloader.

I can confirm that sudo dpkg-reconfigure -phigh xserver-xorg doesn't do anything anymore. It's not generating a new Xorg.conf at all.

The only command that generates a new Xorg.conf that I'm away of is "Xorg -reconfigure" which creates a "Xorg.conf.new" file in your root folder. That's all well and good, but the Xorg.conf file it generates is nowhere near the one that dpkg-reconfigure -phigh xserver-xorg did...

... so, not so good. I don't really fancy re-writing my Xorg from scratch each time in a recovery terminal.

Does someone want to report a bug?

---

### Post by bodhi.zazen on 2009-11-05
With xorg 7 , xorg.conf is depreciated, everything is supposed to be automatic now.

dpkg-reconfigure -phigh xserver-xorg  

has done nothing for me since 8.10 ?

With nvidia cards you simply 

gksu nvidia-settings 

with intel cards it has been hit and miss. Sometimes you can manually write and xorg.conf, and sometimes not.

xorg.conf does not even exist on my 9.10 install , had to write a custom file for my netbook.

---

### Post by Tony Newton on 2009-11-23
Sooo....  the answer is .....  what?

This is the supposed bulletproox-X that was heralded as such an improvement.  Ha!

Still trying to figure out how to fix....  thinking about going to another OS....

---

### Post by HeadHunter00 on 2009-11-23
Hey, you're right.

---

### Post by HeadHunter00 on 2009-11-23
Just don't move to another OS please. What do you need it for?

---

### Post by HeadHunter00 on 2009-11-23
I found out that it isn't supposed to open anything. This command just restarts xorg-server.

---

### Post by HeadHunter00 on 2009-11-23
> **Tony Newton said:**
> Sooo....  the answer is .....  what?

This is the supposed bulletproox-X that was heralded as such an improvement.  Ha!

Still trying to figure out how to fix....  thinking about going to another OS....

You won't need bulletproofx. Again, don't switch ubuntu, PLEASE! PLEASE!

---

### Post by doas777 on 2009-11-23
if you have nvidia drivers installed and nvidia-settings says it cannot parse the existing file, you can either delete the old xorg, or use 
```
sudo nvidia-xconfig
```

for ati, I believe it is 
```
ati-config --initial
```

---

### Post by Sealbhach on 2009-11-23
Is there any new Community documentation been written up about this? It seems there's been so many changes in 9.10 that even experienced users are sort of starting from scratch again.

This page looks out of date now: [https://help.ubuntu.com/community/Video](https://help.ubuntu.com/community/Video)

.

---

### Post by lpanebr on 2009-11-24
same problem here on a fresh 9.10 install. Managed to fix like this:

restore default lowres driver:

1. enter the shell (ctrl+alt+F1)
2. sudo nano /etc/X11/xorg.conf
3. change the "nvidia" to "nv"
4. sudo reboot -f now
this restored my lowres default driver...

after login:

1. open System>Administration>Hardware Drivers
2. choose the oldest version and restart after it is installed
3. login and open System>Preferences>Display
it will prompt to open the nvidia manager. accept and change settings...

it worked for me.

---

### Post by klemperal on 2009-12-05
I'm having this same problem of "gksudo dpkg-reconfigure -phigh xserver-xorg,"and similar aforementioned commands, not doing anything.  Where I think the confusion is coming from is that this is the case when Nvidia drivers are NOT installed.  The reason I am needing to reconfigure xserver is because the xserver wants to use the old xorg.conf that was made via Nvidia-settings when the nvidia-driver was installed.  Something like this should just work on Ubuntu--what program should I file this under in a bug report by the way?

---

### Post by bodhi.zazen on 2009-12-05
> **klemperal said:**
> I'm having this same problem of "gksudo dpkg-reconfigure -phigh xserver-xorg,"and similar aforementioned commands, not doing anything.  Where I think the confusion is coming from is that this is the case when Nvidia drivers are NOT installed.  The reason I am needing to reconfigure xserver is because the xserver wants to use the old xorg.conf that was made via Nvidia-settings when the nvidia-driver was installed.  Something like this should just work on Ubuntu--what program should I file this under in a bug report by the way?

For the nvidia driver use :

```
gksu nvidia-settings
```

If you wish to file a bug report, please do so with Nvidia as the driver is not maintained by Ubuntu (Nvidia is a closed source, proprietary driver).

---

### Post by klemperal on 2009-12-05
> "Where I think the confusion is coming from is that this is the case when Nvidia drivers are NOT installed"

Again, the various commands to reconfigure xserver-xorg do nothing when the Nvidia drivers are **_NOT_** installed.  Because there are no Nvidia drivers installed, using Nvidia settings isn't even an option (Nvidia-settings usually gets uninstalled when the nvidia driver is uninstalled correct?).  So, now that we are all on the same page about the status of Nvidia drivers (them being uninstalled) does anyone have any potential solutions to this problem?  Also, since this is not an nvidia-settings problem, under what program should I reprt this as a bug--xserver-xorg?

---

### Post by bodhi.zazen on 2009-12-05
> **klemperal said:**
> Again, the various commands to reconfigure xserver-xorg do nothing when the Nvidia drivers are **_NOT_** installed.  Because there are no Nvidia drivers installed, using Nvidia settings isn't even an option (Nvidia-settings usually gets uninstalled when the nvidia driver is uninstalled correct?).  So, now that we are all on the same page about the status of Nvidia drivers (them being uninstalled) does anyone have any potential solutions to this problem?  Also, since this is not an nvidia-settings problem, under what program should I reprt this as a bug--xserver-xorg?

So, install the nvidia driver. It is in the Ubuntu repositories.

[http://packages.ubuntu.com/search?searchon=names&keywords=nvidia](http://packages.ubuntu.com/search?searchon=names&keywords=nvidia)

[http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html](http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html)

Again, in terms of a bug report, you will need to report the bug against the nvidia driver with nvidia.

Ubuntu, Fedora, Xorg, etc will reject any bug reoprt you file aginst the nvidia driver as they do not maintain the nvidia driver.

---

### Post by humphreybc on 2009-12-05
I think I have heard that removing the functionality of restoring the original Xorg is a design decision. The X server team are slowly trying to remove the dependency on the complicated Xorg.conf file, and just have the whole system automated.

Don't take me 100% on this, but I think dpkg-reconfigure -phigh xserver-xorg is actually meant to do nothing in Karmic.

Unfortunately problems do still arise, it's not completely automated right now - so it would be nice to still have some command to reset the Xorg.conf file to default.

---

### Post by klemperal on 2009-12-05
> **humphreybc said:**
> I think I have heard that removing the functionality of restoring the original Xorg is a design decision. The X server team are slowly trying to remove the dependency on the complicated Xorg.conf file, and just have the whole system automated.

Don't take me 100% on this, but I think dpkg-reconfigure -phigh xserver-xorg is actually meant to do nothing in Karmic.

Unfortunately problems do still arise, it's not completely automated right now - so it would be nice to still have some command to reset the Xorg.conf file to default.

Thanks for the reply.  I just wish the xserver people would have figured out how to replace this functionality before they went and removed it.

---

### Post by IntuitiveNipple on 2010-01-10
There are two problems here:

[LIST=1]
[*]Displays that don't provide [Extended Display Identification Data]("http://en.wikipedia.org/wiki/Extended_display_identification_data") (EDID) (bug [#194760]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/194760")) - usually because they are older models.

[*]Xorg server using the RandR extension (Resolution and Refresh) to determine the best settings for the display based on graphic adaptor capabilities and EDID information.
[/LIST]

So when the display doesn't/can't supply EDID the system has to choose sensible defaults that are guaranteed to work on all systems. They use the VESA standard modes for 640x480 and 800x600 for this.

Because Xorg relies on RandR which provides no easy mechanism to select a display resolution manually the user ends up having to manually create an /etc/X11/xorg.conf that describes the display's timing and resolution characteristics. 

```
dpkg-reconfigure -phigh xserver-xorg
```
Before RandR this would work to write the sections of xorg.conf based on the user's manual choices.

Now this has gone it is a backward step in terms of supporting older hardware and doesn't provide a fallback.

Consequently the user must manually create a correct xorg.conf themselves.

Here's an example **/etc/X11/xorg.conf** for a Sony Vaio SRX41 or SRX51 that has a 1024x768 LCD panel and an Intel 815 controller:
```

Section "Device"
	Identifier	"Intel Corporation 82815 CGC"
	Driver		"intel"
EndSection

Section "Monitor"
	Identifier	"LCD Panel 1024x768"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82815 CGC"
	Monitor		"LCD Panel 1024x768"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

```
The key thing to understand is that each section's Identifier is the key that other sections use to refer to it. You can see that a Screen is a combination of a Device and a Monitor, and a ServerLayout specifies the Screen.

I determined the monitor frequencies from the original Windows XP monitor device .inf file but these can also be found by searching for the model number via a search engine. The correct driver for the graphics controller needs to be specified under Device (don't use "intel" on an Nvidia "nv" system, for example).

After writing the file with super-user privileges (Xubuntu: gksudo mousepad /etc/X11/xorg.conf, Ubuntu: gksudo gedit /etc/X11/xorg.conf) log-out and Xorg will restart with the new settings.

If the settings chosen cause a failure which makes the display unusable, restart the PC and at the boot menu choose Recovery mode. Once at the shell prompt you can move the file 'out of the way':
```

# let Xorg auto-detect the display again
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bad

```
and/or experiment with the settings:
```

nano /etc/X11/xorg.conf

```

---

### Post by lzd on 2010-01-25
I'm having a similar problem after doing some messing around in synaptic I shouldn't have. Only thing is though I'm using ATI drivers and it doesn't recognize them when I try that settings command even though I installed the drivers using envyng. I guess I'll just have to reinstall Ubuntu.

---

### Post by DarkN00b on 2010-04-08
I am running Karmic (UNR) with an ATI card and I can _confirm_ that entering

```
ati-config --initial
```

into a terminal window and hitting the Enter key fixed my problems after installing the FGLRX driver. I was just getting my top panel, its associated applets and a blank desktop until I entered that command. After entering the command I restarted my graphical environment and everything worked fine. I had my desktop and interface back.

---

