---
title: "WPC54G ver 5, can't get it working!"
date: 2006-08-06
forum: Networking &amp; Wireless
---

### Post by Praxidike on 2006-08-06
Hi
Does anyone know how I'd get this working?  I've done a few searches, only found solutions for lower versions, but I've downloaded the drivers, tried some of the same techniques, but it doesn't seem to be working.

I'm quite new to Linux too, not installed any drivers before (although I'm competent enough and installing other things.... I just don't know how to do drivers, all confusing!)

One thing that might be messing it up... when trying this

[http://www.ubuntuforums.org/showthread.php?t=201633&highlight=WPC54G]]("http://www.ubuntuforums.org/showthread.php?t=201633&highlight=WPC54G")

 method, when I get to 




sudo ndiswrapper -i lsbcmmds.inf




it says lsbcmmds is already installed.  Use -e to remove it...

so I type
sudo ndiswrapper -i lsbcmmds.inf
and it says lsbcmmds.inf is not installed!!!  ](*,) 

And then...

sudo ndiswrapper -l
gives me

Installed ndis drivers:
lsbcmds invalid driver!
lsbcmmds    invalid driver!
lsbcmnds   driver present
lstinds    driver present





Thanks :)

---

### Post by Praxidike on 2006-08-07
Nobody knows? :(

---

### Post by casaschi on 2006-12-21
Better late than never, I got everything working starting from instructions below and then using wifi-radar for managing WPA encryption:

From [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

Card: Linksys #[WPC54G v5], 54mbps -- [link here|List#WPC54G v5]

Chipset: Marvell 88w8335
pciid: 11ab:1faa
Driver: [http://www.linksys.com/servlet/Satellite?blobcol=urldata&blobheadername1=Content-Type&blobheadername2=Content-Disposition&blobheadervalue1=application%2Fzip&blobheadervalue2=inline%3B+filename%3DWPC54Gv5.zip&blobkey=id&blobtable=MungoBlobs&blobwhere=1130950145165&ssbinary=true](http://www.linksys.com/servlet/Satellite?blobcol=urldata&blobheadername1=Content-Type&blobheadername2=Content-Disposition&blobheadervalue1=application%2Fzip&blobheadervalue2=inline%3B+filename%3DWPC54Gv5.zip&blobkey=id&blobtable=MungoBlobs&blobwhere=1130950145165&ssbinary=true)

Other: The ridiculous URL above appears to be the only way to get at the official driver, since there's nothing obvious at the Linksys ftp site. Tried now and the link seems to have issues, other option is to go to [http://www.linksys.com](http://www.linksys.com) , click on downloads and select WPC54G v5, the driver and take it from there...

Unpack WPC54Gv5.zip, then

sudo ndiswrapper -i LSMVNDS.inf. 

at this point, after 

sudo modrobe ndiswrapper

you should have the wlan0 interface showing up, ready to be configured.
I used wifi-radar (sudo apt-get install wifi-radar) to get it working with WPA and then made ndiswrapper loaded at startup (adding it to /etc/modules)

---

