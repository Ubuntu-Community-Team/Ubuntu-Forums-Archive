---
title: "Need Wireless PCMCIA advice"
date: 2006-11-27
forum: Networking &amp; Wireless
---

### Post by jimpreston on 2006-11-27
I'm brand new to ubuntu and linux in general, but trying to learn.  I've installed ubuntu on my Dell Latitude CPx and that was fairly uneventful - quite easy actually, I was impressed. But now I need to get some connectivity on my wireless network.  Reading what I can find available on the internet, has lead to nothing but confusion, and wondering if I'm barking up the wrong tree with linux/ubuntu.  Seems to be no easy way for a beginner to do this.

All I'd like is the name of a wireless card that is known to work and the associated (beginners level) instructions for getting it to work.

Can anyone help ?  Thanks a lot for taking the time to read this.

jim in florida

---

### Post by cilynx on 2006-11-27
This is the list of supported wireless cards:

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

Anything based on the Prism54 chipset generally just works.  Broadcom works reliably, but requires quite a bit of tom-foolery.

Anything requiring ndiswrapper is too much of a pain for a beginner.

Personally, I have experience with the Linksys Prism, Xteresis Prism54, and Broadcom bcm43xx cards.

---

### Post by jml on 2006-11-27
The list referenced is a good start.  One other wrinkle to consider.  What kind of wireless network are you planning to connect to?  If you are planning to connect to either an unencrypted network, or to one encrypted with WEP, you should be ok.  If you are going to be connecting to a network encrypted with WPA-PSK, then your task will be a bit more complicated.  To be frank, I have never been able to set up WPA encryption in Ubuntu, despite a lot of help from these forums.  The only distros I have been able to get WPA encryption working out of the box are Kanotix (my current distro,) Mandriva 2006 (have not tried 2007,) SUSE 10.1.  Others on this forum have gotten WPA working with Ubuntu, but I havent.

Joe

---

### Post by FrodoB on 2006-11-27
If you want a plug and play card Linux in PCI or  PCMCIA (PC Card) you need to get an Atheros card.   Just be warned that USB Atheros is not supported by mAdWiFi. But for your purpose it has the best support. Back when the Prism54 cards were all so called FullMAC cards they would have been on the top of my list as well, but Atheros has had the longest compatibility with Linux in 802.11g.

These can be found by looking for cards that advertise that they are Atheros G, Atheros Super G, and in general anything that is advertised as 108Mbps throughput.

Also if you are interested in the D-Link cards look for AirPlus Extreme G. Such as the DWL-G650. Here is an example of one such card:

[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=485115&CatId=367](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=485115&CatId=367)

and

[http://www.amazon.com/D-Link-DWL-G650-Wireless-Cardbus-Adapter/dp/B00007LTB6](http://www.amazon.com/D-Link-DWL-G650-Wireless-Cardbus-Adapter/dp/B00007LTB6)

and

[http://www.newegg.com/Product/Product.asp?Item=N82E16833127116](http://www.newegg.com/Product/Product.asp?Item=N82E16833127116)

---

### Post by jimpreston on 2006-11-27
Thank you folks - really appreciate the help.

FrodoB - when you say 'plug and play' are you saying that it really will detect it, ask for a driver CD or files, and then load and configure it ?  Similar to what I might find in Windows ?  Sorry for the newbie questions, but I'm a newbie !  Or will i need to go find files, run some sort of installer (I know linux flavors use different types of installer systems for apps and such), edit files, build from source files, etc. ?

jim

---

### Post by FrodoB on 2006-11-27
I am saying that if you do an install using the normal Dapper or Edgy CD, not the Alternate CD, that the card will immediately be recognised and you can configure it in the System -> Adminstration -> Networking utility to use either WEP or no encryption. That is about as easy as it gets, you don' t have to install the driver, Dapper and Edgy are already setup for it on PCMCIA or PCI.

Warning Atheros (mAdWiFi) does not work on USB sticks, not a problem for you. I just don't want others to think that just becase it worked for PCI or PCMCIA that it would work for USB as well.

---

### Post by iClouseau88 on 2006-11-27
Hi,
I can't find Alternate CD any where on the Forum.  Mine is from burning Dapper ISO onto a CD.  Is it the normal Dapper CD or Alternate Dapper CD?  Sorry for butting in, as I want to make sure my Dapper is already set up for WPA-PSK and madwifi.

Thanks in advance.

---

### Post by FrodoB on 2006-11-28
As long as you are not using the Alternate CD mAdWifi is going to be installed.  I don't know anything about it working with WPA or not, so I cannot comment. I am would consult the mAdWiFi site for details on WPA and WEP, etc.

---

