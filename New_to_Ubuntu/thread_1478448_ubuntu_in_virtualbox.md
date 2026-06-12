---
title: "ubuntu in virtualbox"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by harDRain on 2010-05-09
I am new to Linux.  To try it out I installed it in virtualbox as the main os.  Is there any way I can access files (especially my air card to go online) from my windows xp files?  Any help with this would be appreciated.  Thanks

---

### Post by linuxman94 on 2010-05-09
You should be able to share the network connection by changing the settings to share the network.  As for file sharing, I think you have to have virtual machine additions installed.

---

### Post by Aurora@FleetBuzz on 2010-05-09
harDRain, unclear as to what you are saying.  Are you stating that you installed Ubuntu in Virtualbox on an XP host and you want to access the files on your XP system?

---

### Post by harDRain on 2010-05-09
> **Aurora@FleetBuzz said:**
> harDRain, unclear as to what you are saying.  Are you stating that you installed Ubuntu in Virtualbox on an XP host and you want to access the files on your XP system?


Yes that is exactly what I mean.  I'm not sure if I have to do something with windows to network with the virtualbox, or if it is all done through the virtualbox.  I can't at this time get online because we connect with an air card that is installed in xp.  Do I have to install the software to run the air card in Ubuntu or is there some way to network it through the virtualbox to the file in xp?

---

### Post by scrooge_74 on 2010-05-09
Virtualbox can handle network conections (at list when linux is the host). Try giving your linux guest to use NAT for the network. Don't know if you need to do anything on the XP.

The other way around I know is easy when using a linux host for a windows guest

---

### Post by harDRain on 2010-05-09
> **scrooge_74 said:**
> Virtualbox can handle network conections (at list when linux is the host). Try giving your linux guest to use NAT for the network. Don't know if you need to do anything on the XP.

The other way around I know is easy when using a linux host for a windows guest

I know just enough to make me dangerous.  I would love it if someone could walk me through the process of networking xp and virtualbox.  Thanks

---

### Post by Sealbhach on 2010-05-09
Try selecting the [Host Interface]("http://www.ubuntugeek.com/host-interface-networking-made-easy-in-virtualbox-210.html").

Here's a [simple guide ]("http://www.giannistsakiris.com/index.php/2008/04/09/virtualbox-access-windows-host-shared-folders-from-ubuntu-guest/")on using shared folders from an Ubuntu guest.

.

---

### Post by 3rdalbum on 2010-05-09
When you use Virtualbox, the guest OS does not directly access the hardware. So in order to do networking, the virtual machine presents an "ethernet port" to the guest. The virtual Ethernet port just piggybacks off your host OSes internet connection (which in your case is the wireless card).

This should all be set up for you; just use the Ethernet port in the Ubuntu network manager. Maybe it might require you to tick a box in the virtual machine settings.

Virtualbox presents virtual hardware to Ubuntu, not hardware directly - so don't try to install hardware drivers. This is also why you can't get desktop effects in a virtual machine.

---

### Post by harDRain on 2010-05-13
Thank you for the help.  I was able to get into the files through network connections, but am still having trouble getting the printer to work and the aircard for internet connection.  I've seen some other posts on this and will try it out.  Thanks again.

---

