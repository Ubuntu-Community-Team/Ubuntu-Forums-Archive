---
title: "Wi-Fi, but no internet - Ubuntu 14.04"
date: 2014-05-24
forum: Networking &amp; Wireless
---

### Post by louis9 on 2014-05-24
I just installed Ubuntu 14.04 on my computer and I can connect to the wifi, but then can't access the internet. If it helps, I'm using an Edimax EW-7612Pin V2 NIC. Also, a couple of years ago, I installed Linux Mint 13 on the same computer and managed to get the connection working fine.

Please help if you can?

Thanks a lot,
Louis

---

### Post by chili555 on 2014-05-24
Let's start by disconnecting the ethernet, if any, try to connect and run and post:```
nm-tool
```

---

### Post by louis9 on 2014-05-24
No ethernet, but just disconnected from the wi-fi and here is the result:

NetworkManager Tool
 
State: disconnected
 
- Device: eth0-----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        50:E5:49:CB:06:91
 
  Capabilities:
    CarrierDetect:  yes
 
  Wired Properties
    Carrier:         off
 
 
- Device: wlan0----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             disconnected
  Default:           no
  HW Address:        80:1F:02:49:3F:6D
 
  Capabilities:
 
  Wireless Properties
    WEPEncryption:  yes
    WPAEncryption:  yes
    WPA2 Encryption:yes
 
  Wireless AccessPoints

---

### Post by louis9 on 2014-05-24
Here's the output when it is connected to the wi-fi:

NetworkManager Tool
 
State: connected (global)
 
- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        50:E5:49:CB:06:91
 
  Capabilities:
    Carrier Detect:  yes
 
  Wired Properties
    Carrier:         off
 
 
- Device: wlan0  [fattysdad] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             connected
  Default:           yes
  HW Address:        80:1F:02:49:3F:6D
 
  Capabilities:
    Speed:           1 Mb/s
 
  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes
 
  Wireless Access Points (* = current AP)
    SKYF0F8D:        Infra, 7C:4C:A5:02:76:21, Freq 2457 MHz, Rate 54 Mb/s, Strength 77 WPA2
    OrangeD13918:    Infra, 00:26:91:D1:39:1A, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    SKY830D4:        Infra, 7C:4C:A5:7C:56:F5, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WPA2
    *fattysdad:      Infra, 1C:AF:F7:7B:19:01, Freq 2412 MHz, Rate 54 Mb/s, Strength 80 WPA WPA2
 
  IPv4 Settings:
    Address:         192.168.1.4
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
 
    DNS:             192.168.1.1

Thanks again!

---

### Post by chili555 on 2014-05-26
I love when this happens; everything looks just perfect except it doesn't work! Let's try a couple of things. First, confirm that you are actually connected with:```
nm-tool
```We don't need to see the actual result, just confirm you are associated with the access point:> Wireless Access Points (* = current AP)
<snip>
[COLOR="#FF0000"]*[/COLOR]fattysdad: Infra, 1C:AF:F7:7B:19:01, Freq 2412 MHz, Rate 54 Mb/s, Strength 80 WPA WPA2And that you have an IP address:> IPv4 Settings:
Address: 192.168.1.4If so, can you ping the router?```
ping -c3 192.168.1.1
```And a DNS nameserver?```
ping -c3 8.8.8.8
```If the pings fail, let's see what Network Manager is doing:```
dmesg | grep rtl
cat /var/log/syslog | grep -e wlan -e etwork | tail -n20
```You could also try a driver parameter:```
sudo modprobe -r rtl8192ce
sudo modprobe rtl8192ce swenc=1
```Finally, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, I have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. After making these changes, reboot the router.

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or vim if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close gedit.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

---

### Post by louis9 on 2014-05-26
[SIZE=2][FONT=courier new]It all seems to be connected fine, but I can't ping either the router or the DNS.
Here's the result when I ping did "dmesg | grep rtl" then "cat /c/log/syslog | grep -e wlan -e etwork | tail -n20":
[/FONT][/SIZE][SIZE=2][FONT=courier new]
louis@louis-GA-970A-UD3:~$ dmesg | grep rtl[/FONT][/SIZE]
[SIZE=2][FONT=courier new][    9.013559]rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin[/FONT][/SIZE]
[SIZE=2][FONT=courier new][    9.084276]ieee80211 phy0: Selected rate control algorithm 'rtl_rc'[/FONT][/SIZE]
[SIZE=2][FONT=courier new][    9.084479] rtlwifi:wireless switch is on[/FONT][/SIZE]
[SIZE=2][FONT=courier new][   13.876413] Moduleslinked in: ctr ccm rfcomm bnep bluetooth snd_hda_codec_hdmi joydev hid_genericusbhid hid uvcvideo snd_usb_audio videobuf2_vmalloc videobuf2_memopsgspca_sn9c20x snd_usbmidi_lib videobuf2_core gspca_main videodev arc4snd_seq_midi snd_seq_midi_event snd_rawmidi snd_hda_codec_realtek snd_hda_intelsnd_hda_codec kvm snd_seq snd_hwdep snd_pcm rtl8192ce rtl_pci serio_rawsnd_seq_device snd_page_alloc k10temp rtlwifi edac_core rtl8192c_commonedac_mce_amd snd_timer radeon mac80211 sp5100_tco i2c_piix4 cfg80211 ttmdrm_kms_helper drm snd mac_hid i2c_algo_bit wmi soundcore parport_pc ppdev lpparport pata_acpi usb_storage firewire_ohci firewire_core crc_itu_t ahci r8169pata_atiixp libahci mii[/FONT][/SIZE]
[SIZE=2][FONT=courier new][   13.876489]  [<ffffffffa04503ad>] ?rtl_is_special_data+0x2d/0x110 [rtlwifi][/FONT][/SIZE]
[SIZE=2][FONT=courier new]louis@louis-GA-970A-UD3:~$ cat /c/log/syslog | grep -e wlan-e etwork | tail -n20[/FONT][/SIZE]
[SIZE=2][FONT=courier new]cat: /c/log/syslog: No such file or directory

I got disconnected when I did "sudo modprobe -r rtl8192ce" then "sudo modprobe rtl8192ce swenc=1" didn't output anything.

My router is currently on a mode with both WPA and WPA2. There is no WPA2-AES - only WPA and WPA2. Which of these is best, and will changing this affect other computers using this router?

The regdomain is currently set to 00. I do have gedit, but it says that I don't have gksudo, so I can't change the regdomain like that.

The IPv6 was set to automatic, but I just changed it to ignore.

Thanks again![/FONT][/SIZE]

---

### Post by chili555 on 2014-05-26
> louis@louis-GA-970A-UD3:~$ cat [COLOR="#FF0000"]/c/log/syslog[/COLOR] | grep -e wlan-e etwork | tail -n20
cat: /c/log/syslog: No such file or directory
I actually asked for:```
cat [COLOR="#FF0000"]/var/log/syslog[/COLOR] | grep -e wlan -e etwork | tail -n20
```> only WPA and WPA2. Which of these is best, and will changing this affect other computers using this router?WPA2 only; see if, in selecting this, there is a choice between WPA2-TKIP and WPA2-AES. WPA2-AES is preferred.

It will only affect any other users if they have *really* old equipment that doesn't support WPA2. Of course, when you make the change and reboot the router, all the users will drop off momentarily, therefore, I suggest you make any changes late at night, early in the morning or when everyone else is at work or school.> [ 13.876413] [COLOR="#FF0000"]Modules linked in[/COLOR]: ctr ccm rfcomm bnep bluetooth snd_hda_codec_hdmi joydev hid_genericusbhid hid uvcvideo snd_usb_audio videobuf2_vmalloc
<snip>This is sometimes indicative of a bigger problem or something that crashed or almost crashed. I suggest you find out what happened around 13.876xx in the boot process:```
dmesg | less
```Use the arrow keys to scroll down to that moment and see what went wrong. It may or may not be a part of the problem here.

---

### Post by louis9 on 2014-05-26
[FONT=arial]Sorry about that... Here is the code for "cat /var/log/syslog | grep -e wlan -e etwork | tail -n20":

[/FONT][FONT=arial]May 26 19:56:00 louis-GA-970A-UD3 NetworkManager[818]: <info>   gateway 192.168.1.1 [/FONT]
[FONT=arial]May 26 19:56:00 louis-GA-970A-UD3 NetworkManager[818]: <info>   hostname 'dhcppc2' [/FONT]
[FONT=arial]May 26 19:56:00 louis-GA-970A-UD3 NetworkManager[818]: <info>   nameserver '192.168.1.1' [/FONT]
[FONT=arial]May 26 19:56:00 louis-GA-970A-UD3 NetworkManager[818]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled... [/FONT]
[FONT=arial]May 26 19:56:00 louis-GA-970A-UD3 NetworkManager[818]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started... [/FONT]
[FONT=arial]May 26 19:56:01 louis-GA-970A-UD3 NetworkManager[818]: <info> (wlan0): device state change: ip-config -> secondaries (reason 'none') [70 90 0] [/FONT]
[FONT=arial]May 26 19:56:01 louis-GA-970A-UD3 NetworkManager[818]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete. [/FONT]
[FONT=arial]May 26 19:56:01 louis-GA-970A-UD3 NetworkManager[818]: <info> (wlan0): device state change: secondaries -> activated (reason 'none') [90 100 0] [/FONT]
[FONT=arial]May 26 19:56:05 louis-GA-970A-UD3 NetworkManager[818]: <info> NetworkManager state is now CONNECTED_GLOBAL [/FONT]
[FONT=arial]May 26 19:56:05 louis-GA-970A-UD3 NetworkManager[818]: <info> Policy set 'fattysdad' (wlan0) as default for IPv4 routing and DNS. [/FONT]
[FONT=arial]May 26 19:56:05 louis-GA-970A-UD3 NetworkManager[818]: <info> DNS: starting dnsmasq... [/FONT]
[FONT=arial]May 26 19:56:05 louis-GA-970A-UD3 NetworkManager[818]: <warn> dnsmasq not available on the bus, can't update servers. [/FONT]
[FONT=arial]May 26 19:56:05 louis-GA-970A-UD3 NetworkManager[818]: <error> [1401130565.38131] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name [/FONT]
[FONT=arial]May 26 19:56:05 louis-GA-970A-UD3 NetworkManager[818]: <warn> DNS: plugin dnsmasq update failed [/FONT]
[FONT=arial]May 26 19:56:05 louis-GA-970A-UD3 NetworkManager[818]: <info> Writing DNS information to /sbin/resolvconf [/FONT]
[FONT=arial]May 26 19:56:15 louis-GA-970A-UD3 NetworkManager[818]: <info> Activation (wlan0) successful, device activated. [/FONT]
[FONT=arial]May 26 19:56:15 louis-GA-970A-UD3 NetworkManager[818]: <info> WiFi hardware radio set enabled [/FONT]
[FONT=arial]May 26 19:56:15 louis-GA-970A-UD3 NetworkManager[818]: <warn> dnsmasq appeared on DBus: :1.50 [/FONT]
[FONT=arial]May 26 19:56:15 louis-GA-970A-UD3 NetworkManager[818]: <info> Writing DNS information to /sbin/resolvconf [/FONT]
[FONT=arial]May 26 19:56:25 louis-GA-970A-UD3 wpa_supplicant[1088]: wlan0: CTRL-EVENT-SCAN-STARTED 


And here is the code for "dmesg | less" from just before it starts changing around [[COLOR=#000000][I]13.876413]:

[/I][/COLOR][/FONT][   13.516356]  [<ffffffff8172719d>] apic_timer_interrupt+0x6d/0x80 
[   13.516357]  <EOI> 
[   13.516359] ---[ end trace f91bce5bd6e39414 ]--- 
[   14.869162] 3:2:1: cannot get freq at ep 0x84 
[   14.870537] 3:2:1: cannot get freq at ep 0x84 
[   14.881173] 3:2:1: cannot get freq at ep 0x84 
[   14.882675] 3:2:1: cannot get freq at ep 0x84 
[   14.887934] retire_capture_urb: 168 callbacks suppressed 
[   15.919907] ata1.00: exception Emask 0x10 SAct 0x9 SErr 0x90202 action 0xe frozen 
[   15.919913] ata1.00: irq_stat 0x00400000, PHY RDY changed 
[   15.919916] ata1: SError: { RecovComm Persist PHYRdyChg 10B8B } 
[   15.919919] ata1.00: failed command: READ FPDMA QUEUED 
[   15.919923] ata1.00: cmd 60/20:00:e0:2a:93/00:00:48:00:00/40 tag 0 ncq 16384 in 
[   15.919923]          res 40/00:00:e0:2a:93/00:00:48:00:00/40 Emask 0x10 (ATA bus error) 
[   15.919925] ata1.00: status: { DRDY } 
[   15.919927] ata1.00: failed command: READ FPDMA QUEUED 
[   15.919931] ata1.00: cmd 60/88:18:20:dd:95/00:00:48:00:00/40 tag 3 ncq 69632 in 
[   15.919931]          res 40/00:00:e0:2a:93/00:00:48:00:00/40 Emask 0x10 (ATA bus error) 
[   15.919933] ata1.00: status: { DRDY } 
[   15.919937] ata1: hard resetting link 
[   20.793607] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300) 
[   20.794757] ata1.00: configured for UDMA/133 
[   20.809599] ata1: EH complete 
[  122.484665] systemd-hostnamed[2120]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname! 
(END)




Also, I just changed to WPA2, but haven't noticed any difference.

Hope this helps and thanks again!

---

### Post by chili555 on 2014-05-27
> And here is the code for "dmesg | less" from just before it starts changing around [13.876413]:Evidently you rebooted because now the difficulty is earlier. Here > we see just the last lines of the trouble:> [ 13.516356] [<ffffffff8172719d>] apic_timer_interrupt+0x6d/0x80 
[ 13.516357] <EOI> 
[ 13.516359] ---[ end trace f91bce5bd6e39414 ]--- You might reboot and run:```
dmesg > dmesg.txt
```Find the file dmesg.txt in your user directory and paste it here so we can examine the whole thing: [http://paste.ubuntu.com/](http://paste.ubuntu.com/)> The regdomain is currently set to 00. I do have gedit, but it says that I don't have gksudo, so I can't change the regdomain like that.Just use sudo and do this before the reboot I requested above, please.

---

### Post by louis9 on 2014-07-11
Hi Chili, sorry it's taken so long, but I had exams and thought it would be better if I was focusing on them rather than my computer. Anyway, I set the regdomain to GB as you requested and ran the code "dmesg > dmesg.txt". Here is the code from the dmesg.txt file: [http://paste.ubuntu.com/7782015/](http://paste.ubuntu.com/7782015/)

Sorry again for the long delay and thanks again for helping me out! Cheers :)

---

### Post by chili555 on 2014-07-12
> I had exams and thought it would be better if I was focusing on them rather than my computer. Absolutely! Education and, by extension, your career will influence the entire rest of your life. On the other hand, ten years from now, no-one will recall the twitchy Edimax and the less twitchy Chili.

We see this in the paste:> WARNING: CPU: 4 PID: 743 at /build/buildd/linux-3.13.0/net/mac80211/rate.c:526 ieee80211_get_tx_rates+0x273/0x7f0 [mac80211]() This clearly is a wireless issue. A Google search suggests that firmware may be an issue here. Is your package linux-firmware up to date?```
sudo dpkg -s linux-firmware | grep -i version
```The version I have is 1.127.4. If yours is earlier, please update:```
sudo apt-get update && sudo apt-get -y upgrade
```Reboot and check dmesg for the warning. If it persists, we'll install a later driver.

---

### Post by Sljepac on 2014-07-13
Hi,

I have had very similar problems and wanted to join the conversation and ask for help. I have a fresh install of Xubuntu 14.04. Network manager would show connection, but I couldn't ping even my router. Drivers didn't seem to be a problem.

However, before posting here, I first went through this guide: [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)
It covers every possible problem to detect what is wrong with wireless connection. With me, it was the encryption. Once I disabled encryption, everything worked perfectly. Then, I turned the encryption back on (WPA2 with AES, but this time without WPS) and it continued to work.

I am not saying the same will work for everyone, but this guide helped a lot.
I hope it helps!

---

### Post by louis9 on 2014-07-13
The version is 1.127, so I assume it's not quite the latest but I can't actually update the firmware, because my internet connection isn't working haha... any ideas? - Could I perhaps download the firmware on a different computer? Thanks again :)

---

### Post by chili555 on 2014-07-13
Indeed you can. Get this: [http://security.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.127.4_all.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.127.4_all.deb)

Drop it on the desktop of the subject computer and install it from the terminal:```
cd ~/Desktop
sudo dpkg -i linux-firmware*.deb
```I would also heed Sljepac's suggestion and turn off WPS in the router. Reboot the computer and the router and check:```
dmesg | grep -e rtl -e rate.c
```Any improvements?

---

### Post by louis9 on 2014-07-13
Tried both those things, but no joy I'm afraid :(

---

### Post by chili555 on 2014-07-13
> **louis9 said:**
> Tried both those things, but no joy I'm afraid :(Is the error sequence the same in *dmesg*?

---

### Post by louis9 on 2014-07-14
Yep I'm afra[FONT=arial]id it looks exactl[/FONT]y the same around "[COLOR=#000000]*WARNING: CPU: 4 PID: 743 at /build/buildd/linux-3.13.0/net/mac80211/rate.c:526 ieee80211_get_tx_rates+0x273/0x7f0 [mac80211]()"[FONT=arial]  [SIZE=2]if that's what you mean?[/SIZE][/FONT]*[/COLOR]

---

### Post by chili555 on 2014-07-14
> because my internet connection isn't working haha.In order to update the wireless driver, we really need to use the ethernet. What is wrong with it? Which device is it?```
lspci -nn | grep 0200
```We are painting ourselves into a corner here.

---

### Post by louis9 on 2014-07-14
I don't actually have an ethernet port on the computer. Is that a problem? I meant that the internet connection doesn't work on that computer, but it does on the others, so if there's any way to find drivers on the internet I can then transfer them via USB, but I can't find any Linux drivers for my NIC on the edimax website.
Anyway, here's the code you requested: "04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)"

---

### Post by chili555 on 2014-07-14
> I don't actually have an ethernet port on the computer.Really? This strongly suggests that you do:> 04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)Can you please double-check?

Actually, if you can use ethernet instead of the twitchy Edimax, you will have a safer, more reliable internet connection. 

My suggestion is to compile the driver from source code. It requires the code as well as linux-headers and build-essential and all their dependencies; a grueling, complex task using nothing but another computer and a USB drive. With a working ethernet connection, it's about a five minute task.

Are you able to use the ethernet instead?

---

### Post by louis9 on 2014-07-14
How does it take 2 years for me to notice that a computer that I built has an ethernet port built into the motherboard? I don't know, but thank you chili, you truly are some sort of amazing wizard-guru thing. I will try to find an ethernet cable somewhere now and get back to you...

---

### Post by louis9 on 2014-07-14
Joy at last! Connected via the ethernet cable, which runs right around the outside of my house - but it works nonetheless, so thank you! How do I get drivers now then?

---

### Post by chili555 on 2014-07-14
You have drivers but we are going to try a later version. It may or may not help. You may safely copy and paste this command:```
sudo apt-get update && sudo apt-get -y upgrade
```You will probably get a later kernel version, also known as linux-image, requiring a reboot. After doing so, check dmesg for our famous warning. If it is not there, detach the ethernet and see if you connect with wireless. If so, we'll stop here.

I'll be here for a while, so I'll wait for your interim report.

---

### Post by coffeecat on 2014-07-14
> **chili555 said:**
> You may safely copy and paste this command:```
sudo apt-get update && sudo apt-get -y upgrade
```You will probably get a later kernel version, also known as linux-image, requiring a reboot.

@chili555, sorry to interfere, but I believe the OP will need dist-upgrade rather than upgrade to get a newer kernel.

---

### Post by louis9 on 2014-07-14
Got the drivers, but no luck - still showing that warning in dmesg. I think I've got the latest distro (14.04), but if not, how do I upgrade it? Cheers :)

---

### Post by chili555 on 2014-07-14
> **louis9 said:**
> Got the drivers, but no luck - still showing that warning in dmesg. I think I've got the latest distro (14.04), but if not, how do I upgrade it? Cheers :)Did you proceed as my esteemed colleague coffeecat suggests, quite correctly?```
sudo apt-get -y dist-upgrade
```Was a reboot suggested?

---

### Post by louis9 on 2014-07-14
I did do it. It didn't suggest a reboot, but I did anyway. I just ran that code, but it did nothing, saying "0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade"

---

### Post by chili555 on 2014-07-14
Let's try the easy way first:```
sudo apt-get install build-essential linux-headers-generic git
git clone https://github.com/FreedomBen/rtl8188ce-linux-driver.git
cd rtl8188ce-linux-driver
make
```Answer 'y' for yes to the kernel question.```
sudo make install
```Reboot.

I will be away for a few hours; I'll check in later.

---

### Post by louis9 on 2014-07-14
Did that, but still getting the same message in dmesg. Sorry, this must be getting quite boring...

---

### Post by louis9 on 2014-07-15
I just went to get some new graphics drivers and saw something saying (I assume referring to all types of drivers) that I had no proprietary drivers installed. Unless I'm mistaken or the NIC drivers you got me to install before were open source, it looks like the drivers didn't install properly. Any thoughts? Thanks :)

---

### Post by chili555 on 2014-07-15
The only proprietary drivers I am aware of that are referred to by the 'Additional Drivers' tool are for Broadcom. You have and need none.

I am still trying to work out another try at a solution. I hope to have an answer this evening.

Edit: I have been trying to compile the backports package in order to get a possibly better rtl8192ce but have run into a roadblock. Please see: [https://bugs.launchpad.net/ubuntu/+bug/1342703](https://bugs.launchpad.net/ubuntu/+bug/1342703)

---

