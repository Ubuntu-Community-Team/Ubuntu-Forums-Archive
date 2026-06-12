---
title: "Can't connect to the Internet using Netgear WG111v3 USB wireless adapter"
date: 2008-11-14
forum: Networking &amp; Wireless
---

### Post by 123581321 on 2008-11-14
Hi! I just installed Kubuntu 8.10 (KDE 4.1) in my Dell Optiplex GX270. Everything went fine except the Wireless adapter. At first, the network manager in the taskbar recognised the Wi-Fi connection (although it still does), and I could browse the web with Konqueror. But now, it connects to the Wi-Fi hotspot, it shows it in the taskbar, but when I open Firefox or Konqueror they will not load anything, because it can't connect to the Internet. 

So I tried installing NDISwrapper. I installed the ndiswrapper-common, the ndiswrapper-utils and the ndisgtk, but I still need the .inf and .sys from the driver to be able to install them using ndiswrapper. The ID I got using lsusb is 0846:4260, and I've googled it to find the Windows driver, but I haven't found it. 

If anybody knows how to fix the KNetwork problem or knows where to find the Windows driver, I would be very thankful.

---

### Post by stooshbunutu on 2008-12-09
Hey,

I have compiled a tutorial for the start to finish installation of a WG111v3. I must admit that I have not used it on Kubuntu but it certainly works on Ubuntu 8.10 (using it now). At the very least though there is a wget link to the required WG111v3 drivers.

see my tutorial:
[On My Website]("http://helpbuntu.mstrutt.co.uk/wireless.html")
[On Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=732827&highlight=wg111v3")

Regards

---

