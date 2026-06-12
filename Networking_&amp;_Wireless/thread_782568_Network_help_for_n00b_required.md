---
title: "Network help for n00b required"
date: 2008-05-05
forum: Networking &amp; Wireless
---

### Post by alferret on 2008-05-05
I'll start with saying I am a total virgin where linux is concerned, so please be gentle with me and talk to me like I'm 5 that way I may just be able to get this Ubuntu box working properly so I can understand it.

8.04 is installed on a 19gb primary partition so it boots straight in.

The mobo is a Jetway v266b with 512mb AMD XP2000+, Nvidia mx400.

Here is the first task I need help with.

The NIC is a Realtek RTL-8139d pci card for which I have no idea how to install drivers or where to find them. I dont even know if ubuntu knows that there is a NIC card on the machine. If I look at drivers it just says that Nvidia is installed and enabled and if I test hardware when it gets to the NIC it comes up with something that isnt realtek, I think.

Where can I find the drivers, how do I install them and how do I configue my protocols for the device so that the machine can access the net and work as a server.

Many thanks to the poor souls who help me with this task

Al

---

### Post by alferret on 2008-05-05
Just to add a bit more info.

When I run test hardware I get the following for the network controller.

Hangzhou Silan Microelectronics Co., Ltd
Unknown Device 2031 (rev01)

---

### Post by superprash2003 on 2008-05-05
plese go to the terminal(System->accessories->terminal) and type ifconfig and post results here

---

### Post by alferret on 2008-05-05
Hi Super


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1532 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1532 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:76600 (74.8 KB)  TX bytes:76600 (74.8 KB)

---

### Post by alferret on 2008-05-05
Hi Super


oppps double post

---

### Post by Prefix100 on 2008-05-05
what about lspci in terminal?

---

### Post by schmildo on 2008-05-05
Looks like you have no network access up and running...
Post results of:
***ifconfig -a***
and
***lshw -C network***

---

### Post by alferret on 2008-05-05
ifconfig -a


eth0      Link encap:Ethernet  HWaddr 00:e0:20:6b:12:c3  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Memory:ef000000-ef0000ff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1538 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1538 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:76900 (75.0 KB)  TX bytes:76900 (75.0 KB)


lshw -c network

alan@alan-desktop:~$ lshw -c network
Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.12.01)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)

---

### Post by Prefix100 on 2008-05-05
lshw -C network is with a capital C :P

just repaste it :)

---

### Post by alferret on 2008-05-05
Opsssss lol my bad

WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Ethernet interface
       product: Hangzhou Silan Microelectronics Co., Ltd.
       vendor: Hangzhou Silan Microelectronics Co., Ltd.
       physical id: c
       bus info: pci@0000:00:0c.0
       logical name: eth0
       version: 01
       serial: 00:e0:20:6b:12:c3
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sc92031 driverversion=2.0c latency=32 maxlatency=40 mingnt=20 module=sc92031 multicast=yes

---

### Post by alferret on 2008-05-07
bump!!!!

---

### Post by schmildo on 2008-05-09
Sorry man I keep checking this forum when its late and i'm too exhausted to think. I've not forgotten you i'm just busy at the moment. I'm surprised more people haven't popped in to help on this one.
  I'm too tired again tonight *Yawn* But i'll be back before monday.


Sorry!

---

### Post by breadlord on 2008-05-09
alferret, according to your info you've got a hardware driver loaded, but the device isn't coming up...

I suspect this is a problem with network manager. Do me a favour, run the following.

```

# dmesg > ~/dmesg.txt
# cat /var/log/syslog > ~/syslog.txt

```

Then zip the two new files you get in your home directory and attach the file to the forum.

Second, this *might* help...

```

# sudo su - *(Then enter your password*
# /etc/dbus-1/event.d/25NetworkManager stop
# ifconfig eth0 up
# dhclient
# exit

```

This will bypass NetworkManager and *might* bring your card back to life. If not, there's some more config that can be done. If the driver's crashing then you're better off spending £10 on a better network card...

---

### Post by alferret on 2008-05-10
> **schmildo said:**
> Sorry man I keep checking this forum when its late and i'm too exhausted to think. I've not forgotten you i'm just busy at the moment. I'm surprised more people haven't popped in to help on this one.
  I'm too tired again tonight *Yawn* But i'll be back before monday.


Sorry!


Dont worry about it mate I apreaciate all the help I have had so far :)

I'm getting married today so for me this thread is going to have to wait for a couple of weeks till I get back from my honeymoon.

Thanks again.

---

### Post by alferret on 2008-05-10
> **breadlord said:**
> alferret, according to your info you've got a hardware driver loaded, but the device isn't coming up...

I suspect this is a problem with network manager. Do me a favour, run the following.

```

# dmesg > ~/dmesg.txt
# cat /var/log/syslog > ~/syslog.txt

```

Then zip the two new files you get in your home directory and attach the file to the forum.

Second, this *might* help...

```

# sudo su - *(Then enter your password*
# /etc/dbus-1/event.d/25NetworkManager stop
# ifconfig eth0 up
# dhclient
# exit

```

This will bypass NetworkManager and *might* bring your card back to life. If not, there's some more config that can be done. If the driver's crashing then you're better off spending £10 on a better network card...


RE above the married bit.

I was thinking about changing the NIC, although only a few months old the abuse it got when it was installed has probrably FUBAR'd it. 

I'll try when I'm back from Turkey.
Cheers
Al

---

### Post by schmildo on 2008-07-18
Are you back from Turkey yet?

---

