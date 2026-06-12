---
title: "Network Settings, nm-applet, and Network Manager"
date: 2008-07-01
forum: Networking &amp; Wireless
---

### Post by zacktu on 2008-07-01
I used System -> Administration -> Network to use set up wireless networking at home with WEP in the Network Settings window.  That works great.  Yesterday I went to a coffee shop and tried to use their open wireless network.  I tried to do this with Network Services with no success.  I then tried the nm-applet in the taskbar.  If I right click on the nm-applet icon I see that Enable Networking is checked and that my only choice is Edit Wireless Networks.  If I select Edit Wireless Networks, then I get a window with all blank fields.  I assume that I should be seeing a list of networks. Do I need to do something in Network Settings in order to see a list of wireless networks with nm-applet? 

Thanks.

zack

---

### Post by pytheas22 on 2008-07-01
Unless the network that you're connecting to requires special settings (like a static IP address), you shouldn't need to use the Network utility.  Just *left* click on the NM applet and you will see a list of wireless networks.  Click the one you want to connect to, you'll be asked for the password if necessary, and voilà.

Note that you may have go to back to the Network utility and reclick the box that says "enable roaming mode" for your wireless card.  Otherwise it's going to be able to connect only to the network that you explicitly configured, which is why you can connect only at home and not at the coffee shop.  In roaming mode, you can connect to any network in range whose password you know.

FYI right-clicking on the NM applet and selecting the "edit wireless networks" allows you to specify a few special options that NM should use, like which router it should try to connect to if there's more than one for the same network.  But in most cases you should never need to touch these settings.

If you don't understand what I'm talking about, let me know and I'll post screen shots showing what you need to click and unclick.

---

### Post by zacktu on 2008-07-08
Today was my first opportunity to be in a setting with an open wireless network.  I followed your instructions, and everything worked like a charm.  Thanks very much for your help.

---

