---
title: "Linux - Sprint PCS / Novatel EX720"
date: 2008-08-30
forum: Networking &amp; Wireless
---

### Post by dwitkin on 2008-08-30
**[SIZE="4"]Linux - Sprint PCS / Novatel EX720[/SIZE]**

Hello. I've searched a number of forums and tried several solutions, but I haven't been able to find anything to address the problem I'm having. I'm hoping someone here will take the time to help.

I have a Sony FZ160E laptop and currently run Ubuntu Hardy 8.04. I'm using Sprint PCS EVDO service with a Novatel Merlin EX720 express card. Using the instructions on the Sprint PCS site, I configured the modem and am able to successfully connect.

The problem is speed -- I'm only getting 120k downstream and maybe 80k upstream. I've read a number of posts where people were "limited" to 500k downstream, but I would be ecstatic to get those speeds.

This is not a problem related to my location: using Windows XP and Vista, I get speeds in excess of 1.2mbps in the same locations.

I have tried:
1. Disabling the airprime driver. I've read that it can cause problems, so I disabled (blacklisted) it. No help -- same speed issues.
2. Using WVdial instead of KPPP. Followed various instructions in the Ubuntu forums... in short, they didn't seem to do much different other than make sure I had blacklisted airprime and they used WVdial instead of KPPP. No help.

Any suggestions? I've seen instructions to re-build the kernel and use the airprime driver. But I'm still fairly new to Linux and don't want to pursue that since that's not guarantted to address the problem and if there is an easy way to get at least 500k with the USBserial driver.

There is an article (link below) that suggests two problems and a potential fix, but it is old (several years, I think) and I haven't seen any recent articles suggesting that either problem is still valid. The problems stated were:
1. The current usbcore and usbserial driver do not correctly recognize the maximum packet size on the inbound bulk endpoint.
2. The cards themselves are not advertising the correct maximum data packet size to the usb sub-system on Linux.

Here's a link to the related article: [http://www.junxion.com/opensource/linux_highspeed_usbserial](http://www.junxion.com/opensource/linux_highspeed_usbserial). If someone can tell me that these could still be valid problems with Ubuntu Hardy, then I'll go down the path of trying them.

I'm using the following modprobe settings, which appear to be right according to the Novatel website instructions:
modprobe usbserial vendor=0x1410 product=0x1120

Running: "lsmod | grep -E 'airprime|option|usbserial' " returns:
option                 11520  0
usbserial              35816  1 option
usbcore               146028  7 option, usbserial, uvcvideo, usbhid, uhci_hcd, ehci_hcd

If I need to provide more info to help troubleshoot, let me know. Again, I'm still fairly new to Linux, so please give me the appropriate terminal commands.

I appreciate your help.

---

