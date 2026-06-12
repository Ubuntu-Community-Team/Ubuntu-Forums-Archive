---
title: "linksys usb adapter help"
date: 2007-12-31
forum: Networking &amp; Wireless
---

### Post by ziploc67 on 2007-12-31
It seems that linksys does not have very good support for my usb model wireless network adapter. the model's code, if you will, is WUSB54GSC, or Wireless-G Adapter with Speedbooster. It has installed, but I can't get it to work, due to a EAccessViolation error that pops up every time I try to start the Wireless Network Manager that comes with the setup CD. Does anyone have any knowledge on the subject, the latest thread I saw on this matter was very remote in contrast to mine, and was back in 2005.

edit: as a side note, i tried ndiswrapper on my setup cd, located the .inf file, and it tells me that the driver is invalid!

---

### Post by ziploc67 on 2008-01-01
does anyone have a clue about this????

---

### Post by Vadi on 2008-01-01
No clue, and my friend has the same card. Lets hope someone cluefull will answer.

---

### Post by chimerical_brio on 2008-01-01
From the ndiswrapper site:
> 
Driver: Downloaded driver [http://www.linksys.com/servlet/Satellite?c=L_Download_C2&childpagename=US%2FLayout&cid=1115417109934&packedargs=sku%3D1154470123093&pagename=Linksys%2FCommon%2FVisitorWrapper](http://www.linksys.com/servlet/Satellite?c=L_Download_C2&childpagename=US%2FLayout&cid=1115417109934&packedargs=sku%3D1154470123093&pagename=Linksys%2FCommon%2FVisitorWrapper) here and install. Copied the win files (usb8023.sys and rndismp.sys) from the F5D7051.exe [http://www.belkin.com/support/download/downloaddetails.asp?download=1871&lang=1](http://www.belkin.com/support/download/downloaddetails.asp?download=1871&lang=1) download to the /etc/ndiswrapper/wusb54gsc/ folder. Lastly, use the script detailed [http://www.ubuntuforums.org/showthread.php?t=225206](http://www.ubuntuforums.org/showthread.php?t=225206) here , modidifed with the correct USB ProdID (0026), to get the power working. It’s in the section ‘Getting WUSB54GS to Work in Edgy and Feisty’ Also check out the thread [http://www.linuxquestions.org/questions/showthread.php?p=2559643](http://www.linuxquestions.org/questions/showthread.php?p=2559643) here for why the script is needed and works.
which is found on [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/)

So I would try a manual install of ndiswrapper ([https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)) and install in the above manner.

---

