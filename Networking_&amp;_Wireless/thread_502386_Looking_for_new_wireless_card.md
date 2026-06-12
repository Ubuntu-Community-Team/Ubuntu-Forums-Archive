---
title: "Looking for new wireless card"
date: 2007-07-16
forum: Networking &amp; Wireless
---

### Post by File13 on 2007-07-16
Hi all, well ive had some luck with getting my internal wireless working on my V3019 compaq presario but the internal wireless card has been acting weird even on windows, its going really slow for some reason. Anyways i was wondering if anyone had a good suggestion. My laptop to my knowledge doesnt have a slot for normal wireless cards so im thinking more the usb route?

---

### Post by MyR on 2007-07-16
this card works well:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16833315067](http://www.newegg.com/Product/Product.aspx?Item=N82E16833315067)
peace

---

### Post by File13 on 2007-07-16
does this work "out of the box"?

---

### Post by MyR on 2007-07-16
hmm not sure ( but it does support packet injection ;] )
theres a list of usb devices supported out of the box here:
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
peace

---

### Post by File13 on 2007-07-16
Any other usb sticks that are "out of the box" compatible?

---

### Post by MalcolmCarmen on 2007-07-16
I just recently went on the usb wireless adapter crusade, and I've come to the conclusion the edimax (rt73 chipset) is basically the best at the moment. I believe starting with edgy, rt73 drivers come with ubuntu, but I hear they are a bit unstable. There's a thread on the forums here if you search them with 30+ replies which details how to install newer drivers. I believe there are cheaper usb adapters on newegg, but you'll have to use ndiswrapper and will have no chance of using kismet/aircrack.

If you want to use aircrack, make sure to read the section on the site for the rt73 which contains some more information for using the rt73. Also, there's a more expensive version of the adapter with a detachable antenna which might aid in the search for APs; [http://www.newegg.com/Product/Product.aspx?Item=N82E16833315075](http://www.newegg.com/Product/Product.aspx?Item=N82E16833315075)

---

### Post by File13 on 2007-07-16
im not really ATM looking for it to be able to do wireless cracking things but its nice to know its available if i ever did want to do that. looks like ill go with that one its cheap and appears to work nicely for a few people. im getting frustrated trying to get my own internal one to work, i followed the steps to do it work for word but the wireless adapter is running very very slow reguardless, both on windows and ubuntu. I have a wireless USB adapter right now from Addlogix that im trying to see if anyones ever tried it under ubuntu but its not on the Wiki.

---

### Post by File13 on 2007-07-20
I ordered the edimax usb one off newegg but no dice, when i plugged it in before i launched the laptop when it booted it was as a prompt screen saying something along the lines of recognizing it yet when it launched to the GUI ubuntu locked up, had to remove it from the USB slot to boot, then when i rebooted and plugged in the USB wireless adapter i would launch programs and they would hang in the launch bar then disappear and not do anything?

---

### Post by File13 on 2007-07-20
can any one think why the USB adapter would be causing the computer to do that?

---

### Post by stchman on 2007-07-20
> **File13 said:**
> Hi all, well ive had some luck with getting my internal wireless working on my V3019 compaq presario but the internal wireless card has been acting weird even on windows, its going really slow for some reason. Anyways i was wondering if anyone had a good suggestion. My laptop to my knowledge doesnt have a slot for normal wireless cards so im thinking more the usb route?

You can get an Intel 3945 new off ebay for around $20 shipped.  The Atheros line of cards are very Linux friendly as well.  I recommend the mini-PCI over USB.

---

### Post by File13 on 2007-07-20
bump

---

