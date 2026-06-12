---
title: "NetworkManager: can't save any connection as system-wide"
date: 2008-08-24
forum: Networking &amp; Wireless
---

### Post by VinzC on 2008-08-24
Hi.

I've gently filled the WPA key for my wireless network and now I'd like to make it a system connection -- presumably so that it starts when my computer boots. I have Xubuntu Intrepid Alpha4 on a Dell Inspiron 9400 and the wireless card is Intel Pro/Wireless 3945.

Note this is the first time I really wanted to work with NetworkManager since a long time ago -- everytime I got my fingers on it I got disgusted but I presumed it was me. I'm a Gentoo user and I never had to install it. Mostly the XML format (gconf) in which data are stored is... how can I say... absolutely horrible -- just an illustration of the worst way storing data in XML. (I wonder which tortured mind invented that :twisted:.) But Ok. Let's go.

When I click the "System" checkbox for my Wireless connection and save it, I get an error message saying "Adding connection failed: Saving connection failed."

Never mind, I went for removing the connection and create it again but manually. No way. I get the same error message. Apart from doing it the good old way, i.e. setting all my wireless networks in /etc/wpa_supplicant/wpa_supplicant.conf I'm stuck.

Any idea?

Thanks in advance.

---

### Post by VinzC on 2008-08-24
See [Bug 255839]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/255839")
Fix: manually create directory **/etc/NetworkManager/system-connections**.

---

