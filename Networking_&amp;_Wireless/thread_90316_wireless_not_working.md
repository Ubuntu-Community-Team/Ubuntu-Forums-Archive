---
title: "wireless not working"
date: 2005-11-14
forum: Networking &amp; Wireless
---

### Post by vegos on 2005-11-14
Everytime I startup the wireless is not detected, I have installed ndiswrapper. I may have ndiswrapper wrong, because after i go through a few steps my wireless is detected and picks up my AP but no packets are being sent.

Thanks

---

### Post by Lambert on 2005-11-14
When you set up ndiswrapper did you ```
ndiswrapper -m
```

Thiss adds the driver so it starts on boot up.

When you say it's connected to the router but no packets sent I take it you mean you can't access any sites or a lan (if you have one set up)

Can you ping your router; another pc in your network; external website?

Do you have an ip address assigned. ```
ifconfig
``` will show it.

---

### Post by vegos on 2005-11-14
i did the ndiswrapper -m command and i think that fixed the detection problem but i still cant access the web. I have full signal.....anyway here is the result of the ifconfig

wlan0  Link encap:Ethernet  HWaddr 00:90:4B:EB:34:88
          inet6 addr: fe80::290:4bff:feeb:3488/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Memory:b0204000-b0205fff

Your help is appreciated

---

### Post by Lambert on 2005-11-14
It looks like you're not being assigned an ip address from the router.

My second line says this

inet addr:192.168.0.150  Bcast:192.168.255.255  Mask:255.255.0.0

Post the contents of your /etc/network/interfaces file here.

Are you using a static ip or dhcp

---

### Post by vegos on 2005-11-14
Im not to familiar with linux. could you tell me how to get the content of those interfaces (commands).  Im using dhcp.

also, my firefox seems to not be working. when i click the icon nothing happens.

Thanks

---

### Post by Lambert on 2005-11-14
Here is my interface.

```
# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

iface ath0 inet dhcp
wireless-essid <essid>
wireless-key <wep_key>

auto ath0
``` 
Yours should say wlan0 inplace of ath0.
I'm using an open wep setting; 64bit hexadecimel setting. So yours may need other lines.

Are you using encryption? If so wep or wpa?

cat /etc/network/interfaces

or 

sudo gedit /etc/network/interfaces will open it in a text editor.

---

### Post by vegos on 2005-11-14
here is the output

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

iface wlan0 inet dhcp
wireless-essid ShitgooseNet
wireless-key s:bushleague



iface eth0 inet dhcp







auto wlan0

auto eth0
```

---

### Post by Lambert on 2005-11-14
Do you have other computers connected and working via wireless with this router?

---

### Post by vegos on 2005-11-14
yes, when i access my windows partition the wirless works fine

---

### Post by Lambert on 2005-11-14
try this

```
sudo dhclient wlan0
```

or

add to your /etc/network/interfaces this line right below the iface wlan0 line

 wireless-mode managed

---

### Post by vegos on 2005-11-14
here is the output:
```
brooks@Brooks-Ubuntu-Linux:~$ sudo dhclient wlan0
Password:
Sorry, try again.
Password:
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:90:4b:eb:34:88
Sending on   LPF/wlan0/00:90:4b:eb:34:88
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
brooks@Brooks-Ubuntu-Linux:~$
```


and i cant edit the interface because its read only....




do you think i have the wrong driver being wrapped

---

### Post by Lambert on 2005-11-14
The next step I would do is disable wep and go to an open network to test. I know that's a bad option for some but sometimes it's a necessary step to troubleshoot.

I know how frustrating this is. When I first started with my laptop a couple months ago I spent many hours working with my wireless.

When you opened the interfaces file you had to use sudo gedit /etc/network/interfaces for write permission.

I've seen many posts like this where no dhcp offer was received. Try to search for that term to see how others solved it.

Not sure what router you're using, I have a d-link di624. I can access a log to see what's happening. You're connecting to the router it appears but just no ip address is being assigned. Maybe that log has some info that could help.

---

### Post by Lambert on 2005-11-14
Last suggestions then I need to cut out.

1. when you installed the drivers did you include the .sys and .dll files? if not uninstall the drivers, copy all the files from the driver folder on the disk to a local folder on your hard drive, ususually you can find a .inf a .sys or a .dll in the folder. then reinstall pointing to the files on the drive.
2. Download a different driver from vendors website and try.
3. try connecting using a static ip setting

Maybe somebody else come jump in and post something that's being overlooked.

best of luck

---

### Post by marcel.patoulachi on 2005-11-15
your wep key for the AP use the "open" method ? 
if yes u have to had it to /etc/network/interfaces :

wireless-key open yourpassword

your AP got the same frequency as your pc "adaptor-interfaces" (both use the same channel) ?

---

### Post by Lambert on 2005-11-15
A couple more ideas.

Look in /etc/init.d/ for something named network and dhcpd

type in a terminal

sudo /etc/init.d/<network??> restart
sudo /etc/int.d/<dhcpd??> restart


I'm not at my box so I'm not sure where this is at or if I have the correct name. Look for a file called dhclient.conf.

Open that with sudo gedit /<path>/dhclient.conf

Look for the wlan0 interface and see what it shows. Here is a sample of an ethenet iface. 



interface "ep0" {
    send host-name "andare.fugue.com";
    send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
    send dhcp-lease-time 3600;
    supersede domain-name "fugue.com rc.vix.com home.vix.com";
    prepend domain-name-servers 127.0.0.1;
    request subnet-mask, broadcast-address, time-offset, routers,
            domain-name, domain-name-servers, host-name;
    require subnet-mask, domain-name-servers;
    script "/etc/dhclient-script";
    media "media 10baseT/UTP", "media 10base2/BNC";
}

---

### Post by vegos on 2005-11-15
After much upset over this, i decided late last night to reinstall because i was having trouble with other programs also....

Im going to try the stuff already discussed and see what happens. Ill post the wireless troubles here as it comes (again)....


thanks

---

### Post by vegos on 2005-11-15
Ok, i may have found the problem.  I think i wrapped the windows driver wrong...

I have the folder of driver files on my desktop. Should they be moved somewhere befor i run the ndiswrapper -i filename.inf command?
If so, how do i login as root to move them ( it seems i cant unless im root)...
Im familiar with copying a file from one directory to another but what about the whole folder?


Thanks

---

### Post by corrosive23 on 2005-11-15
Just open a terminal and go to the ndiswrapper directory. Then do SU and enter the root password.

---

### Post by vegos on 2005-11-15
i dont remember setting a root password, just the one for my account...

---

### Post by Lambert on 2005-11-15
alt+F2 then gksudo nautilus and you can move them around via the file manager.

or from command line sudo cp /<from path> /<to path>

---

### Post by vegos on 2005-11-15
does the driver files go directly into the ndiswrapper folder

---

### Post by vegos on 2005-11-15
Ok, im back where i started. 
I have installed ndiswrapper with the windows driver files in the ndiswrapper folder...
I have gone to the gui network settings, and my network ssid is visible, i selected it, inserted the security password (ascii) and hit ok....
I have to go to the connection in the upper right hand corner, click it and type wlan0 in the box (where l0 was)......
This is where im stuck, there are no packets being transfered and i cant access the net.....

Please someone help me.....


Thanks,

---

### Post by Lambert on 2005-11-15
Hello again vegos, I'm not sure I have the expertise to help you with this, someone else may have to jump in. I've seen a couple posts lately where there are router connections but no ip address assigned.

You original post though said you were connected to your router but no packets sent. So if you run iwconfig does it show you're connected to the router. 

If you're connected then running ifconfig do you have an ip address? 2nd line inet address: <ip>

And if you're connected but no ip address assigned did you try sudo dhclient wlan0

Going back through I don't see where the make and model of the device was said. What is the make and model?

---

### Post by vegos on 2005-11-15
ok, i have a belkin wireless router and a BCM4306 802.11b/g Wireless LAN Controller

here are a few outputs:

brooks@ubuntu:~$ ndiswrapper -l
Installed ndis drivers:
bcmwl5  driver present, hardware present

/etc/network/interfaces
```

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

iface wlan0 inet dhcp
wireless-essid ShitgooseNet
wireless-key s:bushleague



iface eth0 inet dhcp

auto eth0

```

brooks@ubuntu:~$ lsusb
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

```
brooks@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:99/100  Signal level:-77 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:12  Invalid misc:46811   Missed beacon:0


```

```
brooks@ubuntu:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14217 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14217 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1291619 (1.2 MiB)  TX bytes:1291619 (1.2 MiB)

wlan0     Link encap:Ethernet  HWaddr 00:90:4B:EB:34:88
          inet6 addr: fe80::290:4bff:feeb:3488/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2567 (2.5 KiB)  TX bytes:378 (378.0 b)
          Memory:b0204000-b0205fff

```

---

### Post by Lambert on 2005-11-15
What's in the top panel just shows status, you can right click, properties and then configure which takes you to the network-admin window.

Let's check one more thing.

```
lsmod | grep ndis
``` 
the | key is shift + the key with \ on it. usually right above the enter key.

With the iwcongif command where it shows Access point and a bunch of 0's means you're not connected to the router at this time.

Depending on the output of lsmod my next reccomendation is to try connecting with out any encryption. This will rule out wether wep is the problem. Then you can go from there.


eidit- What channel is your router set to broadcast on? maybe try sudo iwconfig wlan0 channel X

---

