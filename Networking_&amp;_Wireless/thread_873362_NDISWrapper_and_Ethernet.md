---
title: "NDISWrapper and Ethernet"
date: 2008-07-28
forum: Networking &amp; Wireless
---

### Post by gaelfx on 2008-07-28
I have been having many problems with my internet connection lately on an nVidia MCP51 ethernet controller, and I was wondering if anyone here has any experience with using NDISWrapper to install drivers for ANY ethernet device. I'm running AMD64 version of 8.04, so I know that I probably need the 64-bit drivers, and I believe I may have found them, but I need some assistance in figuring out exactly what to do with NDISWrapper to get them installed. I realize that NDISWrapper's forum is probably a better place to go, but I've gotten little response on their forums and I was hoping the Ubuntu community might be more help. And please don't respond with "well, it works just fine out of the box on my computer," I'm getting really sick of hearing this from other people. It's not a problem with my hardware since the connection works fine on my Windows partition. Also, I have to connect through Static IP and then dial PPPoE, so there's all the relevant information I think anyone would need. If you need more info, just let me know.

---

### Post by gaelfx on 2008-08-01
bumperoo

---

### Post by mb_webguy on 2008-08-02
AFAIK, ndiswrapper is for wireless, not Ethernet, but you can give it a try...

The easy way to use ndiswrapper is to use the GUI interface, which you can install by typing "sudo apt-get install ndisgtk" in the terminal.  If you have your Windows driver, it's just a matter of going to System->Windows Wireless Drivers, clicking "Install New Driver", and selecting the driver (the .inf file).  Then restart networking by typing "sudo /etc/init.d/networking restart" in the terminal.  You should now be able to connect.  If not, try rebooting your computer (or at least logging out and back in again).

---

### Post by gaelfx on 2008-08-04
Thanks for the reply, I'll give it a try as soon as I'm back on Ubuntu.

---

### Post by caljohnsmith on 2008-08-04
How exactly does "lspci" list your ethernet card? It's just that I'm not familiar with your "nVidia MCP51" ethernet controller and I'm wondering if lspci refers to at something a little different.

---

### Post by gaelfx on 2008-08-09
that's how it refers to it, I think rev a3 or something like that

---

### Post by jimv on 2008-08-10
That's the same card I have...it works fine under Hardy 32 bit (and it worked fine in 64 bit when I tried it).  What problems are you having?

---

