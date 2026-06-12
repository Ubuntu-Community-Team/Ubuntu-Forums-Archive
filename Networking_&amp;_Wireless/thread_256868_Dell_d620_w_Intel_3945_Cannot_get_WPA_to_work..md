---
title: "Dell d620 w/ Intel 3945 Cannot get WPA to work."
date: 2006-09-13
forum: Networking &amp; Wireless
---

### Post by neum on 2006-09-13
*This is my first Linux install ever so I know nothing.*

After developing on Windows for years I decided it was time to give Linux a try. Install was great. Using other threads I got 3D for the nvidia card working. Upgraded to 686 and dual processors.  

But... I need wireless to work at my workplace. (It works fine at home) Work uses standard WPA. I have used synaptic to get network-manager-gnome and wpasupplicant according to this thread - (I didn't do anything else because it sounded like WPA was supported by using wpasupplicant)

[http://www.ubuntuforums.org/showthread.php?t=125150&highlight=3945](http://www.ubuntuforums.org/showthread.php?t=125150&highlight=3945)

So connecting should now be easy, but I can't figure it out. Am I supposed to have a different network manager now? Because I can't find one except at system/administration/networking. When I open that there is only a box for a WEP key when trying to configure my work connection.

What am I missing / doing wrong?

Also the internet is considerably slower to load pages compared to my old Windows laptop. It seems to pause for about 20 seconds then once a page starts loading it loads as fast as the windows laptop. Same firefox extensions, same wireless connection (at home). Anyone have any ideas?

Thanks for the help.

---

### Post by jblake on 2006-09-13
Hi there,
I am a relative newbie to the wireless thing. I was hoping that my modem/firewall/router would work just fine in Linux - the router does but not the dongle attached to a usb port on a family members PC. Apparently, no USB Wi-fi is currently supported. You must make sure that you are using pcmcia wi-fi cards for Laptops and PCI wifi cards in Desktops.  The other problem having browsed various linux websites is that there is a requirement for the cards to have the Atheros chipset present. This might not be known until you have bought the card from the shop and found out in hardware information that it is not! (Anybody out there correct me if I am wrong!). A place to start might be to visit the unofficial site for Wifi which 
I believe is Madwifi. Try this link - madwifi.org/wiki/Compatibility.
Hope this helps!\\:D/

---

### Post by neum on 2006-09-15
I finally got it to work. I saw a post somewhere about how if you install KDE before network manager, then network manager will not work. I guess I selected a KDE app and it installed KDE as a dependency? I'm still trying to figure out the whole KDE Gnome thing.

I just did a complete fresh reinstall and then used synaptic manager to install network manager. It works like a champ. 

Thanks for the help.

---

### Post by puma1824 on 2006-09-24
> **neum said:**
> I finally got it to work. I saw a post somewhere about how if you install KDE before network manager, then network manager will not work. I guess I selected a KDE app and it installed KDE as a dependency? I'm still trying to figure out the whole KDE Gnome thing.

I just did a complete fresh reinstall and then used synaptic manager to install network manager. It works like a champ. 

Thanks for the help.


I can't seem to get it working...new install of Ubuntu then ran updates, wpasupplicant was already installed, installed network-manager-gnome and nothing....

Please help.

Thanks,
Puma

---

### Post by neum on 2006-10-18
It no longer works for me. I broke my X server somehow and so when I restarted the screen was black. So I figured I could just reinstall and go thru the steps I had previously to get it to work. I can no longer get network manager to recognize my wireless card. It's just like the problem I had before. ](*,) 

If I have that working and Aptana the switch to Linux is complete for me. But I've been trying different things for days and nothing seems to work.

Does anyone have any ideas where I should start?

---

