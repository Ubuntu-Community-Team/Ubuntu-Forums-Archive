---
title: "Internet fails when resuming from sleep or hibernation"
date: 2010-08-23
forum: New to Ubuntu
---

### Post by lbrty on 2010-08-23
When I resume the computer from sleep (or hibernation), the internet (ethernet adapter -- not wireless) does not work. I must restart the computer in order to get it to work again. I have an HP Pavilion dv4 notebook with Lucid Lynx and all updates installed.

Thank you in advance for your help!

---

### Post by scorp123 on 2010-08-23
That's most likely because your network modules (= network drivers) get unloaded during suspend/resume ... 

Can you please open a terminal and then copy & paste the output of this command:

```
sudo lspci
sudo lsusb
```

When the system asks for a password: It's your own password. And there won't be any feedback when you type it -- no asterisks, no question marks, nothing. Just type in your password blindly and hit the "enter" key.

If the system complains that it does not know such a command, please install these packages and then try again:
```
sudo apt-get install pciutils usbutils
```

These commands (lspci, lsusb) should list all PCI and USB devices in your laptop ... this should help us find which modules (= drivers) have to be stopped from unloading at suspend/resume.

How can they be stopped?

If you know their names you can insert them into this file:
**/etc/default/acpi-support**

To edit that file you need to open it as root, e.g. via this command:
```
gksu gedit /etc/default/acpi-support
```



In that file there is a line that says:
```
# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=""

```

Once you know the name of your network driver modules you will have to enter them into that line, separated by spaces.

But before we could do that you will need to give us the output of "lspci" and "lsusb" so we know what hardware you have in your laptop ... :)

---

### Post by Thryn on 2010-08-23
I had the same problem, but only on 64-bit. That is, if your problem is that it can't find the (wireless) network. If such is the case, I suggest that you try what worked for me: when this problem happens, turn off your wireless card (assuming you have a switch or a key combination to do so) and then turn it back on again. Input the info for your network again.

For some reason this worked for me, but I have an ASUS UL30a so your mileage may vary.

EDIT: to clarify, since I did that, I have not once had that problem.

---

### Post by lbrty on 2010-08-23
_**@scorp123**_
Thanks for the reply!

I did everything as suggested and the internet does not work when resuming.

I then copied the line below from the command results into this file **acpi-support** with this command: gksu gedit /etc/default/acpi-support

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST="03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)"

I then saved the file and tested it out.

Please let me know what I missed. Thanks!

Here are the results from the commands below
sudo lspci
sudo lsusb

```
sudo lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
04:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
04:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
04:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
04:00.4 System peripheral: JMicron Technology Corp. xD Host Controller
sudo lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 045e:00d1 Microsoft Corp. Optical Mouse with Tilt Wheel
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 174f:1107 Syntek 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```[U][B]@Thryn
[/B][/U]Thanks for reply! I have a 32-bit OS and I do not use the wireless function on the notebook. This is for a wired connection (ethernet).

---

### Post by scorp123 on 2010-08-23
> **linuxliberty said:**
> I then copied the line below from the command results into this file **acpi-support** with this command: gksu gedit /etc/default/acpi-support

NOOOO!

**_Don't do such stuff if you don't know what you're doing!!!_**


That "lspci" command will simply spit out the hardware you have **BUT YOU DON'T ENTER THAT STUFF INTO THE FILE**.

**[COLOR="Red"]Patience. Please.[/COLOR]**

Once we know the hardware we now have to find the driver names, OK?

[COLOR="Red"]But please undo that crazy editing you have done![/COLOR]

---

### Post by scorp123 on 2010-08-23
Please give me the output of this command:
```
sudo lsmod
```

This will spit out all the drivers that are loaded. It should be easy to spot the ones we need now that we know what hardware you have (e.g. the driver for your Broadcom chip will most likely be named *bcmxxx-something* ... )


Example:

One stupid Fujitsu-Siemens laptop that I have here has the same problem. It has a Atheros WiFi chip. So "lspci" will say something like *"00x0:xxxx  Atheros Electronics Wireless Network Controller"*.

That's the hardware. But to find out what needs to be put into that "acpi-support" file you look at the list of loaded drivers, e.g. this command:
```
sudo lsmod
```

And taaddaaaa ... in that list there was a driver called ***ath_pci***

So that's what in my case needed to go into the ***MODULES_WHITELIST=*** line


So please ... remove that change you have done and let's find out what driver names need to go in there, OK?

The reason I asked for "lspci" and "lsusb" is that it is otherwise pointless to look at "lsmod" if we don't know what hardware is in the system ... 

I hope this clears up the misunderstanding. English is not my native language.

---

### Post by lbrty on 2010-08-23
I removed the line from the file **acpi-support**. Looking forward to your reply! Thank.

---

### Post by texaswriter on 2010-08-23
This is not a substitute to any of the great advice being given out here, but sometimes I would have problems when coming out of suspend because I was now connecting to a different WIFI connection. Like, I suspended my computer at home, where I was on my home's wifi, let's say it's name is Home_Internet... Then I wake up my computer at school, where the WIFI is the school's, let's say it's name is School_Auto_login... Until I disconnect from my home wifi and connect to school, the network manager will try connecting [repeatedly] to the home wifi. Obviously it will fail.

---

### Post by lbrty on 2010-08-23
_**@scorp123**_
Broadcom is the wireless network adapter (not using, no issues)
**Realtek is the wired network adapter (the one I use and does not work when resuming the computer from sleep mode)**

```
sudo lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
vboxnetadp              6326  0 
vboxnetflt             15280  0 
vboxdrv               191010  2 vboxnetadp,vboxnetflt
snd_hda_codec_intelhdmi    11622  1 
snd_hda_codec_idt      51978  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_intel          22037  2 
snd_hda_codec          74201  3 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
arc4                    1153  2 
snd_pcm                70886  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
i915                  285891  3 
drm_kms_helper         29297  1 i915
snd_seq_midi            4557  0 
drm                   163098  4 i915,drm_kms_helper
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
b43                   164132  0 
mac80211              205146  1 b43
uvcvideo               57022  0 
videodev               34361  1 uvcvideo
snd                    54148  17 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              24415  2 i915
v4l1_compat            13251  2 uvcvideo,videodev
jmb38x_ms               7407  0 
i2c_algo_bit            5028  1 i915
psmouse                63245  0 
serio_raw               3978  0 
agpgart                31788  2 drm,intel_agp
cfg80211              126517  2 b43,mac80211
soundcore               6620  1 snd
snd_page_alloc          7172  2 snd_hda_intel,snd_pcm
sdhci_pci               5502  0 
sdhci                  15654  1 sdhci_pci
memstick                8237  1 jmb38x_ms
joydev                  8708  0 
hp_accel               11144  0 
video                  17375  1 i915
output                  1871  1 video
lirc_ene0100            6600  0 
lirc_dev                8884  1 lirc_ene0100
lis3lv02d               6096  1 hp_accel
input_polldev           2482  1 lis3lv02d
led_class               2864  3 b43,sdhci,hp_accel
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36174  0 
hid                    67032  1 usbhid
ahci                   32232  2 
r8169                  34300  0 
mii                     4381  1 r8169
ssb                    38671  1 b43
```[U][B]@texaswriter
[/B][/U]Thanks for your reply! I am using a wired connection (ethernet).

---

### Post by lbrty on 2010-08-23
[U][B]@scorp123
[/B][/U]I found a quick and easy way of finding the driver for the ethernet (Realtek) adapter. Right click the NetworkManager Applet in the system tray and click Connect Information and the information is listed under Driver. The information matches the last command to display the drivers. Driver: r8169

What do you think? What should the next step be? Thanks!

---

### Post by scorp123 on 2010-08-24
> **linuxliberty said:**
> Driver: r8169 Bingo!

I'd guess that's the one then. This line in your "lsmod" output suggests a dependency between "mii" and "r8169" (e.g. one module loads the other):
```
...
...
mii                     4381  1 r8169

```

So IMHO it can't hurt to try it. So you'd edit the file via this command:
```
gksu gedit /etc/default/acpi-support
```

... and then change it so the relevant line looks like this:
```
# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST="r8169"
```

... and then reboot. Just to make sure that the ACPI sub-system is aware of that config change. And then try it out! Suspend the system .... leave it like that for like 15 min. ... and then resume.

If that didn't work add the "mii" driver there as well, e.g.
```
MODULES_WHITELIST="mii r8169"
```


What you should do in any case is to take a look at **"lsmod"** again! This could give us a clue about what drivers get unloaded during suspend and resume. You can redirect the output to a file so you can copy & paste the output after regaining network connectivity (e.g. after a reboot in case this didn't work). Redirecting the output can be done like this:
```
lsmod > $HOME/lsmod_output.txt
```

... this would write the output to the file ***"lsmod_output.txt"*** which gets saved into your home directory (**'$HOME'** is a system variable that should automatically and correctly resolve that location). So in case our messing with ***"acpi-support"*** didn't have the desired effect: Please reboot again and then post that text file here so we can compare the list of loaded drivers before and after a suspend/resume cycle ...

---

### Post by lbrty on 2010-08-24
I tried all different methods and the ethernet adapter does not work when resuming from sleep mode.

What else do you think it could be? Thanks for all your help!

Here is the output from the last command: lsmod > $HOME/lsmod_output.txt

```
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
vboxnetadp              6326  0 
vboxnetflt             15280  0 
vboxdrv               191010  2 vboxnetadp,vboxnetflt
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_codec_intelhdmi    11622  1 
snd_hda_codec_idt      51978  1 
i915                  285891  3 
arc4                    1153  2 
snd_hda_intel          22037  2 
snd_hda_codec          74201  3 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70886  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54148  17 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
b43                   164132  0 
drm_kms_helper         29297  1 i915
mac80211              205146  1 b43
jmb38x_ms               7407  0 
uvcvideo               57022  0 
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
memstick                8237  1 jmb38x_ms
drm                   163098  4 i915,drm_kms_helper
intel_agp              24415  2 i915
agpgart                31788  2 drm,intel_agp
soundcore               6620  1 snd
i2c_algo_bit            5028  1 i915
snd_page_alloc          7172  2 snd_hda_intel,snd_pcm
psmouse                63245  0 
serio_raw               3978  0 
sdhci_pci               5502  0 
sdhci                  15654  1 sdhci_pci
cfg80211              126517  2 b43,mac80211
joydev                  8708  0 
hp_accel               11144  0 
video                  17375  1 i915
output                  1871  1 video
lirc_ene0100            6600  0 
lirc_dev                8884  1 lirc_ene0100
lis3lv02d               6096  1 hp_accel
input_polldev           2482  1 lis3lv02d
led_class               2864  3 b43,sdhci,hp_accel
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36174  0 
hid                    67032  1 usbhid
r8169                  34300  0 
mii                     4381  1 r8169
ssb                    38671  1 b43
ahci                   32232  2 
```

---

### Post by dfairley on 2010-08-24
@Texaswriter..... This is not a WIFI issue.  He states his PC does not have wireless and is for ethernet connectivty... Ofcourse when your PC goes to sleep connected  to one WIFI site and when you bring it back up it does not know you've traveled across town so it continues to look for the last site it was connected to....

---

### Post by scorp123 on 2010-08-25
> **linuxliberty said:**
> I tried all different methods and the ethernet adapter does not work when resuming from sleep mode. Hmmm ... do you use NetworkManager and DHCP?

---

### Post by texaswriter on 2010-08-25
My apologies, I misread that... thought it was a wireless.

---

### Post by lbrty on 2010-08-25
> **scorp123 said:**
> Hmmm ... do you use NetworkManager and DHCP?

Yes and yes.

---

### Post by scorp123 on 2010-08-25
If you manually kill and restart NetworkManager ... does that help?
```
killall -1 nm-applet
```

(What the code does: "killall" searches the list of running programs for a process with the name "nm-applet" -- that's the NetworkManager Applet. Once the process is identified it is killed with a "-1" signal which basically means: *"Go kill yourself and then start again!"* ... So sending "killall -1" or "kill -1" to a process should usually get rid of a previously running instance and then immediately restart the same process again ...)

Did that help? I am really running out of ideas here ... :(

---

### Post by lbrty on 2010-08-26
**I really appreciate all your help and assistance!**

These are the steps I took with no success:
-suspended the computer
-resumed the computer (with no network connectivity)
-entered the following command:
```
killall -1 nm-applet
```The NetworkManager Applet is killed however does not automatically restart. I then manually start the NetworkManager Applet by going to /usr/bin/nm-applet

The NetworkManager then starts but without network connectivity. I must restart the system to regain a network connection.

Once again, I appreciate all your help and assistance scorp123! :D

---

### Post by lbrty on 2010-08-28
Anyone else have any recommendations to regain network connectivity once resuming from sleep or hibernation?

Thank you!

---

### Post by scorp123 on 2010-08-29
> **linuxliberty said:**
>  The NetworkManager then starts but without network connectivity.  Please repeat and reproduce those steps, e.g. going into standby, resuming, killing network manager applet, etc. ... But then: When you (right?)-click on the network applet icon ... does it even list any network interfaces?

And what happens if you go to the terminal and issue this command:
```
ifconfig -a
``` ... does it list an *"Ethernet 0"* interface? Short form would be **eth0** ... 

Example:

```
> ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:60:72:10:62:dd  
          inet addr:192.168.1.43  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::260:72ff:fe10:62dd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16381481 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19804077 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:952578267 (952.5 MB)  TX bytes:3150203976 (3.1 GB)
          Interrupt:17 Base address:0xd000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9680 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9680 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2405368 (2.4 MB)  TX bytes:2405368 (2.4 MB)

wlan0     Link encap:Ethernet  HWaddr 00:0e:2e:90:89:83  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

You can redirect the output into a file:
```
ifconfig -a > /home/yourUser/ifconfig.txt
```

... and then post that file here after you have rebooted and regained network connectivity.

---

### Post by lbrty on 2010-08-30
Hey scorp123!

Before I repeated the steps I clicked the NetworkManager Applet and this is what it shows when [COLOR=Red]connected[/COLOR]:
---
Wired Network
**WN** (name of my network)
Disconnect
Wireless Networks
disconnected
---

I then followed the steps below as I did before from my previous post:

> **linuxliberty said:**
> 
These are the steps I took with no success:
-suspended the computer
-resumed the computer (with no network connectivity)
-entered the following command:
```
killall -1 nm-applet
```The NetworkManager Applet is killed however does not automatically restart. I then manually start the NetworkManager Applet by going to /usr/bin/nm-applet

The NetworkManager then starts but without network connectivity. I must restart the system to regain a network connection.

The same results occurred when following the directions above.

> **scorp123 said:**
> ...But then: When you (right?)-click on the  network applet icon ... does it even list any network  interfaces?
Answer: No, it does not. I clicked the NetworkManager Applet and this is what it shows when [COLOR=Red]disconnected[/COLOR]:
---
Wired Network
disconnected
Wireless Networks
disconnected
---

> **scorp123 said:**
> 
And what happens if you go to the terminal and issue this command:
```
ifconfig -a
``` ... does it list an *"Ethernet 0"* interface? Short form would be **eth0** ...
Answer: Yes, it does list eth0

> **scorp123 said:**
> 
You can redirect the output into a file:
```
ifconfig -a > /home/yourUser/ifconfig.txt
```... and then  post that file here after you have rebooted and regained network  connectivity.

I only copied eth0 and x out my hardware mac address. Here is the output:

```
eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:32089 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32469 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:28428634 (28.4 MB)  TX bytes:5189334 (5.1 MB)
          Interrupt:29 Base address:0xa000 
```Thanks again!

---

### Post by scorp123 on 2010-09-02
When at that step (you resume from standby) can you issue this command and see if that would help?

```
sudo service network-manager restart
```

Or this one (not sure it works ... got this one via Google!):
```
sudo initctl restart network-interface INTERFACE=eth0
```

---

### Post by lbrty on 2010-09-02
Thanks for your persistence on this issue! I really appreciate it!

After the computer resumed from sleep mode, I entered this command:
```
sudo service network-manager restart
```Received the following output:
```
network-manager start/running, process 15894
```Nothing happened. 


I then entered this command:
```
sudo initctl restart network-interface INTERFACE=eth0
```Received the following output:
```
network-interface (eth0) start/running
```Nothing happened. 


Thanks again for all your help! :)

---

### Post by texaswriter on 2010-09-02
Lol, is all this trouble worth just shutting down and rebooting. 

It takes me less than 30 seconds from turning on my computer to when I can load applications and begin using.  

Just my 2cents..

---

### Post by owenlinx on 2010-09-02
I have the same hardware and just managed to fix it. It has worked well all day. 

```
gksudo gedit /etc/default/acpi-support
```

```
ACPI_SLEEP_MODE=standby
```

I still have r8169 & mii on the whitelist.

Hope it works!

---

### Post by lbrty on 2010-09-02
> **owenlinx said:**
> I have the same hardware and just managed to fix it. It has worked well all day. 

```
gksudo gedit /etc/default/acpi-support
``````
ACPI_SLEEP_MODE=standby
```I still have r8169 & mii on the whitelist.

Hope it works!

Thanks for the reply! 

I tried it and was not able to regain network activity.

Below is what my acpi-support file shows. Does yours look like this too? Do you think you could copy and paste what your acpi-support file shows so I compare with my acpi-support file? What do you think?

Thanks again! :D

```
# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
ACPI_SLEEP_MODE=standby

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST="mii r8169"
```

---

### Post by owenlinx on 2010-09-02
This is the acpi-support file

[http://paste.ubuntu.com/487511/]("http://paste.ubuntu.com/487511/")

Try that first restart and everything. 

If that doesn't work try this

```
gksudo gedit /etc/pm/config.d/load
```

just put in

```
SUSPEND_MODULES="r8169"
```

then
```
sudo chmod +x /etc/pm/config.d/load
```

I have the same hardware. Running 64 bit 10.04 and mine has worked for about 9 hrs:)

---

### Post by lbrty on 2010-09-02
> **owenlinx said:**
> This is the acpi-support file

[http://paste.ubuntu.com/487511/](http://paste.ubuntu.com/487511/)

Try that first restart and everything. 

If that doesn't work try this

```
gksudo gedit /etc/pm/config.d/load
```just put in

```
SUSPEND_MODULES="r8169"
```then
```
sudo chmod +x /etc/pm/config.d/load
```I have the same hardware. Running 64 bit 10.04 and mine has worked for about 9 hrs:)

[COLOR=Red]**You did it! It works! Problem solved!**[/COLOR] =D> :D 

I first compared (I used *Diffuse Merge Tool *in Ubuntu Software Center for quick automated file comparison) my acpi-support file to your acpi-support file and there was one difference:

Yours:
```
# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST="r8169 mii"
```Mine:
```
# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST="mii r8169"
```I mirrored your acpi-support file and rebooted. I placed the computer in sleep mode and then resumed it and was unable to regain network activity.

I then completed the last steps you stated and it worked perfectly!

```
gksudo gedit /etc/pm/config.d/load
```just put in

```
SUSPEND_MODULES="r8169"
```then
```
sudo chmod +x /etc/pm/config.d/load
```[COLOR=Red]**Thanks again owenlinx!!!**[/COLOR] =D> :-D

---

### Post by owenlinx on 2010-09-02
Glad to help. Enjoy standing by:)

---

### Post by scorp123 on 2010-09-03
So I was right and indeed it was something in that acpi-support file ... \\:D/

Bye ):P

---

### Post by lbrty on 2010-09-04
> **scorp123 said:**
> So I was right and indeed it was something in that acpi-support file ... \\:D/

Bye ):P

Definitely on the right path! :) Thanks scorp123!

---

### Post by Marran77 on 2011-12-16
Thanks, this thread helped me with my problem.

---

