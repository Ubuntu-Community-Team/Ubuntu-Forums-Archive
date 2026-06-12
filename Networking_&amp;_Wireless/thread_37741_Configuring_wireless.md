---
title: "Configuring wireless"
date: 2005-05-28
forum: Networking &amp; Wireless
---

### Post by lrm on 2005-05-28
I'm new to linux...

Just installed Ubuntu on my laptop, networking was not configured during installation because it wasn't connected to network.  I've got two netgear network cards in the laptop, a wireless and a wired one.  

Looking at the Device Manager, I see "RTL8180L 802.11b MAC", which must be the wireless card.  I don't see the wired card.

Looking at the Connections tab of Network Settings, I see "Ethernet Connection: The interface eth0 is not configured".  Is it safe to assume that eth0 is my wireless card?  Is configuration as simple as checking "This device is configured" and selecting DHCP?

I'm confused because my "Connections" tab does not look like the one in the Help files.  THere is no "Add" button for creating a new connection, which would allow me to specify ESSID, etc.

I'm guessing the wireless card is not as ready out of the box as I thought it might be...Any advice on how to get it working?

Thanks!

---

### Post by thrift on 2005-05-28
If you go to the command line and enter the command:
dmesg > dmesg.txt

and then attach the file dmesg.txt in your home directory, people will be able to try to help quite a bit more.

Do you know what model of wireless card you are using?  Just knowing netgear is not enough.  If not as well you should enter this command on the command line lspci > lspci.txt and attach that.

Wireless cards in Linux can be a bumpy ride.  If yours is well supported on the other hand this might be quite simple.  Figuring out the type of support this card has in Linux is the first step.  Running those commands and attaching their output will help others find out this information.

I think it is pretty safe to say that if you are only seeing an eth0 and not an eth0 and eth1, your wireless card has probably not been properly detected by Ubuntu.

---

### Post by jalingo on 2005-05-28
I am having the same problem with a Realtek based wireless card in my laptop. See:

[http://ubuntuforums.org/showthread.php?t=37003](http://ubuntuforums.org/showthread.php?t=37003) 

I'm a linux newbie too so this may help. I configured the driver with the ndiswrapper and Ubuntu sees it but on my laptop it doesn't give me the option of using it as an eth0 in the Networking panel. So,....I switched cards with my wife's laptop - a 2wire (really a D-Link?) card and wham there it is in the Networking panel. I got the same greyed out options as you did though and it saying it's not configured. Well I put a check box in the configured box and configured it. Put the SSID name in there and the WEP key and selected DHCP. And guess what happened? A few seconds later I'm typing this message. Wireless! Finally.

Can you even enter a check any options? Did you read the Wireless config help area in the Wiki section? 

I guess you get what you pay for or don't do research first. My GigaFast card was $14 on a clearance shelf - maybe I should of spent more and avoided the headaches.

Good luck.

---

### Post by thrift on 2005-05-29
You certainly do get what you pay for.  The thing that's not great about ndiswrapper is you can't use WEP.  Not that WEP is great anyway, but you know.

I'd recommend anything with an Orinoco chipset.  They are not cheap but they work flawlessly.

---

