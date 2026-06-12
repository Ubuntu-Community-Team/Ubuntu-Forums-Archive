---
title: "Help!! UR054g wireless adapor wont work (8.10)"
date: 2008-11-08
forum: Networking &amp; Wireless
---

### Post by Jontyy on 2008-11-08
new to linux.
i cannot figure out how to install the windows drivers, ive followed topics on this forum but still cannot manage to do it.
somebody please help
thanks

---

### Post by Jontyy on 2008-11-08
anyone?

---

### Post by Jontyy on 2008-11-08
bump, sorry lol

---

### Post by Steve1961 on 2008-11-08
Well, if you have the windows drivers the first thing to make sure is that you have the right files.  An exe file wont work, you need a *.inf and *.sys file.  If you have those great, if not, you may need to install the driver on a windows machine first and then grab the .inf and .sys files and put them in a folder in your home directory.  

Once you have the files just install ndiswrapper and follw this how to:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by Jontyy on 2008-11-08
i have all of the drivers on a cd my ISP sent me ages ago.
thanks

---

### Post by Jontyy on 2008-11-08
in windows i checked the drivers the device needs on control panel> administrative tools > computer management then driver details on the device.
i have copied all of these driver it says it uses.
ndiswrapper doesnt work in ibex does it?

---

### Post by Steve1961 on 2008-11-08
> **Jontyy said:**
> in windows i checked the drivers the device needs on control panel> administrative tools > computer management then driver details on the device.
i have copied all of these driver it says it uses.
ndiswrapper doesnt work in ibex does it?


ndiswrapper does work in Intrepid.  Just install the ndiswrapper packages from your cd.  Open a terminal and move to the folder where you dropped the driver files (cd folder).  Type ls so that you can see each of the files and install the .inf file (sudo ndiswrapper -i *.inf).  If it installs then type modprobe ndiswrapper and click on network manager to see if you can see your wireless network.

---

### Post by Jontyy on 2008-11-08
i installed ubuntu using wubi so i dont have the cd. thanks

---

### Post by HotCupOfJava on 2008-11-08
There is also a graphical ndiswrapper tool that you can use if you find that easier. Go to "system" -> "administration" and choose "Synaptic package Manager". Do a search for ndiswrapper. Click the box next to the one that is marked "ndisgtk". It will tell you that it will need to install a couple of other packages as well. Let it do it. Click "apply". Once it is finished you should have a new menu option under "system" that says something like "Windows network drivers". Open it. You can then add new drivers by selecting the ".inf" file for your card. 

Of course, you can only do this if you have a WIRED internet connection you can use temporarily.

---

### Post by Steve1961 on 2008-11-08
> **Jontyy said:**
> i installed ubuntu using wubi so i dont have the cd. thanks

In that case just go to that link I posted earlier and download the ndiswrapper packages manually.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by Jontyy on 2008-11-08
lol av nt gt a wired connection to the pc. A can try to use my ps3 to download it, btw i searched in the synaptic package manager and it didnt find ndiswrapper or ndisgtk.

---

### Post by HotCupOfJava on 2008-11-08
Well, Synaptic wouldn't be able to find the package without a connection....

Do you have access to the wireless router? If so, just plug the comp into it temporarily so Synaptic can get the packages for ndiswrapper......if not, you might want to see if someone can let you plug into theirs long enough for you to do it....

---

### Post by Jontyy on 2008-11-08
right im on another compuyter ill download the ndiswrapper from the link and put it on a usb drive

---

### Post by Jontyy on 2008-11-08
right, i think ive installed ndiswrapper. i dont know which is the driver for the wireless card. this is on the cd the isp sent me
This in the folder "driver"

/media/cdrom0/Drivers/USB/BlueDSL.inf
/media/cdrom0/Drivers/USB/dw200-0A5C.inf
/media/cdrom0/Drivers/USB/dw200-0F4F.inf
/media/cdrom0/Drivers/USB/InventelGateway.inf
/media/cdrom0/Drivers/USB/resc_dwb.sys
/media/cdrom0/Drivers/USB/RescueDrv.inf
/media/cdrom0/Drivers/USB/rndismp.sys
/media/cdrom0/Drivers/USB/RNDISMPK.sys
/media/cdrom0/Drivers/USB/rndismpm.sys
/media/cdrom0/Drivers/USB/rndismpw.sys
/media/cdrom0/Drivers/USB/usb8023.sys
/media/cdrom0/Drivers/USB/usb8023k.sys
/media/cdrom0/Drivers/USB/usb8023m.sys

would someone be able to give me like a noob step-by-step guide
thanks

---

### Post by Steve1961 on 2008-11-08
None of those look obvious candidates.  I've done a google search and most of the results point to French sites, and my french is dreadful.  However, many say that the adapter uses PRISMA02.inf as the driver.  Anything like that on the cd?

---

