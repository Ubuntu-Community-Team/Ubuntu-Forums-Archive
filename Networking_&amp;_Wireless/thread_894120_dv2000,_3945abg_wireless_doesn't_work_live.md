---
title: "dv2000, 3945abg wireless doesn't work live?"
date: 2008-08-19
forum: Networking &amp; Wireless
---

### Post by teryret on 2008-08-19
Hello all.  For the longest time I've been an ubuntu encourager, but as a .NET programmer I couldn't really justify running it myself.  But now that I no longer have that job I think it's about time to make that switch.  Trouble is, I rather like my computer as is, so I'm not going to format it until I'm sure this computer will run ubuntu entirely, which means I'm doing all of this in an 8.04 live session (but that shouldn't cause any problems, right?).

So far everything has worked out of the box with the exception of the wireless networking.

lspci -v | less   says:

> 05:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)
        Subsystem: Hewlett-Packard Company Unknown device 30cd
        Flags: bus master, fast devsel, latency 0, IRQ 218
        Memory at f4200000 (64-bit, non-prefetchable) [size=16K]
        I/O ports at 3000 [size=256]
        Capabilities: <access denied>

07:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 135b
        Flags: bus master, fast devsel, latency 0, IRQ 217
        Memory at f4300000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>


According to [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel)  it should* work "out of the box", but it doesn't seem to.

iwconfig  reports:
> lo        no wireless extensions.

eth0      no wireless extensions.


As I was searching around I found a thread that talked about some hp laptops needing to turn the wifi card on.  This resonated with me because the LED that indicates that wifi is enabled in windows is showing what would mean in windows that the card is turned off.  But for all I know that's simply due to lack of installed drivers for that particular LED on this particular laptop.  The problem is, if it's turned off, I don't know how to turn it on, since the switch is already set to on (and flipping it either way didn't seem to do anything).

So, uh, where should I start on troubleshooting this?

---

### Post by jualin on 2008-08-19
Can you type the output of > lsmod to check if the correct module has been loaded.

---

### Post by teryret on 2008-08-19
I'm sure I could type it, but it's pretty long, so I think I'll just cheat and copy/paste it ;-) .

lsmod:

> 
Module                  Size  Used by
arc4                    2944  2 
ecb                     4480  2 
blkcipher               8324  1 ecb
i915                   32512  2 
drm                    82452  3 i915
ipv6                  267780  10 
af_packet              23812  2 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
acpi_cpufreq           10796  2 
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9740  1 
freq_table              5536  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8712  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
container               5632  0 
dock                   11280  0 
usblp                  15872  0 
usbhid                 31872  0 
hid                    38784  1 usbhid
snd_hda_intel         344728  2 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
uvcvideo               58116  0 
compat_ioctl32          2304  1 uvcvideo
videodev               29440  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
joydev                 13120  0 
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
v4l2_common            18304  2 uvcvideo,videodev
iwl3945                89844  0 
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iwlwifi_mac80211      219108  1 iwl3945
psmouse                40336  0 
cfg80211               15112  1 iwlwifi_mac80211
battery                14212  0 
snd                    56996  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
video                  19856  0 
sdhci                  19076  0 
sky2                   47492  0 
ac                      6916  0 
intel_agp              25492  1 
output                  4736  1 video
serio_raw               7940  0 
ricoh_mmc               4352  0 
mmc_core               51460  1 sdhci
wmi_acer                9644  0 
evdev                  13056  9 
button                  9232  0 
shpchp                 34452  0 
iTCO_wdt               13092  0 
agpgart                34760  3 drm,intel_agp
soundcore               8800  1 snd
pcspkr                  4224  0 
pci_hotplug            30880  1 shpchp
iTCO_vendor_support     4868  1 iTCO_wdt
squashfs               49160  1 
loop                   18948  2 
unionfs                76752  1 
nls_cp437               6656  1 
isofs                  36388  1 
sr_mod                 17956  1 
cdrom                  37408  1 sr_mod
sg                     36880  0 
sd_mod                 30720  0 
ata_piix               19588  1 
pata_acpi               8320  0 
ohci1394               33584  0 
ahci                   28420  0 
ata_generic             8324  0 
ieee1394               93752  1 ohci1394
libata                159344  4 ata_piix,pata_acpi,ahci,ata_generic
scsi_mod              151436  4 sr_mod,sg,sd_mod,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  6 usblp,usbhid,uvcvideo,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  4 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3 


---

### Post by jualin on 2008-08-19
The "iwlwifi" and "iwl3945" modules are loaded, and those are suppose to be related to your card. Not sure why they are not being picked up. Maybe since you are using the Live CD the drivers are not enabled until after you restart (Nvidia cards work that way). Why don't you try installing Ubuntu using the Wubi installer (installing within Windows) which doesn't require partitioning or anything complicated, and which you can uninstall using Windows Control Panel. You can think of Wubi like a way to try Ubuntu real power with a "It works or your Windows back no questions asked" guarantee. :)

---

### Post by teryret on 2008-08-19
I didn't know there was any such installer.  That's forking awesome.  I'm going to go play with that right now, I'll let you know how it goes.

---

### Post by jualin on 2008-08-19
If you have the latest Ubuntu 8.04 Live CD, just put the CD inside Windows and install it just like you would install any other software in Windows. Make sure you select the option of "Install within Windows". If the wireless still doesn't work out of the box then let us know. Keep us posted and good luck!

---

### Post by teryret on 2008-08-19
Nothing is ever easy with me.  I don't know why.  After I installed it within windows it asked me to reboot, so I did.  

As it was rebooting it displayed a behavior that I had been ignoring in hopes that it was a live disk only issue.  Namely, it would freeze while the booting loading bar was on the screen.  On the live CD a simple three finger solute bypassed the problem, on the HD install it froze up again later, and the second three finger solute rebooted the computer.

So, the second time it was coming up I selected verbose mode to see where it was having issues.  As I was watching I noticed an error (probably not a real error but more of a verbose line item) that said to the effect of, "your hardware kill switch is ON, and must be OFF for wireless to work" accompanied by what I have to assume is a timestamp that said "68.754902".  Once I had that written down I immediatly toggled the wifi switch (from the Wifi-On position to Wifi-Off) and rebooted, again in verbose mode, to find the exact same error.

This third time I let it boot all the way to fruition and it went through some installing proceedure and rebooted the system at the end.

At this point there was no more verbose mode to rely on both for errors and to get past the sticky parts of loading, and sure enough, it froze in the same spot as it had been, which was the same spot as the live disk had been.

So the takeaway from all of this is that A) I'm fairly certain that somehow I need to configure Ubuntu to recognize the wifi switch and enable the card correctly (but I'd settle for an always on wifi card, battery life be damned), and after I do that Wifi will "just work".  B) I need to figure out how to get it to boot since the three finger solute doesn't seem to be doing it anymore.

Suggestions?

---

### Post by teryret on 2008-08-19
Quick bump with some additional info.  I can boot reliably by selecting Recovery Mode at GRUB, but in the text that flies by I'm noticing the same type of error about the hardware killswitch.  At this point I have two questions:

1)  I'm sure the messages that scroll by when booting in Recovery Mode are logged somewhere, where is that log and how would I most easily search it (given that I'm already fluent in regex) for the timestamp (36.191153 in this most recent boot)?

2)  I'd like to go on the assumption that the hardware wifi switch is in fact the problem (or a lack of drivers for it, either way), any suggestions for where in the software I should start poking around trying to find something that changes based on the state of the switch?  My thinking is that if I can find that access then I should be able to come up with some hack that enables my wifi card based on it, right?  My guess would be somewhere in /dev/, but I'm not sure.

---

### Post by teryret on 2008-08-20
Bump/progress report.

In fooling around with it I ran updates on everything and since then regular booting works most of the time.  The rest of the time after I provide my login credentials it freezes with a black background with a white bar (same size as the default gnome menubar) at the top.  If that happens it will not respond to any keyboard input (even ctrl+alt+del/ctrl+alt+backspace) and must be hard booted.  I consider this progress compared to freezing while loading the OS.

Also, I discovered that there is something fishy about my wifi card.  In Vista if I have the wifi switch enabled while it boots it will not list any networks, once that happens if I switch the wifi off then back on again they all show up.  When I tried the same thing in ubuntu wlan0 started showing up!  After cycling the wifi card iwconfig reads:

> lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


So, that's major progress.  For my next trick I'll get it to list the networks in the area (of which there are many according to vista).  Any idea how to do that?

BTW, it turns out to read the log I was looking for in my last post the command is dmesg (which I then pipe into a file).

---

### Post by jualin on 2008-08-22
I am sorry for taking so long to respond, I just started the University and I was moving in to my dorm. 
I have been reading your thread and my next suggestion would be to try scanning the wireless networks on your area. Go to the terminal and type > iwlist scan and it should show the wireless networks in your area. Let me know if you need further help. And keep us posted, I will answer you as soon as I can.

---

### Post by teryret on 2008-08-22
iwlist scan says:

> lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results


I've also tried going from System->Administration->Network and set the wireless connection to the ESSID of a nearby open network with no success (no DHCP information).  Actually I couldn't even find the option in the GUI to turn off any type of password scheme.  Further, when I right click on the network icon near the top and select Edit Wireless Networks none are listed... but then again if networks did show up there and didn't show up for iwlist scan there would be something horribly amiss.

---

### Post by teryret on 2008-08-27
Sorry for the delay, this thread slipped my mind once I got it working.  I'm really not sure what the trick was.  The most important bit was figuring out that the card doesn't turn on unless the switch is switched to on after the computer has booted.  After that I suspect it took a few enabling and rebootings in order for everything to get loaded and autoconfigured correctly, because I hadn't really changed anything before I noticed it had started working.

Thanks for your help jualin, and good luck in college.  If you're going computer science and want help (I won't help you cheat) just LMK, I've been told I'm a pretty good tutor.

---

