---
title: "WiFi range problems"
date: 2017-04-02
forum: Networking &amp; Wireless
---

### Post by carobaldino on 2017-04-02
Hi there! I'm new to this great Community and new in Ubuntu Linux (This is my first distro ever), and I'm very surprised and glad of it, I really found my first contac with the terminal very friendly and easy to use, unlike the "windows" one.


So, regarding the problem that I have, is that I find a problem with the reception of my WiFi and I think that some configuration here in ubuntu might be involved.
The thing is that, I have a tower PC that I use with a "High Power Wireless USB Adapter" from TP-LINK: TL-WN8200ND.Wait... I now what you think now... 'this newbie did't read the posts before writing this '. Here it's what I did:


At first, the adapter didn't work because it is not compatible with linux, but as this is a huge community, found this beautiful and effective solution here: [https://github.com/pvaret/rtl8192cu-fixes](https://github.com/pvaret/rtl8192cu-fixes) (and following the troubleshooting step)


After that, my adapter is working fine, I tried to conect it to two differents and closer networks and it worked fine... but here is the 'problem'..


I have always used this adapter from Windows, with the utility that comes with the cd (but also, only for windows). It is placed in the same site as always, and on Windows it reach and connects to my house network (I have to say, the network that I connect is not close, it is downstairs - half floor. But untill I can afford a wired connection, I have to survive..), BUT on Ubuntu, it can see it and try to connect, but never finally connect. I tried this several times, and it makes me think that the problem is with Ubuntu..  the adapter does not reach the same effectivity or range power than on Windows.. that's what I think.. 
But.. as this is an amazing OS I was wondering if there is any command or something that could make this powerful, as it works with windows, even without the utility, only the driver.


I've read lots of posts about wifi problems, and based on them, I think that this information from my terminal might be useful for you to think the issue.. 


```

**$ lspci -nnk | grep -iA2 net**
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 01)
    Subsystem: Elitegroup Computer Systems Device [1019:8136]
    Kernel driver in use: r8169

```


```

**$ lsusb**
Bus 001 Device 004: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 001 Device 006: ID 2357:0100  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

```

**$ iwconfig**
wlan0     unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


lo        no wireless extensions.


eth0      no wireless extensions.



```

```

**$ lsmod**
Module                  Size  Used by
bnep                   20480  2 
rfcomm                 65536  0 
bluetooth             466944  10 bnep,rfcomm
binfmt_misc            20480  1 
8192cu                475136  0 
mac80211              651264  0 
cfg80211              487424  1 mac80211
joydev                 20480  0 
i915                 1114112  3 
snd_hda_codec_idt      53248  1 
snd_hda_codec_generic    69632  1 snd_hda_codec_idt
snd_hda_intel          32768  3 
snd_hda_codec         114688  3 snd_hda_codec_idt,snd_hda_codec_generic,snd_hda_intel
gpio_ich               16384  0 
snd_wavefront          36864  0 
snd_cs4236             32768  0 
snd_hda_core           61440  4 snd_hda_codec_idt,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
snd_opl3_lib           20480  2 snd_wavefront,snd_cs4236
snd_wss_lib            28672  2 snd_wavefront,snd_cs4236
snd_hwdep              16384  3 snd_wavefront,snd_hda_codec,snd_opl3_lib
coretemp               16384  0 
video                  36864  1 i915
input_leds             16384  0 
snd_pcm                94208  5 snd_wss_lib,snd_hda_codec,snd_hda_intel,snd_cs4236,snd_hda_core
serio_raw              16384  0 
drm_kms_helper        135168  1 i915
snd_mpu401_uart        16384  2 snd_wavefront,snd_cs4236
snd_seq_midi           16384  0 
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            28672  3 snd_wavefront,snd_mpu401_uart,snd_seq_midi
snd_seq                57344  2 snd_seq_midi_event,snd_seq_midi
drm                   303104  5 i915,drm_kms_helper
lpc_ich                20480  0 
snd_seq_device         16384  4 snd_seq,snd_rawmidi,snd_opl3_lib,snd_seq_midi
snd_timer              28672  4 snd_wss_lib,snd_pcm,snd_seq,snd_opl3_lib
snd                    69632  21 snd_hwdep,snd_timer,snd_hda_codec_idt,snd_wss_lib,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_wavefront,snd_hda_codec,snd_hda_intel,snd_mpu401_uart,snd_seq_device,snd_cs4236,snd_opl3_lib
shpchp                 32768  0 
soundcore              16384  1 snd
i2c_algo_bit           16384  1 i915
fb_sys_fops            16384  1 drm_kms_helper
syscopyarea            16384  1 drm_kms_helper
ns558                  16384  0 
gameport               16384  1 ns558
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
8250_fintek            16384  0 
parport_pc             32768  1 
mac_hid                16384  0 
ppdev                  20480  0 
lp                     16384  0 
parport                45056  3 lp,ppdev,parport_pc
uas                    20480  0 
usb_storage            53248  1 uas
hid_generic            16384  0 
usbhid                 49152  0 
hid                    98304  2 hid_generic,usbhid
pata_acpi              16384  0 
r8169                  77824  0 
fjes                   28672  0 
mii                    16384  1 r8169

```



Thanks for reading and sorry for bothering you! 

FIX 1.0: The version that I'm using is Ubuntu 14.04 lts

Caro.

---

### Post by howefield on 2017-04-03
Thread moved to the "*Networking & Wireless[ubuntu]*" forum, for a better fit.

---

### Post by Bucky Ball on 2017-04-03
Welcome. I suggest you try setting up the connection manually using Network Manager, but first, try this. You will need the IP address of the router (the access point; whatever device is connected directly to the internet and you're connecting to it locally).

Open a terminal and run this:

```
ping 192.168.0.1
```

Replacing '192.168.0.1' with the IP of your router (and there's a good chance that is the IP :)). 

Do you get a reply or are you getting 'Host unreachable' message repeatedly? Also, please let us know which release of Ubuntu you are using (16.04?).

---

### Post by chili555 on 2017-04-03
So many issues here! I hardly know which juicy morsel to try first!

In most recent Ubuntu versions, rtl8192cu is included by default and supports your exact device. Which (old??) version are you using?```
lsb_release -a
uname -r
```Maybe using an older version is the problem. 

As a matter of fact, in newer Ubuntu versions, circa-16.04 and later, *TWO* drivers claim the device and blacklisting one to let the more correct do the job is the usual fix.

As well, there are things I suggest everyone do to help connectivity.  First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:

    ```
sudo iw reg get
```

If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:

    ```
sudo iw reg set IS
```

Of course, substitute your country code if not Iceland. Set it permanently:

    ```
gksudo gedit /etc/default/crda
```

Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:

    ```
REGDOMAIN=IS
```

Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

---

### Post by carobaldino on 2017-04-03
Hi there! Thanks so much for the answer! I will try and let you know how it went. 
BTW the Ubuntu version that I'm using is 14.04 lts.

Caro.

---

### Post by carobaldino on 2017-04-03
Thanks so much!
I'll try and let you know the results!!

BTW the Ubuntu version in 14.04 lts

Caro.

---

