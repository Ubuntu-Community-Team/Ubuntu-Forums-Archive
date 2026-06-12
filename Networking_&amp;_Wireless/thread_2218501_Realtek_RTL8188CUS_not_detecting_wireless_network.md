---
title: "Realtek RTL8188CUS not detecting wireless network"
date: 2014-04-20
forum: Networking &amp; Wireless
---

### Post by lhcpr on 2014-04-20
Hi all,

I understand that there are many threads re. wireless connections not working. After a search of these - I am still yet to find my solution. Here goes ...

[LIST]
[*]Running ubuntu 12.04 LTS
[*]Have netgear usb wiress adaptor NetGear, Inc. WNA1000M 802.11bgn [Realtek RTL8188CUS]
[*]Have an iinet BoBLite modem model GL411 - [http://www.iinet.net.au/hardware/bob/boblite/](http://www.iinet.net.au/hardware/bob/boblite/)
[*]Wired ethernet cxn works fine
[*]WCID and ntp tool installed
[/LIST]

Ok so the issue is connecting to the wireless network under the modem-router above - Ubuntu does not recognise the wireless network im trying to connect to
Now - considering that this could be an adaptor problem:
[LIST=1]
[*]I can connect to the wireless network using the same wireless adaptor in a windows environment
[*]I set my android device to "portable wi-fi hotspot". Under this condition Ubuntu/wireless adaptor has no issues recognising or connecting to the device and I can use the internet fine
[/LIST]

So this is telling me that my wireless adaptor is working fine - it is just that the network is not being recognised

As before I have trawled the forums and have not encountered this specific issue. Was hoping that someone may be able to help me out with this. Please see result of wireless info script attached

Thanks a bunch

Graham

---

### Post by varunendra on 2014-04-22
Please follow the instructions in this post to try a newer driver (the post was written for a different driver of the same family, instructions would be same for you too) : [http://ubuntuforums.org/showpost.php?p=12926946](http://ubuntuforums.org/showpost.php?p=12926946)

If that doesn't help, please download the wireless_script again (the newer one includes some more commands, providing more information) and run it to generate and post back a fresh report.

---

### Post by wgn on 2014-04-24
There is a patch for the rtl8192 driver at [https://github.com/pvaret/rtl8192cu-fixes]("https://github.com/pvaret/rtl8192cu-fixes"). Instructions included.
Found it at [http://askubuntu.com/questions/387807/rtl8188cus-module-for-ubuntu-13-10]("http://askubuntu.com/questions/387807/rtl8188cus-module-for-ubuntu-13-10") while googling for similar problem.

---

### Post by praseodym on 2014-04-24
Run this commands for that new driver
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git 
git clone https://github.com/pvaret/rtl8192cu-fixes.git
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.8
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf   
```
Reboot.

---

### Post by lhcpr on 2014-05-03
Hi Varun - thanks for the input

I followed the instructions in the link:

1) Tried the backports-3.12.8-1 and no wireless network on iwlist scan
2) Tried the lastest backports and scanned again with no wireless networks detected
3) See wireless-info.txt attached

Any other suggestions? Will give praseodym's suggestions a crack in the interim

Thanks

Graham

---

### Post by varunendra on 2014-05-04
Before trying another driver, I would suggest to try one more thing, based on the following part in your dmesg -
```
[   12.137517] rtl8192cu: Loading firmware **rtlwifi/rtl8192cufw_TMSC.bin**
[   12.462749] rtlwifi: Loading **[COLOR="#FF0000"]alternative firmware[/COLOR] rtlwifi/rtl8192cufw.bin**
```

Let's provide the original firmware that the driver expects initially, so that it doesn't have to fall back to the alternative one.

Please download the attached file (extracted and repacked from Debian's official firmware package provided **[here]("https://packages.debian.org/wheezy-backports/firmware-realtek")**), and copy it onto your Desktop. Then, open a terminal (Ctrl-Alt-T) and run the following commands in it (assuming the downloaded firmware archive is on your Desktop) -
```
cd Desktop
tar xjf rtl8192cufw_TMSC.bin.tar.bz2
sudo cp rtl8192cufw_TMSC.bin /lib/firmware/rtlwifi/
```

Then either reboot the system, or reload the driver with -
```
sudo modprobe -rv rtl8192cu
sudo modprobe -v rtl8192cu
```
Report back if you get any errors in the whole process. If not, check -
```
dmesg | grep firm | tail -4
```
Does it still load any alternative firmwares? If not, does it work now?

Please make sure the Ethernet (cable) is disconnected while trying the wireless interface, else Network Manager may not attempt the wireless connection at all.

---

### Post by lhcpr on 2014-11-05
Hi guys - thank you for your assistance with the above. I know that its been a while but I just wanted to update on a couple of things:

1) Backports solution as above no dice for getting the rtl8192CU wireless connected in 12.04
2) The solution as posted using the drivers from github worked just fine in the end!!!

Now .... updated to 14.10 and could no longer connect with wireless using the same rtl8192CU :-(
1) Tried back port solution again - no dice
2) Tried the github driver solutions [HTML]https://github.com/pvaret/rtl8192cu-fixes[/HTML] wit the code below and now works fine once again

```
git clone https://github.com/pvaret/rtl8192cu-fixes.git
sudo dkms add ./rtl8192cu-fixes
cd rtl8192cu-fixes
sudo dkms install 8192cu/1.9
sudo depmod -a
```

Now the only difference to note from the original driver solution was:
1) Rename existing rtl8192-fixes
2) "1.8" in the original ```
dkms install 8192cu/1.8
``` code was changed to ```
dkms install 8192cu/1.9
```

Now works fine on 14.10

Thanks for all the assistance here and sorry for the 6 month delay :-( will mark as solved

Graham

---

