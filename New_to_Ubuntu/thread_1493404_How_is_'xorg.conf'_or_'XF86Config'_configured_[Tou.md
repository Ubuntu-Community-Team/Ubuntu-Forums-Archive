---
title: "How is 'xorg.conf' or 'XF86Config' configured? [Touchpad problem]"
date: 2010-05-25
forum: New to Ubuntu
---

### Post by a-guy-in-japan on 2010-05-25
This is my 1st time trying Linux--I am a beginner, however I did search the forums for an answer but most of what I've found so far is a bit over my head. 
I am converting over from Windows and am fairly good at resolving hardware & software conflicts in it (I am good with navigating menus but not experienced in using command line interfaces, such as 'Terminal').
That being said, I realize Linux is not Windows and am here to learn, so I can use Ubuntu (or some other version of Linux) myself and to help others after I've gained experience. I hope to get enough experience to help everyone I know to eventually use some version of Linux--it is free after all! :P
 
Problem background: 
Installed Lucid Lynx on a 5 year old Panasonic laptop and all hardware is recognized, however the touchpad is very slow regardless of the System/Preferences/Mouse Preferences settings (Pointer speed's Acceleration and Sensitivity are both set to maximum). 
I found a forum post stating "installing GSynaptic should fix the touchpad's low sensitivity problem" so I went to Applications/Ubuntu Software Center and did a search for 'gsynaptic.' The 1st result returned is "Touchpad" so I installed it.
 
When I run Touchpad (from System/Prefences/), this message is displayed:
"GSynaptics couldn't initialize. You have to set 'SHMConfig' 'true' in xorg.conf ot XF86Config to use GSynaptics"
 
Please tell me the procedure for properly editing the above mentioned file(s) so I can use the GSynaptic Touchpad application.
 
Thank you for taking the time to read this post!

---

### Post by mikewhatever on 2010-05-26
Do you know for sure you have a synaptics touchpad? It is something worth while verifying, before you plunge into configuring a piece of hardware you don't have. Ubuntu has various tools to get hardware profiles, for example 'hardinfo' from the repositories. It is a lot like Windows programs, lots of menus to navigate. :P

---

### Post by a-guy-in-japan on 2010-05-30
Good advice! It's a touchpad on a Panasonic CF-29 Toughbook and even the manual doesn't list the manufacturer. I didn't see a maker for it in the hardware info (will check again when I get home day after tomorrow--it's at home now & I'm not)
I used the Terminal command ' sudo apt-get install lshw-gtk ' to get a graphic hardware list--found this commad it in one this forum's stickys--extremely helpful tho some parts way over my head.
I'll check the 'hardinfo' from the repositories as well. Thanks very much for the advice!

---

### Post by Eisenwinter on 2010-05-30
I suggest trying to let Xorg configure itself with the following command:

```
Xorg -configure
```

Do this command as a root user.

It will generate a file called "xorg.conf.new" in your root user's directory. View that file, and edit necessary parts.

Then do this:

```
cp ~/xorg.conf.new /etc/X11/xorg.conf
```

Do this command also as a root user.

Hope this solves your problem.

----

Another thing.

Do you have HAL (Hardware Abstraction Layer) installed? It may be worth checking out.

If you have HAL, you can run Xorg successfully without having a configuration file.

Sometimes you do need to have a configuration file, if your hardware is very "rare", or requires some special config option, but usually running Xorg without a configuration file, using HAL, will do the trick.

---

### Post by mikewhatever on 2010-05-30
Try running the following command:

dmesg | grep -i "touchpad\|mouse"

On my HP5000 notebook, the output is as follows
```
dmesg | grep -i touchpad
[   25.178106] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x200000
[   25.245590] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8

```
Another way is to check the device manager in Windows.

---

### Post by a-guy-in-japan on 2010-06-06
> **Eisenwinter said:**
> I suggest trying to let Xorg configure itself with the following command:

```
Xorg -configure
```Do this command as a root user.

It will generate a file called "xorg.conf.new" in your root user's directory. View that file, and edit necessary parts.

Then do this:

```
cp ~/xorg.conf.new /etc/X11/xorg.conf
```Do this command also as a root user.

Hope this solves your problem.

----

Another thing.

Do you have HAL (Hardware Abstraction Layer) installed? It may be worth checking out.

If you have HAL, you can run Xorg successfully without having a configuration file.

Sometimes you do need to have a configuration file, if your hardware is very "rare", or requires some special config option, but usually running Xorg without a configuration file, using HAL, will do the trick.

I really appreciate the feedback and help!

Inputing 'Xorg -configure' in Terminal renders this message:

Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.


Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 

 ddxSigGiveUp: Closing log

I installed HAL from the Software Center prior to inputting that in Terminal.
In Applications/System Tools/Device Manager under "Platform Device/i8042 AUX port/pointing device" it reads, "Model: PS/2 Touchpad" and "/dev/input/event8."
Does that help understand the root of the touchpad's low response?

---

### Post by a-guy-in-japan on 2010-06-06
> **mikewhatever said:**
> Try running the following command:

dmesg | grep -i "touchpad\|mouse"

On my HP5000 notebook, the output is as follows
```
dmesg | grep -i touchpad
[   25.178106] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x200000
[   25.245590] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8

```Another way is to check the device manager in Windows.

Thank you again for more help!

Inputing  dmesg | grep -i "touchpad\|mouse" in Terminal renders this message:

[    0.547354] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.648311] mice: PS/2 mouse device common for all mice
[    1.500654] input: Dell Dell USB Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input5
[    1.500892] generic-usb 0003:413C:3200.0001: input,hidraw0: USB HID v1.10 Mouse [Dell Dell USB Mouse] on usb-0000:00:1d.0-1/input0
[   14.648856] input: PS/2 Touchpad as /devices/platform/i8042/serio1/input/input8


In System/Preferences/Windows I didn't see anything for the touchpad but in Applications/System Tools/Device manager I did see mention of the touchpad (please see response one post above).
Thanks again for taking the time to respond and help me learn!

---

### Post by Professor IllDog43 on 2010-06-11
This might help you [http://crunchbanglinux.org/forums/topic/4282/disabling-touchpad-taptoclick-with-gsynaptics-nb-the-caveat/](http://crunchbanglinux.org/forums/topic/4282/disabling-touchpad-taptoclick-with-gsynaptics-nb-the-caveat/)

---

### Post by canac on 2010-06-23
Hi, I'm having a similar problem, and I'm hoping someone can help me.

I'd like to temporarily disable the touchpad while I'm typing. I first tried to follow the instructions [here]("https://help.ubuntu.com/community/SynapticsTouchpad") under "Advanced Configuration with a Graphical Interface." After completing those steps, I try to run "Touchpad," but I get the error, "You have to set ‘SHMConfig’ ‘true’ in xorg.conf or XF86Config."

I found [this]("http://agoranetbook.kayno.net/2009/05/11/you-have-to-set-%E2%80%98shmconfig%E2%80%99-%E2%80%98true%E2%80%99-even-though-you-have-created-shmconfigfdi/"), which explains how to fix the same problem I'm having, but the file he says to delete doesn't exist.

I then tried to modify the xorg.conf file as described [here]("http://ubuntuforums.org/archive/index.php/t-844414.html"), but no xorg.conf file exists. Same with an XF86Config file.

I then tried to install the program "TouchFreeze," but that does nothing.

Then, back in the original link, I followed the instructions under "Disabling the Touchpad Temporarily While Typing," but I get the following message: "Unable to find a synaptics device."

Then I ran the command, "xinput list" to look for my touchpad device, and I got this:

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)	id=9	[slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Logitech Wheel Mouse             	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; USB 2.0 UVC 0.3M Webcam                 	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]
    &#8627; Asus Laptop extra buttons               	id=14	[slave  keyboard (3)]

I don't see anything about synaptics or touchpad, but I'm not entirely sure what I'm looking at. Everything about the touchpad works, so it must be detected correctly, right?

Lastly, I followed the instructions [here]("http://crunchbanglinux.org/forums/topic/4282/disabling-touchpad-taptoclick-with-gsynaptics-nb-the-caveat/"), which are basically the same as the first set, but with one discrepancy, "on" is changed to "True" in shmconfig.fdi. Didn't have any luck with that either.

Any help or advice would be greatly appreciated. Thanks.

---

