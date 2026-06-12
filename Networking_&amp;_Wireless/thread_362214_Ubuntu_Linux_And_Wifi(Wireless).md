---
title: "Ubuntu Linux And Wifi(Wireless)"
date: 2007-02-15
forum: Networking &amp; Wireless
---

### Post by xboomerx on 2007-02-15
I  am an Absolute Beginner!!!
Installed Ubuntu 6.10 and Windows XP on my HP KAYAK XU/550X.
How do I connect to my home network(802.11b) using Ubuntu 6.10?
My HP KAYAK XU/550X has 550MHz Pentium III XEON
processor, 80GB drive and 766MB ram.
I have a HP KAYAK XU/550X running Ubuntu 6.10 and Windows XP.
Can I install and connect my 
USB LinkSYS Wireless-B (Model WUSB11v4) Network Adapter?
How do I install and connect this Network Adapter?

Do you have any suggestions?
Thank You 
Bob Whitman

---

### Post by sumgi on 2007-02-15
It looks like some have reported that V2 of your device works from the start. Please have a look at this [guide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide"). Make sure you look at section 1 because it discusses the most basic step of setting up your wireless connection. Read through that document including the commands and you will have a much greater chance of getting yourself online.

---

### Post by ltcolfury on 2007-02-15
Ok, first off you will need to install "Ndiswrapper." Some other people may suggest another alternative but I will give you the another way to accomplish what you are trying to do.

Open up your Package Manager and download Ndiswrapper. (Administration/Synaptic Package Manager)

After installation, put in your Linksys CD disk that contains your driver for your wireless USB. Just copy the folder that contains your driver for Windows 2000 & WIndows XP onto your desktop. (Not sure which will work that's why I suggest copying both to desktop. I've had to use the Win 2K driver when I used a different flavor of Linux. I don't use Ndiswrapper anymore but I've used it many, many times and it works perfectly.) All you will need is the .INF file of the driver. If the Win 2K driver doesn't work, try using the Win XP driver.

If you prefer, you can use this as a guide line instead of my instructions. Jusat start at Installation.

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

Open up a Terminal (Accessories/Terminal) and type:

cd Desktop/folder where your driver is goes here (For example: cd Desktop/Linksys Windows 2000 driver)

ndiswrapper -i filename.inf (type in "exactly" what the name is of that driver.) (EX: ndiswrapper -i linksys WUSN11.INF)

Check to make sure it loaded with this command.

ndiswrapper -l

If all went well...

type in:

modprobe ndiswrapper

Now from here I configure my own settings by going to:

System/Administration/Networking

It is all pretty much basic form here. Also, I found it easier to enable the SSID in the router before doing this. It just makes it easier and afterward I will disable it.

---

