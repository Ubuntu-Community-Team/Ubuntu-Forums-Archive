---
title: "Connecting to Wireless Network with USB Adaptor"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by J Baker on 2009-11-01
Hi apologies if this is a really basic question. I've just installed Ubuntu 9.10 and am totally new to the linux environment. I've tried looking at the help guides and previous threads but can't find anything that helps (or at least at a basic enough level).

The problem I have is that I can't seem to connect to my wireless network through my usb adaptor (it's an edimax EW7711-UAN). Using a network cable is fine but if I go to the network connections from the top right of the screen there are no wireless ones available. If I use 'create a new wireless connection' and pass my network name and password it says I am connected though the Internet connection doesn't work. If I then disconnect my network does not appear on the list of those available though a few others do mysteriously appear but all with unintelligible characters for the name.

I am assuming that my adaptor is not recognised and do have some linux drivers that came with the windows installation disc. However, I am not sure if this is the problem or how to install the drivers in any case.

Would be grateful for any pointers or a link to a basic article that can get me started. I've been trying for the last few hours but am no nearer to resolving this.

Also, as a complete aside - when booting up and periodically when switching windows I get very loud interference type click. Do you know what is causing this?

Thanks in advance for any help

John

---

### Post by Tahakki on 2009-11-01
Taken from the Help program that comes with Ubuntu...

> 5.2.3.&#8195;Using Windows Wireless Drivers

Ubuntu supports a system known as NDISWrapper. This allows you to use a Windows wireless device driver under Ubuntu.

   1. Obtain the Windows Driver for your system and locate the file that ends with .inf.
   2. Install the ndisgtk package.
   3. Open ndisgtk (System &#9656; Administration &#9656; Windows Wireless Drivers).
   4. Select Install new driver.
   5. Choose the location of your Windows .inf file and click Install.
   6. Click OK.

---

### Post by autocrosser on 2009-11-01
First...you should look at the community docs: [https://help.ubuntu.com/community/WifiDocs/WirelessNetworking?highlight=%28network%29|%28wireless%29#head-ce415853bb8f9c18e52168777c376ef4a80e5de1]("https://help.ubuntu.com/community/WifiDocs/WirelessNetworking?highlight=%28network%29%7C%28wireless%29#head-ce415853bb8f9c18e52168777c376ef4a80e5de1")

And then look to see if your adapter is supported: [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

Linux supports a fair amount of wireless devices, but there are some that are far more trouble to use than others. USB adapters seem to fall into the harder group.

Also look at: [https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

---

### Post by J Baker on 2009-11-15
Thank you both for the advise. It's taken me a while to get to grips with this but the pointers you gave were very helpful.

Unfortunately, I didn't manage to get my edimax usb adpator to work - but from reading all the documentation I realise this is an unsupported adaptor and it seems that people with far more knowledge than me have failed to get it to work.

Have found than a netgear adaptor I have is supported and am currently trying to get that to work with NDISwrapper. It seemed to work but since a restart I can't get it work again. Think I may have partially installed drivers with my attempts with the first adaptor so trying a clean system install and trying again.

---

