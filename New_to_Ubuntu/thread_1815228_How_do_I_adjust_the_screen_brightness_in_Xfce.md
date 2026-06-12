---
title: "How do I adjust the screen brightness in Xfce?"
date: 2011-07-30
forum: New to Ubuntu
---

### Post by raginkestrel on 2011-07-30
I recently installed Xubuntu on an old Sony Vaio laptop.  I normally would use the function keys to adjust the screen brightness, but they do not work. I checked the settings menu, but the only option I found was to adjust the brightness of the desktop background. How can I adjust the brightness of the entire screen?

---

### Post by Toz on 2011-07-30
What model of Vaio do you have? Have you tried the **acpi_backlight=vendor** kernel parameter? For instructions on how to test it, see: [https://help.ubuntu.com/community/Grub2#Editing the GRUB 2 Menu During Boot]("https://help.ubuntu.com/community/Grub2#Editing the GRUB 2 Menu During Boot")

If that doesn't work, open a terminal window (Accessories->Terminal Emulator), type in the following command and post back the results:
```
lspci -vnn
```

---

### Post by raginkestrel on 2011-07-31
Hi Toz,

Thank you for your help.  The model number is: PCG-7G2L.  I added the entry to the grub menu and I still cannot change the brightness via the function keys.

I entered the command and here are the results:

00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)
	Subsystem: Sony Corporation Vaio VGN-S3XP [104d:81b7]
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2592] (rev 03) (prog-if 00 [VGA controller])
	Subsystem: Sony Corporation Device [104d:81b8]
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at b0080000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 1800 [size=8]
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Memory at b0040000 (32-bit, non-prefetchable) [size=256K]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: intelfb, i915

00:02.1 Display controller [0380]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2792] (rev 03)
	Subsystem: Sony Corporation Device [104d:81b8]
	Flags: fast devsel
	Memory at 44000000 (32-bit, non-prefetchable) [disabled] [size=512K]
	Capabilities: <access denied>

00:1b.0 Audio device [0403]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller [8086:2668] (rev 03)
	Subsystem: Sony Corporation Device [104d:81bb]
	Flags: bus master, fast devsel, latency 0, IRQ 40
	Memory at b0000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03) (prog-if 00 [UHCI])
	Subsystem: Sony Corporation Device [104d:81b9]
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 1820 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03) (prog-if 00 [UHCI])
	Subsystem: Sony Corporation Device [104d:81b9]
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1840 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03) (prog-if 00 [UHCI])
	Subsystem: Sony Corporation Device [104d:81b9]
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 1860 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03) (prog-if 00 [UHCI])
	Subsystem: Sony Corporation Device [104d:81b9]
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1880 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03) (prog-if 20 [EHCI])
	Subsystem: Sony Corporation Device [104d:81b9]
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at b0004000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d3) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=0a, sec-latency=32
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: b0100000-b01fffff
	Prefetchable memory behind bridge: 0000000040000000-0000000043ffffff
	Capabilities: <access denied>

00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 03)
	Subsystem: Sony Corporation Device [104d:81b9]
	Flags: bus master, medium devsel, latency 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [8086:266f] (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Sony Corporation Device [104d:81b9]
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1810 [size=16]
	Kernel driver in use: ata_piix

00:1f.3 SMBus [0c05]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [8086:266a] (rev 03)
	Subsystem: Sony Corporation Device [104d:81b9]
	Flags: medium devsel, IRQ 10
	I/O ports at 18a0 [size=32]
	Kernel modules: i2c-i801

06:03.0 CardBus bridge [0607]: Texas Instruments PCI7420 CardBus Controller [104c:ac8e]
	Subsystem: Sony Corporation Device [104d:818f]
	Flags: bus master, medium devsel, latency 168, IRQ 16
	Memory at b0108000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=06, secondary=07, subordinate=0a, sec-latency=176
	Memory window 0: 40000000-43fff000 (prefetchable)
	Memory window 1: 48000000-4bfff000
	I/O window 0: 00002400-000024ff
	I/O window 1: 00002800-000028ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

06:03.2 FireWire (IEEE 1394) [0c00]: Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller [104c:802e] (prog-if 10 [OHCI])
	Subsystem: Sony Corporation Device [104d:818f]
	Flags: bus master, medium devsel, latency 32, IRQ 18
	Memory at b0104000 (32-bit, non-prefetchable) [size=2K]
	Memory at b0100000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: firewire_ohci
	Kernel modules: firewire-ohci

06:03.3 Mass storage controller [0180]: Texas Instruments PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller [104c:ac8f]
	Subsystem: Sony Corporation Device [104d:8190]
	Flags: bus master, medium devsel, latency 57, IRQ 17
	Memory at b0105000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: tifm_7xx1
	Kernel modules: tifm_7xx1

06:04.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
	Subsystem: Intel Corporation Device [8086:2751]
	Flags: bus master, medium devsel, latency 32, IRQ 22
	Memory at b0106000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ipw2200
	Kernel modules: ipw2200

06:08.0 Ethernet controller [0200]: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile [8086:1068] (rev 03)
	Subsystem: Sony Corporation Device [104d:81d0]
	Flags: bus master, medium devsel, latency 66, IRQ 20
	Memory at b0107000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 2000 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: e100
	Kernel modules: e100

:confused: I hope this helps.  Is there an application that can change the screen brightness?

---

### Post by Toz on 2011-07-31
A few more things to try:

1. Also try the kernel parameters:
```
acpi_osi=Linux
acpi_osi=\"Linux\"
acpi_osi=Linux acpi_backlight=vendor
acpi_osi=
```

2. Try the sony_laptop module:
```
sudo modprobe sony_laptop
```

3. You have an intel video card. Kamal (a canonical kernel developer) has an intel-specific kernel that fixes the backlight issue with these video cards on some laptops. You may wish to give his kernel a try. See: [https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight]("https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight")

4. If still no luck, when you press the brightness function keys, do you get a notification bubble indicating that the brightness changed (but the brightness doesn't change)?

5. What do the following commands return?
```
sudo dmidecode -s system-product-name
```

---

### Post by raginkestrel on 2011-07-31
Hi Toz,

1. None of the parameters worked.

2. No Luck.

3. According to the page this kernel is only for Gnome or Unity.

4. I don't get any responses when I press the buttons.

5. Here is the return: VGN-FS850

This is strange, as everything else on this laptop works better on Xubuntu, except that the function keys don't work. Could something be blocking them?

---

### Post by Toz on 2011-07-31
> **raginkestrel said:**
> Hi Toz,

1. None of the parameters worked.

2. No Luck.

3. According to the page this kernel is only for Gnome or Unity.
It should work for xfce as well (he makes i915-specific changes to the kernel for the intel driver like you have). You won't be able to use the gnome utilities but the Fn keys might work. Could be worth a try.

> 4. I don't get any responses when I press the buttons.

5. Here is the return: VGN-FS850

This is strange, as everything else on this laptop works better on Xubuntu, except that the function keys don't work. Could something be blocking them?

Does this command do anything:
```
sudo setpci -s 00:02.0 F4.B=96
```

Another thing to try is to edit the udev keymap file and add your system (it doesn't look like it processes VGN-FS* systems):
```
sudo mousepad /lib/udev/rules.d/95-keymap.rules
```
search for:
> VGN-FW*
and replace it with:
```
VGN-FS*
```
reboot and see if there is a difference.

---

### Post by raginkestrel on 2011-08-01
[QUOTE=Toz;11106390]It should work for xfce as well (he makes i915-specific changes to the kernel for the intel driver like you have). You won't be able to use the gnome utilities but the Fn keys might work. Could be worth a try.

I will give this a try, as editing the keymap file did not work, neither did the "setpci" command.

I will be a little slower on responding during the week, but I have not given up! :)

---

### Post by raginkestrel on 2011-08-02
Hi Toz,

I installed the new kernel, but the function keys still do not work.  However, I noticed that the screen is now a little dimmer, and I don't feel like I am staring into the sun every time I look at it.  Any other options that you can think of?  Otherwise, this current brightness setting is workable.

---

### Post by Toz on 2011-08-02
With the new kernel, try: 
[LIST]
[*]the **acpi_backlight=vendor** kernel parameter again.
[*]the setpci command again ```
sudo setpci -s 00:02.0 F4.B=96
```
[*]install xbacklight (sudo apt-get install xbacklight) and try:
```
xbacklight -set 50
```
[/LIST]

---

### Post by raginkestrel on 2011-08-02
Hi Toz,

:D Success! I can adjust the brightness with xbacklight. Now I can finally say that I have resurrected this poor old laptop from Windows.  Plus, I learned a lot about Grub, installing a new kernel, and getting back to using the command line.  This was an excellent learning experience.  Thank you.

---

### Post by Toz on 2011-08-03
Glad to hear. You can also map your FN brightness keys to adjust the brightness using xbacklight. Let me know if you'd like a script that would do that for you.

---

### Post by raginkestrel on 2011-08-03
Hi Toz,

Absolutely.  If I could dim the screen by pressing FN+F5 and brighten it by pressing FN+F6 that would match the keys on my keyboard.

---

### Post by Toz on 2011-08-03
Try this (from a command prompt):

1. Create the script:
```
gksudo mousepad /usr/local/bin/brightness
```

2. Paste in this code:
```
#!/bin/bash

# constants - edit as required
UPPER=100
LOWER=0
INCREMENT=10
DECREMENT=10

# current xbacklight value
CURRENT=`xbacklight -get | sed -e 's/\..*//g'`
NEW=$CURRENT

case $1 in
	up)
		if [ $(($CURRENT+$INCREMENT)) -le $UPPER ]; then
			NEW=$(($CURRENT+$INCREMENT))
		fi
	;;
	down)
		if [ $(($CURRENT-$DECREMENT)) -ge $LOWER ]; then
			NEW=$(($CURRENT-$DECREMENT))
		fi
	;;
	*)
	;;
esac

# set the new backlight 
xbacklight -set $NEW

exit 0

```

3. Save the file.

4. Make it executable:
```
sudo chmod +x /usr/local/bin/brightness
```

5. Test it. From a command prompt, go nuts with the following two commands to see if it changes the brightness:
```
brightness up
brightness down
```

If it works without any problems, go to Settings Manager, Keyboard, Application Shortcuts tab and create shortcuts for your FN+F5 and FN+F6 keys for the commands "brightness up" and "brightness down".

If it doesn't work, post back any error messages that come up.

---

### Post by raginkestrel on 2011-08-04
Hi Toz,

There are no error messages, but nothing happens when I enter the command, "brightness up".  However, "brightness down" does work.

I tried to create the keyboard shortcut FN+F5 for the command "brightness down" but the "Shortcut Command" window that pops up when I press the "+Add" button only allows me to enter the command and not the shortcut.  Am I missing something? Shouldn't there be a prompt beside "Shortcut:" where I enter the keys?  I attached a screenshot, so you can see the window.

---

### Post by Toz on 2011-08-04
The brightness up command will only work if the brightness isn't at the maximum setting. Try brightness down a few times then brightness up. Does it work now?

To set the shortcuts, try the following:
1. Go to the Keyboard Shortcuts
2. Click the Add button and type in **brightness up** and press OK.
3. On the next screen, press Fn+F5 (or FN+F6) depending on which is the brightness up function key.
4. Repeat for brightness down.

---

### Post by raginkestrel on 2011-08-04
Hi Toz,

I used "brightness down" before using the "up" command.  I even set the backlight to 50% and the "up" command still doesn't work.

As for the shortcuts, I discovered that the "Fn" key is not being  recognized for some reason.  When I set the shortcut to "Ctrl+d" the "brightness down" command works.

---

### Post by Toz on 2011-08-04
I just verified that the script works on my system.

What happens when you type:
```
xbacklight -set 50
```
followed by:
```
xbacklight -set 100
```

Can you double-check that the script contents are correct?

EDIT: Also, can you do this:
1. Open a terminal window.
2. Run the command:```
acpi_listen
```
3. Then press your Brightness up FN key (FN+F6?)
4. Post back what is displayed in the terminal window
5. Then press your Brightness down FN key (FN+F5?)
6. Post back what is displayed in the terminal window

(source: [http://code.google.com/p/vaio-f11-linux/wiki/ProgrammableKeys]("http://code.google.com/p/vaio-f11-linux/wiki/ProgrammableKeys"))

---

### Post by 123662981 on 2011-08-04
Learned a lot&#65281;:D

---

### Post by raginkestrel on 2011-08-04
@123662981: You and me both!:)

@Toz: The "50" command dims the screen to 50% and the "100" command brings it back up to full brightness.

The script contents are exactly like you typed them.  I copied and pasted them into mousepad.

When I type "acpi_listen", nothing happens when I press Fn+F5 or F6.  When I press my shorcut, Ctrl+d, the green cursor blanks out and then returns to normal as the screen dims.

---

### Post by Toz on 2011-08-04
Looks like your system doesn't hear the function keys. Something else that needs to be investigated.

I've updated the script to include debugging info. Can you replace the current brightness script with this:
```
#!/bin/bash

# constants - edit as required
UPPER=100
LOWER=0
INCREMENT=10
DECREMENT=10

# current xbacklight value
CURRENT=`xbacklight -get | sed -e 's/\..*//g'`
NEW=$CURRENT

case $1 in
	up)
		echo "DEBUG: up selected"
		echo "DEBUG: up->CURRENT="$CURRENT
		if [ $(($CURRENT+$INCREMENT)) -le $UPPER ]; then
			NEW=$(($CURRENT+$INCREMENT))
		fi
		echo "DEBUG: up->NEW="$NEW
	;;
	down)
		echo "DEBUG: down selected"
		echo "DEBUG: down->CURRENT="$CURRENT
		if [ $(($CURRENT-$DECREMENT)) -ge $LOWER ]; then
			NEW=$(($CURRENT-$DECREMENT))
		fi
		echo "DEBUG: down->NEW="$NEW
	;;
	*)
	;;
esac

# set the new backlight
echo "DEBUG: beforeset->current_xbacklight="`xbacklight -get | sed -e 's/\..*//g'`
xbacklight -set $NEW
echo "DEBUG: afterset->current_xbacklight="`xbacklight -get | sed -e 's/\..*//g'`

exit 0
```

Then:
```
brightness down
```
.....post back results
```
brightness up
```
.....post back results

---

### Post by Toz on 2011-08-04
Can you also post back the results of:
```
lsmod
```

---

### Post by Toz on 2011-08-05
Just came across this link: [http://ubuntuforums.org/showthread.php?t=759150&highlight=vgn-fs]("http://ubuntuforums.org/showthread.php?t=759150&highlight=vgn-fs"). I know its a little old, but it might be worth a shot.

---

### Post by raginkestrel on 2011-08-05
Hi Toz,

My numbered function keys do work(eg. F5 in Chromium refreshes the page). It is when I press the "Fn" key and then press the numbered keys that they are ignored.

I set the brightness to 50%. Here is what comes back when I enter the "brightness down" command:
DEBUG: down selected
DEBUG: down->CURRENT=42
DEBUG: down->NEW=32
DEBUG: beforeset->current_xbacklight=42
DEBUG: afterset->current_xbacklight=28

Here is what comes back when I enter the "brightness up" command:
DEBUG: up selected
DEBUG: up->CURRENT=28
DEBUG: up->NEW=38
DEBUG: beforeset->current_xbacklight=28
DEBUG: afterset->current_xbacklight=28 :confused:

Now, I decided to raise the increment from 10 to 20 and...
It works! :D Why, I have no idea. Here is the debug info:
DEBUG: up selected
DEBUG: up->CURRENT=28
DEBUG: up->NEW=48
DEBUG: beforeset->current_xbacklight=28
DEBUG: afterset->current_xbacklight=42

---

### Post by Toz on 2011-08-05
That's good news. Set both the INCREMENT and DECREMENT values to 20. It must be that you have less than 10 backlight settings.

What does **lsmod** return?

---

### Post by raginkestrel on 2011-08-05
Hi Toz,

Here are the results for lsmod:

```
Module                  Size  Used by
xt_limit               12541  8 
xt_tcpudp              12531  7 
ipt_LOG                12784  8 
ipt_MASQUERADE         12663  0 
xt_DSCP                12549  0 
ipt_REJECT             12512  1 
nf_conntrack_irc       13138  0 
nf_conntrack_ftp       13106  0 
xt_state               12514  6 
cryptd                 19801  0 
aes_i586               16956  2 
aes_generic            38023  1 aes_i586
lib80211_crypt_ccmp    12785  2 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_realtek   255882  1 
snd_hda_intel          24140  4 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
i915                  446502  2 
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
ipw2200               145664  0 
snd_rawmidi            25269  1 snd_seq_midi
binfmt_misc            13213  1 
drm_kms_helper         40745  1 i915
acpi_igd_opregion      13574  1 i915
snd_seq_midi_event     14475  1 snd_seq_midi
libipw                 46641  1 ipw2200
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
tifm_sd                17415  0 
pcmcia                 39671  0 
drm                   180037  4 i915,drm_kms_helper,acpi_igd_opregion
snd_timer              28659  2 snd_pcm,snd_seq
joydev                 17322  0 
cfg80211              156212  2 ipw2200,libipw
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
iptable_nat            12977  0 
nf_nat                 24827  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19024  9 iptable_nat,nf_nat
tifm_7xx1              12898  0 
nf_conntrack           69744  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
sony_laptop            34432  0 
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
iptable_mangle         12615  0 
iptable_filter         12706  1 
ip_tables              18125  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               21907  11 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,iptable_mangle,iptable_filter,ip_tables
snd                    55295  17 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           27230  0 
pcmcia_rsrc            18292  1 yenta_socket
tifm_core              15040  2 tifm_sd,tifm_7xx1
psmouse                73312  0 
i2c_algo_bit           13184  1 i915
soundcore              12600  1 snd
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
video                  18951  1 i915
serio_raw              12990  0 
lib80211               14570  3 lib80211_crypt_ccmp,ipw2200,libipw
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
firewire_ohci          31504  0 
firewire_core          56138  1 firewire_ohci
e100                   40108  0 
crc_itu_t              12627  1 firewire_core

```

I finally discovered the code tags. :)

---

### Post by Toz on 2011-08-05
I was looking to see if the sony_laptop module was running. Looks like it is. It's what makes the function keys work on viaos. For some reason ubuntu is not picking them up. Have you had a chance to try the solution from [http://ubuntuforums.org/showthread.php?t=759150&highlight=vgn-fs]("http://ubuntuforums.org/showthread.php?t=759150&highlight=vgn-fs")?

---

### Post by raginkestrel on 2011-08-05
I got a weird message from the Software Center when I tried to install the package.  It said "This package is of bad quality" and provided the following details:

```
Lintian check results for /home/david/Desktop/fsfn_2.1-1_i386.deb:
E: fsfn: wrong-file-owner-uid-or-gid debian-binary 1000/1000
E: fsfn: wrong-file-owner-uid-or-gid etc/ 1000/1000
E: fsfn: wrong-file-owner-uid-or-gid etc/fsfn.conf 1000/1000
E: fsfn: wrong-file-owner-uid-or-gid etc/init.d/ 1000/1000
E: fsfn: wrong-file-owner-uid-or-gid etc/init.d/fsfn 1000/1000
E: fsfn: wrong-file-owner-uid-or-gid usr/ 1000/1000
E: fsfn: wrong-file-owner-uid-or-gid usr/local/ 1000/1000
E: fsfn: wrong-file-owner-uid-or-gid usr/local/bin/ 1000/1000
E: fsfn: wrong-file-owner-uid-or-gid usr/local/bin/fsfn 1000/1000
E: fsfn: wrong-file-owner-uid-or-gid usr/local/share/ 1000/1000
E: fsfn: wrong-file-owner-uid-or-gid usr/local/share/man/ 1000/1000
E: fsfn: wrong-file-owner-uid-or-gid usr/local/share/man/man1/ 1000/1000
E: fsfn: wrong-file-owner-uid-or-gid usr/local/share/man/man1/fsfn.1 1000/1000
E: fsfn: wrong-file-owner-uid-or-gid usr/local/share/man/man5/ 1000/1000
E: fsfn: wrong-file-owner-uid-or-gid usr/local/share/man/man5/fsfn.5 1000/1000

```

---

### Post by Toz on 2011-08-05
I guess not - too old. That package hasn't been updated since then either.

I'm sorry, but I'm out of ideas for getting the Fn keys to work. Perhaps you should create a bug report (like this one: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/691826]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/691826")) and see if you can get a solution there.

---

### Post by raginkestrel on 2011-08-05
Hi Toz,

I am not worried about it.  The only keys I needed were the ones to adjust the backlight, and I now have those set to "Ctrl d" and "Crtl u". The other keys, zoom, volume control, sleep, etc., I always control by software; even on my netbook which does have a working Fn key. Thank you for your help. It is a relief being able to look at the screen without sunglasses! :)

---

### Post by Toz on 2011-08-06
Is your numlock enabled (on)? If so, try disabling it then try the function keys on their own.

and, open a terminal window, type in :
```
acpi_listen
```
then press the function keys with and without the numlock on. Do you get any response on the terminal when you press these keys?

---

### Post by raginkestrel on 2011-08-06
Hi Toz,

I never have "Num Lk" on, as there isn't a separate keypad. Sony basically put a pseudo keypad in the middle of the keyboard which is a pain to use. 

There is no response on "acpi_listen" when I press the "Fn" key with or without the "Num Lk" on.

I am not worried about the "Fn" key not working.  The only two keys I ever use are the backlight controls and that has been fixed with the keyboard shortcuts.

---

### Post by Toz on 2011-08-06
Ok. I was just curious because I just remembered that on my other notebook, a toshiba, the Fn keys only work if the Numlock is off.

---

### Post by velko on 2012-06-25
here is a tiny script that I save as "xb" somewhere in my PATH and use like:

xb 10

The arg is from 0 to 100.


```
#!/bin/bash


#xbacklight -set $1

file="/sys/class/backlight/intel_backlight/brightness"

b="4648"

min="0"
max="4648"

steps="100"

step="$1"

if [[ -z $step ]]
then step=50
fi


b=`calc "int($min + ($max-$min)*$step/$steps + 0.5)"`

#echo $b; exit

echo $b | sudo tee $file >/dev/null

```



----


it relies on the system's brightness file residing in

/sys/class/backlight/intel_backlight/brightness


to find out - go to /sys/class/backlight and see whats in there...


try seeing if you can find a brightness file in there and see what are the min/max vals in there when you use the fn keys...

Also note : I use the 

GRUB_CMDLINE_LINUX_DEFAULT="quiet nosplash  acpi_backlight=vendor"

line in my 

/etc/default/grub file

you put this acpi_backlight=vendor in there and then sudo update-grub

and reboot...

---

