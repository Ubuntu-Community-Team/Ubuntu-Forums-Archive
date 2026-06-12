---
title: "Wifi/ethernet not working, need ath10k drivers (?) or new firmware?"
date: 2015-12-24
forum: Networking &amp; Wireless
---

### Post by eric100 on 2015-12-24
[U][B]
EDIT: This bugreport appears to outline the problem (and solution) to what appears to be a problem highly related to this series of laptops (MSI G-series, GS60 for me: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1383184](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1383184)). I've tried the approach described in post #324, but unsuccessfully).[/B][/U]

Hello there,

I am attempting my first installation ever of linux on a new MSI GS60 computer, in a dual boot set-up with windows 10. As such, I've managed to install Ubuntu 14.04 through my windows 10 partition using the USB/.iso method. Apparently there is an issue with the hardware in my computer and a lack of supporting drivers in Ubuntu, meaning I have to manually install the drivers somehow. Is it possible to simply download the required file to my windows 10 partition, subsequently copy it over from ubuntu (which has access to the windows files, but curiously not the other way around), and install it that way? I have attempted this already with an nvidia driver, but this only resulted in an abnormally long wait time, until the an error message saying there was a problem with some symbols in the file, and that continued editing may be problematic - or something to that effect. In other words, I'm unsure I actually *installed* it, more than just opened it as a text file with some problems. I am a complete linux novice, if you couldn't tell. 

As per the suggestions of the "before posting in Network & Wireless" ([http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)) post, I tried 

```
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get update
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get dist-upgrade[/FONT][/COLOR]
```

However, as I have no internet access, this did nothing.

I instead downloaded the wireless-info file suggested, ran it as a .txt, which resulted in tar.gz file. I am unsure where to go from here. 

Thankful for any help.

---

### Post by jeremy31 on 2015-12-24
The script result was a mess and I am hoping you just need firmware that can be downloaded at [http://security.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.149.2_all.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.149.2_all.deb)
Then copy to the home folder in ubuntu then ```
sudo dpkg -i linux-firmware_1.149.2_all.deb
```

Hopefully wireless functions after a reboot, otherwise post the results of ```
dmesg | grep ath10k > dmesg.txt
``` then you can copy the dmesg.txt file from your home folder to windows to post the results

---

### Post by eric100 on 2015-12-24
Will try just that and report back. Thanks!

---

### Post by eric100 on 2015-12-29
OK, so I did what you suggested, and also installed the "linux-image-extra-4.2.0-16-generic 4.2.0-16.19.deb" as suggested in the bugreport for this problem (posts #324, 325 and 326: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1383184](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1383184)), but so far now Wi-Fi. By no WiFi, I mean, I am unable to find or chose any WiFi networks in an area where I know there are available networks. 


Also, my dmesg.txt just came out empty. Is this expected if there's a problem (as in missing ath10k)? Ill try again. 

Edit: Confirmed. The dmesg.txt is just empty, 0 kb.

---

### Post by eric100 on 2015-12-29
If the dmesg.txt ends up emtpy, what other diagnostic could I run to understand the problem?

---

### Post by eric100 on 2015-12-29
Anyone willing to throw me a bone? Would appreciate.

---

### Post by jeremy31 on 2015-12-29
```
lspci -nnk | grep -iA2 net; rfkill list all; modinfo ath10k_pci | grep -i 003e
```

---

### Post by eric100 on 2015-12-30
Thanks, Jeremy31.

Here's the output:
  
[IMG]http://i.imgur.com/FDzAMPf.jpg?1[/IMG]

---

### Post by jeremy31 on 2015-12-31
Something strange going on, post ```
modinfo cfg80211
```

---

### Post by praseodym on 2015-12-31
Hi,

please check:
```

dpkg -l linux-image-* | grep ii
```

---

### Post by chili555 on 2015-12-31
Please see: [http://askubuntu.com/questions/661424/ubuntu-14-04-wireless-not-working-no-network-interface-atheros-168c003e-dev](http://askubuntu.com/questions/661424/ubuntu-14-04-wireless-not-working-no-network-interface-atheros-168c003e-dev)

---

### Post by eric100 on 2015-12-31
Thanks again for taking the time to help.


Modinfo returned nothing, dpkg can be seen below. 

[http://i.imgur.com/KmF6i6G.jpg?1](http://i.imgur.com/KmF6i6G.jpg?1)

[IMG]http://i.imgur.com/KmF6i6G.jpg?1[/IMG]

---

### Post by jeremy31 on 2015-12-31
Download [http://ppa.launchpad.net/canonical-kernel-team/ppa/ubuntu/pool/main/l/linux-meta-lts-wily/linux-generic-lts-wily_4.2.0.23.17_amd64.deb](http://ppa.launchpad.net/canonical-kernel-team/ppa/ubuntu/pool/main/l/linux-meta-lts-wily/linux-generic-lts-wily_4.2.0.23.17_amd64.deb) and install it, then reboot

---

### Post by eric100 on 2015-12-31
Will do. Be right back. Is it supposed to be so small (1.74 kb)?

---

### Post by jeremy31 on 2015-12-31
Not going to work then

---

### Post by eric100 on 2015-12-31
Yup, didnt work. Dependency problem.

[http://i.imgur.com/BuHyCbP.jpg?1](http://i.imgur.com/BuHyCbP.jpg?1)

---

### Post by jeremy31 on 2015-12-31
[http://security.ubuntu.com/ubuntu/pool/main/l/linux-lts-wily/linux-image-extra-4.2.0-22-generic_4.2.0-22.27~14.04.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-lts-wily/linux-image-extra-4.2.0-22-generic_4.2.0-22.27~14.04.1_amd64.deb)
[http://security.ubuntu.com/ubuntu/pool/main/l/linux-lts-wily/linux-image-4.2.0-22-generic_4.2.0-22.27~14.04.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-lts-wily/linux-image-4.2.0-22-generic_4.2.0-22.27~14.04.1_amd64.deb)
[http://security.ubuntu.com/ubuntu/pool/main/l/linux-lts-wily/linux-headers-4.2.0-22-generic_4.2.0-22.27~14.04.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-lts-wily/linux-headers-4.2.0-22-generic_4.2.0-22.27~14.04.1_amd64.deb)
[http://security.ubuntu.com/ubuntu/pool/main/l/linux-lts-wily/linux-headers-4.2.0-22_4.2.0-22.27~14.04.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-lts-wily/linux-headers-4.2.0-22_4.2.0-22.27~14.04.1_all.deb)

You might be able to put them in a folder on your desktop then cd into the same directory in terminal then ```
sudo dpkg -i linux*4.2.0*.deb
``` to install.  Been a while since I manually installed a kernel

---

### Post by eric100 on 2015-12-31
Installation appeared to work, and I've restarted. The modinfo still does not return anything. 

Now what? :)

---

### Post by jeremy31 on 2015-12-31
What does ```
uname -a; dkms status
``` show

---

### Post by praseodym on 2015-12-31
You need the respective package for kernel 4:

[http://packages.ubuntu.com/search?keywords=linux-image-extra-4&searchon=names&suite=wily&section=all](http://packages.ubuntu.com/search?keywords=linux-image-extra-4&searchon=names&suite=wily&section=all)

---

### Post by eric100 on 2015-12-31
@jeremy: the output was simply that dkms was not installed.

@praseodym: sorry, could you specify which out of those files I need (I assume the last one)? Clicking them also leads to several potential downloads, I'm a tad confused.

---

### Post by jeremy31 on 2015-12-31
What is the ```
uname -a
``` result?  Does it say 4.2.0-22?

---

