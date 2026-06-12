---
title: "Linksys WPC 11 and laptop"
date: 2005-09-29
forum: Networking &amp; Wireless
---

### Post by Electrobes on 2005-09-29
Hi everyone. I was gifted an older dell laptop from my wife, and so I formatted the thing and stuck on Ubuntu. I have very little experience with Linux, I recently installed it in one of my desktops and even got the wireless internet working on it using a D-Link card. 

On the laptop I have a Linksys card and I found the card on this site as a working card:

Linksys 
 WPC 11 (Ver.3) 
 Prism/Intersil 
 Yes 
 Yes 
 Yes 
 Detected in Network Settings as eth0 and started working after WAP details were input 
 2005-08-15 
 PCMCIA
 
Linksys has a Linux version for the file but I do not know how to use it... so I did what I did on my other computer... I used ndiswrapper and the windows .inf file. Needless to say it did not work. What is strange is that I can see the signal strength of the card and if I do iwconfig I get this: 

eth1      IEEE 802.11-DS  ESSID:"linsys"  Nickname:"Prism  I"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:06:25:60:5D:75
          Bit Rate:11 Mb/s   Tx-Power=15 dBm    Sensitivity:1/3
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=46/92  Signal level=-60 dBm  Noise level=-143 dBm
          Rx invalid nwid:0  Rx invalid crypt:73  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Also what is strange is this: in network settings if I use DCHP and try to log onto a site if down't work in a flash. But if I switch to static IP (Which I used to get the wireless working on my desktop) and write in the info like I did upstairs, I see it trying to connect but then it does... it idles and connects, then idles.. very fast. My desktop yses athl0 instead of eth1... not sure if this makes any difference. 

ALso ndiswrapper claims my driver is invalid.

Any ideas what I should do? thank you.

---

### Post by Electrobes on 2005-09-29
I extracted the tar.gz file from the linksys site.. and I have a folder sitting on my desktop... linux-wlan-ng-0.1.14-prel  

It has a bunch of files in there and I don't know what to do with them to make my card work. as of right now in my network settings I have it on DCHP, though on my router I have DCHP enabled. when I do use DCHP and tried to activate it... "Activating interface "eth1". It takes a long time before, and this is a guess, it gives up. I know this is because I don't have the driver installed... I tried using ndiswrapper with the .inf file version of the wpc 11 v3 but it claimed it was an invalid file and did not work. 

I am guessing that the tar.gz file from linksys for the card will work.. I just don't know how to install it, to make it work. Can someone tell how to do this? Thank you!

---

### Post by az on 2005-09-29
Your card has drivers for it in the kernel.  You do not need to install drivers.

Does the light turn on when you plug it into the slot?

If so, then boot, open up a terminal, type tail -f /var/log/messages
and plug in your card.

Is anything displayed in the terminal?

Are you running Hoary or breezy?

---

### Post by grinchy on 2005-09-29
I had a problem similar to yours recently using a card which also had a driver in the kernel.

can you post the output of 
iwconfig wlan0
ifconfig wlan0
iwlist wlan0 ap

where wlan0 is your card

---

### Post by Electrobes on 2005-09-30
tail -f /var/log/messages got this: get_wireless)stats() called while device not present

none of the iwconfig wlan0, etc gets me anything

just a question, but what is the difference from static IP and DCHP? My desktop is using a static IP and it works with wireless...

---

### Post by az on 2005-10-02
[QUOTE=Electrobes]tail -f /var/log/messages got this: get_wireless)stats() called while device not present[/QUOTE]

Show the output of lsmod

lsmod > file 
and then save the file to a floppy or something to transfer it to another machine and post it here (if you need to do that to get on the net)


[QUOTE=Electrobes]none of the iwconfig wlan0, etc gets me anything[/QUOTE]

That's because your device is eth0 (or eth1)

[QUOTE=Electrobes]just a question, but what is the difference from static IP and DCHP? My desktop is using a static IP and it works with wireless...[/QUOTE]

Static ip means that you decide what your ip address is.  DHCP is a protocol that asks for an address and waits to get one.

---

### Post by JazzCrazed on 2005-10-08
I also got a hold of a Linksys WPC11 (ver. 3, if that's worth anything) for use in my Acer Aspire 3002LCi.

When I type in "tail -f /var/log/messages," and the plugin the card, I get nothing at all.

Here is the output of my lsmod:

```
Module                  Size  Used by
ipv6                  217408  6 
binfmt_misc            10888  1 
rfcomm                 34972  0 
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
powernow_k8            11528  0 
cpufreq_userspace       4444  1 
cpufreq_stats           5124  0 
freq_table              4484  2 powernow_k8,cpufreq_stats
cpufreq_powersave       1920  0 
cpufreq_ondemand        5916  0 
cpufreq_conservative     6820  0 
pcmcia                 24584  2 
video                  16004  0 
tc1100_wmi              6916  0 
sony_acpi               5516  0 
pcc_acpi               11392  0 
hotkey                  9508  0 
dev_acpi               11396  0 
i2c_acpi_ec             5760  0 
button                  6672  0 
battery                 9604  0 
container               4608  0 
ac                      4996  0 
af_packet              20232  2 
p80211                 30992  0 
pcspkr                  3652  0 
rtc                    11832  0 
yenta_socket           22540  2 
rsrc_nonstatic         12032  1 yenta_socket
pcmcia_core            44932  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_intel8x0           30144  1 
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  0 
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm
i2c_sis96x              5252  0 
i2c_core               19728  2 i2c_acpi_ec,i2c_sis96x
shpchp                 80612  0 
pci_hotplug            24628  1 shpchp
sis_agp                 8452  1 
agpgart                32328  1 sis_agp
dm_mod                 50364  1 
joydev                  9280  0 
tsdev                   7616  0 
evdev                   9088  1 
ndiswrapper           114376  0 
psmouse                26116  0 
mousedev               10912  1 
parport_pc             31812  0 
lp                     11460  0 
parport                32072  2 parport_pc,lp
md                     40656  0 
ext3                  115976  1 
jbd                    48536  1 ext3
thermal                13192  0 
processor              23100  2 powernow_k8,thermal
fan                     4740  0 
sis900                 19456  0 
mii                     5248  1 sis900
ehci_hcd               29448  0 
ohci_hcd               18564  0 
usbcore               104188  4 ndiswrapper,ehci_hcd,ohci_hcd
ide_cd                 36996  0 
cdrom                  33952  1 ide_cd
ide_disk               16128  3 
ide_generic             1664  0 
sis5513                14472  1 
ide_core              125268  4 ide_cd,ide_disk,ide_generic,sis5513
unix                   24624  784 
vesafb                  8088  0 
capability              5000  0 
commoncap               6784  1 capability
vga16fb                12232  1 
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72 
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon

```

One thing I *did* notice was when plugging in the card, the device - or rather *a* device - showed up in System->Administration->Device Manager. As a sub-device to "PCI1410 PC card Cardbus Controller," an "Unknown Device" showed up:

[IMG]http://jazzcrazed.com/images/device-manager-unknown-device-screen.png[/IMG]

For what it's worth, that Cardbus Controller has a suspicious "unknown" entry of its own:

[IMG]http://jazzcrazed.com/images/device-manager-cardbus-unknown.png[/IMG]

Note the "unknown" under the Device Type and Capabilities entry. I would expect those fields would be well known if it were to work at all.

Think any of that is relevant at all? Or am I being a naive sherlock?

Any help at all is much appreciated!

Best,
JazzCrazed

---

