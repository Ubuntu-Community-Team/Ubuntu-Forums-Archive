---
title: "Brostrend ac3 driver find/install for 20.04"
date: 2020-12-05
forum: Networking &amp; Wireless
---

### Post by terraclast on 2020-12-05
Hello everyone.  Thanks to the incredibly helpful and informative folks here, I've finally worked out all the snags on getting Ubuntu to dual boot with Win10 on my Z440 box. I'm now able to get to the main goal of getting a BrosTrend AC3 WiFi nic to run in Ubuntu 20.04.  

I downloaded from Github and loaded to a flash drive what is allegedly a driver for it, though I don't remember if it was rtl8812au or something similar.  
At the suggestion of CelticWarrior in a previous post, I am now able to temporarily connect via ethernet cable but the ideal would be to have the wifi nic do the connecting so that I don't have a cable running through the house for people to trip on.  

I am now very hesitant to google solutions because I had a couple scares before I joined this fantastic community.  And so, here I am asking the Ubuntu gods for a little more help.  I have looked around a tiny bit in the OS for a way to find it and I think going through terminal is both the best and most educational/fun method to search for and install the driver. 

Any help would be greatly appreciated and thank you in advance for your help.  

I just found this, but it's for the BrosTrend AC5, not AC3. Will it still work?  

Unrelated but almost certainly important, I'm not sure if I have properly inserted code or really how to, so I hope this is correct, though it probably isn't. 

     Code:
     wget [https://launchpad.net/~timchen119/+archive/ubuntu/mt7610u-dkms/+files/mt7610u-dkms_1.0_amd64.deb](https://launchpad.net/~timchen119/+archive/ubuntu/mt7610u-dkms/+files/mt7610u-dkms_1.0_amd64.deb)
sudo dpkg -i mt7610u-dkms_1.0_amd64.deb

---

### Post by morrownr on 2020-12-05
The Brostrend AC1L and AC3L have shipped with two different chipsets... either the rtl8812au or rtl88x2bu. The AC5L uses the rtl8811cu chipset. With that said, what you need to know is what chipset is in your USB wifi device. A good start to finding that out is to run this command at the terminal interface:

```
lsusb
```

Post the results.

If the results don't directly tell you what chip is in use, you can use this site:

[https://devicehunt.com/](https://devicehunt.com/)

Select "USB" and then the Vendor ID is likely "0bda" since it is a Realtek USB WiFi adapter. You can then put the Device ID in and you likely will see what chipset you have.

Once you have the chipset determined, you can go here:

[https://github.com/morrownr](https://github.com/morrownr)

At this site you will find recent Realtek USB WiFi drivers for numerous Realtek chipsets, including the ones you may have. Hopefully you will find the installation instructions to be easy to follow and additional information is provided to help get you on your way.

FYI: The .deb from Brostrend still requires internet access even though it is a .deb. For out-of-kernel drivers, the only easy solution is to use temporary internet access. Many cel phones provide tethering and that combined with Ubuntu 20.04 should make for a painless install.

Regards

---

### Post by terraclast on 2020-12-05
Thanks.  I'm about to follow your instructions. For clarity's sake, it is the AC3, not AC3L.  When I went to the BrosTrend site, it lists "Linux" as compatible.  Not entirely sure if this will be an issue.  I will report back.

---

### Post by terraclast on 2020-12-05
I searched the internet and performed lsusb.  
On a Mint forum the chipset is listed as RTL8812BU.  I can't really find the device ID for use in your provided link.  

Here is the output from lsusb:

Bus 003 Device 003: ID 0bda:b812 Realtek Semiconductor Corp. 802.11ac NIC

Not super helpful, heh.  

In devicehunt, I tried both "BROSTREND" and "0bda" in the vendor id and both ac3 and the above hex id in the device id and none of the four reported back any devices.  Having just looked up their vendor list, seems silly that I tried the brand seeing that they aren't listed.  
Maybe trying to install the rtl8812bu driver will work.  Will report back.

*Still have no idea how to properly insert code into a post.  Sorry if that's annoying.  I'm also working on that.

---

### Post by terraclast on 2020-12-05
WOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOO HOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOO!!!!

Your Github worked perfectly using RTL88x2BU.  I am currently posting using the WIFI!!!!!!!!!

THANK YOOOOOOOOOOOOOOOOOOOOOOOOOUUUU!!!  Mission accomplished!

*I still have no idea how to properly insert code into a post.  J/S

---

### Post by morrownr on 2020-12-06
Glad to hear that your wifi is working. I've been using Linux since long before WiFi existed. It can take a little time to get used to some of the differences but it is really cool once you learn the details.

Quote: "Bus 003 Device 003: ID 0bda:b812 Realtek Semiconductor Corp. 802.11ac NIC"

Look at the numbers after ID:  0bda:b812

0bda means that this is a Realtek product. b812 means that the device is based on a 8812bu chipset. Products that use the 8812bu chipset may show other device IDs depending on what the device maker decides to do.

Something to keep in mind when investigating what driver is required by hardware on Linux is to find out the maker of the chipset, not the retailer of the end product.

---

### Post by morrownr on 2020-12-06
> **terraclast said:**
> Thanks.  I'm about to follow your instructions. For clarity's sake, it is the AC3, not AC3L.  When I went to the BrosTrend site, it lists "Linux" as compatible.  Not entirely sure if this will be an issue.  I will report back.

FYI: The only difference between the AC3 and the AC3L is whether you bought Linux support. The adapter is the same.

---

### Post by terraclast on 2020-12-18
I kind of figured that, and that the driver disc that comes with the hardware was specifically designed to be &#8220;easily&#8221; run in a Linux distro.  IT just seemed silly that it would run on Windows, OSX, and not Linux.  Maybe people just get scared if they see Linux anywhere on a product?

---

### Post by terraclast on 2020-12-18
> **morrownr said:**
> 
Look at the numbers after ID:  0bda:b812

0bda means that this is a Realtek product. b812 means that the device is based on a 8812bu chipset. Products that use the 8812bu chipset may show other device IDs depending on what the device maker decides to do.

Something to keep in mind when investigating what driver is required by hardware on Linux is to find out the maker of the chipset, not the retailer of the end product.

Copy that.  I had no idea what it meant other than it looked suspiciously like hexadecimal.  I suppose it’s a bit more straightforward, at least the second half, than I thought.  

Thank you for information, it’s all pretty new to me but intensely interesting.

---

