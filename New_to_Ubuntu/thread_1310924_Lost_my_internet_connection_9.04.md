---
title: "Lost my internet connection 9.04"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by aierlan on 2009-11-02
Hi, 

I've been using ubuntu 9.04 for a couple of months now.  Still getting used to the terminology! I had a wired internet connection working fine until recently.  The connection is coming directly from a router which I also have a wireless connection to my windows laptop.  
I seem to have lost my network manager too.  I had recently added a new printer but that didn't seem to interfere and internet and printer were working fine together for a few weeks so don't know if that has anything to do with it.  Any advice in very basic terms is much appreciated.

---

### Post by p_schott on 2009-11-02
I don't know if it can help, but I had the same problem this morning. Incoming ssh worked, but not internet. "apt-get update" and "wget" failed also. Restarting the network services ("sudo /etc/init.d/networking restart") worked for me, everything seems to be back now. I don't know what happenned, perharps related to the recent libsnmp update ([http://packages.ubuntu.com/search?keywords=libsnmp&searchon=names&suite=jaunty-updates&section=all]("http://packages.ubuntu.com/search?keywords=libsnmp&searchon=names&suite=jaunty-updates&section=all")).

---

### Post by aierlan on 2009-11-02
Hi 
Thanks for the reply, I tried that and it gave me the message "reconfiguring network interfaces ...     [OK]"

Unfortunately still no joy.  I used to have an icon in my task bar showing a network connection but it's no longer there too. 

Thanks

---

### Post by ukripper on 2009-11-02
> **aierlan said:**
> Hi 
Thanks for the reply, I tried that and it gave me the message "reconfiguring network interfaces ...     [OK]"

Unfortunately still no joy.  I used to have an icon in my task bar showing a network connection but it's no longer there too. 

Thanks

In terminal type below command:
```
gnome-session-properties
```

Scroll down the list to see whether the Network Manager is in this list and has its checkbox ticked or unticked. If unticked then tick it, log out and log in back again, and the network manager should appear.

---

### Post by aierlan on 2009-11-02
> **ukripper said:**
> In terminal type below command:
```
gnome-session-properties
```

Scroll down the list to see whether the Network Manager is in this list and has its checkbox ticked or unticked. If unticked then tick it, log out and log in back again, and the network manager should appear.

Hey, thanks for the reply

I checked what you said above and network manager was already checked.  I unchecked it and restarted then checked it again and restarted but still can't seem to find network manager.  Still no internet connection.  

Any more ideas? Thanks again.

---

### Post by ukripper on 2009-11-02
> **aierlan said:**
> Hey, thanks for the reply

I checked what you said above and network manager was already checked.  I unchecked it and restarted then checked it again and restarted but still can't seem to find network manager.  Still no internet connection.  

Any more ideas? Thanks again.

Try re-installing it via terminal :
```
sudo apt-get install --reinstall network-manager-gnome
```

---

### Post by Dirtpile on 2009-11-02
Try re-installling Netwoork-manager-gnome and/or network manager packages in synaptic.  You might need to install them from the cd.

---

### Post by aierlan on 2009-11-04
> **ukripper said:**
> Try re-installing it via terminal :
```
sudo apt-get install --reinstall network-manager-gnome
```

Tried reinstall but got message "E: invalid operation install--reinstall" so tried just install instead which gave me the message - network manager gnome is already the newest version.

Will try reinstalling from the cd but have to download and burn a new one first.  

Will let you know how i get on.

---

### Post by ukripper on 2009-11-04
Can you try this then:
Right click on the top panel bar and select "add", then add "notification area"

---

### Post by ukripper on 2009-11-04
> **aierlan said:**
> Tried reinstall but got message "E: invalid operation install--reinstall" so tried just install instead which gave me the message - network manager gnome is already the newest version.

Will try reinstalling from the cd but have to download and burn a new one first.  

Will let you know how i get on.

There is space between install and --reinstall

---

### Post by aierlan on 2009-11-04
> **ukripper said:**
> Can you try this then:
Right click on the top panel bar and select "add", then add "notification area"

Hey thanks, that has allowed me to view my connections again.  When I click on the icon now it gave me the option of auto eth0.  Selected this and it connection to something but tried firefox and still no internet.  
Any more help, thanks so much for your help and patience so far.

---

### Post by ukripper on 2009-11-04
> **aierlan said:**
> Hey thanks, that has allowed me to view my connections again.  When I click on the icon now it gave me the option of auto eth0.  Selected this and it connection to something but tried firefox and still no internet.  
Any more help, thanks so much for your help and patience so far.

can you post output of the following commands:
```
sudo ifconfig
```

```
sudo lshw -C network
```

---

### Post by aierlan on 2009-11-04
> **ukripper said:**
> can you post output of the following commands:
```
sudo ifconfig
```

```
sudo lshw -C network
```

**sudo ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:30:1b:b0:4e:44  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0 
          inet6 addr: fe80::230:1bff:feb0:4e44/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:768 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:46551 (46.5 KB)  TX bytes:3205 (3.2 KB) 
          Interrupt:18 Base address:0x9000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:228 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:228 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:14256 (14.2 KB)  TX bytes:14256 (14.2 KB) 

**sudo lshw -C network**

Hardware Lister (lshw) - B.02.13 
usage: lshw [-format] [-options ...] 
       lshw -version 

	-version        print program version (B.02.13) 

format can be 
	-html           output hardware tree as HTML 
	-xml            output hardware tree as XML 
	-short          output hardware paths 
	-businfo        output bus information 

options can be 
	-class CLASS    only show a certain class of hardware 
	-C CLASS        same as '-class CLASS' 
	-c CLASS        same as '-class CLASS' 
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. ) 
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. ) 
	-quiet          don't display status 
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.) 
	-numeric        output numeric IDs (for PCI, USB, etc.)

---

### Post by ukripper on 2009-11-04
can you restart your network service by following command and check if firefox connects to the internet:
```
sudo /etc/init.d/networking restart
```

and then close and re-open firefox, check if firefox is connected to internet.

---

### Post by aierlan on 2009-11-04
Hey,

Tried that and got this - 

*reconfiguring network interfaces 
Ignoring unknown interface eth0 = eth0

Opened firefox but still nothing
Any ideas?

---

### Post by ukripper on 2009-11-04
> **aierlan said:**
> Hey,

Tried that and got this - 

*reconfiguring network interfaces 
Ignoring unknown interface eth0 = eth0

Opened firefox but still nothing
Any ideas?

Can you tell me how you are connecting to internet, is it via router or modem?

Secondly, Can you post output of the following:
```
cat /etc/network/interfaces
```

---

### Post by aierlan on 2009-11-04
> **ukripper said:**
> Can you tell me how you are connecting to internet, is it via router or modem?

Secondly, Can you post output of the following:
```
cat /etc/network/interfaces
```

output is 

auto lo
iface lo inet loopback


I'm connecting directly via router

---

### Post by ukripper on 2009-11-04
ok now try to manually add eth0 in your interfaces file as below:
run command in terminal:```
sudo gedit /etc/network/interfaces
```

then just add these two lines below where loopback ends:
```
auto eth0
iface eth0 inet dhcp
```

close and save it.

then restart network service:
```
sudo /etc/init.d/networking restart
```

Then try firefox again.

---

### Post by aierlan on 2009-11-04
YES!

You're a genius ukripper thanks a million.  Working perfectly now.

---

### Post by ukripper on 2009-11-04
> **aierlan said:**
> YES!

You're a genius ukripper thanks a million.  Working perfectly now.

Great, welldone! Make sure you restart and check whether changes made now doesn't disappear after restart.

Also make this thread as solved in case someone is looking for same info.

---

