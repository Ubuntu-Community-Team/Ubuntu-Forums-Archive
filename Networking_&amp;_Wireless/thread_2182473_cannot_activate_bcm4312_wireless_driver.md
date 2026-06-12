---
title: "cannot activate bcm4312 wireless driver"
date: 2013-10-21
forum: Networking &amp; Wireless
---

### Post by user987 on 2013-10-21
I have installed ubuntu 12.04 3LTS live cd on a usb flash drive.
The ISO version i downloaded was 1.6G and not the 700g.

I assume that the 1.6 ISO would contain updates and software, but it seem that is not the case.

When i went to additional driver and try to activate it .

I got error var/log/jockey.log

From my research here it seems i need a wire connection to activate the sta linux driver.

My problem is i can only get wireless access at the library.

Is there a easy way to activate it off line?

I thought that all necessary software was included with the ISO

I am using a dell mini 9 netbook with broadcom bcm4312 wireless driver.

It seem mint 13 and 15 have the same problem.

Why the hell did the developer not include wireless driver package in the iso so i can activate to get online

Not every one have wire access.

Please help
Please help.

---

### Post by Bucky Ball on 2013-10-21
Ask Broadcom.

Anyways, the catch22 is if you want the Broadcom driver you need to get online or have access to a machine that is. You can follow this:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access)

... as I think you actually need the b43 driver for your card. Instructions for offline install of STA there also. 

Part of b43 should be on your system. I think you need:

b43-fwcutter
firmware-b43-installer

Look in Software Centre. The former should be there, the later you need to download from a machine that is online. (If you could get your own machine online this would be a snap and done in no time.)

While I understand your frustration, your venom is misdirected. ;)

---

### Post by Hadaka on 2013-10-21
Hi, here is a way to get your driver..no internet
copy the attached b43 zip file to a usb..then load onto
your ubuntu machine.drag and drop to Desktop
At the Desktop, right click and choose..Extract here.
then do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```

---

### Post by user987 on 2013-10-21
Hadaka,

I downloaded your zip and will give it a try.
when i drag it to the desk top and unzip there.

After that i assume i have to go to terminal to type the code?

Will give it a go when i get home and use my other computer.

---

### Post by Hadaka on 2013-10-21
Great , sounds like you know what to do,
dont forget to upcase the "D" in cp Desktop.
keep us posted
thanks.

---

### Post by user987 on 2013-10-22
Hadaka,
i have b43 driver install because I see more options on the internet tab

but wireless network appears light and not bold so I cannot click on it to see available networks
can you tell me what else to do?

---

### Post by Hadaka on 2013-10-22
Hi, is the wired internet working?
*If yes...then please do and post..
```
lsmod
sudo iwlist wlan0 scan
rfkill list all
```
thanks.

---

### Post by Bucky Ball on 2013-10-22
Hadaka:

> **user987 said:**
> 

My problem is i can only get wireless access at the library.



If wired was available this would be fixed in no time and certainly by now. ;)

---

### Post by user987 on 2013-10-23
the b43 driver install in the internet tab shows the wire internet non bold also like wireless network.

so i can not click on either one, but the bottom line even if i could click on the wire internet, i have no wire access only wireless.

Is there any other command i can use to get wireless internet?

By the way a while back i put a live cd of ubuntu 11.04 on a usb and that one work perfectly.

Everything was in the ISO, any idea on what was change since then?

---

### Post by Hadaka on 2013-10-23
Hi, there have been hundreds of changes since 11.04...sooo
Let me get this straight, you are attempting to access wireless
via a usb stick..useing the "try ubuntu" method? Is this correct?

---

### Post by user987 on 2013-10-23
Yes

---

### Post by user987 on 2013-10-24
Hadaka,
i guess the only fix is to try to get to a wires connection and down load the sta Linux driver in the additional driver under the system tab?

---

### Post by Hadaka on 2013-10-24
Having a wired connection should  correct the problem.
I had 12.4 with wirelss on a usb stick. So i wiped it and tried to
re-create your situation. I have yet to find a way to get the wireless
to load while in the "try Ubuntu" mode even with the usb bootable/persistant.
so..yeah...find a wired connection and all should be well.

---

### Post by user987 on 2013-10-25
Hadaka,
           I am going use the internet cable to the library computer at my library on my netbook with the 12.04 3 lts to download the sta driver.
Would i get a direct internet connection or they have some sort of security feature there?
I ask to use it and they refuse me but will do a sneak connect but would like to know if you see any potential problem?

Also thanks for all your help to date.

---

### Post by Bucky Ball on 2013-10-25
Once you get online you probably won't need to do much at all as the card will be detected and you will be notified of which drivers are available. Not positive STA is best for that card (not sure why you think so, either), but something should be offered automagically. If it is the STA and doesn't work, try the b43 drivers as described earlier (from memory). They might be offered up first anyhow. 

I mention this because the STA driver is known to be problematic with some cards. The b43 is generally more robust and has variations for a lot of cards. Good luck.

* When you get online, do an update, and be sure to check in Additional Drivers. The STA and the b43 may both be in there after an update.

* Just wondering: Do you not have internet access with a cable at home or at a friend's, or do you live at the library?

---

### Post by user987 on 2013-10-25
That is my problem, i don't have cable at home but spent 1 or 2 hours a day at the library and get all my cable shows, check emails and that is good enough for me.

I have friends with internet but rather not bother them since we are all busy, but only do it as last resort.

---

### Post by user987 on 2013-10-29
Hi,
     i finally try a wire connection at my friend's house and it was trying to connect and fail, my friend say that he was seeing his connection on his router, so what happen?
Why can't i get internet connection even with a wired connection?

By the way i also tried a mint 13 and same thing happen.

Please help.

Also do anyone know another distro that has internet connection drivers in the iso and i can use right out of the box?

---

