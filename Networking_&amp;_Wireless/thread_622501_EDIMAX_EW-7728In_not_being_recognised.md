---
title: "EDIMAX EW-7728In not being recognised"
date: 2007-11-24
forum: Networking &amp; Wireless
---

### Post by Elusid on 2007-11-24
So I have Ubuntu 7.04 installed on one of my hard drives in my computer (dual boot vista/ubuntu) but I have a problem... Ubuntu isn't seeing that I have a wireless card installed at all. Well I can go into the hardware manager and it sees that there is a PCI card there... What do I need to do to get my wifi card working?

In other words:
I have a EW-7728In from EDIMAX and Ubuntu (Festy Fawn). What do I need to download and do to get my wifi card working? 

Thanks for the help.

---

### Post by Elusid on 2007-11-24
Ok so I started to do the whole NDISwrapper by using the Ubuntu wiki instructions. So I installed the packages fine and found the chipset ID 1814:0601 but when I go to the NDISwrapper wiki [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/) to look for the driver package for my chipset I can't find it... anywhere... I went to each section and searched for it and nothing... There are other EDIMAX chipsets on there but not mine... 

So what now... how am I going to get my wireless card to work?

---

### Post by Elusid on 2007-11-25
*bump* please, I want Ubuntu working correctly...

---

### Post by IamAcoconut on 2007-11-26
- Do you have windows drivers for the card itself? Like on a CD?

- Can you post output of...
```
lshw -C network
```?
(the part reffering to your wireless card)

---

### Post by Elusid on 2007-11-27
Alright I did what you said and this is what i got.

```




WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8052 PCI-E ASF Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 20
       serial: 00:01:29:d8:09:e2
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.18 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 22
       serial: 00:01:29:d8:09:ce
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.18 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: RaLink
       vendor: RaLink
       physical id: 7
       bus info: pci@0000:06:07.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=64 maxlatency=4 mingnt=2

```

the last section is what goes with my wifi card.

---

### Post by IamAcoconut on 2007-11-27
What about my first question from previous post. No windows drivers came with your card?
Anyway, **here they are:**
[http://www.edimax.com/en/support_detail.php?pl1_id=1&pl1_idSelect=support.php%3Fpl1_id%3D1%26mwsp%3D1&pd_id=225](http://www.edimax.com/en/support_detail.php?pl1_id=1&pl1_idSelect=support.php%3Fpl1_id%3D1%26mwsp%3D1&pd_id=225)

```
ndiswrapper -h
```
And install the unzipped windows driver. Then...
```
lsmod |grep ndiswrapper
```
If you see a ndiswrapper module, then:
```
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
``` 
If there wasn't a ndiswrapper module present you'll have to add it to **/etc/modules** later, and now just type
```
sudo modprobe ndiswrapper
```
Now again do ```
lshw -C network
```
There should now be an entry called 'driver=ndiswrapper' in your wifi card section.

---

### Post by Elusid on 2007-11-27
Well I've been to the site before to get the drivers but they come as a zipped EXE. What am I supposed to do with that? From reading on the ndiswrapper wiki I need to do something with .bin files. Would I need to access the drivers that are installed on my Vista partition? Would the vista drivers even work with ndiswrapper?

---

### Post by IamAcoconut on 2007-11-28
What if you run them with wine? Won't it create an **.inf** file in your wine directory?

---

### Post by Elusid on 2007-11-28
Well in order to go that Iwouldn't I need to connect Ubuntu to the internet in order to install Wine? I mean I guess I could hall my computer upstairs and hard wire it to the router but I would prefer not... thing weighs like 75lbs haha. Well would the vista drivers work because I could just copy those files over to a thumb drive so that I can put them on linux when I boot into that. I just don't know what files I WOULD need to copy...

---

### Post by Elusid on 2007-12-02
*bump* please... I have no idea on how to do this.

---

### Post by IamAcoconut on 2007-12-04
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)
Get it on a CD, then.
```
dpkg -i <path to .deb file on the cd>
```
Sorry if I kept you waiting.

BTW, I wanted to buy an Edimax card some time ago, but found myself unable to compile the linux driver they provided on their site, so I gave up on their products for now.

---

### Post by sfaaikido on 2007-12-15
If you're still having issues, I have the same wireless card. Mine is based on the RALink RT2860 chip. There is a native Linux driver available for that chip. Works perfectly for me.

[http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)

Assuming your card uses the same chip (as far as I know, they all do), you want the RT2860PCI driver. 

When I was looking around for solutions I remember reading something about the driver being added to a future kernel. Can't find the info now (of course) so I have no idea if and when that is going to happen.

---

### Post by Elusid on 2007-12-18
Alright so I downloaded the drivers and put them on my desktop folder in ubuntu now how do I compile the driver and install it? Currently the file is located in /home/chris/Desktop/ and I named it wlan_driver.tar.bz2 but where do I go from here? I'm currently running Ubuntu 7.10 by the way if that helps.

---

### Post by IamAcoconut on 2007-12-19
> **Elusid said:**
> Alright so I downloaded the drivers and put them on my desktop folder in ubuntu now how do I compile the driver and install it? Currently the file is located in /home/chris/Desktop/ and I named it wlan_driver.tar.bz2 but where do I go from here? I'm currently running Ubuntu 7.10 by the way if that helps.

Right-click -> Unpack.
```
cd /home/chris/Desktop/driver
```
Read the readme file or anything that explains the installation proccess.

And also read:
[http://ubuntuforums.org/showthread.php?t=638871&highlight=compile](http://ubuntuforums.org/showthread.php?t=638871&highlight=compile)

The search engine on this forum is realy very friendly :)

---

### Post by Elusid on 2007-12-21
> **IamAcoconut said:**
> Right-click -> Unpack.
```
cd /home/chris/Desktop/driver
```
Read the readme file or anything that explains the installation proccess.

And also read:
[http://ubuntuforums.org/showthread.php?t=638871&highlight=compile](http://ubuntuforums.org/showthread.php?t=638871&highlight=compile)

The search engine on this forum is realy very friendly :)

Hm... ok lost again. So I assume that I'm following this code

```

sudo mkdir ~/src/program_name 
cd ~/src/program_name
tar xvfz ~/Desktop/program_name.tar.gz
./configure
make
make install
make clean

```

Ok so I created a directory ~/src and then I created a directory ~/src/wlan_driver because I had to do that first. So then I go to the folder with 

```

cd ~/src/wlan_driver

```
but the next part is where I get lost. What do I put in? Doing

```

tar xvfz ~/Desktop/wlan_driver.tar.gz

```

doesn't make sense because it's not a .tar.gz package... I tried just moving the contents of the folder on the desktop into the created directory and then running ./configure but that didn't work and when I just tried to make it as is and then run make install that didn't work either so I'm totally lost...

---

### Post by IamAcoconut on 2007-12-23
Why didn't you use the "right-click -> **unpack here**"? The simplest way. 
Or double-click it and... you'll see.
Ubuntu doesn't  require you to know how to manually unpack particular archive types.

Then:
```
cd ~/Desktop/2007_1109_RT2860_Linux_STA_v1.4.0.0 ## OR wherever you downloaded and unpacked this file
sudo make
sudo make install

```

If you run into trouble read this:
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

