---
title: "Help with Belkin Wireless USB receiver"
date: 2007-02-23
forum: Networking &amp; Wireless
---

### Post by Tcgunner90 on 2007-02-23
hey everyone. first off, let me say..i'm VERY new to linux in general. i only just made the switch from windows 2 days ago! so please, remember that as you give me an answer hehe.

well like i said i have a belking wireless G receiver. and i need to know how to install it and get it working. i downloaded that ndwsis wrapper program..but i thinkt the main problem is that i have no idea how to install it. i have no internet on my computer with Ubuntu. so i'm using an alternate computer and have no idea how to run it. 

So i've heard that once you run that you can use the install CD or run the driver by downloading it from the internet.

if you can help me , please, do. and if you would be so kind, as to bear in mind that you will be consorting with the newbiest of newbs. haha

---

### Post by Tcgunner90 on 2007-02-25
bump! this is paramount! i need the internet hehe. please?

---

### Post by bobpaul on 2007-02-25
Have you tried looking on the Ubuntu Wiki? I did ndiswrapper on a laptop last summer, and the wiki gave me everything I needed. Here's an [article]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") that might help you.

---

### Post by benson444 on 2007-02-26
What is the exact model of your receiver? Type this into the terminal (Applications -> Accessories -> Terminal):

lsusb

and paste the output here.

---

### Post by devoncatt on 2007-02-26
You probably will receive more help if you include the version of Ubuntu you are using 
(i.e hoary, edgy, etc.). The version of the belkin usb adapter ( the model number and version- it should be on the original packaging). You can do an lsusb on the command line to see if the device is recognized. I have a Belkin USB F5D7050 version 3 wireless that is also giving me problems. The PCI or pcima(laptop) cards tend to easier to setup. 
You will also need to know what kind of security you are using (WEP, WPA, Shared key etc.)
Hope this helps a little.
You can download the .deb packages from the repositories and copy them to a USB key or a CD and then run them on your machine.
dpkg installs many programmes, once you are connected to the network synaptic or adept are easier to use to find packages you need to install.
Devoncatt

---

### Post by devoncatt on 2007-02-26
[http://opensource.bureau-cornavin.com/belkin/index.html](http://opensource.bureau-cornavin.com/belkin/index.html)
Is a site that lists how to install USB wireless device with linux. There also is another thread in this forum on the next page which also talks about your problem.

---

### Post by benson444 on 2007-02-26
> **devoncatt said:**
> I have a Belkin USB F5D7050 version 3 wireless that is also giving me problems. 
Devoncatt

What problems are you having? I made a post in another thread about the F5D7050 usb receiver. If you get 0x50d:0x200 or 050d:705a in the output from "lsusb" then try this guide.

[http://wiki.ubuntu-it.org/RalinkRT73](http://wiki.ubuntu-it.org/RalinkRT73)

Don't know if it worked for the person who asked as he didn't reply, but it worked for me. I'm using the 050d:705a version with WPA. Had it working on Dapper and Edgy.

---

