---
title: "d Ubuntu can't find modem"
date: 2008-10-18
forum: Networking &amp; Wireless
---

### Post by Gerfgfud on 2008-10-18
I'm using a TP-Link TL-WN821N wireless usb modem, and ubuntu can't detect it. But it works with windows.

Any help?

---

### Post by tibellus on 2008-10-18
Are you positively sure that it can't detect it? Have you tried with "lsusb"?

---

### Post by Gerfgfud on 2008-10-18
> **tibellus said:**
> Are you positively sure that it can't detect it? Have you tried with "lsusb"?

I have no idea what that is.

---

### Post by tibellus on 2008-10-18
Please, open up a terminal and type that command. It will show you all the devices that are connected through a USB port. Let me know if your modem is shown in that list.

---

### Post by Gerfgfud on 2008-10-18
I went to try it, and im stuck with imitramfs.

---

### Post by Gerfgfud on 2008-10-18
it isnt in the list.

---

### Post by tibellus on 2008-10-19
So it doesn't even detect it... I will try to find out more about this problem, I'm sure there's some way to fix it. In the meantime, here's a link that might prove useful:

[http://www.networkedmediatank.com/showthread.php?tid=5276&pid=66067#pid66067](http://www.networkedmediatank.com/showthread.php?tid=5276&pid=66067#pid66067)

---

### Post by rogues29 on 2008-10-22
Hi Gerfgfud,

I've been trying to fix this for a while too! I have the same adapter and have tried for ages to fix it. Anyway, I just figured out a way to get the adapter to work. I've been stuffing around with this for long enough that I'm not totally sure which steps from what I've done are 100% necessary but i think these are what is needed....

Before i start too, please note that this is the first time I've written any instructions and the first time I've posted to these forums, and I'm a Linux newbie so i will most likely get something wrong :-D.

Also, unfortunately my skills are not great enough to help you install the necessary stuff unless you have some way of getting internet access on the computer which, somewhat ironically, you are probably trying to get the internet working on. But perhaps if you can't do this then someone else can help you with the steps that I cant using what I've written below.

Firstly you need to use **ndiswrapper**, it should be installed but on my Ubuntu 8.04 it was only the terminal command version there is a utility that made it much easier to select the driver. I think the package you need to install is called **ndisgtk** it should be in the Synaptic Package manager or you can install it by opening a terminal and typing:

```
sudo apt-get install ndisgtk
```

once that is installed it should put a link in **System->Administration** called **Windows Wireless Drivers**

What that program requires is the windows drivers for the device. unfortunately the drivers for the TP-Link device don't work in ndiswrapper, at least all the ones i could find from TP-Link. There are a few other Wireless USB dongles that come with the same chip set, and it is one of these that i got to work 10 minutes ago. The drivers you need to download are for a IOGear device and are available at [http://www.iogear.com/support/driver/GWU623.zip]("http://www.iogear.com/support/driver/GWU623.zip") or if that link doesn't work then [http://www.iogear.com/support/dm/driver/GWU623#display]("http://www.iogear.com/support/dm/driver/GWU623#display") maybe.

the only things you need are the files in **GWU623.zip/drivers/XP** and then whichever architecture you are running i can only verify that the 32-bit ones worked because i don't have 64-bit. so extract the 3 files in either of those directories all to the same directory (i don't think it matters where).

Then go into the **Windows Wireless Drivers** app and click **Install New Driver** find the folder you extracted the files to and select the file ending in **.inf** click **Install** and that should be it. Wait a couple of seconds to let the device start up and then Left click the network icon in the system tray to connect to wireless networks in range.

I can't guarantee that this will work but i think it's what has worked for me. Hope it helps you too! I'll try to reply to any questions you have but I'm not near the net all that much so replies may be a bit delayed. I'm no expert but will attempt to help.

Cheers,

Rogues

Please excuse me spellink and graMMer.

---

### Post by excogitation on 2009-04-14
@rogues29: Does wpa/wpa2 work for you?

With your method I can get the TL-WN821N to be recognized and even find various networks - but I haven't been able to connect to my wpa/wp2 network so far.

---

### Post by masque7 on 2011-07-14
Recently purchased a WN821N adapter by TP-Link, running Ubuntu 10.04 LTS. No response at all from adapter. This may be beause the chipset has change, with the manufacturer keeping the same model no.

Running *lsusb* in terminal: (you don't *need* to do this -- but should to check what chipset you have)
```
Bus 002 Device 004: ID 0cf3:7015 Atheros Communications, Inc.
```I have uploaded the Windows XP 32-bit driver files from the miniCD provided with the adapter on mediafire and via the forums attachment (bottom).
[http://www.mediafire.com/?corx6u2sj60keic](http://www.mediafire.com/?corx6u2sj60keic)

Install the GUI for ndis wrapper: 
```
sudo apt-get install ndisgtk
```
Extract the 7zip or zip file I uploaded. Run ndisgtk from system --> admin --> Windows Wireless. Add new, select the .inf file you previously extracted. Device then lights up and connects. WPA2 encryption worked fine for me.

Under NetworkManager dropdown device is called "ATHEROS UB95"

---

### Post by pellefantus on 2011-09-15
> **masque7 said:**
> Recently purchased a WN821N adapter by TP-Link, running Ubuntu 10.04 LTS. No response at all from adapter. This may be beause the chipset has change, with the manufacturer keeping the same model no.

Running *lsusb* in terminal: (you don't *need* to do this -- but should to check what chipset you have)
```
Bus 002 Device 004: ID 0cf3:7015 Atheros Communications, Inc.
```I have uploaded the Windows XP 32-bit driver files from the miniCD provided with the adapter on mediafire and via the forums attachment (bottom).
[http://www.mediafire.com/?corx6u2sj60keic](http://www.mediafire.com/?corx6u2sj60keic)

Install the GUI for ndis wrapper: 
```
sudo apt-get install ndisgtk
```Extract the 7zip or zip file I uploaded. Run ndisgtk from system --> admin --> Windows Wireless. Add new, select the .inf file you previously extracted. Device then lights up and connects. WPA2 encryption worked fine for me.

Under NetworkManager dropdown device is called "ATHEROS UB95"
sorry doesnt work at my current 11.04 @ Linux pc 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:05:14 UTC 2011 i686 i686 i386 GNU/Linux

---

### Post by masque7 on 2011-09-15
> **pellefantus said:**
> sorry doesnt work at my current 11.04 @ Linux pc 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:05:14 UTC 2011 i686 i686 i386 GNU/Linux
As I said, the chipset changes but the model numbers stay the same. If you refer back to my post and run the command, or find out what chipset you have.

I thought these cards/adapters were supported out of the box on 11.04...?

Unfortunately with my aforementioned work around to get the adapter working, it only operates at wireless G speeds, not wireless N!

---

### Post by pellefantus on 2011-10-09
is there anyway to enable N speeds for this wlan interface? Have anyone succeeded at this?

---

