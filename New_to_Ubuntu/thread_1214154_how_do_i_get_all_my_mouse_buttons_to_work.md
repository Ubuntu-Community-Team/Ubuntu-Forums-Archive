---
title: "how do i get all my mouse buttons to work?"
date: 2009-07-15
forum: New to Ubuntu
---

### Post by super kim on 2009-07-15
Hello, i have had to get a new mouse and it has extra buttons. the mouse came with an installation CD for windows but it wont install on ubuntu. How can i get the extra buttons to work?
I also got a new drawing tablet, it also came with an installation CD for windows.
I was impressed that ubuntu required no installation CD for either the mouse or the tablet and both of them instantly worked. the only problem is the buttons on the tablet don't do anything, and the mouse has one button that does nothing. How do i assign something to these buttons?

[COLOR=Gray]$ lsusb
Bus 001 Device 003: ID 1bcf:0c31 Sunplus Innovation Technology Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR]
Bus 003 Device 002: ID 056a:0065 Wacom Co., Ltd 
[COLOR=Gray]Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR]
Bus 002 Device 003: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
[COLOR=Gray]Bus 002 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR]

---

### Post by Favux on 2009-07-15
Hi super kim,

Which version of Ubuntu do you have installed?

Which Wacom tablet did you get?

---

### Post by super kim on 2009-07-16
hello favux, 

the ubuntu i have installed is version 2.26 i think its called jaunty jackolope.
the tablet is called bamboo, the model number is MTE-450A

is this any help?

---

### Post by Favux on 2009-07-16
Hi super kim,

If it's Jaunty it would be 9.04 (2009.April).  The kernel is 2.6.28.  If you're sure it is Jaunty...

Post #4 here:  [http://ubuntuforums.org/showthread.php?t=1211425](http://ubuntuforums.org/showthread.php?t=1211425) tells you how to completely set up your Bamboo.

On the mouse have you found any threads dealing with it?  If not do you by any chance know which .fdi configures it?  It should be somewhere in "/usr/share/hal/fdi/", I would think.

Hope this helps.  Good luck!

---

### Post by super kim on 2009-07-16
The system monitor says...

[IMG]http://img266.imagevenue.com/aAfkjfp01fo1i-20009/loc9/37238_Screenshot_122_9lo.jpg[/IMG]


I am reading the bamboo thread now thank you :)

With regards to the mouse, i looked in the folder you mentioned and there was this...

[IMG]http://img247.imagevenue.com/aAfkjfp01fo1i-15003/loc549/37728_Screenshot_122_549lo.jpg[/IMG]

---

### Post by super kim on 2009-07-26
oh no it's all gone wrong, and i thought i had it going well :( how do i start again from the start, i just want one more chance at it!

---

### Post by Favux on 2009-07-26
Hi super kim,

It's probably something simple.  It would help if you could list what you've done in order.

First check on the 10-wacom.fdi and make sure it's the new modified one.

---

### Post by Favux on 2009-07-26
Hi super kim,

OK, so now the new .fdi is in place.  If the dmesg command in a terminal still shows your bamboo try unplugging it.  Check all the connections, make sure they are good and tight.  Reboot again.

It would help if you could give me some idea what you were doing and have done.

---

### Post by super kim on 2009-07-26
Ok to make sure the thread is complete i should explain where i am and how i got here:

I have tried to follow the tutorials but almost certainly due to my habit of clicking too fast have gone wrong.
Favux is kindly trying to fix the user problem with my bamboo to ubuntu marriage lol

I have changed my .fdi to "the modified 10-wacom.fdi in post #176 here:  [http://ubuntuforums.org/showthread.php?t=967147&page=18](http://ubuntuforums.org/showthread.php?t=967147&page=18)  ?"

and rebooted my computer.

Unfortunately my bamboo is still unresponsive.

I should probably mention that i have at this point installed new kernels and so many other things i probably should be less adventurous but at least I'm learning, i hope lol

---

### Post by Favux on 2009-07-26
Hi super kim,

Installing the new kernel may have caused the problem.  The usb kernel driver wacom.ko is included in the linux-images.

So what does:
```
dmesg | grep [Ww]acom
```
show currently?

Check in Synaptic Package Manager that you have both linuxwacom packages installed:  xserver-xorg-input-wacom and wacom-tools.  If not install them.  If they are there reinstall them.  Either way then reboot.

Did you add anything to the xorg.conf?  Or did you try a custom_wacom.fdi?  Also did you try installing a wacom configuration program?

---

### Post by super kim on 2009-07-26
$ dmesg | grep [Ww]acom
[   17.454190] input: Wacom Bamboo as /devices/pci0000:00/0000:00:03.1/usb3/3-3/3-3:1.0/input/input5
[   17.495643] usbcore: registered new interface driver wacom
[   17.495734] wacom: v1.49-pc-1:USB Wacom Graphire and Wacom Intuos tablet driver
[  125.273172] input: Wacom Bamboo as /devices/pci0000:00/0000:00:03.1/usb3/3-3/3-3:1.0/input/input6


and neither of the packages were installed i am installing now and rebooting in a minuite.

and i think i tried installing a wacom configuration program, and the wacomcpl seems to work even if i'm not sure how i should use it :) OK packages are installed now so here goes with the reboot

thank you so much favux

---

### Post by super kim on 2009-07-26
$ dmesg | grep [Ww]acom
[   17.381860] input: Wacom Bamboo as /devices/pci0000:00/0000:00:03.1/usb3/3-3/3-3:1.0/input/input5
[   17.446665] usbcore: registered new interface driver wacom
[   17.446676] wacom: v1.49-pc-1:USB Wacom Graphire and Wacom Intuos tablet driver

I have installed both the packages now, they were not installed before.

I think I tried installing a wacom configuration program when i was copy codes into the terminal without reading everything first. This a valuable lesson to learn, read before clicking!

but the cursor still wont move with the bamboo pen.

---

### Post by Favux on 2009-07-26
Hi super kim,

OK, that's important.  Things won't work without linuxwacom installed.

My fault.  I forgot to mention installing the linuxwacom packages may change the .fdi.  You'll have to check it again, and make sure it's the new one.

Also the wacom configuration program may be a problem.  I know one of them just goes ahead and installs a bunch of Wacom entries in xorg.conf.  It doesn't recognize the ones already there.  And it shouldn't install anything in xorg.conf in Jaunty.  So it obviously hasn't been updated to take .fdi's into account.  So we need to also look at your xorg.conf.

---

### Post by super kim on 2009-07-26
OK my .fdi now reads :

<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">
  <device>
    <match key="info.category" contains="input">
      <match key="info.product" contains="Wacom">
    <merge key="input.x11_driver" type="string">wacom</merge>
    <merge key="input.x11_options.Type" type="string">stylus</merge>
        <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
        <append key="wacom.types" type="strlist">eraser</append>
        <append key="wacom.types" type="strlist">cursor</append>
        <append key="wacom.types" type="strlist">pad</append>
      </match>
      <match key="info.product" contains="WALTOP">
    <merge key="input.x11_driver" type="string">wacom</merge>
    <merge key="input.x11_options.Type" type="string">stylus</merge>
        <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
        <append key="wacom.types" type="strlist">eraser</append>
        <append key="wacom.types" type="strlist">cursor</append>
        <append key="wacom.types" type="strlist">pad</append>
      </match>
    </match>
    <match key="info.capabilities" contains="serial">
      <match key="@info.parent:pnp.id" contains_outof="WACf001;WACf002;WACf003;WACf004;WACf005;WACf006;WACf007;WACf008;WACf009;WACf00a;WACf00b;WACf00c;FUJ02e5">
        <append key="info.capabilities" type="strlist">input</append>
        <merge key="input.x11_driver" type="string">wacom</merge>
        <merge key="input.x11_options.Type" type="string">stylus</merge>
        <merge key="input.x11_options.ForceDevice" type="string">ISDV4</merge>
        <merge key="input.device" type="copy_property">serial.device</merge>
        <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
        <append key="wacom.types" type="strlist">eraser</append>
        <match key="@info.parent:pnp.id" contains_outof="WACf008;WACf009">
          <!-- Serial tablets with touch capabilities -->
          <append key="wacom.types" type="strlist">touch</append>
        </match>
      </match>
    </match>
    <!-- N-Trig Duosense Electromagnetic Digitizer -->
    <match key="info.product" contains="HID 1b96:0001">
      <match key="info.parent" contains="if0">
       <merge key="input.x11_driver" type="string">wacom</merge>
       <merge key="input.x11_options.Type" type="string">stylus</merge>
      </match>
    </match>
  </device>
  <!-- Match the Wacom Bluetooth A5 pen tablet -->
  <device>
    <match key="info.capabilities" contains="input.mouse">
      <match key="info.product" contains="WACOM">
        <match key="info.product" contains="Tablet">
          <merge key="input.x11_driver" type="string">wacom</merge>
          <merge key="input.x11_options.Type" type="string">stylus</merge>
          <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
          <append key="wacom.types" type="strlist">eraser</append>
          <append key="wacom.types" type="strlist">cursor</append>
        </match>
      </match>
    </match>
  </device>

</deviceinfo>

I will change it back to  ;

<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">
  <device>
    <match key="input.originating_device" contains="if0">
      <match key="info.product" contains="Wacom">
        <merge key="input.x11_driver" type="string">wacom</merge>
        <merge key="input.x11_options.Type" type="string">stylus</merge>
        <merge key="info.product" type="string">stylus</merge>
          <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
          <append key="wacom.types" type="strlist">eraser</append>
          <append key="wacom.types" type="strlist">cursor</append>
          <append key="wacom.types" type="strlist">pad</append>
      </match>
    </match>
  </device>
  <device>
    <match key="input.x11_options.Type" contains="eraser">
      <merge key="info.product" type="string">eraser</merge>
    </match>
  </device>
  <device>
    <match key="input.x11_options.Type" contains="cursor">
      <merge key="info.product" type="string">cursor</merge>
    </match>
  </device>
  <device>
    <match key="input.x11_options.Type" contains="pad">
      <merge key="info.product" type="string">pad</merge>
    </match>
  </device>
</deviceinfo>


save, and reboot. then i will look at my xorg.config, i don't know what that is tho.


====================================================

I have changed the .fdi and I have checked it after a reboot, it is still correct.

How do i look at my xorg.config? if that is indeed the next step :)

---

### Post by super kim on 2009-07-26
my xorg.config file reads :

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

---

### Post by Favux on 2009-07-26
Hi super kim,

Great, you found xorg.conf.  Everything looks good.

-reinstalled linuxwacom drivers
-wacom.ko present and active (dmesg)
-new 10-wacom.fdi installed
-xorg.conf looks good

Still no response?  Try rebooting several times.  When this started did you change the usb port you plug into?  Have you tried changing it?  You aren't plugged in through a hub are you?

---

### Post by super kim on 2009-07-26
I have tried rebooting twice, i have tried using a hub, and i tried both the front and back usb ports on the case still no response.

now earlier i followed this [http://ubuntuforums.org/showthread.php?t=1038949&page=11](http://ubuntuforums.org/showthread.php?t=1038949&page=11) was that where i went wrong?

---

### Post by Favux on 2009-07-26
Hi super kim,

Mystery solved.  Boy I wish you had told me earlier you used gali98's HOW TO.  Now we may have mixed different versions of linuxwacom, which is a no no.

Did you get as far as copying the 0.8.3-6 wacom.ko into place?  Is that when things stopped working?

---

### Post by super kim on 2009-07-26
exactly, yes i think thats where it went wrong.

here is where i got to.

6) Next we copy the module to the appropriate directory:

 	Code:
 	sudo cp ./src/2.6.28/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko

---

### Post by super kim on 2009-07-26
It is reassuring that you knew when i had problems, i realize from reading many threads regarding bamboo's that you are somewhat an expert in this field and I'm very grateful for your attention. I went off on tangents when i was trying to follow a tutorial and think it would be cool to have a source somewhere of completed tutorials, there probably is already but i haven't heard of it yet. btw my dinner was lovely :)

---

### Post by Favux on 2009-07-26
Hi super kim,

We may have to uninstall everything and do a linuxwacom scrub.  But let's try this first.  In Synaptic Package Manager search "kernel".  There should be a package called "linux-image-your kernel number-generic kernel number".  Make sure it's the same as the kernel your currently using and install or reinstall it.  That has the 0.8.2-2 wacom.ko for Jaunty.  Then reboot.

---

### Post by super kim on 2009-07-26
the system monitor reports :
Kernel Linux 2.6.28-13-generic
GNOME 2.2.61

the synaptics package manager says :
 Linux-image-generic   2.6.28.13.17      Generic Linux kernel image


i reinstalled that package but it doesn't match?

---

### Post by Favux on 2009-07-26
That's what:
```
uname -r
```
in a terminal gives you.  Your current kernel.  And you should have used the matching linux-image.

---

### Post by SunnyRabbiera on 2009-07-26
Yeh wahcom and Multi button mice can be problematic on linux.
its not like you cant get a mouse with more then 3 buttons to work but these devices mainly have windows in mind.
But really are all the extra buttons that important?
I seem to do just fine with a 3 button mouse, point and click is not that hard to do.

---

### Post by super kim on 2009-07-26
the linux image has a .17 on the end of it? i suppose similar is not exact. how can i get the right kernel, or the right image?

---

### Post by Favux on 2009-07-26
Hi super kim,

Well since you installed it did you reboot?  Did the tablet work?  If you haven't rebooted don't.  Find and install the one that matches.

In Synaptic there should be several linux-image-'s and you chose the one that matches your currently installed kernel.

Does the tablet work in Windows?  Have you checked since it went bad?

---

### Post by super kim on 2009-07-26
i didn't reboot since i reinstalled it since it the numbers didn't match. all of the packages listed as linux-image in the synaptic package manager are 2.6.28.13.17 except for one which is ' linux-image-386    2.6.28.6.3

and i don't have windows. and i don't miss it :)

---

### Post by Favux on 2009-07-26
Hi super kim,

When you PM'd me you said:
```
$ uname -r
2.6.28-13-generic
```
So I'm going to assume Linux-image-generic 2.6.28.13.17 Generic Linux kernel image is the correct one.  Install it if you haven't and reboot.  Hopefully that will install the 0.8.2-2 wacom.ko and the Bamboo will start working.

By checking in Windows the idea is to rule out a hardware problem.  If you have access to another machine you could do it that way if need be.

---

### Post by super kim on 2009-07-26
OK well I'll reboot again, i have a laptop with windows i can try that but i am skeptical of hardware problems as it was working (without the eraser etc) earlier today, moments before i fiddled



i hate windows it is soooo slow why does everything take so long?!?! but it works with windows so it's not a hardware problem.

i also have now rebooted and the bamboo hasnt started working yet :p

---

### Post by super kim on 2009-07-26
bump (am i allowed to do that)

---

### Post by Favux on 2009-07-26
Hi super kim,

OK, we've ruled out hardware.

When you compiled linuxwacom 0.8.3-6 you didn't install it, you were only copying the wacom.ko.  So there shouldn't be a version conflict.

The only thing I don't understand was how did linuxwacom 0.8.2-2 get uninstalled on your Jaunty system?  Did you also try the HOW TO on the first page or something?

Right now, if I understand the picture, the Bamboo should work.  I don't know why it doesn't.

You know the steps to set it up now.  Go through the thread and steps again.  Maybe you can spot whatever it is we're missing.

---

### Post by super kim on 2009-07-26
i did indeed try the how to again after the other tutorial in the hope that if i followed the instructions carefully it would repair any problems i'd created. tbh i think you are more aware of what is set up and not set up than me. is there any way i can remove all the wacom tools etc and install the kernel that i had this morning so i can start over?

---

### Post by Favux on 2009-07-26
Hi super kim,

I don't think you installed a kernel.  Maybe a kernel driver.  Probably we're looking at a conflict of linuxwacom versions.

If you did the first HOW TO on the first post first page, did you download the 0.8.2-2 tar?  If so:

Go to Synaptic Package Manager and completely uninstall both linuxwacom packages.

The rest should sound familiar.  First enter these two commands in a terminal:
```
sudo apt-get install wacom-tools xserver-xorg-input-wacom
sudo apt-get purge wacom-tools xserver-xorg-input-wacom
```
Then change directory into the unpacked linuxwacom tar you used.  Then change directory into the "prebuilt" folder.  Then in a terminal:
```
sudo ./uninstall
```
Then go to "/lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko" where "uname -r" is your current kernel; 2.6.28-?.  You should probably delete the wacom.ko you find there but to be careful you could move it somewhere safe and rename it.  You need the 0.8.2-2 linuxwacom packages' wacom.ko and you can get it (as you now know) by reinstalling your kernel's "linux-image" (it has the kernel modules) in Synaptics.  Go to Synaptics and reinstall the 0.8.2-2 xserver-xorg-input-wacom and wacom tools.

Now you may have to replace the current 10-wacom.fdi with a modified one.  Go to post #176 here:  [http://ubuntuforums.org/showthread.php?t=967147&page=18](http://ubuntuforums.org/showthread.php?t=967147&page=18)

Reboot.

Good luck!

---

### Post by super kim on 2009-07-26
OK i have done all that, now i think i'm back to the start again yay. here is my terminal output now :

$ gksudo gedit /usr/share/hal/fdi/policy/20thirdparty/10-wacom.fdi
$ dmesg | grep [Ww]acom
$ xsetwacom list
$ xinput --list
"Virtual core pointer"    id=0    [XPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
"Virtual core keyboard"    id=1    [XKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"AT Translated Set 2 keyboard"    id=2    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Macintosh mouse button emulation"    id=3    [XExtensionPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
"Microsoft Microsoft Wireless Optical Mouse? 1.00"    id=4    [XExtensionPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 1



I have made sure my .fdi is the one from post #176

---

### Post by super kim on 2009-07-29
I accidentally pressed a sleep button on my keyboard, and i couldnt get my computer to wake up, so i switched it off and on again then the gub says there is no os. HDD works in another machine, so i got a new 10gb hdd to boot ubuntu (rather than booting from my usb hdd) and installed jaunty on that. i plugged in the bamboo and it works just like that?!? the only thing i had to do was configure gimp and inkscape!

ahh when i say works the cursor and eraser work and the pressure on the pen works but the four buttons on the pad ( <, >, FN1, FN2) do nothing, and the little circle at the top which should scroll or preferebly zoom does nothing.

with so much working i will wait to see what favux suggests before i change any settings, every defeat is a victory if you learn from it!

---

### Post by Favux on 2009-07-29
Hi super kim,

Good to hear from you again.  I was about to PM you and see where you're at.

If you go back over the thread you'll see you have all the info. you need to proceed.  But to give you a different perspective and refresh your memory see Turtleman's Bamboo thread:  [http://ubuntuforums.org/showthread.php?t=1184879](http://ubuntuforums.org/showthread.php?t=1184879)  For the pad you want the link to shatterblast's post #188.

Good luck!  Have fun.

---

### Post by super kim on 2009-08-02
thank you favux, so much. i have another issue [http://ubuntuforums.org/showthread.php?t=1227605](http://ubuntuforums.org/showthread.php?t=1227605) which is entirely un-related but takes priority but as soon as i fix/break my video i'll get right onto the task of fixing/breaking my bamboo :)

seriously though i think if i follow just one set of instructions at a time i might do better than before lol i'll read the other threads before i try anything as favux suggests. i agree it will help if i have a broader understanding of the problem before i try and fix anything.

i'll post here again when i finnish trying to set up my graphics card and let you know how the bamboo works.

---

### Post by super kim on 2009-08-02
xserver-xorg-input-evtouch
Touchscreen-Driver for X.Org/XFree86 server

i dont know if this is of any importance but i noticed this in the synaptic package manager and thought i install it since in  /var/log/gdm/:0.log.2 reads mostly like this...
> Warning:          Multiple doodads named ""
>                   Using first definition
Errors from xkbcomp are not fatal to the X server
Wacom Bamboo eraser Wacom X driver grabbed event device
(==) Wacom using pressure threshold of 30 for button 1
(==) Wacom USB Bamboo tablet speed=9600 (38400) maxX=14760 maxY=9225 maxZ=511 resX=2540 resY=2540  tilt=disabled
(==) Wacom device "Wacom Bamboo eraser" top X=0 top Y=0 bottom X=14760 bottom Y=9225 resol X=2540 resol Y=2540
**FATAL: Module evdev not found.**
(==) Wacom device "Wacom Bamboo cursor" top X=0 top Y=0 bottom X=14760 bottom Y=9225 resol X=2540 resol Y=2540
(==) Wacom device "Wacom Bamboo pad" top X=0 top Y=0 bottom X=14760 bottom Y=9225 resol X=2540 resol Y=2540
(==) Wacom device "Wacom Bamboo" top X=0 top Y=0 bottom X=14760 bottom Y=9225 resol X=2540 resol Y=2540
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""


should i be worried about this?

---

### Post by Favux on 2009-08-02
Hi super kim,

You don't want xserver-xorg-input-evtouch installed.  That's for a touchscreen not your Bamboo.  Module evdev is what controls your keyboard among other things and is installed by default.

The error seems to be about duplicate wacom entries for your Bamboo.  I'm not sure what that's about.  If it's working I guess you can ignore it.

---

### Post by super kim on 2009-08-05
> **Favux said:**
> Hi super kim,

The error seems to be about duplicate wacom entries for your Bamboo.  I'm not sure what that's about.  If it's working I guess you can ignore it.

could the error be caused by me plugging the bamboo into different usb slots?

---

### Post by Favux on 2009-08-05
Hi super kim,

That's a good thought.  If you've done that, but things still work, you may be right.  Does it go away with a reboot?

---

### Post by super kim on 2009-08-05
well i upgraded to the karmic koala as i'm part fool lol but it seems to be working just fine, and no error messages at all. i must say nearly all my niggley problems have been resolved from updating to karmic, i was expecting it not to work since its an alpha release. i may pester you again some time soon for help with some tweaking if thats possible to do???

---

### Post by Favux on 2009-08-05
Hi super kim,

Sure.  I'm eager to start learning about Kharmic.

---

### Post by super kim on 2009-08-06
on closer inspection.... using gimp, i noticed that the selected tool is not aligned with the cursor for the stylus and eraser. the mouse is aligned correctly however. this is with karmic, not the case with jaunty it all seems to work fine there lol
this is a gimp issue however so i will check and fiddle with the gimp set up to see if i can set the tool area to be where the cursor is. i'm open to any suggestions on this though and i have to go out for a few hours so i'll check back then to see if you know what this is about :)

---

### Post by Favux on 2009-08-06
Hi super kim,

Did you recalibrate with wacomcpl after you installed Kharmic?

---

### Post by super kim on 2009-08-06
hi sorry for the delay i just got home.

i've not used wacomcpl since the wacom-tools are not installed yet. the cursor is only offset when i'm using gimp. i will try inkscape (i think thats what its called) now and see where it draws the line with that program lol.

i have just run "$ sudo gedit xorg.config" and the file is blank. does that make a difference? i'm going to see if i can find a .fdi.

---

### Post by super kim on 2009-08-06
my .fdi needs changing i think...

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<!-- this is probably a bit imprecise -->
<deviceinfo version="0.2">
  <device>
    <match key="info.category" contains="input">
      <match key="info.product" contains_outof="Wacom;WALTOP">
    <merge key="input.x11_driver" type="string">wacom</merge>
    <merge key="input.x11_options.Type" type="string">stylus</merge>
    <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
    <append key="wacom.types" type="strlist">eraser</append>
    <append key="wacom.types" type="strlist">cursor</append>
    <append key="wacom.types" type="strlist">pad</append>
      </match>
    </match>
    <match key="info.capabilities" contains="serial">
      <match key="@info.parent:pnp.id" contains_outof="WACf001;WACf002;WACf003;WACf004;WACf005;WACf006;WACf007;WACf008;WACf009;WACf00a;WACf00b;WACf00c;FUJ02e5">
    <append key="info.capabilities" type="strlist">input</append>
    <merge key="input.x11_driver" type="string">wacom</merge>
    <merge key="input.x11_options.Type" type="string">stylus</merge>
    <merge key="input.x11_options.ForceDevice" type="string">ISDV4</merge>
    <merge key="input.device" type="copy_property">serial.device</merge>
    <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
    <append key="wacom.types" type="strlist">eraser</append>
        <match key="@info.parent:pnp.id" contains_outof="WACf008;WACf009">
      <!-- Serial tablets with touch capabilities -->
      <append key="wacom.types" type="strlist">touch</append>
    </match>
      </match>
    </match>
    <!-- N-Trig Duosense Electromagnetic Digitizer -->
    <match key="info.product" contains="HID 1b96:0001">
      <match key="info.parent" contains="if0">
       <merge key="input.x11_driver" type="string">wacom</merge>
       <merge key="input.x11_options.Type" type="string">stylus</merge>
      </match>
    </match>
  </device>
  <!-- Match the Wacom Bluetooth A5 pen tablet -->
  <device>
    <match key="info.capabilities" contains="input.mouse">
      <match key="info.product" contains="WACOM">
        <match key="info.product" contains="Tablet">
          <merge key="input.x11_driver" type="string">wacom</merge>
          <merge key="input.x11_options.Type" type="string">stylus</merge>
      <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
      <append key="wacom.types" type="strlist">eraser</append>
      <append key="wacom.types" type="strlist">cursor</append>
        </match>
      </match>
    </match>
  </device>
</deviceinfo>

```

and i looked in the folder that should have the xorg.config and it is not there, sooo should i go and make an xorg.config file and change my .fdi? and install wacom-tools as well.

 is that sounding right favux? inthat order too?

---

### Post by Favux on 2009-08-06
Hi super kim,

It should be:
```
gksudo gedit /etc/X11/xorg.conf
```
unless they've renamed it.  And there shouldn't be any Wacom entries in it.

Are you saying wacom-tools is not present in Synaptic?  Last I saw the version was 0.8.3-2 in Kharmic.

---

### Post by super kim on 2009-08-06
no the wacom tools are there they are not installed automaticly and therefore not yet installed, then anyway they are now installed but i have still not run wacomcpl... my xorg.config is not there however. i cant remember that lil code that rebuilds it but there is an Xorg.0.log and that has mention of wacom at the end of it would you like to see that?

```
$ gksudo gedit /etc/X11/xorg.conf

(gksudo:4374): GLib-WARNING **: Idle source dispatched without callback
You must call g_source_set_callback().


```terminal says that too?

```
$ cd /etc/X11
:/etc/X11$ ls
app-defaults  cursors  fonts  rgb.txt  X  xinit  xkb  Xresources  Xsession  Xsession.d  Xsession.options  XvMCConfig  Xwrapper.config
:/etc/X11$ 

```

---

### Post by super kim on 2009-08-06
i found this thread  [http://ubuntuforums.org/showthread.php?t=1221226](http://ubuntuforums.org/showthread.php?t=1221226)   it appears that karmic has no xorg.config

---

### Post by Favux on 2009-08-06
Hi super kim,

Well either they renamed xorg.conf, moved it, or it's not there.  Don't worry about it for now, you shouldn't need it.

Go ahead and install wacom-tools and reboot.  See how things are.  Try "xsetwacom list" and "xinput --list" like before and see what results you get.

It looks like you may need to use the the modified .fdi.  The current one in Kharmic you're showing me looks like it has the same problems.  Wacomcpl probably won't work with it.

Edit:  Well that explains it, no xorg.conf needed in Kharmic!

---

### Post by super kim on 2009-08-06
hello favux,

i've installed wacom-tools, changed my .fdi and rebooted. 

i started gimp up and at first was excited as the brush area was aligned with the cursor then i noticed the pressure wasnt working so i configured the input devices and set them all to 'screen' then the cursor went back to being about 35 pixels to the right and about 60 pixels below the cursor.

here is my terminal output:

$ gksudo gedit /usr/share/hal/fdi/policy/20thirdparty/10-linuxwacom.fdi

(gksudo:3073): GLib-WARNING **: Idle source dispatched without callback
You must call g_source_set_callback().
$ gksudo gedit /usr/share/hal/fdi/policy/20thirdparty/10-linuxwacom.fdi
$ dmesg | grep [Ww]acom
[   17.994898] input: Wacom Bamboo as /devices/pci0000:00/0000:00:10.2/usb4/4-2/4-2:1.0/input/input7
[   18.107545] usbcore: registered new interface driver wacom
[   18.107556] wacom: v1.51:USB Wacom Graphire and Wacom Intuos tablet driver
$ xsetwacom list
stylus           stylus    
pad              pad       
cursor           cursor    
eraser           eraser    
$ xinput --list
"Virtual core pointer"    id=0    [XPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
"Virtual core keyboard"    id=1    [XKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"AT Translated Set 2 keyboard"    id=2    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Power Button"    id=3    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Power Button"    id=4    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"stylus"    id=5    [XExtensionKeyboard]
    Type is Wacom Stylus
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 5
    Num_axes is 6
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 14760
        Resolution is 2540
    Axis 1 :
        Min_value is 0
        Max_value is 9225
        Resolution is 2540
    Axis 2 :
        Min_value is 0
        Max_value is 511
        Resolution is 1
    Axis 3 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 4 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 5 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1
"Sleep Button"    id=6    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"pad"    id=7    [XExtensionKeyboard]
    Type is Wacom Pad
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 4
    Num_axes is 6
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 14760
        Resolution is 2540
    Axis 1 :
        Min_value is 0
        Max_value is 9225
        Resolution is 2540
    Axis 2 :
        Min_value is 0
        Max_value is 511
        Resolution is 1
    Axis 3 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
    Axis 4 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
    Axis 5 :
        Min_value is 0
        Max_value is 71
        Resolution is 1
"cursor"    id=8    [XExtensionKeyboard]
    Type is Wacom Cursor
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 5
    Num_axes is 6
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 14760
        Resolution is 2540
    Axis 1 :
        Min_value is 0
        Max_value is 9225
        Resolution is 2540
    Axis 2 :
        Min_value is 0
        Max_value is 511
        Resolution is 1
    Axis 3 :
        Min_value is -900
        Max_value is 899
        Resolution is 1
    Axis 4 :
        Min_value is -1023
        Max_value is 1023
        Resolution is 1
    Axis 5 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1
"eraser"    id=9    [XExtensionKeyboard]
    Type is Wacom Eraser
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 5
    Num_axes is 6
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 14760
        Resolution is 2540
    Axis 1 :
        Min_value is 0
        Max_value is 9225
        Resolution is 2540
    Axis 2 :
        Min_value is 0
        Max_value is 511
        Resolution is 1
    Axis 3 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 4 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 5 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1

---

### Post by Favux on 2009-08-06
Hi super kim,

Well that looks like progress.  I'm assuming that "xsetwacom list" was blank with the default Kharmic .fdi you showed me and that "xinput --list" wasn't returning linuxwacom names.

With the modified 10-wacom.fdi in place the correct names are being returned.  Did you calibrate your tablet with wacomcpl yet?

---

### Post by super kim on 2009-08-06
> **Favux said:**
> Hi super kim,

Well that looks like progress.  I'm assuming that "xsetwacom list" was blank with the default Kharmic .fdi you showed me and that "xinput --list" wasn't returning linuxwacom names.

With the modified 10-wacom.fdi in place the correct names are being returned.  Did you calibrate your tablet with wacomcpl yet?


do you know, i've never actually got wacomcpl to work. i read their website and the instructions on setting it up correctly but how can i:
a- check that wacomcpl is installed
b- use wacomcpl to configure my bamboo

if i use the bamboo stylus instead of a mouse the cursor is fine in any program. it is just the brush area is ofset from the cursor in the picture screen in gimp and with inkscape  i tested the caligraphy tool and when i use the stylus it just draw a horizontal line across the screen width even if i only tap the pen??

do you know why if i use my bamboo to select a smiley (here goes):P it works fine? its just the two programs that have the problem.

---

### Post by super kim on 2009-08-06
[http://img269.imageshack.us/img269/2355/screenshotuxjyrx.png](http://img269.imageshack.us/img269/2355/screenshotuxjyrx.png)
[http://img30.imageshack.us/img30/608/screenshot1zcm.png](http://img30.imageshack.us/img30/608/screenshot1zcm.png)
[http://img10.imageshack.us/img10/9065/screenshot2dwv.png](http://img10.imageshack.us/img10/9065/screenshot2dwv.png)
[http://img10.imageshack.us/img10/3907/screenshot3fxq.png](http://img10.imageshack.us/img10/3907/screenshot3fxq.png)

---

### Post by Favux on 2009-08-06
Hi super kim,

If wacom-tools is installed (by the way is it still v. 0.8.3-2?) then wacomcpl is.  In a terminal enter "wacomcpl" (without the quotes) and a gui should pop up.  In the column on the left just select whichever device you want, say stylus.  Then you can calibrate it and configure it.  Some more information in Section 3 here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)

I'm not sure what's going on in Gimp and Inkscape.  It may be just a bug(s) in Kharmic.  You are on alpha 3 after all.  There are suppose to be bugs.  But to make sure you're setting up extended input devices correctly take another look near the bottom here:  [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)

---

### Post by super kim on 2009-08-06
hey favux 

yes it is v. 0.8.3-2

[http://img401.imageshack.us/img401/5356/screenshotrkq.png](http://img401.imageshack.us/img401/5356/screenshotrkq.png)
 thats a screen shot of the extended device settings to make sure but it is right i can assure you lol 

i got wacomcpl (not wacomclp like i had been trying) to run,

---

### Post by Favux on 2009-08-06
Hi super kim,

Great!  Did calibrating with wacomcpl help?

From the screen shot it looks right.

---

### Post by super kim on 2009-08-06
the only thing i can think of to calibrate would be to set the x axis to the left 35 pixels and the y 58 pixels. i got those figures from drawing a spot then positioning the cursor on that spot then trimmed the image what was left was a canvas size of 35x58

only thing is that wont help with inkscape [http://img30.imageshack.us/img30/608/screenshot1zcm.png](http://img30.imageshack.us/img30/608/screenshot1zcm.png)  that line was just from a press on the pen with about 2 or three pixels movement to the right. i cannot recreate that line using the mouse.

as i mentioned before the stylus is calibrated fine for ubuntu only the brush is not at the cursors point. did you notice what i'm talking about in the screenshots? i should of said but those screen shots were made while i was using the tool so you can see where the line is drawing in relation the the cursors position.

---

### Post by Favux on 2009-08-06
Hi super kim,

I didn't mean for you to do that.  Just a standard calibration to see if something clicked in.  Yes, I looked at the screen shots.

At this point it looks to me like a Kharmic bug(s).  You could report it on launchpad.  Either way hopefully one of the updates will shortly fix it.

Don't know where the bug is:  Gimp, Inkscape?  Seems unlikely it would be in both.  So that probably leaves Xserver 1.7 (is it 1.7 in Kharmic, or still 1.6 something?) and/or linuxwacom.

You could try completely uninstalling both linuxwacom packages in Synaptic Package Manager, reboot, and then reinstall them and reboot again.  That would almost for sure knock out the modified 10-wacom.fdi so you'd have to put that back in and reboot yet again.

---

### Post by super kim on 2009-08-06
again your right the xserver-org is indeed 1.7
just out of interest what was evdev again? just there is an upgrade available for "xserver-xorg-input-evdev".
a bug eh it might be hard to report it since i dont know where the problem is. it would be strange for both gimp and inkscape to have a bug, and the problems are different for each.

 i'll have a go at  > You could try completely uninstalling both linuxwacom packages in Synaptic Package Manager, reboot, and then reinstall them and reboot again. That would almost for sure knock out the modified 10-wacom.fdi so you'd have to put that back in and reboot yet again. tomorrow right now i have to finnish writing a super important letter lol i will read up on how to make a bug report since apport is the only way i've reported bugs in the past.

---

### Post by Favux on 2009-08-06
Hi super kim,

Evdev is one of the basic configuration thingies.  It handles the keyboard and mouse etc.  So I'd let it update.  It actually may be related to your problem.

Since you are on Kharmic alpha 3 the idea is to bug test anyway.  What you probably want to do first is start a thread in the Kharmic forum.  You have enough details now to be specific about your problem in the first post.  Maybe someone can help you fix things.  If they tell you to make a bug report you can ask them how.

---

### Post by super kim on 2009-08-06
hey favux,

i did the update for the evdev, and i couldn't wait till tomorrow so i tried everything else you suggested but as expected the problems still there.

anyway i don't know if i should post in the karmic forum since these guys seem busy and i don't like to bother anyone, besides since i've been told by a few people on the forum that i shouldn't be using karmic i fear a big fat 'i told you so' comming lol

instead i will just have to keep upgrading and hope they fix it, i'm in no hurry. since i got my bamboo i have only managed to draw one picture of a mrs. leprichaun for my irish friend [http://img190.imageshack.us/img190/1426/mrsleprichaun.jpg](http://img190.imageshack.us/img190/1426/mrsleprichaun.jpg)
it is still possible to use gimp i just wont be able to paint the top or left of the image but i can move it so i can.

---

### Post by Favux on 2009-08-07
Hi super kim,

Not bad, but where is her Shamrock?

---

### Post by super kim on 2009-08-07
tanks favux. whats a shamrock look like, i have included clovers and a pot of gold but i forgot about the shamrock i'll google image search shamrock i still have the xdf file so it's not too late. it's my first attemt at drawing a body and although the waist is a bit wrong i think i got the proportions right :)

hang on i did a search and her lappel had a shomrock (i'd call it a clover) and there is one lil shamrock in the reeds by the river, and i drew a shamrock bellybutton too lol you should look closer lol

i could make shamrock cuff links too

i wanted to make a super linux penguin for my avatar since i have windows blue screen of death at the moment, god i don't miss window one bit

---

### Post by Favux on 2009-08-07
Hi super kim,

I was teasing you.  I spotted the belly button decoration right away.

Your not getting the waist right because you're not visualizing the hip bones (iliac crests/wings) right.  You have to visualize them pooching out and then the sides of the waist indenting (draping) over them.

Look forward to your tux icon.

---

### Post by super kim on 2009-08-07
[http://img27.imageshack.us/img27/1426/mrsleprichaun.jpg](http://img27.imageshack.us/img27/1426/mrsleprichaun.jpg) i forgot the whites of the eyes. only just noticed lol
i think i messed up the hip yes... i over stretched myself by making her shoulder raised and the hip angled. i got confused and i think the (her)left boob is a tad too high as i was trying to compensate for the hand on hip but the shoulder needs to be higher too. it was hard to see until i had finished the coloring and by then i couldn't face doing a re-draw again lol as i said it is my first human body i've drawn on a computer and i've never tried a penguin so it might take a while before i have a new avatar

favux i have one small question to ask you... there is a lil button on my mouse whch does nothing. i dont know what i want it to do, but it would be nice if it did something. all the other buttons work, the wheel works and it even does horizontal scrolling. oh its half five in the morning and i still havent really started this letter. everything and anything except what i'm supposed to be doing lo

---

### Post by super kim on 2009-08-16
i have now installed hardy heron on a new hard drive in the hope that i can get everything working.
is this a good idea?
[http://ubuntuforums.org/showthread.php?t=765915](http://ubuntuforums.org/showthread.php?t=765915)

---

### Post by Favux on 2009-08-16
Hi super kim,

No.  Don't do it.  Instead see if you can install the 0.8.1-6 deb.s Loic2 has for you at:  [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)  near the top under Intrepid 8.10.  They may not work in Hardy.  Make sure you pick the ones for your cpu architecture.  Otherwise just make sure both linuxwacom packages in Synaptic are installed.

In Hardy you need to use xorg.conf.  I'll check and see if I have a Bamboo version.  You could post your xorg.conf.

Edit:  Do you have the Wacom mouse?

---

### Post by super kim on 2009-08-16
well i put the jumper on my hard drive upside down and instead of it being the master was i was limiting the capacity (doh) so i have had to repartition and reinstall to fix grub error 18.

the state of the computer is a fresh install of hardy lts, i am sure wacom drivers & tools are not yet installed, 

xorg.conf
```
Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "gb"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
EndSection
```

---

### Post by super kim on 2009-08-16
should my xorg.cof look more like this?
```

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "gb"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/wacom" 
  Option        "Type"          "stylus"
  Option        "USB"           "on"              
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/input/wacom" 
  Option        "Type"          "eraser"
  Option        "USB"           "on"              
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/input/wacom"
  Option        "Type"          "cursor"
  Option        "USB"           "on"         
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "pad"
  Option        "Device"        "/dev/input/wacom"   
  Option        "Type"          "pad"
  Option        "USB"           "on"                 
EndSection

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

Section "ServerLayout" 
  Identifier    "Default Layout"
  Screen        "Default Screen"
  InputDevice   "Generic Keyboard"
  InputDevice   "Configured Mouse"
  InputDevice   "stylus"   "SendCoreEvents"
  InputDevice   "eraser"   "SendCoreEvents"
 [COLOR=Red] InputDevice   "cursor"   "SendCoreEvents" # For non-LCD tablets only[/COLOR]
  InputDevice   "pad"                 [COLOR=Red]      # For Intuos3/CintiqV5/Graphire4/Bamboo tablets[/COLOR]
[COLOR=Red]# InputDevice   "touch"    "SendCoreEvents" # Only a few TabletPCs support this type[/COLOR]
EndSection

```

do i need the stuff in red?

---

### Post by Favux on 2009-08-16
Hi super kim,

You pretty much have it.  You only need the cursor if you have the Wacom mouse.  You do the "ServerLayout" entries.  To edit it use:
```
gksudo gedit /etc/X11/xorg.conf
```
Assuming no mouse, something like:
```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "gb"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
EndSection

Section "InputDevice"
    Identifier "stylus"
    Driver "wacom"
    Option "Device" "/dev/input/wacom"
    Option "Type" "stylus"
    Option "USB" "on" # USB ONLY
    Option "Button2" "2"  # make first button a middle button
    Option "Button3" "3"  # make second button a R button
EndSection

Section "InputDevice"
    Identifier "eraser"
    Driver "wacom"
    Option "Device" "/dev/input/wacom"
    Option "Type" "eraser"
    Option "USB" "on" # USB ONLY
EndSection

Section "InputDevice"
    Identifier "pad"
    Driver "wacom"
    Option "Device" "/dev/input/wacom"
    Option "Type" "pad"
    Option "USB" "on" # USB ONLY
EndSection

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

Section "ServerLayout"
    Identifier "Default Layout"
    Screen "Default Screen"
    InputDevice "stylus" "SendCoreEvents"
    InputDevice "eraser" "SendCoreEvents"
    InputDevice "pad" # For Intuos3/CintiqV5/Graphire4/Bamboo tablets
EndSection
```

---

### Post by super kim on 2009-08-16
with regards to the wacom tools and driver, i have downloaded two .deb files. i just want to check i'm doing this right so sorry if this is a bit simple lol

[https://help.ubuntu.com/community/Wacom?action=AttachFile&do=view&target=wacom-tools_0.8.1.6-1ubuntu2_i386.deb](https://help.ubuntu.com/community/Wacom?action=AttachFile&do=view&target=wacom-tools_0.8.1.6-1ubuntu2_i386.deb)
&
[https://help.ubuntu.com/community/Wacom?action=AttachFile&do=view&target=xserver-xorg-input-wacom_0.8.1.6-1ubuntu2_i386.deb](https://help.ubuntu.com/community/Wacom?action=AttachFile&do=view&target=xserver-xorg-input-wacom_0.8.1.6-1ubuntu2_i386.deb)

they are the right architecture i am not using 64 bit. they are on my desktop so i open a terminal, change the directory to my desktop. then run ```
sudo dpkg -i xserver-xorg-input-wacom_0.8.1.6-1ubuntu2_i386.deb
sudo dpkg -i wacom-tools_0.8.1.6-1ubuntu2_i386.deb
```do i need to remove the wacom drivers that are already installed first? i think it can do no harm.

is this sounding right? i just want to check before i commit :D

then change my xorg.conf to
```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "gb"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/wacom" 
  Option        "Type"          "stylus"
  Option        "USB"           "on"              
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/input/wacom" 
  Option        "Type"          "eraser"
  Option        "USB"           "on"              
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/input/wacom"
  Option        "Type"          "cursor"
  Option        "USB"           "on"         
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "pad"
  Option        "Device"        "/dev/input/wacom"   
  Option        "Type"          "pad"
  Option        "USB"           "on"                 
EndSection

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

Section "ServerLayout" 
  Identifier    "Default Layout"
  Screen        "Default Screen"
  InputDevice   "Generic Keyboard"
  InputDevice   "Configured Mouse"
  InputDevice   "stylus"   "SendCoreEvents"
  InputDevice   "eraser"   "SendCoreEvents"
  InputDevice   "pad"                       
EndSection
```

i really think i'm beginning to understand all this now (on a very basic level)

---

### Post by Favux on 2009-08-16
Hi super kim,

You're definitely getting there.

Right, you just double click on the deb to install.  As a deb (Debian package) Synaptic Package Manager is aware of it and vice versa so they play nice.  Not true of a manually compiled and installed driver.

If you don't have the Wacom mouse you can remove the cursor section in the xorg.conf.  If you do have one cursor needs to be in "ServerLayout".

---

### Post by super kim on 2009-08-16
when i tried to install the xserver-xorg-input-wacom i got this error "dependency is not satisfiable: xserver-org-core"
what to do??

---

### Post by Favux on 2009-08-16
Hi super kim,

I assume that was from the deb on Loic2's Wacom wiki?  Oh well, worth a try, the deb must only work in Intrepid.  Go ahead and make sure both packages, wacom-tools & xserver-xorg-input-wacom, are installed through Synaptic.  I forgot which version is in Hardy.

---

### Post by super kim on 2009-08-16
hi favux,

the version is 0.7.9.8

i have checked and the xserver-xorg-core is 2.1.4.1

i have added "deb [http://*ftp.de.debian.org/debian*]("http://%3Ci%3Eftp.de.debian.org/debian%3C/i%3E") sid main" to my sources list and synaptic says that i can upgrade it to 2.1.6.3 if i do this then i might be able to get the wacom drivers to install?





no. i can't

---

### Post by Favux on 2009-08-16
Hi super kim,

I wouldn't try to upgrade my Xserver from 1.4.  That's a big change and you might have problems with Hardy updates.  Intrepid is 1.5 and Jaunty 1.6.

---

### Post by super kim on 2009-08-17
> **Favux said:**
> Hi super kim,

I wouldn't try to upgrade my Xserver from 1.4.  That's a big change and you might have problems with Hardy updates.  Intrepid is 1.5 and Jaunty 1.6.


lol Favux too late, yea i found that out all on my own, i couldn't get anything from mouse, keyboard etc etc. had to reinstall again, thats why i'm doing this all now! if i cock it up again i can just start over, a clean install takes 15 mins so not too much of a loss.

i have installed the wacom tools/drivers and have changed the xorg.conf i'll see how it goes after the next reboot

why is there no smiley for "fingers crossed"? :guitar: nevermind i'll have to use this one

---

### Post by super kim on 2009-08-17
Favux!! it's solved !!!

it did not need the newer wacom drivers or tools, i. just needed to change the xorg.conf and set it up in gimp. not installed inkscape but i have high hopes now

yay thank you Favux again and again 

still not sorted my mouse. i only have the two standard buttons and the scroll wheel but no side scroll the wheel doest work as a button and the mysterious button on the side which never worked all needs setting up.

i'm off to do some research

---

### Post by Favux on 2009-08-17
Hi super kim,

Outstanding!!!  You got there, nice job!

So the default 0.7.9 linuxwacom drivers in Hardy work for the Bamboo.  Good deal.

---

### Post by super kim on 2009-08-17
> **Favux said:**
> So the default 0.7.9 linuxwacom drivers in Hardy work for the Bamboo.  Good deal.

hi Favux, yes it seems the 0.7.9 drivers do the job i just configured xorg.conf and it works.
 thats great, i am still playing with karmic, but this install is supposed to be my all-stable all-working system, now just to get the mouse to work fully. 

does anybody know how to set up a mouse? Favux, is it the same as the bamboo? do i just need to add some lines to the xorg.conf? i have looked in the folder with the fdi files but nothing looks mouse related i really dont know how hardy handles mice, i presume it is the same as the bamboo.

thanks for helping me over and over again Favux i know i must be tiring what with me gong off at tanjents and trying new things but i came through in the end i now know how to set my bamboo up in both hardy, and jaunty. i dont think the bug is fixed with karmic yet i am keeping an eye out for any develpment. the offset is the same as the rulers on the side in gimp, but that comes no further in explaining the bizarre effects created with the caligraphy tool in inkscape, oh well its well above anything i can do but when the bug is fixed i can test it again and now i know how to file bugs or confirm them so i am of some help to the developers at least.

[CENTER]_**[SIZE=2]mouse mouse mouse[/SIZE]**_
[/CENTER]
[B][SIZE=2]
still not working, any ideas on how to set up a mouse in ubuntu 8.04 (hardy heron) please post here thank you ubuntu community your all awsome[/SIZE][/B]

---

### Post by super kim on 2009-08-21
i have completely set up my bamboo in jaunty.

i have firstly installed wacom drivers and tools with the synaptic package manager.
then i used wacomcpl to set the buttons on the tablet to undo, redo, copy, paste and the scroll wheel will zoom in or out.
secondly I have changed my 10-wacom.fdi to the modified 10-wacom.fdi in post #176 here:  [http://ubuntuforums.org/showthread.php?t=967147&page=18](http://ubuntuforums.org/showthread.php?t=967147&page=18)  ?" thank you Favux.
and finally i set gimp to use the bamboo.

i would like to report that i can use every button knob and wheel on the device exactly as i want to.

although my mouse has all the buttons working they are not doing exactly what i want them to do. is there a tool similar to wacomcpl for mice? why have ubuntu developers not made it easier to set up multi button mice when so many people have them?
whats needed is a simple gui that allows you to set what each button press from the mouse should do and this should also be able to set different maps for diffreent apps.
where is the suggestion box, i wish i knew how to make linux i would do it myself!

EDIT

there is already a gui for setting up your mouse its called btnx-config you can find it in synaptic package manager yay i hope it works :)

---

### Post by super kim on 2009-08-21
alas i spoke too soon. for some reason the wacomcpl has lost the settings i put in earlier. i wonder why?

aha i noticed the settings are lost when i unplug the tablet!

---

### Post by Favux on 2009-08-21
Hi super kim,

You could try cyberfish's wacomcpl settings script.  In post #104 here:  [http://ubuntuforums.org/showthread.php?t=1038949&page=11](http://ubuntuforums.org/showthread.php?t=1038949&page=11)  Section 4:  Wacomcpl and settings.  Worth a look see anyway.

---

### Post by super kim on 2009-08-21
> **Favux said:**
> Hi super kim,

You could try cyberfish's wacomcpl settings script.  In post #104 here:  [http://ubuntuforums.org/showthread.php?t=1038949&page=11](http://ubuntuforums.org/showthread.php?t=1038949&page=11)  Section 4:  Wacomcpl and settings.  Worth a look see anyway.

hello Favux
yup i have done it now so fingers crossed it will load the settings when the computer starts. 
i did a [super penguin picture]("http://img515.imageshack.us/img515/6475/supertux.png") to test it out, it's hard to remember i can use the buttons to undo and paste etc, it really is not hard to set up at all. in jaunty anyway and hopefully karmic will just be extra awesome lol

---

### Post by Favux on 2009-08-21
Cool!

I love it, abd.s on Super Tux!

---

### Post by super kim on 2009-08-21
i'm just glad i have got it all to work in the end. it turns out the solutions are the simplest, however it is hard to find the instruction sometimes and the 'bonified' tutorials are often out of date lol we all need some one like Favux to help sort the grain from the chaff. when i get time i will make a final post on this thread with all that i needed to do to set up my bamboo and mouse in jaunty, i hope it helps someone else in the future.

oh did i mention my mouse is doing what its told finally? wel yay it works.

it turns out that despite what i've read about gnome not being as easily customisable as kde it really was easy and mostly gui. it was just knowing what to do!!!

and yea my super tux is ripped! just a fun cartoon but i want to add more to it. i made the penguin's shape like a real penguin perhaps i should make it more like the linux penguin? i also did a rock hopper because they have the cool eyebrows. i might change it or i might just do it again properly :)

firstly i want to make my own home page i am fed up of google.

---

