---
title: "No Wifi - intel 3160 - Linux 3.2.0-70-generic x86_64"
date: 2014-11-12
forum: Networking &amp; Wireless
---

### Post by milton4 on 2014-11-12
Noob trying to get this going 
1) updated firmware iwlwifi-3160-8.ucode
Not sure I was able to actually load the driver...
Any help would be appreciated.

```
lsmod | grep -e wmi -e rtl
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    79081  17 snd_hda_codec_realtek,snd_rawmidi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_seq,snd_pcm,snd_seq_device,snd_timer
mxm_wmi                13021  1 nouveau
wmi                    19256  1 mxm_wmi
```

```
05:00.0 Network controller [0280]: Intel Corporation Wireless 3160 [8086:08b3] (rev 83)

```
```

rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
```

---

### Post by Bucky Ball on 2014-11-13
Welcome. Let's see:

```
sudo lshw -C network
```

That will tell us what driver, if there is one, is currently installed. 

The answer at the bottom of [THIS]("http://askubuntu.com/questions/540580/ubuntu-intel-wireless-3160-ac-not-working-slow-disconnecting-unstable") page might help. Suggests upgrading to 14.04 LTS, though. I am presuming you are using 12.04 LTS?

---

### Post by milton4 on 2014-11-13
Thanks in advance for your time/help. Saw that about 14.04 being helpful. Running CAElinux, need to stick to 12.04 LTS.

 ```
 *-network               
       description: Ethernet interface
       product: Killer E2200 Gigabit Ethernet Controller
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 13
       serial: 44:8a:5b:ec:18:a0
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx duplex=full ip=192.168.1.252 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:46 memory:f7900000-f793ffff ioport:d000(size=128)
  *-network UNCLAIMED
       description: Network controller
       product: Wireless 3160
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 83
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f7800000-f7801fff
```

---

### Post by Bucky Ball on 2014-11-13
Guess you could try installing the 14.04 kernel in 12.04, but I suspect you mean you need to run the 3.2 kernel? I believe it is Xubuntu 12.04 with a customised xfce4 desktop and different default apps, so might be possible. :-k

Good news is, one of the wireless gurus chili555 messaged me about this thread, also suggesting that card won't work 'out of the box' with the 3.2 kernel, so has asked me to confirm his suspicions by asking you to try the following:

[QUOTE=chili555]```
lspci -nn | grep 0280
```

That will give us the pci.id for the device. Something like:

```
03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6200 [8086:4239] (rev 35)
```

Next, see if the pci.id in included in the version of iwlwifi. Search in modinfo. Again, here is an example:

```
chili@T410:~$ modinfo iwlwifi | grep -i 4239
alias:          pci:v00008086d00004239sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00004239sv*sd00001311bc*sc*i*
```

I suspect the latter will come up blank, meaning it isn't supported.

It is possible to compile backports and get it working.[/QUOTE]

See how you go and report back. I have asked him to post on the thread regarding this.

---

### Post by milton4 on 2014-11-13
i will consider trying the 14.04 after we go a little further down this path...

Here is information requested by chilli.

```
05:00.0 Network controller [0280]: Intel Corporation Wireless 3160 [8086:08b3] (rev 83)

```


```

alias:          pci:v00008086d00004239sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00004239sv*sd00001311bc*sc*i*
```

---

### Post by milton4 on 2014-11-13
Note: Was able to get ethernet going for E2100 using backports-3.10-2.tar.bz2.

---

### Post by jeremy31 on 2014-11-13
Since you have the 3.10 backports, try using the same backport package to install iwlwifi as your chipset should have been in 3.10, unless you meant you got wifi going

---

### Post by milton4 on 2014-11-13
Ethernet good, wifi not working. Will try iwlwifi install with same package.

---

### Post by chili555 on 2014-11-13
> **milton4 said:**
> i will consider trying the 14.04 after we go a little further down this path...

Here is information requested by chilli.

```
05:00.0 Network controller [0280]: Intel Corporation Wireless 3160 [[COLOR="#FF0000"]8086:08b3[/COLOR]] (rev 83)

```


```

alias:          pci:v00008086d00004239sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00004239sv*sd00001311bc*sc*i*
```You need to search for *your* device:```
modinfo iwlwifi | grep -i 08b3
```If it comes up blank as I suspect, we can probably compile one backports to fix both ethernet and the wireless!

Hopefully, your 3.10 backports will fix it.

Thanks, Bucky!

---

### Post by jeremy31 on 2014-11-13
> **chili555 said:**
> You need to search for *your* device:```
modinfo iwlwifi | grep -i 08b3
```If it comes up blank as I suspect, we can probably compile one backports to fix both ethernet and the wireless!

Hopefully, your 3.10 backports will fix it.

Thanks, Bucky!

According to [http://wireless.kernel.org/en/users/Drivers/iwlwifi](http://wireless.kernel.org/en/users/Drivers/iwlwifi) the 3160 chipset should be supported in 3.10 but the devs for iwlwifi are constantly making changes, so a newer backport for the wifi work better if there are issues with 3.10

---

### Post by milton4 on 2014-11-13
My backports 3.10 didn't fix it.

modinfo iwlwifi | grep -i 08b3
Comes up blank.

Thanks.

---

### Post by chili555 on 2014-11-13
Backports-3.13.2-1 will do it. Do you want to proceed or do you need some guidance?

You seem pretty adept if you already built and tested 3.10.```
chili@T410:~$ modinfo Desktop/Forum/[COLOR="#FF0000"]backports-3.13.2-1/drivers/net/wireless/iwlwifi/iwlwifi.ko[/COLOR] | grep -i 08b3
alias:          pci:v00008086d0000[COLOR="#FF0000"]08B3[/COLOR]sv*sd00008570bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008470bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008062bc*sc*i*
<snip>
```

---

### Post by milton4 on 2014-11-13
Some guidance would be appreciated.

---

### Post by chili555 on 2014-11-13
Please download this to your desktop: [https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.13.2/backports-3.13.2-1.tar.xz](https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.13.2/backports-3.13.2-1.tar.xz) Right-click it and select 'Extract Here.' 

Since you compiled 3.10, I assume you have headers and build tools installed. If in doubt:```
sudo apt-get install --reinstall build-essential
sudo apt-get install --reinstall linux-headers-generic
```Now we compile:```
cd ~/Desktop/backports-3.13.2-1
make defconfig-iwlwifi
make
sudo make install
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi
```Your wireless should be working. If not check the logs for clues:```
dmesg | grep iwl
```If your ethernet is affected by two different backports packages, post back and we'll work out a fix.

---

### Post by milton4 on 2014-11-13
Replying via WIFI!!!

Strange after last command got:

```
FATAL: Error inserting iwlwifi (/lib/modules/3.2.0-70-generic/updates/drivers/net/wireless/iwlwifi/iwlwifi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

No Wifi.
After reboot, have Wifi and still have Ethernet.

Thank you very much.

Milton

---

### Post by chili555 on 2014-11-13
> After reboot, have Wifi and still have Ethernet.Woo hoo!

When a newer kernel, also known as linux-image is installed by Update Manager, re-compile after the requested reboot:```
cd ~/Desktop/backports-3.13.2-1
make clean
make defconfig-iwlwifi
make
sudo make install
```Please retain the files and these instructions for that time.

---

