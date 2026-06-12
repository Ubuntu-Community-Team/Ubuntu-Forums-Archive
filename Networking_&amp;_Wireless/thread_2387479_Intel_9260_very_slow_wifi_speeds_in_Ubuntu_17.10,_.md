---
title: "Intel 9260 very slow wifi speeds in Ubuntu 17.10, normal in Windows 10."
date: 2018-03-19
forum: Networking &amp; Wireless
---

### Post by ianklug on 2018-03-19
Running dual-boot Windows/Ubuntu on a Dell XPS 15 9560, with the Killer 1535 recently swapped out for a shiny new Intel 9260.
Ubuntu is version 17.10 on Kernel 4.15.11, running Intel firmware v34 with iwlwifi/iwlmvm driver. This card is listed as supported [here]("https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi") for kernels 4.14+.

Speeds in Windows are consistently 200+mbps down, 100mbps up on my home wireless network. The wifi download speed in Ubuntu is really unstable, and speed tests show between 0.5-5mbps down, with the same 100mbps upload speed.

Wireless info script output [here]("https://paste.ubuntu.com/p/jkw7dKfxGQ/").

I've tried some basic diagnostics, such as disabling IPv6 and power management, to no avail. Any ideas as to why this might be? Thanks.

---

### Post by ianklug on 2018-03-21
I have discovered that starting iwlwifi with 11n_disable=1 improves my download speed to 15mbps, but also restricts upload speed to about the same 15mbps.
For now i'll be using it with this enabled as it is better than before, but any insight into getting near the speeds I should be seeing would be greatly appreciated.

---

### Post by jeremy31 on 2018-03-21
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
To disable wifi power management
I would try with 11n_disable=8 as that enables aggressive TX

---

### Post by ianklug on 2018-03-21
Thanks for the suggestions Jeremy31!

I'm not sure if it was before, but wifi power management is now definitely off. It seems using 11n_disable=8 has the same result as just leaving it at 0; I get the same extremely slow down speeds from before with it set to use aggressive TX.

I've since upgraded my kernel to the newest mainline, set 11n_disable=1, and re-ran the wireless info script. [Here]("https://i.imgur.com/9xS3iQV.png") is the best speed test reading I got and [here]("https://paste.ubuntu.com/p/rKGbWB47wy/") are the new wireless info results.

I'm not entirely sure why wireless-N settings have affected things (let alone improved anything), considering my laptop and access point are both AC wireless compatible.

Edit: I do notice that all my wireless speeds now seem to be capped to 54mbps according to wireless info. It was not like this before.

---

### Post by jeremy31 on 2018-03-21
Did you try 11n_disable=8 in the conf file and rebooted or did you try it before the change?

---

### Post by ianklug on 2018-03-21
I set 11n_disable=8 in iwlwifi.conf and rebooted. I saw the same 0.5mbps down as with no setting, and the 8 setting also limited my upload speed drastically to around 2mbps. For kicks I also tried 2 and 4 in this slot and got very similar results.
With no setting or 0 in the config file, I go back to .5mbps down, 100+ up. With it set to 1, I manage 15mbps down and 15mbps up, which is the most usable result but still far from ideal.

With wireless-n enabled "iwconfig" shows a max bit rate of 866mbps for wireless adapter wlp2s0, and with it disabled (11n_disable=1) it only shows 54mbps as the max bit rate. I'm curious why this would be the case... it seems disabling wireless-n also has some effect on the way iwlwifi handles ac wireless connections.

---

### Post by ianklug on 2018-03-21
note: recorded the [insane speeds]("https://i.imgur.com/PurrE3y.png") I get when connected to AC with wireless N enabled.

---

### Post by jeremy31 on 2018-03-21
Might need to see if 18.04 and the 4.15 kernel does any better.  The 9260 is really new to Linux and the iwlwifi module has probably been tweaked a lot

---

### Post by ianklug on 2018-04-02
Update for anyone watching: Today the problem sorted itself out when I  installed kernel 4.16.0 mainline, which shipped with a microcode  update.

  For usable speeds in a pinch on a kernel <4.16, setting  "11n_disable=1" in iwlwifi.conf works alright, but it seems that full  speed with my 9-series card on this hardware (XPS 15 9560) requires the  new kernel. Sometimes it's hard living on the bleeding edge.

---

### Post by troywolf on 2018-07-16
I know this thread is a little old, but with a new laptop and Ubuntu 18.04, I'm having what seems to be the exact same issue. I am curious about @ianklug's report that this issue went away in April with kernel [COLOR=#000000]4.16.0. I am curious if you have upgraded to Ubuntu 18 and if the problem returned.

My HP Spectre X360 came with the [/COLOR]Intel Corporation Device 2526 (rev 29) and is using the iwlwifi-9260-th-b0-jf-b0-34.ucode driver. This appears to be the latest driver I can use, and I tried forcing an older driver, but that did not fix the issue.

[COLOR=#000000]Exactly as ianklug reported, I am getting closer to 200MB upload speed but am lucky to get better than 1MB download. My ASUS laptop with Ubuntu 16 enjoyed fast download speeds on my home network. My daughter's Windows 10 Dell laptop downloads fast.

I've tried the various recommendations to tweak 11n_disable setting. While I see some differences when I do this, none get me the download speeds I should see.

I'm holding onto hope that someone smarter than me will fix this and one day I'll update and this problem will go POOF. Until then, it's so bad, it has me USB tethering my Android phone to share it's WiFi. When I do that, I can get around 70MB download and 25MB upload.

Any good ideas? Hope on the horizon? Proof that somebody with power to fix this is even aware of the issue? Recommendation for proper channels to report this other than right here?

[/COLOR]```
lspci -v
3b:00.0 Network controller: Intel Corporation Device 2526 (rev 29)
	Subsystem: Intel Corporation Device 0014
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at dd300000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: iwlwifi
	Kernel modules: iwlwifi


sudo dmesg | grep iwl
[    6.316873] iwlwifi 0000:3b:00.0: enabling device (0000 -> 0002)
[    6.325923] iwlwifi 0000:3b:00.0: loaded firmware version 34.0.0 op_mode iwlmvm
[    6.355949] iwlwifi 0000:3b:00.0: Detected Intel(R) Dual Band Wireless AC 9260, REV=0x324
[    6.411965] iwlwifi 0000:3b:00.0: base HW address: 74:e5:f9:88:d7:54
[    6.483308] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    6.671419] iwlwifi 0000:3b:00.0 wlo1: renamed from wlan0

```

On my Google Fiber WiFi
[IMG]https://i.imgur.com/A9zqYMZ.png[/IMG]

USB-Tethered to Android phone on same WiFi network a few seconds later:
[IMG]https://i.imgur.com/sfSHZi7.png[/IMG]

---

### Post by troywolf on 2018-07-17
I got desperate, so I took a chance. I have 16 logical CPUs, and this patch seemed to be relevant:
[https://git.kernel.org/pub/scm/linux/kernel/git/iwlwifi/backport-iwlwifi.git/commit/drivers/net/wireless/intel?id=998ce0330c94eca4b13b8f062b3f0ca9ef9ad6d8](https://git.kernel.org/pub/scm/linux/kernel/git/iwlwifi/backport-iwlwifi.git/commit/drivers/net/wireless/intel?id=998ce0330c94eca4b13b8f062b3f0ca9ef9ad6d8)

I downloaded it, unpacked the archive, moved into the directory, then did this as root to build and install:

```

make defconfig-iwlwifi-public
make -j4
make install


```

The install did throw several errors around "SSL" related things. Here is the start of them:

```

Makefile:976: "Cannot use CONFIG_STACK_VALIDATION=y, please install libelf-dev, libelf-devel or elfutils-libelf-devel"
  Building modules, stage 2.
  MODPOST 6 modules
Makefile:976: "Cannot use CONFIG_STACK_VALIDATION=y, please install libelf-dev, libelf-devel or elfutils-libelf-devel"
  INSTALL /home/twolf/Downloads/backport-iwlwifi-998ce0330c94eca4b13b8f062b3f0ca9ef9ad6d8/compat/compat.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: ../crypto/bio/bss_file.c:74
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: ../crypto/bio/bss_file.c:81

```

When I rebooted, my system did not even show a WiFi device. :(  modprobe indicated an error due to a key.... Google search suggested I disable secure boot. I did, and now my WiFi works and I have fast downloads and uploads.

[IMG]https://i.imgur.com/U19qrPm.png[/IMG]

---

### Post by mikehardy on 2018-08-12
I'm posting this in a few threads because it may be pertinent, the TL;DR is that an upgrade to the kernel, using the UKUU package, choosing kernel 4.17.14 which is the most current at the moment, fixed it for me and was otherwise painless.

[https://unix.stackexchange.com/a/462175/304207](https://unix.stackexchange.com/a/462175/304207)

---

