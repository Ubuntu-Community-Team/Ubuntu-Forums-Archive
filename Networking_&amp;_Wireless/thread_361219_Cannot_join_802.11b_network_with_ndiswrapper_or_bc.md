---
title: "Cannot join 802.11b network with ndiswrapper or bcm43xx"
date: 2007-02-14
forum: Networking &amp; Wireless
---

### Post by waster on 2007-02-14
Does anyone have this problem?

Using Feisty, I can set of 802.11g networking fine using ndiswrapper and until recently bcm43xx. However, the network_type is 802.11g and although iwlist eth0 scan shows the 802.11b network, the AP never associates.

iwpriv eth0 network_type b

is supposed to work, but ndiswrapper reports this as "invalid". bcm43xx doesn't offer this ioctl at all.

Using bcm43xx, I've redone all the fwcutter stuff, but in the dmesg output, I now get:

bcm43xx: YOUR FIRMWARE IS TOO OLD. Firmware from binary drivers older than version 4.x is unsupported. You must upgrade your firmware files.

Is there new firmware, or is the Feisty kernel just confused?

Any ideas? Any other sufferers? Thanks.

---

### Post by darrenm on 2007-02-14
Same here. Only with 2.6.20-8. Doesnt happen with 2.6.20-6

---

### Post by jrb114 on 2007-02-15
I've got the same problem with the latest 2.6.20.8 kernel, running on my iBook (powerpc). I've tried using the widely used wl_apsa (or similar) and the installed firmware from Mac OS (which is version 3.90.34.0.p18 ) according to bcm43xx-fwcutter.

So, until I get this sorted out, I'm wireless less again :( 

On a positive note, 2.6.20 is the only kernel version I've ever managed to get to play well with the wireless, using WPA and network manager.

Let's hope this is just a short lived bug.

J

---

### Post by jrb114 on 2007-02-15
Having done a quick google...

I'm not sure that it is a bug.

[http://www.mail-archive.com/bcm43xx-dev@lists.berlios.de/msg03052.html](http://www.mail-archive.com/bcm43xx-dev@lists.berlios.de/msg03052.html)

Seems the developers are changing things. However, these things are /way/ beyond me, so I hoep I haven't got the wrong end of the stick

---

### Post by pidgas on 2007-02-16
exact same problem...PLUS with previous 2.6.20 kernels on feisty haven't been able to connect reliably to unencrypted networks.

---

### Post by android6011 on 2007-02-16
me too. any one have any ideas?

---

### Post by darrenm on 2007-02-16
Well it looks like Feisty is using the new devicescape stack rather than the old softmac. The new driver is supposed to be better but it only supports V4 firmware. Where that firmware is going to come from is another matter...
[https://bugs.launchpad.net/ubuntu/+source/bcm43xx-fwcutter/+bug/85099](https://bugs.launchpad.net/ubuntu/+source/bcm43xx-fwcutter/+bug/85099)

---

### Post by jrb114 on 2007-02-16
*Warning*: this doesn't work... as at 16 February 2007. If anyone else has any other version 4 firmware for the bcm43xx, please post and let us know.

Hi all, I've got an update, but I haven't yet had the chance to test it.

This will allow you to get the latest version (release 4.80) of the broadcom firmware.

I'm using a dapper machine now, so it's got an old version of bcm43xx-fwcutter. You need the new one. I'm not sure if it's in feisty yet, but I'll check when I can.

Get the latest version of the firmware cutter, and unzip it.

```

wget -c http://download2.berlios.de/bcm43xx/bcm43xx-fwcutter-006.tar.bz2
bunzip2 bcm43xx-fwcutter-006.tar.bz2
tar -xvvf bcm43xx-fwcutter-006.tar

```

We now need to build the latest version. And you may well need build-essential, too.

```

cd bcm43xx-fwcutter-006
sudo apt-get install build-essential
make

```

If you look inside the README file, it lists places where you can get firmware revisions from. We want the latest version, 4.80:

```

wget -c http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2
bunzip2 broadcom-wl-4.80.53.0.tar.bz2
tar -xvvf broadcom-wl-4.80.53.0.tar

```

Now we can cut the firmware from this, using the newly compiled version of bcm43xx-fwcutter (hence ./bcm43xx-fwcutter) and we want to put it in /lib/firmware

```

sudo ./bcm43xx-fwcutter -w /lib/firmware/ broadcom-wl-4.80.53.0/kmod/wl_apsta.o

```

Now, assuming bcm43xx isn't loaded, we can correctly load the module with the latest firmware. (This is the bit I've not tried, as I'm not on my feisty machine.)

So, remove the existing module *this will kill anything currently using it*, and then reload it.

```

sudo rmmod bcm43xx
sudo modprobe bcm43xx

```

And hopefully, you won't get any of those pesky wrong version errors :)

I'll test this soon, so please let me know how it goes.

J

---

### Post by intosi on 2007-02-16
This doesn't seem to work properly.  The bcm4300-fwcutter-006 works as it should, and it extracts the firmware correctly.  The wireless card, however, only comes to live partially.

With plain Herd-3, I could connect to all my networks, both WPA, WEP and unencrypted using my Dell Latitude D610 with a BCM4318.  With the new kernel and the just extracted firmware files, I can load the driver again, and ifconfig returns correct data.  However, iwlist eth1 scan gives 'No scan results', the network connection applet doesn't give me a list of networks, and I cannot connect manually to any network.

When running [FONT="Courier New"]iwlist eth1 channel[/FONT], I get:
```
eth1      0 channels
          Current Frequency=2.412 GHz
```

---

### Post by darrenm on 2007-02-16
Nope doesnt work. Exactly the same as the Windows driver firmware for this card that I tried earlier, firmware gets loaded, light starts flashing but no network access and it hard locks the system. 

The 2 links for the bcmwl5.sys v4 in the README don't work so it looks like no-one has any v4 firmware that will work and the new drivers don't support v3. Fabulous. I hope the devs don't stick with this new driver otherwise everyone with a Broadcom card will have to end up using ndiswrapper.

---

### Post by darrenm on 2007-02-16
I'm sick of these crap-*** companies that provide less than zero support for the community. Broadcom, ATi etc. so I've already got rid of my ATi card, now I've just bought an Intel wifi mini-PCI card and I'm using Intel GMA915 video on my laptop.

---

### Post by jrb114 on 2007-02-16
Yep, Darren's right. I get exactly the same problem on my iBook, it doesn't work and just locks up the kernel.

It gives an interesting line in /var/log/syslog

Feb 16 19:33:58 monster kernel: [  372.533912] eth1: Initial auth_alg=0
Feb 16 19:33:58 monster kernel: [  372.533931] eth1: authenticate with AP 00:00:00:00:00:00
Feb 16 19:33:58 monster kernel: [  372.562461] ssb: Switching to core 0
Feb 16 19:33:58 monster kernel: [  372.562678] ssb: Switching to core 1
Feb 16 19:33:58 monster kernel: [  372.564472] ------------[ cut here ]------------
Feb 16 19:33:58 monster kernel: [  372.564484] kernel BUG at mm/slab.c:597!
Feb 16 19:33:58 monster kernel: [  372.564794] Oops: Exception in kernel mode, sig: 5 [#1]
Feb 16 19:33:58 monster kernel: [  372.564800] 
Feb 16 19:33:58 monster kernel: [  372.564804] Modules linked in: hci_usb binfmt_misc rfcomm l2cap bluetooth radeon drm ppdev lp parport cpufreq_powersave cpufreq_conservative cpufreq_userspace cpufreq_stats cpufreq_ondemand ipv6 sbp2 apm_emu snd_powermac fuse snd_aoa_codec_tas snd_aoa_fabric_layout snd_aoa snd_aoa_i2sbus snd_pcm_oss snd_mixer_oss snd_pcm snd_page_alloc snd_seq_dummy snd_seq_oss sg snd_seq_midi joydev snd_rawmidi snd_seq_midi_event snd_seq sd_mod snd_timer snd_seq_device snd usblp soundcore appletouch snd_aoa_soundbus pmac_zilog serial_core arc4 ecb blkcipher rc80211_simple bcm43xx ssb 80211 uninorth_agp agpgart af_packet tsdev evdev usb_storage scsi_mod libusual ext3 jbd mbcache usbhid hid ide_cd cdrom ide_disk sungem sungem_phy ohci1394 ieee1394 ehci_hcd ohci_hcd usbcore capability commoncap
Feb 16 19:33:58 monster kernel: [  372.564972] NIP: C0084688 LR: C01CDD90 CTR: C01CDC50
Feb 16 19:33:58 monster kernel: [  372.564982] REGS: d90a5c40 TRAP: 0700   Not tainted  (2.6.20-8-powerpc)
Feb 16 19:33:58 monster kernel: [  372.564989] MSR: 00021032 <ME,IR,DR>  CR: 24002482  XER: 00000000
Feb 16 19:33:58 monster kernel: [  372.565005] TASK = e4fbe7c0[5536] 'wpa_supplicant' THREAD: d90a4000
Feb 16 19:33:58 monster kernel: [  372.565012] GPR00: 00000001 D90A5CF0 E4FBE7C0 EFEF1000 00000018 D90A5D38 EFFEA0FC 00000000 
Feb 16 19:33:58 monster kernel: [  372.565030] GPR08: C09909D8 C09A4E20 C03A7000 00000000 84002424 1006D534 00000000 00000000 
Feb 16 19:33:58 monster kernel: [  372.565048] GPR16: 3082EAE8 3082EBDC 1003E5F4 3082EBFC ED0E7B0C EDF07800 D90A5E58 FFFF8914 
Feb 16 19:33:58 monster kernel: [  372.565067] GPR24: ED0E7B00 E7596560 00000000 00000000 ED09E750 EFEF1000 00009032 EF642560 
Feb 16 19:33:58 monster kernel: [  372.565087] NIP [C0084688] kfree+0x50/0xc4
Feb 16 19:33:58 monster kernel: [  372.565104] LR [C01CDD90] skb_release_data+0x80/0xc4
Feb 16 19:33:58 monster kernel: [  372.565118] Call Trace:
Feb 16 19:33:58 monster kernel: [  372.565124] [D90A5CF0] [EF608B20] 0xef608b20 (unreliable)
Feb 16 19:33:58 monster kernel: [  372.565147] [D90A5D10] [C01CDD90] skb_release_data+0x80/0xc4
Feb 16 19:33:58 monster kernel: [  372.565158] [D90A5D20] [C01CDA28] kfree_skbmem+0x18/0xf4
Feb 16 19:33:58 monster kernel: [  372.565169] [D90A5D30] [F24E655C] bcm43xx_destroy_dmaring+0xcc/0x1a4 [bcm43xx]
Feb 16 19:33:58 monster kernel: [  372.565212] [D90A5D60] [F24E6820] bcm43xx_dma_free+0x7c/0xa0 [bcm43xx]
Feb 16 19:33:58 monster kernel: [  372.565234] [D90A5D80] [F24D3334] bcm43xx_shutdown_all_wireless_cores+0x9c/0xe8 [bcm43xx]
Feb 16 19:33:58 monster kernel: [  372.565256] [D90A5DA0] [F24D3468] bcm43xx_free_board+0x3c/0x64 [bcm43xx]
Feb 16 19:33:58 monster kernel: [  372.565276] [D90A5DC0] [F24D45AC] bcm43xx_net_stop+0x4c/0x68 [bcm43xx]
Feb 16 19:33:58 monster kernel: [  372.565298] [D90A5DD0] [F24A8E44] ieee80211_stop+0x148/0x160 [80211]
Feb 16 19:33:58 monster kernel: [  372.565364] [D90A5E00] [C01D462C] dev_close+0xa4/0xd8
Feb 16 19:33:58 monster kernel: [  372.565380] [D90A5E10] [C01D3524] dev_change_flags+0x64/0x168
Feb 16 19:33:58 monster kernel: [  372.565392] [D90A5E30] [C022396C] devinet_ioctl+0x5bc/0x71c
Feb 16 19:33:58 monster kernel: [  372.565409] [D90A5EA0] [C0224024] inet_ioctl+0xb0/0xdc
Feb 16 19:33:58 monster kernel: [  372.565421] [D90A5EB0] [C01C6E94] sock_ioctl+0xd8/0x278
Feb 16 19:33:58 monster kernel: [  372.565439] [D90A5ED0] [C00971D0] do_ioctl+0x38/0x84
Feb 16 19:33:58 monster kernel: [  372.565455] [D90A5EE0] [C00972A0] vfs_ioctl+0x84/0x3f4
Feb 16 19:33:58 monster kernel: [  372.565467] [D90A5F10] [C00976A0] sys_ioctl+0x90/0xa0
Feb 16 19:33:58 monster kernel: [  372.565479] [D90A5F40] [C0013510] ret_from_syscall+0x0/0x38
Feb 16 19:33:58 monster kernel: [  372.565498] --- Exception: c01 at 0xfcf6008
Feb 16 19:33:58 monster kernel: [  372.565512]     LR = 0xfcf5fa0
Feb 16 19:33:58 monster kernel: [  372.565517] Instruction dump:
Feb 16 19:33:58 monster kernel: [  372.565523] 7c000124 3d60c035 3d3d4000 814b066c 5529c9f4 7c09502e 7d295214 700b4000 
Feb 16 19:33:58 monster kernel: [  372.565542] 4082005c 80090000 68000080 5400cffe <0f000000> 80690018 83e30000 813f0000 
Feb 16 19:34:18 monster kernel: [  372.565561]  <0>------------[ cut here ]------------
Feb 16 19:34:18 monster kernel: [  392.342829] kernel BUG at mm/slab.c:597!
Feb 16 19:34:18 monster kernel: [  392.342846] Oops: Exception in kernel mode, sig: 5 [#2]
Feb 16 19:34:18 monster kernel: [  392.342852] 
Feb 16 19:34:18 monster kernel: [  392.342856] Modules linked in: hci_usb binfmt_misc rfcomm l2cap bluetooth radeon drm ppdev lp parport cpufreq_powersave cpufreq_conservative cpufreq_userspace cpufreq_stats cpufreq_ondemand ipv6 sbp2 apm_emu snd_powermac fuse snd_aoa_codec_tas snd_aoa_fabric_layout snd_aoa snd_aoa_i2sbus snd_pcm_oss snd_mixer_oss snd_pcm snd_page_alloc snd_seq_dummy snd_seq_oss sg snd_seq_midi joydev snd_rawmidi snd_seq_midi_event snd_seq sd_mod snd_timer snd_seq_device snd usblp soundcore appletouch snd_aoa_soundbus pmac_zilog serial_core arc4 ecb blkcipher rc80211_simple bcm43xx ssb 80211 uninorth_agp agpgart af_packet tsdev evdev usb_storage scsi_mod libusual ext3 jbd mbcache usbhid hid ide_cd cdrom ide_disk sungem sungem_phy ohci1394 ieee1394 ehci_hcd ohci_hcd usbcore capability commoncap
Feb 16 19:34:18 monster kernel: [  392.343023] NIP: C0084688 LR: C00A7F70 CTR: C00A7FD8
Feb 16 19:34:18 monster kernel: [  392.343032] REGS: ec26dde0 TRAP: 0700   Not tainted  (2.6.20-8-powerpc)
Feb 16 19:34:18 monster kernel: [  392.343039] MSR: 00021032 <ME,IR,DR>  CR: 20004448  XER: 00000000
Feb 16 19:34:18 monster kernel: [  392.343055] TASK = effcc050[4437] 'pbbuttonsd' THREAD: ec26c000
Feb 16 19:34:18 monster kernel: [  392.343062] GPR00: 00000001 EC26DE90 EFFCC050 ED3D7000 DC62BBC0 00000000 00000000 00000000 
Feb 16 19:34:18 monster kernel: [  392.343079] GPR08: DC62BBC0 C094EAE0 C03A7000 00000000 00000000 10036C58 0171CAEC 00241AC8 

== end of long waffle ==

So, there seems to be something weird in slab.c at line 597 (beyond me), and also, the access point hasn't been recognised at all, it's down as 00:00:00:00 etc.

Well, I think I'm out of ideas. I'll put a note on the other message, that it doesn't really work.

James

---

### Post by darrenm on 2007-02-16
Post on the bug report [https://launchpad.net/ubuntu/+source/bcm43xx-fwcutter/+bug/85099](https://launchpad.net/ubuntu/+source/bcm43xx-fwcutter/+bug/85099) , its still undecided importance and needs to be critical.

---

### Post by intosi on 2007-02-16
I was so happy when my network card started to work almost out of the box with Feisty, only to be utterly disappointed when it broke this evening...  Unfortunately my new notebook (which my boss already ordered) has a Broadcom p.o.s. card, as well...

---

### Post by jrb114 on 2007-02-16
Well this is new.

I'm configuring the interface manually, using wpa_supplicant and *not* Network Manager. And I'm now posting this via bcm43xx. I don't know what mechanism NM uses to talk to the driver, but it's not reliable. I had a similar thing before under Dapper, it would work through wpa_supplicant but not NM.

I'll post the information to the bug report, although this might suggest that the problem isn't entirely with the firmware.

Cheers,

J

---

### Post by darrenm on 2007-02-16
Interesting. It would suggest a new function of the V4 firmware is not supported correctly in NM, possibly to do with WPA/WEP ? I'm only using WEP here.

---

### Post by pidgas on 2007-02-16
First, where can the 4.x firmware be found?  Anyone got a linky?

Second, when it was working for me (<=2.6.20-6),  I had tremendous difficulty connecting to unencrypted networks (using Broadcom 4318 adapter and either ndiswrapper or bcm43xx).  Connected like a charm with my WPA network at home.  Anyone else have a similar experience?  Anyone have the same experience and fix it?

---

### Post by Golgoth on 2007-02-17
> **darrenm said:**
> Same here. Only with 2.6.20-8. Doesnt happen with 2.6.20-6

I can confirm this...

---

### Post by guX on 2007-02-19
> **intosi said:**
> This doesn't seem to work properly.  The bcm4300-fwcutter-006 works as it should, and it extracts the firmware correctly.  The wireless card, however, only comes to live partially.

With plain Herd-3, I could connect to all my networks, both WPA, WEP and unencrypted using my Dell Latitude D610 with a BCM4318.  With the new kernel and the just extracted firmware files, I can load the driver again, and ifconfig returns correct data.  However, iwlist eth1 scan gives 'No scan results', the network connection applet doesn't give me a list of networks, and I cannot connect manually to any network.

When running [FONT="Courier New"]iwlist eth1 channel[/FONT], I get:
```
eth1      0 channels
          Current Frequency=2.412 GHz
```

Slightly off-topic, but did you say you had WPA working? I can't (or couldn't, wireless isn't working at all anymore) get NetworkManager to connect to any WPA networks, I'm just interested to know how you did that. I haven't found anything on the Internet for that.

---

### Post by darrenm on 2007-02-20
Just to make everyone jealous ;) I've bought an Intel mini-PCI wifi card and removed that rubbish BCM4318 based card. I can't believe how much better it is. The wifi light works perfectly, only coming on when there is wifi traffic, it very quickly connects to the AP and I'm now running 2.6.20-8 kernel using the wifi perfectly. I'm now fully Intel on my laptop and its fab. :D

---

### Post by vishna on 2007-02-25
Same problem here using 

05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
        Subsystem: AMBIT Microsystem Corp. Aspire 3022WLMi, 5024WLMi
        Flags: bus master, fast devsel, latency 128, IRQ 23
        Memory at bc000000 (32-bit, non-prefetchable) [size=8K]

and v4 firmware. I upgraded fwcutter to 006 version, made wifi scan, detected 2 networks yet every join attempt causes system lock. Either my card won't work with v4 firmware, either bcm43xx+dscape is not fully functional atm. 

The best configuration seems to be bcm43xx+softmac+v3 firmware (kernel 2.6.20-6-generic) yet after a few hours connection breaks - system reset and then everything is back ok. dmesg is helpful to see what's going on.

Using ndiswrapper I was unable to detect/connect to WPA Enterprise network that is available at my university, on the contrary using normal network it is more stable and faster (g mode available)

---

### Post by darrenm on 2007-02-25
Go Intel. Best thing I ever did..

---

### Post by geekphreak on 2007-02-26
Which intel card did you buy and are you using 32-bit or 64-bit Ubuntu, Edgy, or Feisty?

---

### Post by darrenm on 2007-02-26
lspci says its a ```
Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
``` Im on 32-bit Feisty

---

### Post by geekphreak on 2007-02-26
> **darrenm said:**
> lspci says its a ```
Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
``` Im on 32-bit Feisty
OK, thanks, I am so sick of the bcm4318 that I am seriously thinking about getting a different card... What's gonna suck is removing the keyboard to get to it... But I'd do it to get Ubuntu running the way I want it.

---

### Post by darrenm on 2007-02-27
Dead easy removing the keyboard on most laptops. took me all of 5 mins to do mine.

---

### Post by jrb114 on 2007-02-27
Problem is now solved in 2.6.20.9. I think they've reverted to the old softmac way of working.

See [https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/85404](https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/85404) for more info.

---

