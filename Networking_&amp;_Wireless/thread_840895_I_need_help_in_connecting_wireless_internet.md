---
title: "I need help in connecting wireless internet"
date: 2008-06-25
forum: Networking &amp; Wireless
---

### Post by rwar_baby on 2008-06-25
So I just got Ubuntu today and everything seems to be working fine, but I cant connect to the internet. I have an HP dv6000 with a BCM4328 card. I tried looking at the other tutorials but they don't seem to help me. Any ideas?

---

### Post by lisati on 2008-06-25
Please post the output from the following commands:
```
iwconfig
``````
ifconfig
``````
iwslist scan
```This will help other forum members know what your system recognizes in the way of connections.

(You can enter the commands by going to Applications->Accessories->Terminal)

---

### Post by rwar_baby on 2008-06-25
so this is what I got...

iwconfig
```

lo     no wireless extensions
eth0   no wireless extensions
```

ifconfig
```

eth0     Link encap:Ethernet  HW 00:1b:24:b0:1f:b2
         UP BROADCAST MULTICAST MTU:1500 Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:0 errors:0 dropped:0 overruns:0 frame:0
         collisions:0 txqueuelen:1000
         RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
         Interupt:220 Base adress:0x2000

eth0:avahi Link encap:Ethernet  HWaddr 00:1b:24:b0:1f:b2
          inet addr:169.254.6.106 Bcast:169.254.255.255 Mask:255.255.0.0
          UP BROADCAST MULTICAST MTU:1500 Metric:1
          Interrupt:220 Base address:0x2000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING MTU:1500 Metric:1
          RX packets:194 errors:0 dropped:0 overruns:0 frame:0
          TX packets:194 errors:0 dropped:0 overruns:0 frame:0
          collisions:0 txqueuelen:0
          RX bytes:10084 (9.8 KB) TX bytes:10084 (9.8 KB)

```

iwslist scan
```

bash: iwslist:command not found
```

---

### Post by hussainbtk on 2008-06-25
Please help, i have also the same problem...

---

### Post by cdtech on 2008-06-25
Actually this is what you need:
lshw -C network

Also be sure you have the "Proprietary drivers" and the "Software restricted" selected in the System > Admin > Software Sources. Then do the "update" thing.

---

### Post by UbuntuNerd on 2008-06-25
found this somewhere hope it works!!!
 
Model of  wifi card is &#8220;Broadcom BCM4328 802.11a/b/g/n (rev 01)&#8221;



Steps

1. Install Ndiswrapper Common and Ndiswrapper Utils (You can do it using synaptic)
2. Download The Driver from [ftp://ftp.dell.com/network/R151517.EXE](ftp://ftp.dell.com/network/R151517.EXE) and unzip it somewhere. You will see a folder named DRIVER
3. Execute the following commands


sudo ndiswrapper -i /download_directory/DRIVER/bcmwl5.inf
sudo ndiswrapper -l
sudo modprobe ndiswrapper

4. Then, set ndiswrapper to load on startup:

sudo ndiswrapper -m
gksudo gedit /etc/modules

and add the following module to the list


ndiswrapper

5. Restart (This is a must)

Now you can use Fn+F2 to turn on your wifi :D )

---

### Post by rwar_baby on 2008-06-25
> **cdtech said:**
> Actually this is what you need:
lshw -C network

Also be sure you have the "Proprietary drivers" and the "Software restricted" selected in the System > Admin > Software Sources. Then do the "update" thing.


ok... how do you update? and 

lshw -C network
```

WARNING: you should run this program as super-user.
  *-network
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1b:24:b0:1f:b2
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 64 bits
       clocks: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0

```

---

### Post by Ayuthia on 2008-06-25
> **rwar_baby said:**
> ok... how do you update? and 

lshw -C network
```

WARNING: you should run this program as super-user.
  *-network
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1b:24:b0:1f:b2
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 64 bits
       clocks: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0

```

The 4328 card is currently not supported by the b43 drivers (done by activating the proprietary drivers) because it has the wireless-n feature.  You will have to go the NDISwrapper route.  You can try the steps in jperez78's post and come back if you have problems.

---

### Post by lisati on 2008-06-26
> **rwar_baby said:**
> iwslist scan
```

bash: iwslist:command not found
```

My bad - it was a typo, should have been ```
iwlist scan
```

Anyhow, it looks like other forum members have jumped in with some useful suggestions.

p.s. Sorry about the delay responding, I was researching some stuff not directly related to Ubuntu/Linux

---

### Post by cdtech on 2008-06-26
Here's a good how-to:
[[COLOR="DarkRed"]BCM4328[/COLOR]]("http://www.micahcarrick.com/11-04-2007/ubuntu-d830-install-notes.html#4")

This is for your Broadcom.

Hope this helps........

---

### Post by rwar_baby on 2008-06-26
> **jperez78 said:**
> found this somewhere hope it works!!!
 
Model of  wifi card is “Broadcom BCM4328 802.11a/b/g/n (rev 01)”



Steps

1. Install Ndiswrapper Common and Ndiswrapper Utils (You can do it using synaptic)
2. Download The Driver from [ftp://ftp.dell.com/network/R151517.EXE](ftp://ftp.dell.com/network/R151517.EXE) and unzip it somewhere. You will see a folder named DRIVER
3. Execute the following commands


sudo ndiswrapper -i /download_directory/DRIVER/bcmwl5.inf
sudo ndiswrapper -l
sudo modprobe ndiswrapper

4. Then, set ndiswrapper to load on startup:

sudo ndiswrapper -m
gksudo gedit /etc/modules

and add the following module to the list


ndiswrapper

5. Restart (This is a must)

Now you can use Fn+F2 to turn on your wifi :D )

I tried to install it, but it did not show up in Synaptic

---

### Post by Ayuthia on 2008-06-26
> **rwar_baby said:**
> I tried to install it, but it did not show up in Synaptic

The actual package that you should be looking for is ndiswrapper-utils-1.9.

---

### Post by rwar_baby on 2008-06-26
> **Ayuthia said:**
> The actual package that you should be looking for is ndiswrapper-utils-1.9.

its not there... =(

---

### Post by cdtech on 2008-06-26
Did you see the How-to I posted, it's tells you how to install the proper version of the ndiswrapper.

---

### Post by rwar_baby on 2008-06-26
> **lisati said:**
> My bad - it was a typo, should have been ```
iwlist scan
```

Anyhow, it looks like other forum members have jumped in with some useful suggestions.

p.s. Sorry about the delay responding, I was researching some stuff not directly related to Ubuntu/Linux

hm... well i did that.

```

lo     Interface doesn't support scanning

eth0   Interface doesn't support scanning

```

---

### Post by Ayuthia on 2008-06-26
> **rwar_baby said:**
> its not there... =(

Do you have the Hardy install CD?  If so, try the following:
```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install ndiswrapper-utils-1.9
```
You will need to run those commands in the Terminal.  These steps load the CD repository information into Ubuntu and then install ndiswrapper from your CD.  The first command will ask you to insert your install CD.

You should be able to do this in Synaptic also.  There should be an item in the menu bar options to manage repositories.  You will then need to find the section for adding the CD (might be under third party sources).  I am not too familiar with Synaptic though because I am a Kubuntu user and it has Adept instead of Synaptic.

---

### Post by rwar_baby on 2008-06-26
> 
4. Then, set ndiswrapper to load on startup:

sudo ndiswrapper -m
gksudo gedit /etc/modules

and add the following module to the list


ndiswrapper



Ok... so how do i add that? I tried to save it and it wouldn't save.

---

### Post by Ayuthia on 2008-06-26
> **rwar_baby said:**
> Ok... so how do i add that? I tried to save it and it wouldn't save.

Try this instead from the Terminal:
```
echo ndiswrapper|sudo tee -a /etc/modules
```
It does the same thing, but you don't have to edit the file because it does it for you.

---

### Post by rwar_baby on 2008-06-26
> **Ayuthia said:**
> Try this instead from the Terminal:
```
echo ndiswrapper|sudo tee -a /etc/modules
```
It does the same thing, but you don't have to edit the file because it does it for you.

k so i did that
 ```

ndiswrapper

```

what else?

---

### Post by CarbineReloaded on 2008-07-16
> **cdtech said:**
> Here's a good how-to:
[[COLOR="DarkRed"]BCM4328[/COLOR]]("http://www.micahcarrick.com/11-04-2007/ubuntu-d830-install-notes.html#4")

This is for your Broadcom.

Hope this helps........


I have a DV9700 with the problem of no wifi as well... BCM4328.

I just installed the newest download of ubuntu, and tried your suggestion... unfortunately I'm getting "sudo: ndiswrapper: command not found"


Any suggestions?

---

