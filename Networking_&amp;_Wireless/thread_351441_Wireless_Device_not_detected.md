---
title: "Wireless Device not detected"
date: 2007-02-01
forum: Networking &amp; Wireless
---

### Post by dano2769 on 2007-02-01
I recently installed Ubuntu, but my wireless card was not fully recognized.

lspci:
[php]02:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)[/php]

So I attempted to install Madwifi using 'make; sudo make install.' That when fine and dandy; however when I 'modprobe ath_pci' still nothing shows up in iwconfig.

iwconfig:
[php]lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.[/php]

What am I missing?

---

### Post by empthollow on 2007-02-02
the drivers you are looking for are in a package named something like linux-restricted-modules-kernelname. If you type atheros in the synaptic search it will pop up

---

### Post by dano2769 on 2007-02-02
Okay, I used the Synaptic Package Manager to download and install linux-restricted-modules-2.6.17-10-386 and madwifi-tools, but my wireless card is still not detected in system>administration>networking. Anyone?

---

### Post by empthollow on 2007-02-03
the first thing i would do is doubble check to see that my card is on as i have often wondered why i don't have internet, panic, and promptly realize that my card is no turned on on my laptop.:lolflag: 

to investigate further i would type this in the terminal to check if all the modules are loaded there
```
lsmod | grep ath
```
there should be 4 modules listed
```
ath_pci                97184  0 
ath_rate_sample        15616  1 ath_pci
wlan                  204764  5 wlan_tkip,wlan_scan_sta,ath_pci,ath_rate_sample
ath_hal               192080  3 ath_pci,ath_rate_sample

```

if all of those are listed

do a 
```
ifconfig -a
```

one of the devices should be "ath0" if your modules are loading properly and you still do not see "ath0" you may need to look into a different version of madwifi.  I can't say i've been able to successfully figure out all of how madwifi works and why it sees the card with different installs of the same program, but i had this issue when i was using slackware and using different packages/builds it worked. good luck

---

### Post by dano2769 on 2007-02-03
Okay, so lsmod|grep ath yields

```
ath_pci                97184  0 
ath_rate_sample        15616  1 ath_pci
wlan                  204764  2 ath_pci,ath_rate_sample
ath_hal               192080  2 ath_pci,ath_rate_sample

```

But ifconfig -a shows nothing new. How can I install another version of madwifi? Whenever I try to compile from source (ie, not the package manger) I get an error about kernel build not existing.
```
Makefile.inc:66: *** /lib/modules/2.6.17-10-386/build is missing, please set KERNELPATH.  Stop.
```

---

### Post by empthollow on 2007-02-04
your best bet would probably be to build from source, most if not all of the errors i've encountered when compiling progs were due to development packages not being installed.  In this case i would try
```
sudo apt-get -y install linux-headers-2.6.17-10-386
```
i have this package installed and i have some files in the /lib/modules/2.6.17-10-386 directory on my system.  That should contain your headers.  The other option could be to search for other debian packages but you would probably run into dependency issued which in my experence is more frustrating that building from source.

---

