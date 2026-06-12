---
title: "Wi-Fi is disabled by hardware switch - HP Pavilion"
date: 2013-10-01
forum: Networking &amp; Wireless
---

### Post by Mitchell_Herndon on 2013-10-01
Hello, I just installed ubuntu 13.04 yesterday on my HP Pavilion m7 (dual-booting with Windows 8), and I haven't been able to connect to wireless in ubuntu since. I know this is a common problem in the forums, but I've been at it for a day without any luck, so I figured I might need some more specific help. 
The network menu says "Wi-Fi is disabled by hardware switch." I have a wireless hardware switch on my f12 key, which lights up orange when it's turned off, and white when it's on. When I boot into Windows it lights up white by itself and wireless works fine, but going into ubuntu just stays orange. Pressing the button has no response in ubuntu. 
I tried rfkill list all in terminal and here are the results:

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

Rfkill unblock all has no effect either. I've also tried various things on the forums but none of them seem to do anything so far. Please help!

Thank you,
Mitch

---

### Post by varunendra on 2013-10-03
Welcome to the forums Mitch !

Sometimes the hardware switch problem may also be an indication that you don't have the required driver loaded for your card. To let us see the wireless card and version of the kernel, please post back the outputs of -
```
uname -mr
lspci -nnk | grep -iA2 net
```

While posting the outputs, please use the '**Code**' box. It preserves its formatting and makes your post cleaner, compact and more readable. Follow the "Using Code Tags" link in my signature to see how.

---

### Post by grahammechanical on 2013-10-03
When using Windows do you switch wireless off and then shutdown Windows? Sometimes, so I have read, this prevents wireless from working in Ubuntu because Ubuntu does not have any mechanism for over-riding that switch off by Windows. I think we need the wireless adapter to be switched on and working before we load Ubuntu.

Regards.

---

### Post by Mitchell_Herndon on 2013-10-03
Thanks for the replies!
Here's the output.
```

mitch@:~$ uname -mr
3.8.0-31-generic x86_64
mitch@:~$ lspci -nnk | grep -iA2 net
04:00.0 Network controller [0280]: Ralink corp. Device [1814:539a]
	Subsystem: Hewlett-Packard Company Device [103c:1839]
	Kernel driver in use: rt2800pci
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 07)
	Subsystem: Hewlett-Packard Company Device [103c:1818]
	Kernel driver in use: r8169

```

I never manually switch off wireless in Windows. However, every time I boot up the switch is orange until some point in the Windows boot. It just stays orange if I choose to boot into ubuntu.

---

### Post by Mitchell_Herndon on 2013-10-03
Hey guys, just discovered something strange.


When I unplugged my ethernet cable and suspended my computer, then opened it back up the wifi was magically working just fine! I rebooted to see if it would stay on, and it didn't. However, I replicated the process and found that it works every time I suspend and then open back up. 
I'm glad I have some sort of wireless connection, but I would rather not have to suspend every time I want to use wifi. Any ideas?


Thanks!

---

### Post by varunendra on 2013-10-04
> **Mitchell_Herndon said:**
> found that it works every time I suspend and then open back up.....Any ideas?

Oh no, not in HP please ! First Acer, then Asus, now in HP too?? What is going on here.. (asking to myself) [COLOR="#808080"](and to the developers)[/COLOR]

I may have *some* idea, but is really very vague and possibly misleading. It *may* become clearer with some more info.

Does the hardware switch (Fn+<whatever>) work if you keep the Ethernet cable unplugged all the while? Some BIOS (especially some HP models) have a setting to automatically disable wifi if an Ethernet connection is detected. So try a few reboots without the cable plugged in, and check the BIOS to see if you can find such setting (if you can, there should be option to turn this 'feature' off).

Also, don't trust what is marked on those F1....F12 keys. Although it's been a long time now, we have had threads where it turned out to be a different key for wifi than what is marked as such. For example, despite F12 having the wifi symbol, sometimes F5 or F9 (just examples) may work as hardware switch for wifi. This was especially reported with HP/Compaq laptops.

These keys may behave differently in Windows (do what they are marked as), but in Linux, they got crazy in some models (most probably due to incompatibility with the WMI driver). One more of this craziness is - on some models (I've personally witnessed this more than once), the F1....F12 keys perform their primary function when pressed in combination with Fn key, while the secondary function without it (by default it should be opposite of this). So if you think Fn+F12 is the key for wifi, try F12 alone (without Fn).

Fortunate you are that you don't have one of those "touch-type" hardware switches that HP proudly features, otherwise one of my suggestions would have included - "take a sledge hammer and....." *(okay, let's leave this one alone)*.

Please so some experiments as suggested above (except the sledge hammer) and when you are confident that your model does not suffer any of such bugs, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates. That should be able to give us more clue on the software part.

---

### Post by Mitchell_Herndon on 2013-10-04
Did a few experiments, and ended up pretty confident that none of those bugs are relevant to my problem. I ran the script you suggested, here are the results:

[http://pastebin.ubuntu.com/6194240/](http://pastebin.ubuntu.com/6194240/)

---

### Post by varunendra on 2013-10-04
The NetworkManager.conf block is empty? Did you manually remove the block (nothing sensitive is there), or does it not exist in your system at all?

Please check if it exists, and post back the output if it does -
```
cat /etc/NetworkManager/NetworkManager.conf
```

Although I don't think it can cause or affect the "hard block" state, it not being there is strange.

Also, please download an **alternate** version of the **wireless_script** from the bottom link of the same post linked in my signature, and run it after a fresh reboot, when the wifi seems to be soft-blocked. The current report is from when it is enabled. I also need to see the state when it is hard-blocked after a fresh boot, and the alternate script is a little more verbose.

---

### Post by Mitchell_Herndon on 2013-10-04
I removed NetworkManager.conf yesterday while trying to solve the problem. Apparently for one person, removing it and then doing the rfkill unblock all command solved his problem, although it didn't seem to affect anything for me.
Wifi was never in a soft-blocked state, but here's the output while hard-blocked after a fresh boot:
[http://pastebin.ubuntu.com/6194434/](http://pastebin.ubuntu.com/6194434/)

---

### Post by varunendra on 2013-10-05
Sorry to bother you again with (almost) the same thing, but you used the same script again, and the result contains even less information (naturally, since it is from a fresh boot with lesser activity).

Please download and run this one instead : [http://dl.dropboxusercontent.com/s/qjc87hzk1z5x6z0/wireless_script](http://dl.dropboxusercontent.com/s/qjc87hzk1z5x6z0/wireless_script)

It covers *slightly* more info, especially in the dmesg and lsmod parts. Those are the areas where I expect to get some useful hints. So far we have none. I could ask you for outputs of specific commands, but running the script is just as easy (you already know that) and the output is more comprehensive.

Let's hope it give us something significant.

---

### Post by Mitchell_Herndon on 2013-10-05
Sorry about that. Here's the new output:
[http://pastebin.ubuntu.com/6197908/](http://pastebin.ubuntu.com/6197908/)
Thanks for all the help so far! I'd be lost without it :D

---

### Post by Mitchell_Herndon on 2013-10-05
Also, and I don't know if this is relevant at all, on boot up my screen says:
kvm: disabled by bios

Could this be related at all to my wifi problem?

---

### Post by varunendra on 2013-10-06
Nope, still no hints. But be assured - the "kvm: disabled by bios" message is not related. It is a BIOS bug which is mostly harmless and so is the message.

Please try a couple of wild shots -
```
sudo modprobe -rv rt2800pci
sudo morprobe -v rt2800pci
```
Does it make the hard block go away? If not, try this -
```
echo "blacklist hp_wmi[COLOR="#FF0000"]"[/COLOR] | sudo tee -a /etc/modprobe.d/blacklist.conf
```
[COLOR="#FF0000"](EDIT: Forgot the closing double-quote ("))[/COLOR]
This will add the hp_wmi driver to blacklist file. Doing so may break some Fn+ key functions from next boot, so consider this a test. If it works, we can then decide whether to keep it blacklisted or not depending on whether it really affects any Fn+ functions.

Reboot to see if it helps or not. If not, check to make sure it is not loaded -
```
lsmod | grep wmi
```
you shouldn't get any output from above. If you do, report back.

If the above check confirms that hp_wmi (or wmi) is not loaded (returns blank output) and the wifi is still hard blocked, remove it from blacklist -
```
sudo sed -i '/hp_wmi/ d' /etc/modprobe.d/blacklist.conf
```
..and do a suspend --> resume cycle to enable wifi, then immediately after the it is enabled, run dmesg -
```
dmesg | tail -40
```
..and post back its output.

---

### Post by Mitchell_Herndon on 2013-10-06
Those first two did not make the hard block go away. The third command just started a prompt inside the terminal. Was that quote at the beginning misplaced, or is there more I'm supposed to type for that command?
I rebooted anyway to check and the lsmod command printed a bunch of stuff:
```

mitch@Alan:~$ lsmod | grep wmi
snd_rawmidi            30180  1 snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
wmi                    19070  0 
snd                    68876  16 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device

```

---

### Post by varunendra on 2013-10-06
> **Mitchell_Herndon said:**
> The third command just started a prompt inside the terminal. Was that quote at the beginning misplaced

Oops! Yeah, it was a mistake, a closing double-quote was supposed to be after "hp_wmi". Just corrected that, sorry for the typo..

The wrong command would have done nothing, so please try again and let me know the result after reboot. (the correct command will just echo back the word "hp_wmi" in the terminal, while writing it in the conf file in the background).

**EDIT:**
Please also post back the output of -
```
cat /etc/modprobe.d/blacklist.conf
```
to make sure there is no funny line in it, written because of my mistake earlier..

---

### Post by Mitchell_Herndon on 2013-10-06
Still no luck. I got the following from lsmod | grep wmi after a fresh reboot:
```

mitch@Alan:~$ lsmod | grep wmisnd_rawmidi            30180  1 snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd                    68876  16 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
wmi                    19070  0 

```

Here's the output of the cat command (also after a fresh reboot): [http://pastebin.ubuntu.com/6202880/](http://pastebin.ubuntu.com/6202880/)

---

### Post by varunendra on 2013-10-06
> **Mitchell_Herndon said:**
> ```

wmi                    19070  0 

```

Hmm.. I wonder what wmi is now loaded for. But lets first take a look at dmesg, as I mentioned in post 13 -
> do a suspend --> resume cycle to enable wifi, then immediately after the it is enabled, run dmesg -
```
dmesg | tail -40
```
..and post back its output.
..assuming a suspend --> resume still does enable the wifi.

---

### Post by Mitchell_Herndon on 2013-10-06
Yep, still does! Here's the output:
```

mitch@Alan:~$ dmesg | tail -40
[   48.062715] smpboot: Booting Node 0 Processor 6 APIC 0x6
[   48.076516] CPU6 is up
[   48.076576] smpboot: Booting Node 0 Processor 7 APIC 0x7
[   48.090424] CPU7 is up
[   48.097330] ACPI: Waking up from system sleep state S3
[   48.640413] xhci_hcd 0000:00:14.0: System wakeup disabled by ACPI
[   48.672393] ehci-pci 0000:00:1a.0: System wakeup disabled by ACPI
[   48.704373] ehci-pci 0000:00:1d.0: System wakeup disabled by ACPI
[   48.768437] PM: noirq resume of devices complete after 159.992 msecs
[   48.768534] PM: early resume of devices complete after 0.074 msecs
[   48.768562] i915 0000:00:02.0: setting latency timer to 64
[   48.768566] xhci_hcd 0000:00:14.0: setting latency timer to 64
[   48.768575] ehci-pci 0000:00:1a.0: setting latency timer to 64
[   48.768613] ehci-pci 0000:00:1d.0: setting latency timer to 64
[   48.768614] ahci 0000:00:1f.2: setting latency timer to 64
[   48.768772] mei 0000:00:16.0: irq 44 for MSI/MSI-X
[   48.768794] snd_hda_intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   48.992325] usb 1-1.3: reset high-speed USB device number 4 using ehci-pci
[   49.032249] r8169 0000:05:00.0: System wakeup disabled by ACPI
[   49.096110] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   49.099989] ata5.00: configured for UDMA/100
[   49.156251] usb 1-1.1: reset full-speed USB device number 3 using ehci-pci
[   50.771581] [drm] Enabling RC6 states: RC6 on, RC6p on, RC6pp off
[   50.879324] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   51.149768] ata1.00: configured for UDMA/133
[   51.163243] sd 0:0:0:0: [sda] Starting disk
[   53.050192] i8042 kbd 00:07: System wakeup disabled by ACPI
[   53.059356] PM: resume of devices complete after 4293.020 msecs
[   53.074304] Restarting tasks ... done.
[   53.075810] video LNXVIDEO:00: Restoring backlight state
[   53.366512] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   53.491958] r8169 0000:05:00.0 eth0: link down
[   53.491998] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   55.721401] wlan0: authenticate with 00:1a:1e:83:7a:22
[   55.737764] wlan0: send auth to 00:1a:1e:83:7a:22 (try 1/3)
[   55.741183] wlan0: authenticated
[   55.744683] wlan0: associate with 00:1a:1e:83:7a:22 (try 1/3)
[   55.749213] wlan0: RX AssocResp from 00:1a:1e:83:7a:22 (capab=0x421 status=0 aid=3)
[   55.749334] wlan0: associated
[   55.749359] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

```

---

### Post by varunendra on 2013-10-06
Looks like we missed some initial messages even in 40 lines. Please reboot (so that wifi is originally blocked), suspend --> resume, and post back -
```
dmesg | tail -80
cat /var/log/syslog | tail -80
```
With the number of lines being 80 and syslog also included, obviously we are getting desperate and aggressive ! X(

If it looks like we are still missing some initial messages after resume in syslog (dmesg will certainly be covered this time), make it even higher for syslog.

---

### Post by Mitchell_Herndon on 2013-10-06
Output to both: [http://pastebin.ubuntu.com/6203256/](http://pastebin.ubuntu.com/6203256/)

---

### Post by varunendra on 2013-10-07
Okay, dmesg is more than expected this time, but nothing that I can recognize as a hint. Syslog was apparently 3-4 times the size of dmesg, the messages in it are from the state when most of the resume process was finished. Although chances are very thin that the whole log since suspend may give us much of a hint either. So please try these on a fresh boot (some of the Linux guys might kill me for using the words "reboot", "fresh boot" so many times..!) -

```
sudo service network-manager stop
sudo service networking stop
sudo modprobe -rv rt2800pci
sudo modprobe -v rt2800pci
sudo service networking start
sudo service network-manager start
```
then check if the hard block is still there. It almost certainly will be, because I don't think these services have anything to do with a 'hard-block' state. Although I am still a little bit hopeful with the modprobe part.

Anyway, if (and it will) the above fails to remove the hard block, try this -
```
sudo modprobe -rv wmi
sudo modprobe -v wmi
```
any errors? If not, any improvement? If not, then time to take another (pretty hopeless) look at full logs this time. Reboot --> Suspend --> Resume (make sure wifi is up) and copy the full logs this time -
```
cp /var/log/{dmesg,syslog} Desktop/
```
This will copy the whole dmesg and syslog files to your desktop. Pastebin both and post the link.

---

### Post by Mitchell_Herndon on 2013-10-07
The sudo service networking stop made the OS crash and I had to reboot, and I'm assuming those modprobes don't do anything unless the networking stop command works.
The other two modprobes gave me this output:
```

mitch@Alan:~$ sudo modprobe -rv wmi
rmmod wmi
mitch@Alan:~$ sudo modprobe -v wmi
insmod /lib/modules/3.8.0-31-generic/kernel/drivers/platform/x86/wmi.ko 
mitch@Alan:~$ 

```

and here are the full dmesg and syslog files: [http://pastebin.ubuntu.com/6206931/](http://pastebin.ubuntu.com/6206931/)

---

### Post by varunendra on 2013-10-10
> **Mitchell_Herndon said:**
> The sudo service networking stop made the OS crash and I had to reboot
That's weird !:-k

Anyway, I closely looked at the logs (yup, I really did!) and followed 'everything' that looked like a possible hint (yup, I honestly did that too!!). While some looked promising at beginning, with already reported bugs, they turned out to be red herrings after digging deeper. So for now, just quoting back here, for my own reference, whatever looked significant to me (stripped out apparently irrelevant 'parts' and entirely what looked like part from previous boots) -
```
syslog:
Oct  7 14:46:01 Alan kernel: imklog 5.8.11, log source = /proc/kmsg started.
<snip>
Oct  7 14:46:01 Alan kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-31-generic root=UUID=32fdbc71-9633-44ed-a8ed-cdd89bab91b2 ro quiet splash [COLOR="#FF0000"]vt.handoff=7[/COLOR]
<snip>
Oct  7 14:46:01 Alan kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-31-generic root=UUID=32fdbc71-9633-44ed-a8ed-cdd89bab91b2 ro quiet splash [COLOR="#FF0000"]vt.handoff=7[/COLOR]
<snip> **[COLOR="#0000CD"]# Some suspicious acpi errors/notifications here, although may be unrelated to the hard-block issue[/COLOR]**
Oct  7 14:46:01 Alan kernel: [    0.218562] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
Oct  7 14:46:01 Alan kernel: [    0.218564] ACPI: bus type pci registered
<snip>
Oct  7 14:46:01 Alan kernel: [    0.240880] ACPI: Executed 1 blocks of module-level executable AML code
Oct  7 14:46:01 Alan kernel: [    0.243047] ACPI Error: No handler for Region [RAM_] (ffff880243837798) [EmbeddedControl] (20121018/evregion-376)
Oct  7 14:46:01 Alan kernel: [    0.243051] ACPI Error: Region EmbeddedControl (ID=3) has no handler (20121018/exfldio-305)
Oct  7 14:46:01 Alan kernel: [    0.243053] ACPI Error: Method parse/execution failed [\_SB_.ACCL._STA] (Node ffff88024386f4d8), AE_NOT_EXIST (20121018/psparse-537)
Oct  7 14:46:01 Alan kernel: [    0.243058] ACPI Error: Method execution failed [\_SB_.ACCL._STA] (Node ffff88024386f4d8), AE_NOT_EXIST (20121018/uteval-103)
Oct  7 14:46:01 Alan kernel: [    0.243366] ACPI: SSDT 00000000aae3a018 0083B (v01  PmRef  Cpu0Cst 00003001 INTL 20121220)
Oct  7 14:46:01 Alan kernel: [    0.243666] ACPI: Dynamic OEM Table Load:
Oct  7 14:46:01 Alan kernel: [    0.243668] ACPI: SSDT           (null) 0083B (v01  PmRef  Cpu0Cst 00003001 INTL 20121220)
Oct  7 14:46:01 Alan kernel: [    0.243875] ACPI: SSDT 00000000aaeada98 00303 (v01  PmRef    ApIst 00003000 INTL 20121220)
Oct  7 14:46:01 Alan kernel: [    0.244196] ACPI: Dynamic OEM Table Load:
Oct  7 14:46:01 Alan kernel: [    0.244198] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20121220)
Oct  7 14:46:01 Alan kernel: [    0.244317] ACPI: SSDT 00000000aabadd98 00119 (v01  PmRef    ApCst 00003000 INTL 20121220)
Oct  7 14:46:01 Alan kernel: [    0.244617] ACPI: Dynamic OEM Table Load:
Oct  7 14:46:01 Alan kernel: [    0.244619] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20121220)
Oct  7 14:46:01 Alan kernel: [    1.595573] ACPI: Interpreter enabled
Oct  7 14:46:01 Alan kernel: [    1.595576] ACPI: (supports S0 S3 S4 S5)
Oct  7 14:46:01 Alan kernel: [    1.595591] ACPI: Using IOAPIC for interrupt routing
Oct  7 14:46:01 Alan kernel: [    1.617126] ACPI: EC: GPE storm detected(9 GPEs), transactions will use polling mode
Oct  7 14:46:01 Alan kernel: [    1.689504] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
Oct  7 14:46:01 Alan kernel: [    1.689710] ACPI: ACPI Dock Station Driver: 1 docks/bays found
Oct  7 14:46:01 Alan kernel: [    1.689713] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Oct  7 14:46:01 Alan kernel: [    1.689896] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
Oct  7 14:46:01 Alan kernel: [    1.689898] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Oct  7 14:46:01 Alan kernel: [    1.690042] [COLOR="#FF0000"]\_SB_.PCI0:_OSC invalid UUID[/COLOR]
Oct  7 14:46:01 Alan kernel: [    1.690043] _OSC request data:1 8 0 
Oct  7 14:46:01 Alan kernel: [    1.690386] PCI host bridge to bus 0000:00
Oct  7 14:46:01 Alan kernel: [    1.690388] pci_bus 0000:00: root bus resource [bus 00-fe]
Oct  7 14:46:01 Alan kernel: [    1.690390] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
Oct  7 14:46:01 Alan kernel: [    1.690391] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
Oct  7 14:46:01 Alan kernel: [    1.690392] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
Oct  7 14:46:01 Alan kernel: [    1.690394] pci_bus 0000:00: root bus resource [mem 0xafa00000-0xfeafffff]
Oct  7 14:46:01 Alan kernel: [    1.690402] pci 0000:00:00.0: [8086:0154] type 00 class 0x060000
Oct  7 14:46:01 Alan kernel: [    1.690431] pci 0000:00:02.0: [8086:0166] type 00 class 0x030000
Oct  7 14:46:01 Alan kernel: [    1.690440] pci 0000:00:02.0: reg 10: [mem 0xc2000000-0xc23fffff 64bit]
Oct  7 14:46:01 Alan kernel: [    1.690445] pci 0000:00:02.0: reg 18: [mem 0xb0000000-0xbfffffff 64bit pref]
Oct  7 14:46:01 Alan kernel: [    1.690449] pci 0000:00:02.0: reg 20: [io  0x4000-0x403f]
Oct  7 14:46:01 Alan kernel: [    1.690495] pci 0000:00:14.0: [8086:1e31] type 00 class 0x0c0330
Oct  7 14:46:01 Alan kernel: [    1.690516] pci 0000:00:14.0: reg 10: [mem 0xc2600000-0xc260ffff 64bit]
Oct  7 14:46:01 Alan kernel: [    1.690583] pci 0000:00:14.0: PME# supported from D3hot D3cold
Oct  7 14:46:01 Alan kernel: [    1.690606] pci 0000:00:16.0: [8086:1e3a] type 00 class 0x078000
Oct  7 14:46:01 Alan kernel: [    1.690628] pci 0000:00:16.0: reg 10: [mem 0xc2614000-0xc261400f 64bit]
Oct  7 14:46:01 Alan kernel: [    1.690700] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
Oct  7 14:46:01 Alan kernel: [    1.690732] pci 0000:00:1a.0: [8086:1e2d] type 00 class 0x0c0320
Oct  7 14:46:01 Alan kernel: [    1.690752] pci 0000:00:1a.0: reg 10: [mem 0xc2619000-0xc26193ff]
Oct  7 14:46:01 Alan kernel: [    1.690837] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
Oct  7 14:46:01 Alan kernel: [    1.690863] pci 0000:00:1b.0: [8086:1e20] type 00 class 0x040300
Oct  7 14:46:01 Alan kernel: [    1.690877] pci 0000:00:1b.0: reg 10: [mem 0xc2610000-0xc2613fff 64bit]
Oct  7 14:46:01 Alan kernel: [    1.690940] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Oct  7 14:46:01 Alan kernel: [    1.690967] pci 0000:00:1c.0: [8086:1e10] type 01 class 0x060400
Oct  7 14:46:01 Alan kernel: [    1.691094] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Oct  7 14:46:01 Alan kernel: [    1.691131] pci 0000:00:1c.1: [8086:1e12] type 01 class 0x060400
Oct  7 14:46:01 Alan kernel: [    1.691259] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Oct  7 14:46:01 Alan kernel: [    1.691299] pci 0000:00:1c.3: [8086:1e16] type 01 class 0x060400
Oct  7 14:46:01 Alan kernel: [    1.691425] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
Oct  7 14:46:01 Alan kernel: [    1.691459] pci 0000:00:1c.5: [8086:1e1a] type 01 class 0x060400
Oct  7 14:46:01 Alan kernel: [    1.691533] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
Oct  7 14:46:01 Alan kernel: [    1.691562] pci 0000:00:1d.0: [8086:1e26] type 00 class 0x0c0320
Oct  7 14:46:01 Alan kernel: [    1.691581] pci 0000:00:1d.0: reg 10: [mem 0xc2618000-0xc26183ff]
Oct  7 14:46:01 Alan kernel: [    1.691666] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
Oct  7 14:46:01 Alan kernel: [    1.691690] pci 0000:00:1f.0: [8086:1e57] type 00 class 0x060100
Oct  7 14:46:01 Alan kernel: [    1.691808] pci 0000:00:1f.2: [8086:282a] type 00 class 0x010400
Oct  7 14:46:01 Alan kernel: [    1.691825] pci 0000:00:1f.2: reg 10: [io  0x4088-0x408f]
Oct  7 14:46:01 Alan kernel: [    1.691832] pci 0000:00:1f.2: reg 14: [io  0x4094-0x4097]
Oct  7 14:46:01 Alan kernel: [    1.691840] pci 0000:00:1f.2: reg 18: [io  0x4080-0x4087]
Oct  7 14:46:01 Alan kernel: [    1.691847] pci 0000:00:1f.2: reg 1c: [io  0x4090-0x4093]
Oct  7 14:46:01 Alan kernel: [    1.691855] pci 0000:00:1f.2: reg 20: [io  0x4060-0x407f]
Oct  7 14:46:01 Alan kernel: [    1.691863] pci 0000:00:1f.2: reg 24: [mem 0xc2617000-0xc26177ff]
Oct  7 14:46:01 Alan kernel: [    1.691904] pci 0000:00:1f.2: PME# supported from D3hot
Oct  7 14:46:01 Alan kernel: [    1.691920] pci 0000:00:1f.3: [8086:1e22] type 00 class 0x0c0500
Oct  7 14:46:01 Alan kernel: [    1.691933] pci 0000:00:1f.3: reg 10: [mem 0xc2615000-0xc26150ff 64bit]
Oct  7 14:46:01 Alan kernel: [    1.691953] pci 0000:00:1f.3: reg 20: [io  0x4040-0x405f]
Oct  7 14:46:01 Alan kernel: [    1.692047] pci 0000:00:1c.0: PCI bridge to [bus 01]
Oct  7 14:46:01 Alan kernel: [    1.692221] pci 0000:02:00.0: [10ec:5229] type 00 class 0xff0000
Oct  7 14:46:01 Alan kernel: [    1.692286] pci 0000:02:00.0: reg 10: [mem 0xc1000000-0xc1000fff]
Oct  7 14:46:01 Alan kernel: [    1.692771] pci 0000:02:00.0: supports D1 D2
Oct  7 14:46:01 Alan kernel: [    1.692772] pci 0000:02:00.0: PME# supported from D1 D2 D3hot
Oct  7 14:46:01 Alan kernel: [    1.697196] pci 0000:00:1c.1: PCI bridge to [bus 02-03]
Oct  7 14:46:01 Alan kernel: [    1.697204] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
Oct  7 14:46:01 Alan kernel: [    1.697211] pci 0000:00:1c.1:   bridge window [mem 0xc1000000-0xc1ffffff]
Oct  7 14:46:01 Alan kernel: [    1.697223] pci 0000:00:1c.1:   bridge window [mem 0xc0000000-0xc0ffffff 64bit pref]
Oct  7 14:46:01 Alan kernel: [    1.697360] **pci 0000:04:00.0: [COLOR="#FF0000"][1814:539a][/COLOR] type 00 class 0x028000**
Oct  7 14:46:01 Alan kernel: [    1.697388] pci 0000:04:00.0: reg 10: [mem 0xc2500000-0xc250ffff]
Oct  7 14:46:01 Alan kernel: [    1.705175] **pci 0000:00:1c.3: PCI bridge to [bus 04]**
Oct  7 14:46:01 Alan kernel: [    1.705187] pci 0000:00:1c.3:   bridge window [mem 0xc2500000-0xc25fffff]
Oct  7 14:46:01 Alan kernel: [    1.705302] pci 0000:05:00.0: [10ec:8168] type 00 class 0x020000
Oct  7 14:46:01 Alan kernel: [    1.705322] pci 0000:05:00.0: reg 10: [io  0x2000-0x20ff]
Oct  7 14:46:01 Alan kernel: [    1.705355] pci 0000:05:00.0: reg 18: [mem 0xc2404000-0xc2404fff 64bit pref]
Oct  7 14:46:01 Alan kernel: [    1.705375] pci 0000:05:00.0: reg 20: [mem 0xc2400000-0xc2403fff 64bit pref]
Oct  7 14:46:01 Alan kernel: [    1.705465] pci 0000:05:00.0: supports D1 D2
Oct  7 14:46:01 Alan kernel: [    1.705466] pci 0000:05:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Oct  7 14:46:01 Alan kernel: [    1.713158] pci 0000:00:1c.5: PCI bridge to [bus 05]
Oct  7 14:46:01 Alan kernel: [    1.713166] pci 0000:00:1c.5:   bridge window [io  0x2000-0x2fff]
Oct  7 14:46:01 Alan kernel: [    1.713182] pci 0000:00:1c.5:   bridge window [mem 0xc2400000-0xc24fffff 64bit pref]
Oct  7 14:46:01 Alan kernel: [    1.713267] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
Oct  7 14:46:01 Alan kernel: [    1.713288] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
Oct  7 14:46:01 Alan kernel: [    1.713307] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
Oct  7 14:46:01 Alan kernel: [    1.713326] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
Oct  7 14:46:01 Alan kernel: [    1.713389] [COLOR="#FF0000"]\_SB_.PCI0:_OSC invalid UUID[/COLOR]
Oct  7 14:46:01 Alan kernel: [    1.713389] _OSC request data:1 1f 0 
Oct  7 14:46:01 Alan kernel: [    1.713392]  [COLOR="#FF0000"]pci0000:00: ACPI _OSC support notification failed, disabling PCIe ASPM[/COLOR]
Oct  7 14:46:01 Alan kernel: [    1.713393]  pci0000:00: Unable to request _OSC control (_OSC support mask: 0x08)
Oct  7 14:46:01 Alan kernel: [    1.713789] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 10 11 12 14 15) *7
Oct  7 14:46:01 Alan kernel: [    1.713820] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 10 *11 12 14 15)
Oct  7 14:46:01 Alan kernel: [    1.713848] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
Oct  7 14:46:01 Alan kernel: [    1.713876] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 *10 11 12 14 15)
Oct  7 14:46:01 Alan kernel: [    1.713904] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
Oct  7 14:46:01 Alan kernel: [    1.713933] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 10 11 12 14 15) *7
Oct  7 14:46:01 Alan kernel: [    1.713961] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 *10 11 12 14 15)
Oct  7 14:46:01 Alan kernel: [    1.713989] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 10 *11 12 14 15)
<snip>
Oct  7 14:46:01 Alan kernel: [    1.948868] Simple Boot Flag at 0x44 set to 0x1
Oct  7 14:46:01 Alan kernel: [    1.949217] Initialise module verification
Oct  7 14:46:01 Alan kernel: [    1.949244] audit: initializing netlink socket (disabled)
<snip>
Oct  7 14:46:01 Alan kernel: [    2.002732] ACPI: AC Adapter [ADP1] (on-line)
Oct  7 14:46:01 Alan kernel: [    2.002850] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
Oct  7 14:46:01 Alan kernel: [    2.034710] ACPI: Lid Switch [LID0]
Oct  7 14:46:01 Alan kernel: [    2.034782] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Oct  7 14:46:01 Alan kernel: [    2.034785] ACPI: Power Button [PWRF]
<snip> **[COLOR="#0000CD"]# FS remounted here (all three times from previous boots).. errors on disk ?[/COLOR]**
Oct  7 14:46:01 Alan kernel: [    4.524752] sr 4:0:0:0: Attached scsi generic sg1 type 5
Oct  7 14:46:01 Alan kernel: [    4.525622]  sda: sda1 sda2 sda3 sda4
Oct  7 14:46:01 Alan kernel: [    4.526016] sd 0:0:0:0: [sda] Attached SCSI disk
Oct  7 14:46:01 Alan kernel: [   **[COLOR="#0000CD"] 5.385097[/COLOR]**] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: (null)
Oct  7 14:46:01 Alan kernel: [   **[COLOR="#FF0000"]15.938451[/COLOR]**] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro
Oct  7 14:46:01 Alan kernel: [   16.538389] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct  7 14:46:01 Alan kernel: [   16.805878] lp: driver loaded but no devices found
<snip>
Oct  7 14:46:01 Alan kernel: [   16.910015] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20121018/utaddress-251)
Oct  7 14:46:01 Alan kernel: [   16.910021] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Oct  7 14:46:01 Alan kernel: [   16.910025] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
Oct  7 14:46:01 Alan kernel: [   16.910028] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \_SB_.GPIO 2 (20121018/utaddress-251)
Oct  7 14:46:01 Alan kernel: [   16.910032] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Oct  7 14:46:01 Alan kernel: [   16.910033] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
Oct  7 14:46:01 Alan kernel: [   16.910036] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \_SB_.GPIO 2 (20121018/utaddress-251)
Oct  7 14:46:01 Alan kernel: [   16.910039] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Oct  7 14:46:01 Alan kernel: [   16.910041] lpc_ich: Resource conflict(s) found affecting gpio_ich
Oct  7 14:46:01 Alan kernel: [   16.921364] [drm] Memory usable by graphics device = 2048M
Oct  7 14:46:01 Alan kernel: [   16.921371] i915 0000:00:02.0: setting latency timer to 64
Oct  7 14:46:01 Alan kernel: [   16.923473] cfg80211: Calling CRDA to update world regulatory domain
Oct  7 14:46:01 Alan kernel: [   16.936216] microcode: CPU0 sig=0x306a9, pf=0x10, revision=0x15
Oct  7 14:46:01 Alan kernel: [   16.942421] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
Oct  7 14:46:01 Alan kernel: [   16.948483] i915 0000:00:02.0: irq 45 for MSI/MSI-X
Oct  7 14:46:01 Alan kernel: [   16.948491] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
Oct  7 14:46:01 Alan kernel: [   16.948493] [drm] Driver supports precise vblank timestamp query.
Oct  7 14:46:01 Alan kernel: [   16.948525] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
Oct  7 14:46:01 Alan bluetoothd[765]: Bluetooth daemon 4.101
Oct  7 14:46:01 Alan bluetoothd[765]: Starting SDP server
Oct  7 14:46:01 Alan bluetoothd[765]: DIS cannot start: GATT is disabled
Oct  7 14:46:01 Alan bluetoothd[765]: Failed to init deviceinfo plugin
Oct  7 14:46:01 Alan bluetoothd[765]: Failed to init proximity plugin
Oct  7 14:46:01 Alan bluetoothd[765]: Failed to init time plugin
Oct  7 14:46:01 Alan bluetoothd[765]: Failed to init alert plugin
Oct  7 14:46:01 Alan bluetoothd[765]: Failed to init thermometer plugin
Oct  7 14:46:01 Alan bluetoothd[765]: Failed to init gatt_example plugin
Oct  7 14:46:01 Alan bluetoothd[765]: Bluetooth Management interface initialized
Oct  7 14:46:01 Alan kernel: [   16.983434] Bluetooth: Core ver 2.16
Oct  7 14:46:01 Alan kernel: [   16.983449] NET: Registered protocol family 31
Oct  7 14:46:01 Alan kernel: [   16.983450] Bluetooth: HCI device and connection manager initialized
Oct  7 14:46:01 Alan kernel: [   16.983456] Bluetooth: HCI socket layer initialized
Oct  7 14:46:01 Alan kernel: [   16.983459] Bluetooth: L2CAP socket layer initialized
Oct  7 14:46:01 Alan kernel: [   16.983464] Bluetooth: SCO socket layer initialized
Oct  7 14:46:01 Alan kernel: [   16.985520] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Oct  7 14:46:01 Alan kernel: [   16.985523] Bluetooth: BNEP filters: protocol multicast
Oct  7 14:46:01 Alan kernel: [   16.985528] Bluetooth: BNEP socket layer initialized
Oct  7 14:46:01 Alan kernel: [   16.986233] Bluetooth: RFCOMM TTY layer initialized
Oct  7 14:46:01 Alan kernel: [   16.986239] Bluetooth: RFCOMM socket layer initialized
Oct  7 14:46:01 Alan kernel: [   16.986240] Bluetooth: RFCOMM ver 1.11
<snip>
Oct  7 14:46:01 Alan kernel: [   16.997232] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
Oct  7 14:46:01 Alan kernel: [   17.002379] kvm: disabled by bios
Oct  7 14:46:01 Alan kernel: [   17.004732] type=1400 audit(1381182361.716:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=778 comm="apparmor_parser"
Oct  7 14:46:01 Alan kernel: [   17.004738] type=1400 audit(1381182361.716:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=732 comm="apparmor_parser"
Oct  7 14:46:01 Alan kernel: [   17.004745] type=1400 audit(1381182361.716:4): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=757 comm="apparmor_parser"
Oct  7 14:46:01 Alan kernel: [   17.005002] type=1400 audit(1381182361.716:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=778 comm="apparmor_parser"
Oct  7 14:46:01 Alan kernel: [   17.005009] type=1400 audit(1381182361.716:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=732 comm="apparmor_parser"
Oct  7 14:46:01 Alan kernel: [   17.005015] type=1400 audit(1381182361.716:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=757 comm="apparmor_parser"
Oct  7 14:46:01 Alan kernel: [   17.005149] type=1400 audit(1381182361.716:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=778 comm="apparmor_parser"
Oct  7 14:46:01 Alan kernel: [   17.005157] type=1400 audit(1381182361.716:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=732 comm="apparmor_parser"
Oct  7 14:46:01 Alan kernel: [   17.005164] type=1400 audit(1381182361.716:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=757 comm="apparmor_parser"
Oct  7 14:46:01 Alan kernel: [   17.007633] kvm: disabled by bios
Oct  7 14:46:01 Alan **[COLOR="#FF0000"]failsafe: Failsafe of 120 seconds reached.[/COLOR]**
Oct  7 14:46:01 Alan avahi-daemon[832]: Found user 'avahi' (UID 111) and group 'avahi' (GID 118).
Oct  7 14:46:01 Alan avahi-daemon[832]: Successfully dropped root privileges.
Oct  7 14:46:01 Alan avahi-daemon[832]: avahi-daemon 0.6.31 starting up.
Oct  7 14:46:01 Alan avahi-daemon[832]: Successfully called chroot().
Oct  7 14:46:01 Alan avahi-daemon[832]: Successfully dropped remaining capabilities.
Oct  7 14:46:01 Alan kernel: [   17.066970] lis3lv02d: 8 bits 3DC sensor found
Oct  7 14:46:01 Alan avahi-daemon[832]: Loading service file /services/udisks.service.
Oct  7 14:46:01 Alan kernel: [   17.100598] ppdev: user-space parallel port driver
Oct  7 14:46:01 Alan kernel: [   17.112226] cfg80211: World regulatory domain updated:
Oct  7 14:46:01 Alan kernel: [   17.112229] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Oct  7 14:46:01 Alan kernel: [   17.112230] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct  7 14:46:01 Alan kernel: [   17.112231] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Oct  7 14:46:01 Alan kernel: [   17.112232] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Oct  7 14:46:01 Alan kernel: [   17.112233] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct  7 14:46:01 Alan kernel: [   17.112234] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct  7 14:46:01 Alan avahi-daemon[832]: Network interface enumeration completed.
Oct  7 14:46:01 Alan avahi-daemon[832]: Registering HINFO record with values 'X86_64'/'LINUX'.
Oct  7 14:46:01 Alan avahi-daemon[832]: Server startup complete. Host name is Alan.local. Local service cookie is 4161461197.
Oct  7 14:46:01 Alan avahi-daemon[832]: Service "Alan" (/services/udisks.service) successfully established.
Oct  7 14:46:01 Alan kernel: [   17.151668] type=1400 audit(1381182361.864:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=883 comm="apparmor_parser"
Oct  7 14:46:01 Alan kernel: [   17.262996] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input7
Oct  7 14:46:01 Alan kernel: [   17.263531] wmi: Mapper loaded
Oct  7 14:46:02 Alan mtp-probe: checking bus 1, device 4: "/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3"
<snip>
Oct  7 14:46:02 Alan modem-manager[879]: <info>  ModemManager (version 0.6.0.0) starting...
Oct  7 14:46:02 Alan modem-manager[879]: <info>  Loaded plugin 'Wavecom'
..
<snip>
..
Oct  7 14:46:02 Alan modem-manager[879]: <info>  Successfully loaded 20 plugins
<snip>
Oct  7 14:46:03 Alan cron[1017]: (CRON) INFO (pidfile fd = 3)
Oct  7 14:46:03 Alan NetworkManager[989]: <info> [COLOR="#FF0000"]**NetworkManager (version 0.9.8.0) is starting...**[/COLOR]
Oct  7 14:46:03 Alan NetworkManager[989]: <info> [COLOR="#FF0000"]Read config file /etc/NetworkManager/NetworkManager.conf[/COLOR]
Oct  7 14:46:03 Alan NetworkManager[989]: <info> WEXT support is enabled
Oct  7 14:46:03 Alan anacron[1037]: Anacron 2.3 started on 2013-10-07
Oct  7 14:46:03 Alan acpid: starting up with proc fs
Oct  7 14:46:03 Alan cron[1038]: (CRON) STARTUP (fork ok)
Oct  7 14:46:03 Alan anacron[1037]: Normal exit (0 jobs run)
Oct  7 14:46:03 Alan kernel: [   18.682181] acpi device:3d: registered as cooling_device8
Oct  7 14:46:03 Alan kernel: [   18.682282] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
Oct  7 14:46:03 Alan kernel: [   18.682317] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input10
Oct  7 14:46:03 Alan kernel: [   18.682386] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Oct  7 14:46:03 Alan kernel: [   18.682472] snd_hda_intel 0000:00:1b.0: irq 46 for MSI/MSI-X
Oct  7 14:46:03 Alan cron[1038]: (CRON) INFO (Running @reboot jobs)
Oct  7 14:46:03 Alan kernel: [   18.710688] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
Oct  7 14:46:03 Alan kernel: [   18.710815] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
Oct  7 14:46:03 Alan kernel: [   18.710906] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
Oct  7 14:46:03 Alan kernel: [   18.870294] [drm] Enabling RC6 states: RC6 on, RC6p on, RC6pp off
Oct  7 14:46:03 Alan NetworkManager[989]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Oct  7 14:46:03 Alan dbus[534]: [system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)
Oct  7 14:46:03 Alan ntpdate[1149]: Can't find host ntp.ubuntu.com: System error (-11)
Oct  7 14:46:03 Alan ntpdate[1149]: no servers can be used, exiting
Oct  7 14:46:04 Alan polkitd[1191]: started daemon version 0.105 using authority implementation `local' version `0.105'
Oct  7 14:46:04 Alan CRON[1204]: (mitch) CMD (~/bin/brightness.sh)
Oct  7 14:46:04 Alan dbus[534]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Oct  7 14:46:04 Alan NetworkManager[989]: **[COLOR="#FF0000"]Error parsing file '/etc/NetworkManager/NetworkManager.conf': No such file or directory[/COLOR]**
Oct  7 14:46:04 Alan NetworkManager[989]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Oct  7 14:46:04 Alan NetworkManager[989]: Error parsing file '/etc/NetworkManager/NetworkManager.conf': No such file or directory
Oct  7 14:46:04 Alan NetworkManager[989]:    keyfile: parsing UCLA_WIFI_RES ... 
Oct  7 14:46:04 Alan acpid: 33 rules loaded
Oct  7 14:46:04 Alan acpid: waiting for events: event logging is off
Oct  7 14:46:04 Alan NetworkManager[989]:    keyfile:     [B]read connection 'UCLA_WIFI_RES'
Oct  7 14:46:04 Alan NetworkManager[989]:    keyfile: parsing UCLA_SECURE_RES ... 
Oct  7 14:46:04 Alan NetworkManager[989]:    keyfile:     read connection 'UCLA_SECURE_RES'
Oct  7 14:46:04 Alan NetworkManager[989]:    keyfile: parsing UCLA_WEB_RES ... 
Oct  7 14:46:04 Alan NetworkManager[989]:    keyfile:     read connection 'UCLA_WEB_RES'
Oct  7 14:46:04 Alan NetworkManager[989]: Error parsing file '/etc/NetworkManager/NetworkManager.conf': No such file or directory
Oct  7 14:46:04 Alan NetworkManager[989]: <info> modem-manager is now available
Oct  7 14:46:04 Alan NetworkManager[989]: <info> monitoring kernel firmware directory '/lib/firmware'.
Oct  7 14:46:04 Alan NetworkManager[989]: [COLOR="#FF0000"]<info> rfkill0: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:1c.3/0000:04:00.0/ieee80211/phy0/rfkill0) (driver rt2800pci)[/COLOR]
Oct  7 14:46:04 Alan NetworkManager[989]: <info> WiFi hardware radio set enabled
Oct  7 14:46:04 Alan NetworkManager[989]: <info> [COLOR="#FF0000"]WiFi disabled by radio killswitch; enabled by state file[/COLOR]
Oct  7 14:46:04 Alan NetworkManager[989]: <info> WWAN enabled by radio killswitch; enabled by state file
Oct  7 14:46:04 Alan NetworkManager[989]: <info> WiMAX enabled by radio killswitch; enabled by state file
Oct  7 14:46:04 Alan NetworkManager[989]: <info> Networking is enabled by state file
Oct  7 14:46:04 Alan NetworkManager[989]: <info> (wlan0): using nl80211 for WiFi device control
Oct  7 14:46:04 Alan NetworkManager[989]: <info> (wlan0): driver supports Access Point (AP) mode
Oct  7 14:46:04 Alan NetworkManager[989]: <info> (wlan0): new 802.11 WiFi device (driver: 'rt2800pci' ifindex: 3)
Oct  7 14:46:04 Alan NetworkManager[989]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Oct  7 14:46:04 Alan NetworkManager[989]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Oct  7 14:46:04 Alan NetworkManager[989]: <info> (wlan0): bringing up device.
Oct  7 14:46:04 Alan NetworkManager[989]: <info> (wlan0):[COLOR="#FF0000"] deactivating device (reason 'managed')[/COLOR] [2]
Oct  7 14:46:04 Alan NetworkManager[989]: <warn> failed to allocate link cache: (-10) Operation not supported[/B]
Oct  7 14:46:04 Alan NetworkManager[989]: <info> (eth0): carrier is OFF
Oct  7 14:46:04 Alan NetworkManager[989]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Oct  7 14:46:04 Alan NetworkManager[989]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Oct  7 14:46:04 Alan NetworkManager[989]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Oct  7 14:46:04 Alan NetworkManager[989]: <info> (eth0): bringing up device.
Oct  7 14:46:04 Alan kernel: [   19.610691] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct  7 14:46:04 Alan NetworkManager[989]: <info> (eth0): preparing device.
Oct  7 14:46:04 Alan NetworkManager[989]: <info> (eth0): deactivating device (reason 'managed') [2]
Oct  7 14:46:04 Alan NetworkManager[989]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:1c.5/0000:05:00.0/net/eth0
Oct  7 14:46:04 Alan NetworkManager[989]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Oct  7 14:46:04 Alan NetworkManager[989]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Oct  7 14:46:04 Alan kernel: [   19.943576] r8169 0000:05:00.0 eth0: link down
Oct  7 14:46:04 Alan kernel: [   19.943616] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct  7 14:46:04 Alan kernel: [   19.943839] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct  7 14:46:06 Alan postfix/master[1257]: daemon started -- version 2.10.0, configuration /etc/postfix
<snip>
Oct  7 14:46:09 Alan dbus[534]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)
Oct  7 14:46:09 Alan accounts-daemon[1460]: started daemon version 0.6.29
Oct  7 14:46:09 Alan dbus[534]: [system] Successfully activated service 'org.freedesktop.Accounts'
Oct  7 14:46:09 Alan dbus[534]: [system] Activating service name='org.freedesktop.ConsoleKit' (using servicehelper)
Oct  7 14:46:09 Alan dbus[534]: [system] Successfully activated service 'org.freedesktop.ConsoleKit'
Oct  7 14:46:10 Alan dbus[534]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)
Oct  7 14:46:10 Alan dbus[534]: [system] Successfully activated service 'org.freedesktop.UPower'
Oct  7 14:46:11 Alan dbus[534]: [system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)
Oct  7 14:46:11 Alan dbus[534]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
Oct  7 14:46:11 Alan rtkit-daemon[1669]: Successfully called chroot.
<snip> **[COLOR="#0000CD"]# Suspend initiated here..[/COLOR]**
Oct  7 14:46:49 Alan NetworkManager[989]: <info> **[COLOR="#0000CD"]sleep requested (sleeping: no  enabled: yes)[/COLOR]**
Oct  7 14:46:49 Alan NetworkManager[989]: <info> sleeping or disabling...
Oct  7 14:46:49 Alan NetworkManager[989]: <info> **(wlan0): device state change: unavailable -> unmanaged (reason 'sleeping') [20 10 37]**
Oct  7 14:46:49 Alan NetworkManager[989]: <info> (eth0): device state change: unavailable -> unmanaged (reason 'sleeping') [20 10 37]
Oct  7 14:46:49 Alan NetworkManager[989]: <info> (eth0): cleaning up...
Oct  7 14:46:49 Alan NetworkManager[989]: <info> (eth0): taking down device.
Oct  7 14:46:50 Alan anacron[2471]: Anacron 2.3 started on 2013-10-07
Oct  7 14:46:50 Alan anacron[2471]: Normal exit (0 jobs run)
Oct  7 14:46:50 Alan kernel: [   66.024781] PM: Syncing filesystems ... done.
Oct  7 14:47:00 Alan kernel: [   66.074177] Freezing user space processes ... (elapsed 0.01 seconds) done.
Oct  7 14:47:00 Alan kernel: [   66.089881] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
Oct  7 14:47:00 Alan kernel: [   66.105903] Suspending console(s) (use no_console_suspend to debug)
Oct  7 14:47:00 Alan kernel: [   66.106110] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Oct  7 14:47:00 Alan kernel: [   66.106264] sd 0:0:0:0: [sda] Stopping disk
Oct  7 14:47:00 Alan kernel: [   66.221810] i8042 aux 00:08: System wakeup disabled by ACPI
Oct  7 14:47:00 Alan kernel: [   66.257791] i8042 kbd 00:07: System wakeup enabled by ACPI
Oct  7 14:47:00 Alan kernel: [   66.757567] PM: suspend of devices complete after 651.896 msecs
Oct  7 14:47:00 Alan kernel: [   66.757706] PM: late suspend of devices complete after 0.137 msecs
Oct  7 14:47:00 Alan kernel: [   66.793440] r8169 0000:05:00.0: System wakeup enabled by ACPI
Oct  7 14:47:00 Alan kernel: [   66.809570] ehci-pci 0000:00:1d.0: System wakeup enabled by ACPI
Oct  7 14:47:00 Alan kernel: [   66.825701] ehci-pci 0000:00:1a.0: System wakeup enabled by ACPI
Oct  7 14:47:00 Alan kernel: [   66.857470] xhci_hcd 0000:00:14.0: System wakeup enabled by ACPI
Oct  7 14:47:00 Alan kernel: [   66.873451] PM: noirq suspend of devices complete after 115.800 msecs
Oct  7 14:47:00 Alan kernel: [   66.873993] ACPI: Preparing to enter system sleep state S3
Oct  7 14:47:00 Alan kernel: [   66.945413] PM: Saving platform NVS memory
Oct  7 14:47:00 Alan kernel: [   66.947649] Disabling non-boot CPUs ...
Oct  7 14:47:00 Alan kernel: [   67.049286] smpboot: CPU 1 is now offline
Oct  7 14:47:00 Alan kernel: [   67.153232] smpboot: CPU 2 is now offline
Oct  7 14:47:00 Alan kernel: [   67.153712] Broke affinity for irq 16
Oct  7 14:47:00 Alan kernel: [   67.153729] Broke affinity for irq 23
Oct  7 14:47:00 Alan kernel: [   67.154733] smpboot: CPU 3 is now offline
Oct  7 14:47:00 Alan kernel: [   67.257177] smpboot: CPU 4 is now offline
Oct  7 14:47:00 Alan kernel: [   67.257628] Broke affinity for irq 43
Oct  7 14:47:00 Alan kernel: [   67.258631] smpboot: CPU 5 is now offline
Oct  7 14:47:00 Alan kernel: [   67.260019] smpboot: CPU 6 is now offline
Oct  7 14:47:00 Alan kernel: [   67.260591] Broke affinity for irq 40
Oct  7 14:47:00 Alan kernel: [   67.261599] smpboot: CPU 7 is now offline
<No snip here just comment> [COLOR="#0000CD"]**# Was suspend ended immediately? Apparently the suspend didn't last even one full second !**[/COLOR]
Oct  7 14:47:00 Alan kernel: [   67.262836] ACPI: Low-level resume complete
Oct  7 14:47:00 Alan kernel: [   67.262883] PM: Restoring platform NVS memory
Oct  7 14:47:00 Alan kernel: [   67.263346] Enabling non-boot CPUs ...
Oct  7 14:47:00 Alan kernel: [   67.263402] smpboot: Booting Node 0 Processor 1 APIC 0x1
Oct  7 14:47:00 Alan kernel: [   67.293411] CPU1 is up
Oct  7 14:47:00 Alan kernel: [   67.293471] smpboot: Booting Node 0 Processor 2 APIC 0x2
Oct  7 14:47:00 Alan kernel: [   67.307177] CPU2 is up
Oct  7 14:47:00 Alan kernel: [   67.307219] smpboot: Booting Node 0 Processor 3 APIC 0x3
Oct  7 14:47:00 Alan kernel: [   67.321009] CPU3 is up
Oct  7 14:47:00 Alan kernel: [   67.321056] smpboot: Booting Node 0 Processor 4 APIC 0x4
Oct  7 14:47:00 Alan kernel: [   67.334865] CPU4 is up
Oct  7 14:47:00 Alan kernel: [   67.334910] smpboot: Booting Node 0 Processor 5 APIC 0x5
Oct  7 14:47:00 Alan kernel: [   67.348723] CPU5 is up
Oct  7 14:47:00 Alan kernel: [   67.348777] smpboot: Booting Node 0 Processor 6 APIC 0x6
Oct  7 14:47:00 Alan kernel: [   67.362623] CPU6 is up
Oct  7 14:47:00 Alan kernel: [   67.362672] smpboot: Booting Node 0 Processor 7 APIC 0x7
Oct  7 14:47:00 Alan kernel: [   67.376554] CPU7 is up
Oct  7 14:47:00 Alan kernel: [   67.383416] ACPI: Waking up from system sleep state S3
Oct  7 14:47:00 Alan kernel: [   67.926416] xhci_hcd 0000:00:14.0: System wakeup disabled by ACPI
Oct  7 14:47:00 Alan kernel: [   67.958399] ehci-pci 0000:00:1a.0: System wakeup disabled by ACPI
Oct  7 14:47:00 Alan kernel: [   67.990379] ehci-pci 0000:00:1d.0: System wakeup disabled by ACPI
Oct  7 14:47:00 Alan kernel: [   68.054440] PM: noirq resume of devices complete after 159.986 msecs
Oct  7 14:47:00 Alan kernel: [   68.054537] PM: early resume of devices complete after 0.074 msecs
Oct  7 14:47:00 Alan kernel: [   68.054565] i915 0000:00:02.0: setting latency timer to 64
Oct  7 14:47:00 Alan kernel: [   68.054568] xhci_hcd 0000:00:14.0: setting latency timer to 64
Oct  7 14:47:00 Alan kernel: [   68.054579] ehci-pci 0000:00:1a.0: setting latency timer to 64
Oct  7 14:47:00 Alan kernel: [   68.054619] ehci-pci 0000:00:1d.0: setting latency timer to 64
Oct  7 14:47:00 Alan kernel: [   68.054712] ahci 0000:00:1f.2: setting latency timer to 64
Oct  7 14:47:00 Alan kernel: [   68.054719] mei 0000:00:16.0: irq 44 for MSI/MSI-X
Oct  7 14:47:00 Alan kernel: [   68.054744] snd_hda_intel 0000:00:1b.0: irq 46 for MSI/MSI-X
Oct  7 14:47:00 Alan kernel: [   68.278345] usb 1-1.3: reset high-speed USB device number 4 using ehci-pci
Oct  7 14:47:00 Alan kernel: [   68.382178] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Oct  7 14:47:00 Alan kernel: [   68.386273] ata5.00: configured for UDMA/100
Oct  7 14:47:00 Alan kernel: [   68.442237] usb 1-1.1: reset full-speed USB device number 3 using ehci-pci
Oct  7 14:47:00 Alan kernel: [   68.618091] r8169 0000:05:00.0: System wakeup disabled by ACPI
Oct  7 14:47:00 Alan kernel: [   69.773725] [drm] Enabling RC6 states: RC6 on, RC6p on, RC6pp off
Oct  7 14:47:00 Alan kernel: [   70.109299] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Oct  7 14:47:00 Alan kernel: [   70.378792] ata1.00: configured for UDMA/133
Oct  7 14:47:00 Alan kernel: [   70.393328] sd 0:0:0:0: [sda] Starting disk
Oct  7 14:47:00 Alan kernel: [   72.224236] i8042 kbd 00:07: System wakeup disabled by ACPI
Oct  7 14:47:00 Alan kernel: [   72.233556] PM: resume of devices complete after 4181.162 msecs
Oct  7 14:47:00 Alan acpid: client 1305[0:0] has disconnected
Oct  7 14:47:00 Alan NetworkManager[989]: **[COLOR="#FF0000"]<info> WiFi now enabled by radio killswitch[/COLOR]** *[COLOR="#0000CD"]#By magic? or acpi games?[/COLOR]*
Oct  7 14:47:00 Alan kernel: [   72.248379] Restarting tasks ... done.
Oct  7 14:47:00 Alan kernel: [   72.249789] video LNXVIDEO:00: Restoring backlight state
Oct  7 14:47:01 Alan acpid: client connected from 1305[0:0]
Oct  7 14:47:01 Alan acpid: 1 client rule loaded
Oct  7 14:47:01 Alan anacron[2760]: Anacron 2.3 started on 2013-10-07
Oct  7 14:47:01 Alan anacron[2760]: Normal exit (0 jobs run)
Oct  7 14:47:01 Alan anacron[2818]: Anacron 2.3 started on 2013-10-07
Oct  7 14:47:01 Alan anacron[2818]: Normal exit (0 jobs run)
Oct  7 14:47:01 Alan [B]NetworkManager[989]: <info> wake requested (sleeping: yes  enabled: yes)
Oct  7 14:47:01 Alan NetworkManager[989]: <info> waking up and re-enabling...
Oct  7 14:47:01 Alan NetworkManager[989]: <info> WWAN now enabled by management service
Oct  7 14:47:01 Alan NetworkManager[989]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Oct  7 14:47:01 Alan NetworkManager[989]: <info> [COLOR="#FF0000"](wlan0): bringing up device.[/COLOR]
Oct  7 14:47:01 Alan NetworkManager[989]: <info> [COLOR="#FF0000"](wlan0): preparing device.[/COLOR]
Oct  7 14:47:01 Alan NetworkManager[989]: <info> [COLOR="#FF0000"](wlan0): deactivating device (reason 'managed') [2][/COLOR]
Oct  7 14:47:01 Alan NetworkManager[989]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Oct  7 14:47:01 Alan NetworkManager[989]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)[/B]
Oct  7 14:47:01 Alan NetworkManager[989]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Oct  7 14:47:01 Alan NetworkManager[989]: <info> (eth0): bringing up device.
Oct  7 14:47:01 Alan dbus[534]: **[COLOR="#FF0000"][system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)[/COLOR]**
Oct  7 14:47:01 Alan kernel: [   72.540558] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct  7 14:47:01 Alan dbus[534]: **[COLOR="#FF0000"][system] Successfully activated service 'fi.w1.wpa_supplicant1'[/COLOR]**
Oct  7 14:47:01 Alan NetworkManager[989]: <info> (eth0): preparing device.
Oct  7 14:47:01 Alan NetworkManager[989]: <info> (eth0): deactivating device (reason 'managed') [2]
Oct  7 14:47:01 Alan NetworkManager[989]: <info> wpa_supplicant started
Oct  7 14:47:01 Alan kernel: [   72.646035] r8169 0000:05:00.0 eth0: link down
Oct  7 14:47:01 Alan kernel: [   72.646077] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct  7 14:47:01 Alan NetworkManager[989]: <info> (wlan0) supports 4 scan SSIDs
Oct  7 14:47:01 Alan NetworkManager[989]: <warn> Trying to remove a non-existant call id.
Oct  7 14:47:01 Alan NetworkManager[989]: [COLOR="#FF0000"]**<info> (wlan0): supplicant interface state: starting -> ready**[/COLOR]
Oct  7 14:47:01 Alan NetworkManager[989]: <info> **[COLOR="#FF0000"](wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42][/COLOR]**
Oct  7 14:47:01 Alan NetworkManager[989]: <info> (wlan0): supplicant interface state: ready -> inactive
Oct  7 14:47:01 Alan NetworkManager[989]: <info> (wlan0) supports 4 scan SSIDs
Oct  7 14:47:02 Alan NetworkManager[989]: <info> **[COLOR="#FF0000"]Auto-activating connection 'UCLA_WIFI_RES'.[/COLOR]** *[COLOR="#0000CD"]# So wifi is up and active from here[/COLOR]*
Oct  7 14:47:02 Alan NetworkManager[989]: <info> Activation (wlan0) starting connection 'UCLA_WIFI_RES'
Oct  7 14:47:02 Alan NetworkManager[989]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Oct  7 14:47:02 Alan NetworkManager[989]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Oct  7 14:47:02 Alan NetworkManager[989]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Oct  7 14:47:02 Alan NetworkManager[989]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Oct  7 14:47:02 Alan NetworkManager[989]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Oct  7 14:47:02 Alan NetworkManager[989]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Oct  7 14:47:02 Alan NetworkManager[989]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Oct  7 14:47:02 Alan NetworkManager[989]: <info> Activation (wlan0/wireless): connection 'UCLA_WIFI_RES' requires no security.  No secrets needed.
Oct  7 14:47:02 Alan NetworkManager[989]: <info> Config: added 'ssid' value 'UCLA_WIFI_RES'
Oct  7 14:47:02 Alan NetworkManager[989]: <info> Config: added 'scan_ssid' value '1'
Oct  7 14:47:02 Alan NetworkManager[989]: <info> Config: added 'key_mgmt' value 'NONE'
Oct  7 14:47:02 Alan NetworkManager[989]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Oct  7 14:47:02 Alan NetworkManager[989]: <info> Config: set interface ap_scan to 1
Oct  7 14:47:02 Alan NetworkManager[989]: <info> (wlan0): supplicant interface state: inactive -> scanning
Oct  7 14:47:03 Alan wpa_supplicant[2908]: wlan0: SME: Trying to authenticate with 00:1a:1e:83:7a:22 (SSID='UCLA_WIFI_RES' freq=2437 MHz)
Oct  7 14:47:03 Alan kernel: [   74.859433] wlan0: authenticate with 00:1a:1e:83:7a:22
Oct  7 14:47:03 Alan NetworkManager[989]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Oct  7 14:47:03 Alan wpa_supplicant[2908]: wlan0: Trying to associate with 00:1a:1e:83:7a:22 (SSID='UCLA_WIFI_RES' freq=2437 MHz)
Oct  7 14:47:03 Alan kernel: [   74.875254] wlan0: send auth to 00:1a:1e:83:7a:22 (try 1/3)
Oct  7 14:47:03 Alan kernel: [   74.876741] wlan0: authenticated
Oct  7 14:47:03 Alan kernel: [   74.878786] wlan0: associate with 00:1a:1e:83:7a:22 (try 1/3)
Oct  7 14:47:03 Alan NetworkManager[989]: <info> (wlan0): supplicant interface state: authenticating -> associating
Oct  7 14:47:03 Alan wpa_supplicant[2908]: wlan0: Associated with 00:1a:1e:83:7a:22
Oct  7 14:47:03 Alan wpa_supplicant[2908]: wlan0: CTRL-EVENT-CONNECTED - Connection to 00:1a:1e:83:7a:22 completed (auth) [id=0 id_str=]
Oct  7 14:47:03 Alan kernel: [   74.883409] wlan0: RX AssocResp from 00:1a:1e:83:7a:22 (capab=0x421 status=0 aid=2)
Oct  7 14:47:03 Alan kernel: [   74.883568] wlan0: associated
Oct  7 14:47:03 Alan kernel: [   74.883575] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Oct  7 14:47:03 Alan NetworkManager[989]: <info> (wlan0): supplicant interface state: associating -> completed
Oct  7 14:47:03 Alan NetworkManager[989]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'UCLA_WIFI_RES'.
Oct  7 14:47:03 Alan NetworkManager[989]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Oct  7 14:47:03 Alan NetworkManager[989]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Oct  7 14:47:03 Alan NetworkManager[989]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Oct  7 14:47:03 Alan NetworkManager[989]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct  7 14:47:03 Alan NetworkManager[989]: <info> dhclient started with pid 2915
Oct  7 14:47:03 Alan NetworkManager[989]: <info> Activation (wlan0) Beginning IP6 addrconf.
Oct  7 14:47:03 Alan NetworkManager[989]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Oct  7 14:47:03 Alan dhclient: Internet Systems Consortium DHCP Client 4.2.4
Oct  7 14:47:03 Alan dhclient: Copyright 2004-2012 Internet Systems Consortium.
Oct  7 14:47:03 Alan dhclient: All rights reserved.
Oct  7 14:47:03 Alan dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct  7 14:47:03 Alan dhclient: 
Oct  7 14:47:03 Alan NetworkManager[989]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Oct  7 14:47:03 Alan dhclient: Listening on LPF/wlan0/e0:06:e6:0a:05:c2
Oct  7 14:47:03 Alan dhclient: Sending on   LPF/wlan0/e0:06:e6:0a:05:c2
Oct  7 14:47:03 Alan dhclient: Sending on   Socket/fallback
Oct  7 14:47:03 Alan dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3 (xid=0x60a15399)
Oct  7 14:47:04 Alan dhclient: DHCPREQUEST of 149.142.227.198 on wlan0 to 255.255.255.255 port 67 (xid=0x60a15399)
Oct  7 14:47:04 Alan dhclient: DHCPOFFER of 149.142.227.198 from 149.142.227.2
Oct  7 14:47:04 Alan dhclient: DHCPACK of 149.142.227.198 from 149.142.227.2
Oct  7 14:47:04 Alan dhclient: bound to 149.142.227.198 -- renewal in 1543 seconds.
Oct  7 14:47:04 Alan NetworkManager[989]: <info> (wlan0): DHCPv4 state changed preinit -> bound
Oct  7 14:47:04 Alan NetworkManager[989]: <info>   address 149.142.227.198
Oct  7 14:47:04 Alan NetworkManager[989]: <info>   prefix 24 (255.255.255.0)
Oct  7 14:47:04 Alan NetworkManager[989]: <info>   gateway 149.142.227.5
Oct  7 14:47:04 Alan NetworkManager[989]: <info>   nameserver '164.67.128.3'
Oct  7 14:47:04 Alan NetworkManager[989]: <info>   nameserver '164.67.128.1'
Oct  7 14:47:04 Alan NetworkManager[989]: <info>   nameserver '128.97.128.1'
Oct  7 14:47:04 Alan NetworkManager[989]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Oct  7 14:47:04 Alan NetworkManager[989]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Oct  7 14:47:04 Alan avahi-daemon[832]: Joining mDNS multicast group on interface wlan0.IPv4 with address 149.142.227.198.
Oct  7 14:47:04 Alan avahi-daemon[832]: New relevant interface wlan0.IPv4 for mDNS.
Oct  7 14:47:04 Alan avahi-daemon[832]: Registering new address record for 149.142.227.198 on wlan0.IPv4.
Oct  7 14:47:05 Alan avahi-daemon[832]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::e206:e6ff:fe0a:5c2.
Oct  7 14:47:05 Alan avahi-daemon[832]: New relevant interface wlan0.IPv6 for mDNS.
Oct  7 14:47:05 Alan avahi-daemon[832]: Registering new address record for fe80::e206:e6ff:fe0a:5c2 on wlan0.*.
Oct  7 14:47:05 Alan NetworkManager[989]: <info> (wlan0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Oct  7 14:47:05 Alan NetworkManager[989]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Oct  7 14:47:05 Alan NetworkManager[989]: <info> (wlan0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Oct  7 14:47:05 Alan NetworkManager[989]: <info> Policy set 'UCLA_WIFI_RES' (wlan0) as default for IPv4 routing and DNS.
Oct  7 14:47:05 Alan NetworkManager[989]: <info> Writing DNS information to /sbin/resolvconf
Oct  7 14:47:06 Alan postfix/master[1257]: reload -- version 2.10.0, configuration /etc/postfix
Oct  7 14:47:06 Alan NetworkManager[989]: <info> (wlan0): roamed from BSSID 00:1A:1E:83:72:E2 (UCLA_WIFI_RES) to 00:1A:1E:83:7A:22 (UCLA_WIFI_RES)
Oct  7 14:47:06 Alan NetworkManager[989]: <info> Activation (wlan0) successful, device activated.
Oct  7 14:47:06 Alan dbus[534]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Oct  7 14:47:06 Alan dbus[534]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Oct  7 14:47:14 Alan ntpdate[3041]: no server suitable for synchronization found
Oct  7 14:47:23 Alan NetworkManager[989]: <info> (wlan0): IP6 addrconf timed out or failed.
Oct  7 14:47:23 Alan NetworkManager[989]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Oct  7 14:47:23 Alan NetworkManager[989]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Oct  7 14:47:23 Alan NetworkManager[989]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
```

So the first and obvious thing to notice is that Network Manager is still active in some ways although you tried to remove it. I'd recommend to re-install it again, especially since whatever you tried instead didn't help -
```
sudo apt-get update
sudo apt-get install --reinstall network-manager network-manager-gnome
```

Second thing is that it seems the WPA supplicant is working on its own 'After' resume, and the wifi becomes active. I believe it is a result, not the cause of wifi becoming active, but I'm not very sure of anything at this point (I'm just a normal user, not an NM or wifi expert). I think once the Network Manager is installed properly, we can get a better picture of it.

Thirdly, the acpi related errors also make me suspicious of it possibly being one of the acpi errors on the PCI bus or something like that. Regarding this, various boot options, like acpi=noirq, noacpi, nolapic etc. may be tried. Keep it if helps, discard if not. See the wiki page regarding Boot Options and how to use them -
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

and on the same page, near the bottom -
[https://help.ubuntu.com/community/BootOptions#Changing_boot_options_Temporarily_for_an_Existing_Installation](https://help.ubuntu.com/community/BootOptions#Changing_boot_options_Temporarily_for_an_Existing_Installation)
[https://help.ubuntu.com/community/BootOptions#Common_Kernel_Options](https://help.ubuntu.com/community/BootOptions#Common_Kernel_Options)

Lastly, and it is not related to any hints or guesses, it seems the syslog contains everything we are getting from dmesg, plus a lot more. It is clearly providing some hints, only I'm not yet smart enough to throw the dart at the right point... <sigh!>. So if we needed to take a look at logs again, I think only the syslog would be sufficient. I really want to find a workaround, if not a fix for this. But at the same time, I am also at the edge of my knowledge already :(

---

### Post by Mitchell_Herndon on 2013-10-10
Well the network manager reinstall didn't seem to make any changes either. :( I think at this point I need to reinstall ubuntu, and maybe downgrade to 12.04 and hope for fewer bugs. I'll post back here if that works, but it might be a few weeks because my classes are keeping me really busy! If you think of any other ideas, I'll still check back here from time to time. Thank you very much for all your help! You're my hero. :KS

---

### Post by varunendra on 2013-10-10
I wish I could pin it down.. :(

But if you are willing to try an older version, do not forget to test it in live mode first. Since 12.04.3 is using the same kernel as 13.04 now, it may have same 'bugs' if it indeed is a kernel bug.

Good luck ! And let us all know the difference if there is.

---

### Post by crnagora on 2013-10-10
I had the same problem with the same system.  I connected my eithernet cord to the computer and it immediately recognized my internet.  Once I removed my cable my WIFI also started working.  I don't know what it worked but i have retested it and it seems to work all the time.

Good luck
crnagora

---

### Post by ChrisFromOz on 2014-02-23
Hi, I would just like to add that this is the only post on this subject to help my wifi problem. In the entry above dated October 4th, 2013 &                                                                                                                                                                                                     [#5]("http://ubuntuforums.org/showthread.php?t=2178085&p=12806701#post12806701")                                                                                                                                                                                      		Mitchell sited, " When I unplugged my ethernet cable and suspended my computer, then  opened it back up the wifi was magically working just fine! I rebooted  to see if it would stay on, and it didn't. However, I replicated the  process and found that it works every time I suspend and then open back  up". This is the only thing that works with my Asus F550C. I've tested it several times and works every time. I've been scouring posts for months trying to find an answer to this problem. Not quite as it's meant to work, but at least it works. Now all I have to do is solve the Discrete Graphics Card dilemma and my i7 with 2GB of 3D graphics will finally operate as it should. Thanks, for your help! Sincerely, Chris.

---

### Post by praseodym on 2014-02-23
Hi,

check out this parameter for ASUS-notebooks:

```
echo "options asus_nb_wmi wapf=1" | sudo tee /etc/modprobe.d/asus.conf 
```
Reboot.

---

### Post by varunendra on 2014-02-23
> **ChrisFromOz said:**
> ..and found that it works every time I suspend and then open back  up..

It is now a known bug in asus_nb_wmi driver, and the current (and only) workaround (only for Asus) is what praseodym mentioned above (the name of the .conf file doesn't matter).

Please see these bug reports : [https://bugs.launchpad.net/bugs/1277959](https://bugs.launchpad.net/bugs/1277959)
and [https://bugs.launchpad.net/bugs/1173681](https://bugs.launchpad.net/bugs/1173681)

These will link back to this thread as a current workaround/solution : [http://ubuntuforums.org/showthread.php?t=2181558](http://ubuntuforums.org/showthread.php?t=2181558)

Please read the above thread to test, confirm and fix the issue, and a workaround for your non working Fn+F2 key combination to toggle the wifi On/Off.

I'd strongly recommend you to add yourself to the "Affects Me too" list of the two bug reports linked above. The more users report the problem, the sooner it gets fixed.

---

