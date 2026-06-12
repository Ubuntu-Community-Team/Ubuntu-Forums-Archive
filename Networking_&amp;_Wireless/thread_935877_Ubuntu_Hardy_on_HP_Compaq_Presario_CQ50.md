---
title: "Ubuntu Hardy on HP Compaq Presario CQ50"
date: 2008-10-02
forum: Networking &amp; Wireless
---

### Post by jithinkr on 2008-10-02
_Obtaining the required screen resolution._

I own a HP Compaq Presario CQ50 laptop. I installed Ubuntu Hardy 64 bit on it without any problem. Initially I had problems with graphics as the only available screen resolutions were 800 * 600 and 640 * 480. I solved it by installing the required NVIDIA graphics driver. And since then there hasn't been any problem with graphics. 
The post that helped me set up my graphics drivers. : 

_Oh Wireless, please switch on._

The next thing I noticed was that the wireless button on top is not getting enabled, even after pressing it. It remains red and doesn't turn blue. However it works properly on Windows Vista. I tried out various solutions obtained from the forum but in vain. 
An lspci -v command gives the following result.

```
00:00.0 RAM memory: nVidia Corporation Unknown device 0754 (rev a2)
00:01.0 ISA bridge: nVidia Corporation Unknown device 075e (rev a2)
00:01.1 SMBus: nVidia Corporation Unknown device 0752 (rev a1)
00:01.3 Co-processor: nVidia Corporation Unknown device 0753 (rev a2)
00:01.4 RAM memory: nVidia Corporation Unknown device 0568 (rev a1)
00:02.0 USB Controller: nVidia Corporation Unknown device 077b (rev a1)
00:02.1 USB Controller: nVidia Corporation Unknown device 077c (rev a1)
00:04.0 USB Controller: nVidia Corporation Unknown device 077d (rev a1)
00:04.1 USB Controller: nVidia Corporation Unknown device 077e (rev a1)
00:06.0 IDE interface: nVidia Corporation Unknown device 0759 (rev a1)
00:07.0 Audio device: nVidia Corporation Unknown device 0774 (rev a1)
00:08.0 PCI bridge: nVidia Corporation Unknown device 075a (rev a1)
00:09.0 IDE interface: nVidia Corporation Unknown device 0ad0 (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation Unknown device 0760 (rev a2)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 0569 (rev a1)
00:14.0 PCI bridge: nVidia Corporation Unknown device 077a (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
02:00.0 VGA compatible controller: nVidia Corporation Unknown device 0845 (rev a2)
07:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

```
I have ndiswrapper installed, but have not got the required .inf file for the wireless card Broadcom BCM4312. Please help me what to do. I also tried installing madwifi but later realised that it wasn't for the wireless card my laptop. Well, that was silly.

_Bad Bad Touchpad!_

Next I realised that my Synaptics Touchpad is not working the way it is intended to work. Of course I can control the mouse, but the scrolling feature was disabled. Also, the tiny button on top of the pad to enable or disable the Touchpad also malfunctions. The touchpad is functional irrespective of if it is on (white glow) or off (red glow). And when I press that touchpad enable/disable button when the light is red, then the Ubuntu Help opens up! 
Well, I have figured out how to make the scroll feature to work. It seems that the xorg.conf file in /etc/X11 got messed up during the installation of the NVIDIA driver. The entire portion regarding the Touchpad was missing. However i had the backup file and copy pasted the following.
```

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
	Option		"SHMConfig"		"On"
EndSection
```

after that I added the line 'Input Device "Synaptics Touchpad"' without the single quotes to the ServerLayout section. Restarted the xserver and Touchpad scroll works! Also I have added the SHMConfig Option to the Synaptics Section, so that I can get syndaemon to work. Now the touchpad doesn't trouble me when I am typing. It gets temporarily disabled (for 1 second) when I am typing something. (I run syndaemon -i 1 -d -t -K during startup for this to work.) run man syndaemon for more.:D
Note however that the tiny button is still malfunctioning. Touchpad works even if the glow is red and Help opens up when I press the button to change the red glow to white. Please tell me what should I do for this.

_Cracking and Popping Sound._
:confused:
Never found any proper help for this problem, the problem regarding the crackling and popping sound when playing multimedia. I don't have the perfect solution, but I think what I have found can be a starting point. While playing with the Sound Preferences (System>Preferences>Sound), I selected HDA NVidia Alsa Mixer Device and selected Digital in the listbox. What I noticed is that, with this, I am unable to control the volume using the function key and the volume up and volume down keys (In my laptop it is function key + pg up / pg dn). This is because I have selected to control the Digital Volume using the keys. But this is what caught my fascination, When I keep pressing (fn + pg dn) the crackling and popping sound subsides. But if I let go of the keys, the annoying sound comes back. 
I changed the Default Mixer Tracks Device selection and tried. Now the keys function properly and help you control the sound. 
I don't know if that helps, but I hope this observation will be of help to someone, and he/she could get a proper solution to this annoying sound problem in Ubuntu.

---

### Post by Ayuthia on 2008-10-02
For your wireless, have you gone into System->Administration->Hardware Drivers and enabled wl and disabled b43?  Your card should work with the wl driver.

---

### Post by jithinkr on 2008-10-02
The hardware drivers list box is empty. Nothing is displayed there. I guess, the required drivers have not been installed. 

But how can it be. Wireless was initially working. After installing the nvidia drivers, all problems started appearing. Dont' know why.

And also, how to create a restore point in Ubuntu?

Thanks for the response.

---

### Post by Ayuthia on 2008-10-02
Can you try the following:
```
sudo updatedb
locate wl.ko
```
This will update the search database and then look for the wl driver.

As for a restore point, I am not for sure about how to do this.  I have not done much with backups yet.

---

### Post by jithinkr on 2008-10-03
I tried out sudo updatedb and locate wl.ko command. well nothing came up. There wasn't any response on my terminal.

And any idea regarding the sound? Any suggestions etc.
Thanks!

---

### Post by Ayuthia on 2008-10-03
> **jithinkr said:**
> I tried out sudo updatedb and locate wl.ko command. well nothing came up. There wasn't any response on my terminal.

And any idea regarding the sound? Any suggestions etc.
Thanks!

Can you post the results of lspci -nn?  I would like to confirm the chipset of your wireless.

As for the sound, I am not too sure about that one.  I have seen people talk about this in the forum, but I don't remember where.

---

### Post by jithinkr on 2008-10-05
00:00.0 RAM memory [0500]: nVidia Corporation Unknown device [10de:0754] (rev a2)
00:01.0 ISA bridge [0601]: nVidia Corporation Unknown device [10de:075e] (rev a2)
00:01.1 SMBus [0c05]: nVidia Corporation Unknown device [10de:0752] (rev a1)
00:01.3 Co-processor [0b40]: nVidia Corporation Unknown device [10de:0753] (rev a2)
00:01.4 RAM memory [0500]: nVidia Corporation Unknown device [10de:0568] (rev a1)
00:02.0 USB Controller [0c03]: nVidia Corporation Unknown device [10de:077b] (rev a1)
00:02.1 USB Controller [0c03]: nVidia Corporation Unknown device [10de:077c] (rev a1)
00:04.0 USB Controller [0c03]: nVidia Corporation Unknown device [10de:077d] (rev a1)
00:04.1 USB Controller [0c03]: nVidia Corporation Unknown device [10de:077e] (rev a1)
00:06.0 IDE interface [0101]: nVidia Corporation Unknown device [10de:0759] (rev a1)
00:07.0 Audio device [0403]: nVidia Corporation Unknown device [10de:0774] (rev a1)
00:08.0 PCI bridge [0604]: nVidia Corporation Unknown device [10de:075a] (rev a1)
00:09.0 IDE interface [0101]: nVidia Corporation Unknown device [10de:0ad0] (rev a2)
00:0a.0 Ethernet controller [0200]: nVidia Corporation Unknown device [10de:0760] (rev a2)
00:0b.0 PCI bridge [0604]: nVidia Corporation Unknown device [10de:0569] (rev a1)
00:14.0 PCI bridge [0604]: nVidia Corporation Unknown device [10de:077a] (rev a1)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration [1022:1300] (rev 40)
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Address Map [1022:1301]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h DRAM Controller [1022:1302]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control [1022:1303]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Link Control [1022:1304]
02:00.0 VGA compatible controller [0300]: nVidia Corporation Unknown device [10de:0845] (rev a2)
07:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)

the result of lspci -nn is this.

---

### Post by jithinkr on 2008-10-05
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

I followed the steps provided here. Now my wireless button turns blue! That's a development. I have not yet tested if my comp is connecting to any available wireless connection.

Will ubuntu automatically detect available wireless networks, or will i have to set it up or something.

P.S. : I ran a lshw -C network. In the network section regarding wireless, the module was forcedeth instead of ssb or ndiswrapper. After trying out the steps there, the module name became ndiswrapper and now the wireless button turns blue.

---

### Post by cmat on 2008-10-05
I never got this laptop to work. But I'm going to wait for new drivers. If they don't appear then I'm going to file bug reports.

---

### Post by jithinkr on 2008-10-06
the only thing that doesnt' work for me now is sound. I can make it work properly i mean clearly by using the function keys (but i have to keep pressing it). apart from that everything is working properly. the wireless is working real cool! the touchpad (except for the tiny button on top.) 
Now am waiting for Intrepid. Hope that clears up the sound problem. :)

---

### Post by lvm_723 on 2008-10-07
See this post : [http://ubuntuforums.org/showthread.php?p=5926993#post5926993](http://ubuntuforums.org/showthread.php?p=5926993#post5926993)  and many others through the forum.  

This laptop is very difficult to configure with Linux.  And no one knows how to get the sound working...

---

### Post by lvm_723 on 2008-10-08
And this is it for the sound driver : [http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/)


ENJOY !

---

### Post by fuzzyworbles on 2008-12-18
thanks for the synaptics touchpad tip. i never thought of looking to see if nvidia botched my xorg.conf because it still basically worked.

.. and my cq50-116 comes with atheros which works outta the box, but i compiled madwifi anyway.

.. of the laptops i've owned, standby has always been a pain. any ideas on getting the cq50 to standby? er, i should say wakeup..

.. oh, and about the snap crackle pop of the audio: i upgraded from hardy to intrepid and now it sounds as nice as it does under vista.

---

### Post by starscalling on 2009-06-12
update on this laptop:

jaunty installs fine; sound is great; wireless works out of the box; run all updates and it sees the vid card for drivers properly; offers non-free wireless driver from begining [before updates]. touchpad is a bit sensitive as is mouse by default; dual booting with crapsta ultimate. still searching for a way to make fn keys work. [sound does by default but the second usage of f1-12 dont]

---

