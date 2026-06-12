---
title: "wireless over crossover?"
date: 2005-07-15
forum: Networking &amp; Wireless
---

### Post by besouza on 2005-07-15
I'd like to share my wireless windows machine's internet over a crossover cable to my ubuntu machine. How can I do this? :???:

---

### Post by gruepig on 2005-07-15
That's really a Windows problem. Set up Windows to share your connection. I have no idea how to do this, but I'm assuming it's possible. Then attach the computers with the crossover cables, and it should work.  For debugging, you'll want to look at the output of 'ifconfig -a' and 'route -n' on your Ubuntu system and 'ipconfig /all' on your Windows box.  You may need to manually bring up your ethernet interface in Ubuntu; for example, if your ethernet card is eth0, run 'ifdown eth0' to make sure it's down then 'ifup eth0' to bring it up.  Good luck!

---

### Post by evilghost on 2005-07-15
What you're asking is pretty ugly, because you're end up in a dual-NAT situation, and it would be much easier to purchase a PCI or USB (PCMCIA if applicable) WiFi card, however, if you're head-set on using an X-Over cable you have to enable ICS (Internet Connection Sharing) on your Windows box.  This then enables DHCP and the Windows box assumes the IPAddr of 192.168.1.1.  It will then route traffic accordingly and your Ubuntu box should pick up the DHCP address.

Basically, on the Windows machine you expand/enumerate your Network devices, click properties, click "Advanced" and there is an option to "Share this connection with other computers" or similiar.  I'm making the assumption you are Windows XP.  I don't know if Windows 98 supports ICS.

---

### Post by besouza on 2005-07-17
I do have a wireless card, but ubuntu doesn't recognize it. It's a Linxsys WUSB11 usb wifi adapter. I've tried to get it to work, however the fact that I don't know what to do when it comes to linux I couldn't get it to work. I'd just like to set this box up so that I can learn how to use linux but it seems that you have to have some sort of internet connection to find out how to use it. I've tried everything that you guys have said in this but it still won't work. The ubuntu box can see my windows xp (yes it's xp) box but the windows box can't see the ubuntu box, still can't get on the internet. Me=very frustrated... ](*,)

---

