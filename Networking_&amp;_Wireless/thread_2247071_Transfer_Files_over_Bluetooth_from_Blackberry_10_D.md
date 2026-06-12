---
title: "Transfer Files over Bluetooth from Blackberry 10 Device to Ubuntu 14.04"
date: 2014-10-05
forum: Networking &amp; Wireless
---

### Post by gstanden on 2014-10-05
Hi,

Just wanted to share this in case it helps others.  If you want to SEND files from your Blackberry 10 device (say, Blackberry Z10, Z30, Q10, Q20, etc) you need to do an additional step after configuring your Blackberry 10 device on  Ubuntu 14.04.

You need to install "blueman" package, for example:

sudo apt-get install blueman

Or you could use the Ubuntu Software Manager application and search for "blueman" and install it.

Once it is installed, open it up by going into the software search, for example, and typing "blueman" and then click on the launcher.

Select your Blackberry device and click setup (either from top menu bar or from right-click on device itself).

Then select "input device" radio button and follow the steps to complete that activity.  

Now you will be able to send files FROM your Blackberry OS10 device TO your Ubuntu 14.04 laptop or desktop.

This should work for other versions of Ubuntu but I have only tested it on Ubuntu 14.04.  Note also that this was tested on a FRESH install of Ubuntu 14.04.  There are known issues with Ubuntu 14.04 with bluetooth that are upgraded from earlier Ubuntu versions, so there could be issues there too, but hopefully this procedure will work in that case as well.

This was tested on a Lenovo W520 laptop running 64-bit Ubuntu Desktop 14.04.1

HTH, Thanks, Gil

---

