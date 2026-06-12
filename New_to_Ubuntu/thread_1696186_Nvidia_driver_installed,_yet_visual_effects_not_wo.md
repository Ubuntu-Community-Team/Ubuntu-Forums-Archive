---
title: "Nvidia driver installed, yet visual effects not working"
date: 2011-02-27
forum: New to Ubuntu
---

### Post by John Galt on 2011-02-27
Respected members,

my computer configuration is as below:

nvidia geforce 4 mx 4000 graphics card
asrock 854gv chipset mobo
512 mb ram
80+40 gb hdd
dvd/cd rw combo drive
ubuntu maverick meerkat

the issue i am facing is as below:

ubuntu was working right out of the box after installation, i.e. without any properietery drivers (nvidia).

Yesterday, i added the driver version 96 from the additional drivers section in system menu.

As of now everything is fine and no system issues. However, i am not able to switch on the visual effects option in the appearance preferences (the right click menu.) The same was the case even before the driver installation.

When you select radio button to activate atleast the "normal" mode, the system searches for additional drivers,much in the same way as "additional drivers" section did, then the dialog box flickers for a few times and then finally a new dialog box pops up saying "desktop effects could not be enabled."

Another point worthy of mention is that i had installed "compiz" from repositories few days before i had installed the graphics driver. I guess CCSM is pre installed. Hence, wasn't installed.

Is there a conflict between compiz and visual effect settings?

Also, do I have to configure the nvidia graphics driver after it's installation? All at this point i have done is that i have changed the screen resolution from 800x600 to 1024x768 and the refresh rate from auto to 60 hz.

Have I gone wrong somewhere? What is missing and what needs to be done?

---

### Post by emoguitarist06 on 2011-02-27
In System > Administration > Additional Drivers
it says "This driver is activated and currently in use" right?

and of course you've already restarted your computer after install right?

If you said yes to both questions then let's make sure everything "compiz" is installed and run this code in a terminal:
```
sudo apt-get install compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-plugins compiz-gnome

```
change compiz-gnome if you're running Kubuntu

---

### Post by amsterdamharu on 2011-02-27
The following command should give you some output, check to see if there are multiple graphic cards in your computer:
```
sudo lspci
```

Then you can check what driver is in use for your nvidia (given there is only one graphic card).

```
sudo lspci -vv
```

This gives lots of output, the nvidia output should end with:
```
    Kernel driver in use: nvidia
    Kernel modules: nvidia, nouveau, nvidiafb

```

Now if the driver is in use you can log out (not restart) press control + alt + F1 and log in to the non graphic screen. Execute the following commands:
```
sudo service gdm stop
sudo nvidia-xconfig
sudo service gdm start
```

If it doesn't work could you post the output of "lspci" and the graphic card part of "lspci -vv"?

To execute the command(s) you can press alt + F2, type gnome-terminal and click run. Then copy one command and paste it in the terminal (black screen that showed up after you clicked run). Use the mouse to paste commands in the terminal.
Then you can select all the text in the terminal, right click and select copy. When pasting it here please wrap it in code tags: &#91;code][COLOR=Red]Your pasted stuff[/COLOR]&#91;/code]

---

### Post by eliofall on 2011-02-28
im having the same problem. it started the same time the nm-applet stopped 
loading at login. dont know if they have anything to do with each other.


additional drivers says, no proprietary drivers are in use...

tried uninstalling, reinstalling the driver, but that didnt work.

here is the output im getting.

```
01:00.0 VGA compatible controller: nVidia Corporation GT200 GeForce GTX 260 rev a1
```


```

	Capabilities: access denied
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nouveau, nv
```

any ideas?

---

### Post by amsterdamharu on 2011-02-28
@eliofall
According to lspci the driver in use is nvidia and additional drivers says, no proprietary drivers are in use. Are you sure it's not "there are no proprietary drivers found because" nvidia is a proprietary driver and it is in use.

Did you try the following:
[http://ubuntuforums.org/showpost.php?p=10500335&postcount=3](http://ubuntuforums.org/showpost.php?p=10500335&postcount=3)
The part where you stop gdm and then remake the xorg.conf and start gdm.
Could you post the output of the following command?
```
compiz-check
```


About the nm-applet, could you post the output of the following command?
```
cat /etc/network/interfaces 
```

---

### Post by eliofall on 2011-02-28
heres a screen shot
[IMG]http://a3.l3-images.myspacecdn.com/images02/139/ab854ed7212f40b4bff9816ee57dff6f/l.png[/IMG]
[IMG]http://a3.l3-images.myspacecdn.com/images02/146/41462f01fb3a4b97b21644e018715062/l.png[/IMG]
when i go into compizconfig settings manager and restore all my settings it doesnt do anything.

and yes, i followed the institutions in that link and it didnt change anything. then, i uninstalled the driver and installed the newest one from nvidia. x86-260.19.36 


should i have posted the full lspci -vv and lspci?


the code output is ```
eli@eli-box:~$ compiz-check
compiz-check: command not found
eli@eli-box:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

```

---

### Post by thinkinhurtz on 2011-02-28
I'm not sure if anyone has mentioned this yet but it might help for users having nvidia problems while using Compiz and dual monitors. Everyone attempting this please note that effect settings will not work if Xenerama is enabled through Nvidia for dual monitor functions. This might help some people. Just turn off Xinerama and turn on the effects after. Problem solved, but no dual monitors.

---

### Post by John Galt on 2011-03-01
@[amsterdamharu]("http://ubuntuforums.org/member.php?u=898154")

tried your method without any success. The same problem persists.

The output of the commands is as follows:

```
sudo lspci

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 Display controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
03:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 4000] (rev c1)
``````
sudo lspci -vv

03:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 4000] (rev c1) (prog-if 00 [VGA controller])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 248 (1250ns min, 250ns max)
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at de000000 (32-bit, non-prefetchable) [size=16M]
    Region 1: Memory at c0000000 (32-bit, prefetchable) [size=128M]
    [virtual] Expansion ROM at dfde0000 [disabled] [size=128K]
    Capabilities: [60] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [44] AGP version 3.0
        Status: RQ=32 Iso- ArqSz=0 Cal=0 SBA+ ITACoh- GART64- HTrans- 64bit- FW+ AGP3- Rate=x1,x2,x4
        Command: RQ=1 ArqSz=0 Cal=0 SBA- AGP- GART64- 64bit- FW- Rate=<none>
    Kernel driver in use: nvidia
    Kernel modules: nvidia-96, nouveau, nvidiafb
``````
cat /etc/network/interfaces

auto lo
iface lo inet loopback

```Also a new problem with the updates has cropped up.

[IMG]http://ubuntuforums.org/home/john/Desktop/Screenshot.png[/IMG]No update starts without a popup box (plz see attached images) and when i go into the software sources section in the software centre and find that all the required tick boxes are active. Yet this messsage pops up. And ofcourse the update doesn't proceed.

I was able to update however, when i checked the top two options namely, "canonical partners" and "canonical partners source code". After the update and a mandatory restart, the same problem cropped up again. This time every tick box is checked.

So my query is this:

1: how to solve he problem of this compiz and ccsm. I tried uninstalling compiz and reinstalling compiz and ccsm. Is there anything else i need to install for it to work?

2: what to do about this update problem.

Please Advise

---

### Post by John Galt on 2011-03-01
about the "compiz-check" command............it says "command not found"..........

---

### Post by John Galt on 2011-03-02
help.....anyone??!!

---

### Post by John Galt on 2011-03-08
wow, this is the longest i have ever been without an answer....

---

### Post by John Galt on 2011-03-18
closing this thread, too old and feel hijacked.

---

