---
title: "Belkin desktop g pci card problem"
date: 2006-11-30
forum: Networking &amp; Wireless
---

### Post by deadspeak on 2006-11-30
Now i've got my ndis wrapper installed and the driver installed it registers that i have the hardware installed, i also have the network manager applet installed, when i first look at the network managet it registered the card as a wired network, but after a restart it now does'nt see it at all, i've been hunting on forums but can't seem to find the sloution. i've tried some of the networking utilities like iwconfig but that gives me the message...
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.412 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:"deadspeak g"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          
sit0      no wireless extensions.

i also tried iwlist wlan0 scan

but that returned 
wlan0     No scan results

i've even left my g network completly open but still no luck.

Please someone HELP!!!!!

Thanks

---

### Post by poshmoggy on 2006-12-01
I think you should look at the following link. 

[http://ubuntuforums.org/showthread.php?t=296822]("http://ubuntuforums.org/showthread.php?t=296822")

It appears from what you have said that you have a card with a RT61 chipset and that you need to follow the set up information contained in it. I have a Belkin Wireless G card, and this solution worked perfectly for me. It seems that the RT61PCI driver that ships with Edgy has a bug which causes the WLan0 and WMaster0 split you are seeing. The solution replaces this with a driver from the Ralink website (they make the chipset).

Also, you should maybe look at the following thread which contains valuable info on the subject...

[http://ubuntuforums.org/showthread.php?t=132980]("http://ubuntuforums.org/showthread.php?t=132980")

Hope this helps.

---

### Post by deadspeak on 2006-12-01
got most of the way through but i'm having trouble editing the file, and what readme file does it refer to???

---

