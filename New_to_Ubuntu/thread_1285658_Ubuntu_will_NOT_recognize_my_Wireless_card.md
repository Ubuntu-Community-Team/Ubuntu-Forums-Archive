---
title: "Ubuntu will NOT recognize my Wireless card"
date: 2009-10-08
forum: New to Ubuntu
---

### Post by Amockineuropa on 2009-10-08
OK I am new to Ubuntu but I have a problem. Ubuntu will not recignize my wireless card and it is not listed on ndiswrapper. I even tried to hard wire it to the internet but still no go. My Windows Vista works just fine but not my Ubuntu. So what now?

---

### Post by cariboo on 2009-10-08
In order for us to help you solve your problem we need more info. Could you open an Applications-->Accessoriues-->Termianl and type the following command:

```
lspci > lspci.txt
```

The above command will create a text file with a listing of your pci devices. Next in the same terminal type:

```
sudo lshw -C network
```

You will be asked for the password you created when you installed Ubuntu, it will not be echoed back to you. The second command will create a text file with a listing of your network devices and tell us if they are detected and a driver loaded.

Copy the text files to your Windows partition and paste then in your next post.

Please enclosed the pasted text with [noparse]```

```[/noparse] tags.

---

### Post by Amockineuropa on 2009-10-08
I can try

---

### Post by Amockineuropa on 2009-10-08
I ran the code and got the data just not sure HOW to save it to Windows?

---

### Post by RichardLinx on 2009-10-08
> **Amockineuropa said:**
> I ran the code and got the data just not sure HOW to save it to Windows?

Just copy and paste the text that comes up in the terminal after you issue the commands into this thread.

Edit: My badm cariboo907 asked you to copy the text to your windows partition.

---

### Post by Amockineuropa on 2009-10-08
Actually I am not sure HOW to save it. It is not like Windows where I can right click to save then paste. I am lost!

---

### Post by Amockineuropa on 2009-10-08
I am working off 2 different computers right now. My linux will not go online so I am using my other PC. I tried to copy/paste to usb stick but that was a no go. I am in over my head. I guess I should stick with Windows!

---

### Post by ackley on 2009-10-08
OH, I finally get it. You need to get it over to Windows so you can post it here.

You should be able to see your windows partition if you click your places button next to the main menu. You should also be able to write to it. Just save it in a text editor & then either save it to Ubuntu then copy to your ntfs partition, or just save it straight to your ntfs partition.

---

### Post by Amockineuropa on 2009-10-08
rollingstone@ubuntu:~$ sudo lshw -C network 
*-network UNCLAIMED 
description: Network controller 
product: AR9285 Wireless Network Adapter (PCI-Express) 
vendor: Atheros Communications Inc. 
physical id: 0 
bus info: pci@0000:02:00.0 
version: 01 
width: 64 bits 
clock: 33MHz 
capabilities: pm msi pciexpress bus_master cap_list 
configuration: latency=0 
*-network UNCLAIMED 
description: Ethernet controller 
product: Attansic Technology Corp. 
vendor: Attansic Technology Corp. 
physical id: 0 
bus info: pci@0000:08:00.0 
version: c0 
width: 64 bits 
clock: 33MHz 
capabilities: pm msi pciexpress vpd bus_master cap_list 
configuration: latency=0 
*-network DISABLED 
description: Ethernet interface 
physical id: 1 
logical name: pan0 
serial: 76:2a:72:66:ca:b4 
capabilities: ethernet physical 
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes 
rollingstone@ubuntu:~$ 

I figured out how yo do it. So any suggestion?

---

### Post by Amockineuropa on 2009-10-08
Please see below for requested data
 
 
rollingstone@ubuntu:~$ sudo lshw -C network 
*-network UNCLAIMED 
description: Network controller 
product: AR9285 Wireless Network Adapter (PCI-Express) 
vendor: Atheros Communications Inc. 
physical id: 0 
bus info: pci@0000:02:00.0 
version: 01 
width: 64 bits 
clock: 33MHz 
capabilities: pm msi pciexpress bus_master cap_list 
configuration: latency=0 
*-network UNCLAIMED 
description: Ethernet controller 
product: Attansic Technology Corp. 
vendor: Attansic Technology Corp. 
physical id: 0 
bus info: pci@0000:08:00.0 
version: c0 
width: 64 bits 
clock: 33MHz 
capabilities: pm msi pciexpress vpd bus_master cap_list 
configuration: latency=0 
*-network DISABLED 
description: Ethernet interface 
physical id: 1 
logical name: pan0 
serial: 76:2a:72:66:ca:b4 
capabilities: ethernet physical 
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

