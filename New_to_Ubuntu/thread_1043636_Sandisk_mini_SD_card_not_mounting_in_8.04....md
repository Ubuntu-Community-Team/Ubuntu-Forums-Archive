---
title: "Sandisk mini SD card not mounting in 8.04..."
date: 2009-01-18
forum: New to Ubuntu
---

### Post by Adamantus on 2009-01-18
I have an HP dv5 running Hardy Heron. I just recently got a Palm Centro and bought a 2 GB SD card. It came with an SD adapter so you can insert it into a computer, and the first time I did, it worked fine. But, when I put it back into my phone, it asked me to format it, which I did, and it stopped working. So I got a new one. Now, when I put the new one into my computer, my card reader doesn't even read it. The white light flashed 4 four times like it's trying but nothing happens. It works fine in my phone. What's the problem? Is there any way to get my computer reading it again?

---

### Post by adam_kimber on 2009-01-18
At a glance it looks like the original filesytem on the disk was compatible with Linux and the new one isn't. This however does not really make make sense as most SD cards are formatted with [FAT32]("http://en.wikipedia.org/wiki/File_Allocation_Table") or sometimes more rarely [NTFS]("http://en.wikipedia.org/wiki/NTFS"), both of which are pretty much fully supported by Linux and Ubuntu. 

So we come to other things that might be causing the problem. It might be mounting but not bringing up any indication that it has. It might be partially mounting. Or not at all. The first port of call for diagnosing these problems is the "System Log" which can be accessed from System --> Administration. You are looking for the section called messages. 

Open that up and note the time index. Then plug in the USB device and there should be a bunch of "messages". Can you post those here...

---

### Post by Adamantus on 2009-01-18
Craziest thing ever...I've been taking out and putting in the SD card for nearly an hour, and now I put it in with System Log opened and it was recognized. Here's some of the text from the System Log though. I'm not too sure if this is still a problem, but it might get annoying if it only opens up every 1/100 times. There were hundreds of lines, but I'll only put the most recent, just so I don't overwhelm you. Thanks.

Jan 18 18:19:19 aj-laptop kernel: [   59.060370] sd 8:0:0:0: [sdb] Add. Sense: No additional sense information
Jan 18 18:19:19 aj-laptop kernel: [   59.109651] sd 8:0:0:0: [sdb] Sense Key : No Sense [current] 
Jan 18 18:19:19 aj-laptop kernel: [   59.109684] sd 8:0:0:0: [sdb] Add. Sense: No additional sense information
Jan 18 18:19:19 aj-laptop kernel: [   59.159073] sd 8:0:0:0: [sdb] Sense Key : No Sense [current] 
Jan 18 18:19:19 aj-laptop kernel: [   59.159103] sd 8:0:0:0: [sdb] Add. Sense: No additional sense information
Jan 18 18:19:19 aj-laptop kernel: [   59.208499] sd 8:0:0:0: [sdb] Sense Key : No Sense [current] 
Jan 18 18:19:19 aj-laptop kernel: [   59.208532] sd 8:0:0:0: [sdb] Add. Sense: No additional sense information
Jan 18 18:19:19 aj-laptop kernel: [   59.463283] NET: Registered protocol family 10
Jan 18 18:19:19 aj-laptop kernel: [   59.464833] lo: Disabled Privacy Extensions
Jan 18 18:19:19 aj-laptop kernel: [   59.467165] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan 18 18:19:30 aj-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.reason
Jan 18 18:19:32 aj-laptop kernel: [   72.140902] NET: Registered protocol family 17
Jan 18 18:19:39 aj-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.host_name
Jan 18 18:19:39 aj-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.nis_domain
Jan 18 18:19:39 aj-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.nis_servers
Jan 18 18:19:39 aj-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.interface_mtu
Jan 18 18:19:42 aj-laptop kernel: [   81.843112] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
Jan 18 18:24:47 aj-laptop kernel: [  386.280431] sd 8:0:0:0: [sdb] 3862528 512-byte hardware sectors (1978 MB)
Jan 18 18:24:47 aj-laptop kernel: [  386.282436] sd 8:0:0:0: [sdb] Write Protect is off
Jan 18 18:24:47 aj-laptop kernel: [  386.284271] sd 8:0:0:0: [sdb] 3862528 512-byte hardware sectors (1978 MB)
Jan 18 18:24:47 aj-laptop kernel: [  386.285155] sd 8:0:0:0: [sdb] Write Protect is off
Jan 18 18:24:47 aj-laptop kernel: [  386.285169]  sdb: sdb1

---

### Post by adam_kimber on 2009-01-18
Right, this line is the last one currently in the list.

```
Jan 18 18:24:47 aj-laptop kernel: [ 386.285169] sdb: sdb1****
```

Remove the usb and plug it in again without the messages open. Then go back to the messages and post from the above line to the end. 

PS 
Messages contain all sorts of information from startup to programs not working through to mounting and unmounting of devices, such as printers, USB etc.

---

### Post by Adamantus on 2009-01-18
I tried putting it in a couple of times:

Jan 18 18:24:47 aj-laptop kernel: [  386.285169]  sdb: sdb1
Jan 18 18:38:57 aj-laptop -- MARK --
Jan 18 18:45:19 aj-laptop kernel: [ 1613.694778] sd 8:0:0:0: [sdb] 3862528 512-byte hardware sectors (1978 MB)
Jan 18 18:45:19 aj-laptop kernel: [ 1613.695898] sd 8:0:0:0: [sdb] Write Protect is off
Jan 18 18:45:19 aj-laptop kernel: [ 1613.696997] sd 8:0:0:0: [sdb] 3862528 512-byte hardware sectors (1978 MB)
Jan 18 18:45:19 aj-laptop kernel: [ 1613.697868] sd 8:0:0:0: [sdb] Write Protect is off
Jan 18 18:45:19 aj-laptop kernel: [ 1613.697903]  sdb:<6>sd 8:0:0:0: [sdb] Sense Key : No Sense [current] 
Jan 18 18:45:19 aj-laptop kernel: [ 1613.781556] sd 8:0:0:0: [sdb] Add. Sense: No additional sense information
Jan 18 18:45:19 aj-laptop kernel: [ 1613.830964] sd 8:0:0:0: [sdb] Sense Key : No Sense [current] 
Jan 18 18:45:19 aj-laptop kernel: [ 1613.830984] sd 8:0:0:0: [sdb] Add. Sense: No additional sense information
Jan 18 18:45:19 aj-laptop kernel: [ 1613.880518] sd 8:0:0:0: [sdb] Sense Key : No Sense [current] 
Jan 18 18:45:19 aj-laptop kernel: [ 1613.880538] sd 8:0:0:0: [sdb] Add. Sense: No additional sense information
Jan 18 18:45:19 aj-laptop kernel: [ 1613.959343] sd 8:0:0:0: [sdb] Sense Key : No Sense [current] 
Jan 18 18:45:19 aj-laptop kernel: [ 1613.959374] sd 8:0:0:0: [sdb] Add. Sense: No additional sense information
Jan 18 18:45:19 aj-laptop kernel: [ 1614.008881] sd 8:0:0:0: [sdb] Sense Key : No Sense [current] 
Jan 18 18:45:19 aj-laptop kernel: [ 1614.008901] sd 8:0:0:0: [sdb] Add. Sense: No additional sense information
Jan 18 18:45:20 aj-laptop kernel: [ 1614.058334] sd 8:0:0:0: [sdb] Sense Key : No Sense [current] 
Jan 18 18:45:20 aj-laptop kernel: [ 1614.058355] sd 8:0:0:0: [sdb] Add. Sense: No additional sense information
Jan 18 18:45:20 aj-laptop kernel: [ 1614.107753] sd 8:0:0:0: [sdb] Sense Key : No Sense [current] 
Jan 18 18:45:20 aj-laptop kernel: [ 1614.107773] sd 8:0:0:0: [sdb] Add. Sense: No additional sense information
Jan 18 18:45:20 aj-laptop kernel: [ 1614.157184] sd 8:0:0:0: [sdb] Sense Key : No Sense [current] 
Jan 18 18:45:20 aj-laptop kernel: [ 1614.157203] sd 8:0:0:0: [sdb] Add. Sense: No additional sense information
Jan 18 18:45:20 aj-laptop kernel: [ 1614.206487] sd 8:0:0:0: [sdb] Sense Key : No Sense [current] 
Jan 18 18:45:20 aj-laptop kernel: [ 1614.206507] sd 8:0:0:0: [sdb] Add. Sense: No additional sense information
Jan 18 18:45:20 aj-laptop kernel: [ 1614.255798] sd 8:0:0:0: [sdb] Sense Key : No Sense [current] 
Jan 18 18:45:20 aj-laptop kernel: [ 1614.255817] sd 8:0:0:0: [sdb] Add. Sense: No additional sense information
Jan 18 18:45:20 aj-laptop kernel: [ 1614.305352] sd 8:0:0:0: [sdb] Sense Key : No Sense [current] 
Jan 18 18:45:20 aj-laptop kernel: [ 1614.305371] sd 8:0:0:0: [sdb] Add. Sense: No additional sense information
Jan 18 18:45:20 aj-laptop kernel: [ 1614.354772] sd 8:0:0:0: [sdb] Sense Key : No Sense [current] 
Jan 18 18:45:20 aj-laptop kernel: [ 1614.354791] sd 8:0:0:0: [sdb] Add. Sense: No additional sense information
Jan 18 18:45:20 aj-laptop kernel: [ 1614.403954] sd 8:0:0:0: [sdb] Sense Key : No Sense [current] 
Jan 18 18:45:20 aj-laptop kernel: [ 1614.403974] sd 8:0:0:0: [sdb] Add. Sense: No additional sense information
Jan 18 18:45:20 aj-laptop kernel: [ 1614.453514] sd 8:0:0:0: [sdb] Sense Key : No Sense [current] 
Jan 18 18:45:20 aj-laptop kernel: [ 1614.453534] sd 8:0:0:0: [sdb] Add. Sense: No additional sense information
Jan 18 18:45:20 aj-laptop kernel: [ 1614.502937] sd 8:0:0:0: [sdb] Sense Key : No Sense [current] 
Jan 18 18:45:20 aj-laptop kernel: [ 1614.502957] sd 8:0:0:0: [sdb] Add. Sense: No additional sense information
Jan 18 18:45:53 aj-laptop kernel: [ 1647.560102] sd 8:0:0:0: [sdb] 3862528 512-byte hardware sectors (1978 MB)
Jan 18 18:45:53 aj-laptop kernel: [ 1647.561168] sd 8:0:0:0: [sdb] Write Protect is off
Jan 18 18:45:53 aj-laptop kernel: [ 1647.562195] sd 8:0:0:0: [sdb] 3862528 512-byte hardware sectors (1978 MB)
Jan 18 18:45:53 aj-laptop kernel: [ 1647.563065] sd 8:0:0:0: [sdb] Write Protect is off
Jan 18 18:45:53 aj-laptop kernel: [ 1647.563101]  sdb:<6>sd 8:0:0:0: [sdb] Sense Key : No Sense [current] 
Jan 18 18:45:53 aj-laptop kernel: [ 1647.647004] sd 8:0:0:0: [sdb] Add. Sense: No additional sense information
Jan 18 18:45:53 aj-laptop kernel: [ 1647.696418] sd 8:0:0:0: [sdb] Sense Key : No Sense [current] 
Jan 18 18:45:53 aj-laptop kernel: [ 1647.696438] sd 8:0:0:0: [sdb] Add. Sense: No additional sense information
Jan 18 18:45:53 aj-laptop kernel: [ 1647.745841] sd 8:0:0:0: [sdb] Sense Key : No Sense [current] 
Jan 18 18:45:53 aj-laptop kernel: [ 1647.745862] sd 8:0:0:0: [sdb] Add. Sense: No additional sense information
Jan 18 18:45:53 aj-laptop kernel: [ 1647.805120] sd 8:0:0:0: [sdb] Sense Key : No Sense [current] 
Jan 18 18:45:53 aj-laptop kernel: [ 1647.805150] sd 8:0:0:0: [sdb] Add. Sense: No additional sense information
Jan 18 18:45:53 aj-laptop kernel: [ 1647.854551] sd 8:0:0:0: [sdb] Sense Key : No Sense [current] 
Jan 18 18:45:53 aj-laptop kernel: [ 1647.854578] sd 8:0:0:0: [sdb] Add. Sense: No additional sense information
Jan 18 18:45:53 aj-laptop kernel: [ 1647.903972] sd 8:0:0:0: [sdb] Sense Key : No Sense [current] 
Jan 18 18:45:53 aj-laptop kernel: [ 1647.903994] sd 8:0:0:0: [sdb] Add. Sense: No additional sense information
Jan 18 18:45:54 aj-laptop kernel: [ 1647.953404] sd 8:0:0:0: [sdb] Sense Key : No Sense [current] 
Jan 18 18:45:54 aj-laptop kernel: [ 1647.953424] sd 8:0:0:0: [sdb] Add. Sense: No additional sense information
Jan 18 18:45:54 aj-laptop kernel: [ 1648.002708] sd 8:0:0:0: [sdb] Sense Key : No Sense [current] 
Jan 18 18:45:54 aj-laptop kernel: [ 1648.002729] sd 8:0:0:0: [sdb] Add. Sense: No additional sense information
Jan 18 18:45:54 aj-laptop kernel: [ 1648.052132] sd 8:0:0:0: [sdb] Sense Key : No Sense [current] 
Jan 18 18:45:54 aj-laptop kernel: [ 1648.052152] sd 8:0:0:0: [sdb] Add. Sense: No additional sense information
Jan 18 18:45:54 aj-laptop kernel: [ 1648.101568] sd 8:0:0:0: [sdb] Sense Key : No Sense [current] 
Jan 18 18:45:54 aj-laptop kernel: [ 1648.101588] sd 8:0:0:0: [sdb] Add. Sense: No additional sense information
Jan 18 18:45:54 aj-laptop kernel: [ 1648.150995] sd 8:0:0:0: [sdb] Sense Key : No Sense [current] 
Jan 18 18:45:54 aj-laptop kernel: [ 1648.151015] sd 8:0:0:0: [sdb] Add. Sense: No additional sense information
Jan 18 18:45:54 aj-laptop kernel: [ 1648.200296] sd 8:0:0:0: [sdb] Sense Key : No Sense [current] 
Jan 18 18:45:54 aj-laptop kernel: [ 1648.200317] sd 8:0:0:0: [sdb] Add. Sense: No additional sense information
Jan 18 18:45:54 aj-laptop kernel: [ 1648.249731] sd 8:0:0:0: [sdb] Sense Key : No Sense [current] 
Jan 18 18:45:54 aj-laptop kernel: [ 1648.249751] sd 8:0:0:0: [sdb] Add. Sense: No additional sense information
Jan 18 18:45:54 aj-laptop kernel: [ 1648.299039] sd 8:0:0:0: [sdb] Sense Key : No Sense [current] 
Jan 18 18:45:54 aj-laptop kernel: [ 1648.299060] sd 8:0:0:0: [sdb] Add. Sense: No additional sense information
Jan 18 18:45:54 aj-laptop kernel: [ 1648.348592] sd 8:0:0:0: [sdb] Sense Key : No Sense [current] 
Jan 18 18:45:54 aj-laptop kernel: [ 1648.348612] sd 8:0:0:0: [sdb] Add. Sense: No additional sense information

---

### Post by Adamantus on 2009-01-18
What works: I have to have the SD card out when I turn on system log, then put the card in the reader.

If I have the card in when I open the system log then take out and put back in the card, it doesn't work. If I don't have system log open at all, it doesn't work.

---

### Post by adam_kimber on 2009-01-19
OK. I am now confused. :P 

Lets try a couple of things. 

1) When you plug in the stick without the SD card (and without system log) does anything appear in the computer window ? (Places --> Computer) If so does it change when you insert the SD card. If not does it chaneg when you insert the SD card.

2) Insert the SD card and stick together (without system log) and monitor the Computer window again. 

I am attempting to see which of your devices might not be recognised properly. 

Jan 18 18:45:54 aj-laptop kernel: [ 1648.348592] sd 8:0:0:0: [sdb] Sense Key : No Sense [current]
Jan 18 18:45:54 aj-laptop kernel: [ 1648.348612] sd 8:0:0:0: [sdb] Add. Sense: No additional sense information

Not sure what these lines are doing. SOmetimes these are just notices and do not help other times they are very useful...........

---

### Post by adam_kimber on 2009-01-19
It appears the "sense" notices were a indicator. Other people seem to have problems with external USB hard drives and disks with these messages. Have a look at [this]("http://ubuntuforums.org/showthread.php?p=4480147"), [this]("https://bugs.launchpad.net/ubuntu/+source/udev/+bug/221983") (which happens to be a really really similar bug with Sony Ericsson phones namely the C902 and C502 - see my solution to that problem [here]("http://ubuntuforums.org/showpost.php?p=6513274&postcount=75")) and [this ]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/264789"). Bug 264789 has the most info. Try the first link first, then work along them! Be warned patching UDEV is not a recommended course of action as it might break other things. Though currently it seems to work for most people................... 

Hope they help!

---

