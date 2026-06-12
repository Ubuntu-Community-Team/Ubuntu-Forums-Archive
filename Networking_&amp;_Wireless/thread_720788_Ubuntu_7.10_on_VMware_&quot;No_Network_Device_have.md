---
title: "Ubuntu 7.10 on VMware &quot;No Network Device have been found&quot;"
date: 2008-03-10
forum: Networking &amp; Wireless
---

### Post by PS8 on 2008-03-10
Hello, 

Before shifting from XP to ubuntu I thought of trying it using VMware and the experience else than networking issues has been really interesting. 

I just updated today using latest updates and all other things are running smoothly else than internet. At work I am connected to the LAN and at home via ADSL. 

Presently there is a X in the network connections icon and it says "No Network Device have been found". Presently I am using 'Sudo Dhclient' to connect to internet which is working however the network icon still states 'No network device have been found'. 

How can get it to work please?

Any help will be much appreciated.

Just adding my lshw -C network output:

 *-network               
       description: Ethernet controller
       product: 79c970 [PCnet32 LANCE]
       vendor: Advanced Micro Devices [AMD]
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=vmxnet latency=64 maxlatency=255 mingnt=6 module=vmxnet

---

### Post by PS8 on 2008-03-10
I even tried this post in archive [http://ubuntuforums.org/showthread.php?t=179905](http://ubuntuforums.org/showthread.php?t=179905) to no avail. Please help.

---

### Post by jcwmoore on 2008-03-10
There is something wrong with the .vmx file you use to start you VM, I am assuming that you are using Windows, but I don't know how to correct your network settings in the VM config file with out opening it in note pad and manually doing it.  I would recommend that you try Virtual Box rather than vmware.  I believe the you will need to your network settings to NAT.

I think you can change the network while the VM is running, You click on the network icon in the tool bar just above the VM display and I think it gives you the choice to what type of networking is set up.

---

### Post by PS8 on 2008-03-10
The network is set up in NAT mode. Well, till I did all the ubuntu 7.10 updates it was working perfectly fine so am amazed is it due to those 100-120 odd so updates that did it?

Presently I have done the following and I get the internet access however the network icon still shows the X. 

I went to system > administration > network and clicked on wired connection. 
Clicked on properties and unclicked the roaming mode button.
Chose the DHCP from drop down menu on right and click close. 
Then clicked on the box just beside the Wired connection. 

This has given me internet as I stated but the network icon still shown no network device has been found. 

Iwconfig states:
lo        no wireless extensions.

eth0      no wireless extensions.


Ifconfig states (this is the case when dhcp is not enabled)
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

Any suggestions?

---

### Post by jcwmoore on 2008-03-10
That is very strange, in my experience with vmware the lack of network was the NAT issue... I guess this is a little beyond my knowledge... good luck

---

### Post by Anicka on 2008-04-15
I have this too! I have a Ubuntu 7.10 guest with XP as host. I use NAT and have DHCP enabled. My network works (apt, firefox, ping...) but still the network manager claims I don't have "no network connection". Is there a fix, or should I just get used to the annoying exclamation mark in the upper right corner?

---

### Post by Anicka on 2008-04-15
Update: I uninstalled vmware-tools all together (sudo vmware-uninstall-tools.pl), restarted and installed the vmware tools again and restarted (again). Now the networkmanager is happy using the pcnet32 with roaming (I didn't run the recommended restart network to enable vmxnet at the end of installing the tools). I hope this is of any help to you.

---

