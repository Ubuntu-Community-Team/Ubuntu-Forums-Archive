---
title: "Wireless WEP Key Number?"
date: 2005-11-22
forum: Networking &amp; Wireless
---

### Post by crux19 on 2005-11-22
Hello,
Just installed Ubuntu for the first time on an extra laptop I have sitting around.  Installation was a breeze.  I am having some trouble getting my wireless network card (Orinoco Gold PCMCIA) to connect to my wireless network.  

I tried to have it connect when installing but it only asked for an ESSID and a WEP key.  There was no place to enter a key number (happens to be key #3 on my current network).

I have a 26 character WEP key that I have entered multiple times to verify I typed it correctly.  

After everything was loaded, I went into network-admin and found my wireless connection (eth1).  I re-entered the WEP key and ESSID.  I'm sure it's not connecting because of the key number since I turned all WEP off and it worked fine.

My roommates and I have multiple computers connected via wireless so I don't want to have them all change their key number.  Is it possible to asssign a key number?

Thanks!

---

### Post by Manny C on 2005-11-22
Please post the contents of your /etc/network/interfaces file.

---

### Post by crux19 on 2005-11-22
Thanks for the quick reply.  Apologies for not providing the correct information the first go round.  Since I am typing this out, I'm only including what is not commented out.

auto lo
iface lo inet looopback

mapping hotplug
     script grep
     map eth1



I checked this before and it looks like it didn't take what I put in on setup.  If I change the information in the network-admin utility, it shows in ifconfig but this is what the /etc/network/interfaces file looks like right after boot up.

Thanks!

---

### Post by crux19 on 2005-11-22
I have read through  many of the posts and found the below information to be helpful.  I looked at my AP and it said that the MAC address of my laptop with Ubuntu was connected.  My Ubuntu laptop said it was connected to the correct AP MAC.  For some reason it's not giving me a DHCP address.  Please let me know if there is anything else I can provide to help out.  I modified my interfaces file according to a post I saw on the forums.  

Thanks again!


/etc/network/interfaces 
auto lo 
iface lo inet loopback 

iface eth1 inet dhcp 
wireless-essid Lonestar_Love_Palace 
wireless-key 73763c247b67437b627c414f6b 

auto eth1 

mapping hotplug 
script grep 
map eth1 


root@trixie:~# ifconfig 
eth1      Link encap:Ethernet  HWaddr 00:02:2D:37:7F:F3 
         inet6 addr: fe80::202:2dff:fe37:7ff3/64 Scope:Link 
         UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
         TX packets:30 errors:0 dropped:0 overruns:0 carrier:0 
         collisions:0 txqueuelen:1000 
         RX bytes:0 (0.0 b)  TX bytes:10800 (10.5 KiB) 
         Interrupt:3 Base address:0x100 


root@trixie:~# iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

eth1      IEEE 802.11-DS  ESSID:"Lonestar_Love_Palace"  Nickname:"HERMES I" 
         Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:3D:5B:57:02 
         Bit Rate:11 Mb/s   Tx-Power=15 dBm   Sensitivity:1/3 
         Retry limit:4   RTS thr:off   Fragment thr:off 
         Encryption key:7376-3C24-7B67-437B-627C-414F-6B   Security mode:open 
         Power Management:off 
         Link Quality=29/92  Signal level=-64 dBm  Noise level=-93 dBm 
         Rx invalid nwid:0  Rx invalid crypt:748  Rx invalid frag:136 
         Tx excessive retries:0  Invalid misc:0   Missed beacon:0 


root@trixie:~# dhclient eth1 
There is already a pid file /var/run/dhclient.pid with pid 8218 
killed old client process, removed PID file 
Internet Systems Consortium DHCP Client V3.0.2 
Copyright 2004 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP) 

sit0: unknown hardware address type 776 
sit0: unknown hardware address type 776 
Listening on LPF/eth1/00:02:2d:37:7f:f3 
Sending on   LPF/eth1/00:02:2d:37:7f:f3 
Sending on   Socket/fallback 
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7 
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16 
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13 
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9 
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13 
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3 
No DHCPOFFERS received. 
No working leases in persistent database - sleeping.

---

### Post by Lambert on 2005-11-22
Try this and please post back results.

Make sure the interface is down. You can do this through the gui, just select the device and deactivate. Then from terminal

```
sudo route add {default} eth1

then

sudo route add {default} gw <192.168.x.x>
``` 

<192.168.x.x> = your router's address.

Try it with out default in there. (If it doesn't work start over again and use the commands again adding default in there.) Then bring up the interface. If it doesn't connect immediately then try the command

```
sudo dhclient eth1
``` 
And last thing to try is reboot as there is a service that might need to restart for settings to take affect.

If above doesn't work then post back the out put of 

```
ifport eth1
```

---

### Post by crux19 on 2005-11-23
Thanks a ton for your help.  It looks like it's not taking.  I printed the command you requested.  Thanks again for helping me through this.

I deactivated eth1 and ran the following commands:

root@trixie:~# route add eth1
eth1: Host name lookup failure

root@trixie:~# route add {default} eth1
{default}: Host name lookup failure

root@trixie:~# route add gw <192.168.1.1>
bash: syntax error near unexpected token `newline'
root@trixie:~# route add gw 192.168.0.1
gw: Host name lookup failure

(did it with sudo as well, but logged in as root)

root@trixie:~# ifport eth1
eth1    0 (Auto)

---

### Post by Lambert on 2005-11-23
One more thing. POst output of the command

```
route
```

---

### Post by crux19 on 2005-11-23
root@trixie:~# route
Kernel IP routing table
Destination   Gateway  Genmask  Flags Metric Ref  Use Iface


Thanks again.  (FYI- I typed the above out.)

Thanks!

---

### Post by Lambert on 2005-11-23
When you say you typed the followiong out I take it you couldn't just copy and paste? You should have gotten a little more output similar to this.

192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     0      0        0 eth0
loopback        *               255.0.0.0       U     0      0        0 lo
default         192.168.0.1     0.0.0.0         UG    0      0        0 eth0

If you didn't get this then I believe your problem is you don't have an ip route set up so the packet is stopping at the wireless device.

I don't have the exact answer for you now, I'll have to come back when I get home and logged on to my ubuntu pc.

The one thing I would believe you tried is to reboot with the card inserted. If not make sure you try that. A route should have been set up automatically for you.

You can look at the man page for route *man route* but it's not real clear to me even. Or do google search for this using route; linux for keywords.

---

### Post by crux19 on 2005-11-23
I typed it out, but that's all that's shown when I type the route command.  Please let me know if you come up with anything else.  

Thanks!

---

### Post by Lambert on 2005-11-23
There are a few things you will need.

1. An ip in the range of your router. 192.168.X.X (You need to know the range.
2. The netmask of your network 255.255.xxx.xxx
3. The ip address of your router

Numbers 2&3 can be found by your windows pc. If you have 2000 or xp click start>run...type cmd...enter...type ipconfig /all

```
sudo ifconfig eth1 down
```

then

```
sudo ifconfig eth1 192.168.x.x  netmask 255.255.xxx.xxx up
```

Where 192.169.x.x = an ip within your routers range
and netmask is the netmask you looked up on your winxp machine (or you knew it)

Make sure it took by typing just if config. The second line should be something like this.

inet addr:192.168.99.14  Bcast:192.168.99.255  Mask:255.255.255.0

Now run this command

```
sudo route add default gw 192.168.x.x
```

where 192.168.x.x = the ip address of your router

Now try to ping your router.

ping 192.168.x.x

where 192.168.x.x = your routers ip address

Next try to ping an external site

ping 216.239.57.99

then 

ping [www.google.com](www.google.com)


If all goes well open a browser and try to connect to a site

You may want to reboot to see what happens after this and if you don't have internet then try sudo dhclient eth1

---

### Post by stewdog on 2005-11-25
Hello,
I've recently installed kubuntu and am rapidly learning and loving linux:smile: 
One problem I am having is getting my RA2500 wireless adapter to see my router on boot. At the mo, I have to launch the kwifi util(sorry, can't recall the name of the built in one), activate the config, and then it will see the router and I have reception, **but no IP**. So I then have to run dhclient ra0. I then get an IP address and away I go. I have to do this every reboot, even though it is ticked in the wifi util to apply the config at startup. I'm at work right now so if I try these commands you've listed, will they be retained on next boot? I was also in recovery mode as root trying to get it to work at one point, would I have to go back in that way and revert those changes? Or maybe I'll have to setup a script to automate my procedures. Any help would be great. Thx.

ps, I'm using a 128 bit wep key. My router assigns my ip, dhcp, filtered by mac address not hostname. btw, the Gnome install worked out of the box. no faffing:???:

---

### Post by Lambert on 2005-11-25
post your /etc/network/interfaces file here.

You can blank out any encryption keys

---

### Post by stewdog on 2005-11-26
Thanks, here is a piece of my interfaces file:

[B]mapping hotplug
	script grep
	map eth0

iface ra0 inet dhcp
wireless-essid stewdog_wlan_1
wireless-key s:**************************
auto ra0

iface eth0 inet 
[/B]
I'm sorry if I misunderstood your post above. That appears to be for a static IP and prolly won't help me. 
I just hate having to activate my wireless interface every time I reboot.

---

### Post by Lambert on 2005-11-26
You don't have a line like this in the file?

# The loopback network interface
auto lo
iface lo inet loopback

Also maybe add this to the file under the eth0 mapping lines. You may have to comment out the other mapping lines or change the grep to echo for that line.

mapping hotplug
        script echo
        map ra0

---

### Post by stewdog on 2005-11-26
Nice one Lambert! It now boots with the wlan interface enabled. It can see the router and recognises it as the access point but still no IP address. Can I add some more to the interfaces file to specify the gatway, mask, etc to help it get one? I appreciate your help and I'm almost there thanks again to you.

---

### Post by crux19 on 2005-11-28
Thanks again for the help.  Was home over vacation so wasn't able to work on the laptop.  I have posted the output from your earlier suggestions.  Still having issues.  Assigning an IP address, netmask and gateway took but I was not able to ping the router.  I went in to the network admin gui and it sitll showed it set up as DCHP, so just to make sure, I typed in the information there as well (different IP to test).  That took as well but still couldn't ping the router.  After reboot, none of the settings held.  Thanks again for your help.  Again, this is a default install so not sure where things could have gone wrong.  Also of note, my wired connection works just fine.

root@trixie:~# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
root@trixie:~# ifconfig eth1 down
root@trixie:~# ifconfig eth1 192.168.0.66 netmask 255.255.255.0 up
root@trixie:~# ifconfig
eth1      Link encap:Ethernet  HWaddr 00:02:2D:37:7F:F3
          inet addr:192.168.0.66  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::202:2dff:fe37:7ff3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:3396 (3.3 KiB)
          Interrupt:3 Base address:0x100

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1410 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1410 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:124275 (121.3 KiB)  TX bytes:124275 (121.3 KiB)

root@trixie:~# route add default gw 192.168.0.1
root@trixie:~# ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
From 192.168.0.66 icmp_seq=2 Destination Host Unreachable
From 192.168.0.66 icmp_seq=3 Destination Host Unreachable
From 192.168.0.66 icmp_seq=4 Destination Host Unreachable
From 192.168.0.66 icmp_seq=6 Destination Host Unreachable
From 192.168.0.66 icmp_seq=7 Destination Host Unreachable
From 192.168.0.66 icmp_seq=8 Destination Host Unreachable
From 192.168.0.66 icmp_seq=10 Destination Host Unreachable
From 192.168.0.66 icmp_seq=11 Destination Host Unreachable
From 192.168.0.66 icmp_seq=12 Destination Host Unreachable
From 192.168.0.66 icmp_seq=14 Destination Host Unreachable
From 192.168.0.66 icmp_seq=15 Destination Host Unreachable
From 192.168.0.66 icmp_seq=16 Destination Host Unreachable
^X
[1]+  Stopped                 ping 192.168.0.1
root@trixie:~#
root@trixie:~# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth1
default         192.168.0.1     0.0.0.0         UG    0      0        0 eth1
root@trixie:~# dhclient eth1
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:02:2d:37:7f:f3
Sending on   LPF/eth1/00:02:2d:37:7f:f3
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
root@trixie:~#

-----------------after reboot-----------------
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
root@trixie:~#

---

### Post by Lambert on 2005-11-28
I think I may have learned something from you.

Went back and read through this again to see what has been done and if anything was missed.

Your first post said your wep key was # 3 on the router.

So let's try this.

Change your interface file so the wireless_key line looks like this. (ascii format)

wireless-key [3] s:xxxxetc..

or move the [3] to the end of the line if above doesn't work.

Because you're connecting to the router I'm assuming this, you are using an open wep setting and not a sharedkey/restricted setting correct?

---

### Post by punkr0x on 2005-11-28
One thing I noticed with my wireless router, even though I am using open encryption and not restricted, I had to specify:
wireless-key open XXXXXXXXXXXXXXXXXXXXXXXXXXX
in my /etc/network/interfaces to make it work.  Maybe try that?
Also might not hurt to specify
wireless-mode managed
Hopefully one of those helps you..

---

### Post by zork-1 on 2005-11-28
Hi folks .. !

I apologize for the I-must-be-lost/newbie nature of this first (well, and later ones too, I guess) post.  But I have been experimenting for the past few days with a Ubuntu Live CD (uname -r reports 2.6.12-9-386, while "issue" says this is "Breezy Badger"), and have encountered difficulties getting a WEP connection thru a Netgear WG511 card on an IBM X20.  (My intent is to install Ubuntu on an IBM R52 one of these days, and any reassurance on that plan would be very welcome .. a query for another forum, of course.)

The Eth0 connection (cabled to the router) works with no problems.  Iwconfig recognizes there is an Eth1 card but short of connecting to a neighbor's wireless network -- they aren't running WEP nor WPA, but I won't tell -- I was unable to connect to my local nw using the WG511 and WEP (until a few minutes ago). Going thru network configuration and specifying the WEP key there didn't help, no connection could be established and I couldn't even talk with the router.

This post is a summary of what I tried and what worked, and the question is essentially, Why??

Based on reading in these and other Linux forums, I tried

  iwconfig eth1 enc wepkeyid [2]

(which strikes me as a magical incantation), but that produced only " .. Error for wireless request 'Set Encode' ..".

After further searching in the Ubuntu forum entries, I then attempted

  sudo iwconfig eth1 enc wepkeyid [2]

(with as much understanding as before) -- and this .. worked!?  Following this with

  sudo iwconfig eth1 key [2]

gave me a connection to my access point and no further difficulties; at least so far.

And now to my questions: What exactly is "sudo?"  Is this sort of sudo+iwconfig sequence usually necessary to get WEP-protected wireless cards to work with Ubuntu?  And last for the moment, is there online or written documentation available to help me understand a bit more about why these commands worked -- along with further help for my next baby steps?

Thanks, in advance ..

Wayne

---

### Post by crux19 on 2005-11-29
Thanks again for the suggestions.  This is starting to drive me mad.

interfaces file:

auto lo
iface lo inet loopback

iface eth1 inet dhcp
wireless-mode Managed 
wireless-essid Lonestar_Love_Palace
wireless-key [3] XXXXXXXXXXXXXXXXX
auto eth1

mapping hotplug 
script grep
map eth1



OK, so I've also tried the [3] at the end of the key.  Also tried the [3] at the front and beginning along with wireless-defaultkey 3

Tried setting it to static and assigning address, netmask, network, broadcast, gateway.  Also tried specifying wireless-keymode open.  Also researched and saw that the wep key should be in all caps and changed that.

Still not assigned a dhcp address.  Still can't ping the router.

When I am troubleshooting, I deactivate the interface through the network settings dialong, make the changes to the interfaces file, activate the interface and try again (ifconfig, route, dhclient ping, etc)...all with the same result.  

What is the 'correct' way to assign the key number (3 in my case)?  Also, I don't have dashes in my wep key but read I don't need to.  

Should it be this difficult?

Thanks again for your help!

---

### Post by Lambert on 2005-11-29
[QUOTE=zork-1]Hi folks .. !



And now to my questions: What exactly is "sudo?"  Is this sort of sudo+iwconfig sequence usually necessary to get WEP-protected wireless cards to work with Ubuntu?  And last for the moment, is there online or written documentation available to help me understand a bit more about why these commands worked -- along with further help for my next baby steps?

Thanks, in advance ..

Wayne[/QUOTE]

sudo is simply a command that gives you superuser (administrator) priveledges to run tasks need by higher priveledge. It's a built in security measure so you can run as a normal user and if needed to do an administrative task, instead of switching to an administrator user, you just tag sudo at the begininng of a command.

You can read more here.

[https://wiki.ubuntu.com/RootSudo?highlight=%28sudo%29](https://wiki.ubuntu.com/RootSudo?highlight=%28sudo%29)

sudo is for the command line but you can also run sudo with grpahical windows. If you type alt+f2 then type gksudo nautilus you now have the file manager open with admin priveledges so you can open and save files in directories where admin priveledges are needed.

---

### Post by Lambert on 2005-11-29
> Should it be this difficult?

Not it shouldn't be this difficult. There is just something that's being missed.

So a question.

For your wep. is it open or restriced/shared?

run the command 

```
iwpriv eth1
```

You'll get some output that's not cryptic but hard to understand.

I'm looking for something like get_wepmode and/or get_authtype(authmode)

You can post the output of that command here or if you see those commands you can run them by

iwpriv eth1 get_wepmode

You can try to search iwpriv wavelan for some help but you'll probably need to add other keywords in there as that search for me didn't bring anything up real quick that I saw to help.

While writing this during my search I came across this.

> WEP and PrismII : Most PrismII firmwares are completely broken when it come to WEP support, and only firmwares 1.4.9 and later support WEP properly and will work properly with Orinoco. For broken firmwares, it is possible to use driver based encryption, which is available in HostAP or as a patch for Orinoco (and this will slow down operation

Now I don't know how to look up firmware for a device off the top of my head and not at a linux system to figure it out. Maybe somebody else knows. Your card though may not work with wep.

---

### Post by orbinick on 2005-11-29
try this:

[http://ubuntuforums.org/forumdisplay.php?f=74]("http://ubuntuforums.org/forumdisplay.php?f=74")

Just open the "add to panel" menu and move the "wireless connection manager" icon.

for some reason it connects on startup perfectly

I'm guessing the problem is that we're logging as users and network-admin has to be ran as superuser or root. Same with the problems syncing the clock during the session.

It's a good security measure but I think it needs to be more flexible.

---

### Post by crux19 on 2005-11-29
Thanks again

Authentication on my AP = Open System
I am sure this card works since I had the exact same laptop and Orinoco Gold card working with Fedora about a month ago.

orbinick, are you suggesting I try the GTKWifi application?


root@trixie:~# iwpriv eth1
eth1      Available private ioctls :
          force_reset      (8BE0) : set   0       & get   0
          card_reset       (8BE1) : set   0       & get   0
          set_port3        (8BE2) : set   1 int   & get   0
          get_port3        (8BE3) : set   0       & get   1 int
          set_preamble     (8BE4) : set   1 int   & get   0
          get_preamble     (8BE5) : set   0       & get   1 int
          set_ibssport     (8BE6) : set   1 int   & get   0
          get_ibssport     (8BE7) : set   0       & get   1 int
          dump_recs        (8BFF) : set   0       & get   0

root@trixie:~# iwpriv eth1 get_wepmode
Invalid command : get_wepmode

---

### Post by orbinick on 2005-11-29
I am not suggesting. I recommend it. At least until we find an elegant solution.

---

### Post by crux19 on 2005-11-29
Thanks.  I will give it a try when I go home.  Should I make any changes to my interfaces file before trying GTKWifi or can I just leave it the way it is?  Also, do I need to make any changes in the Gnome Network Admin utility?

Thanks!

---

### Post by crux19 on 2005-11-29
Returned home and installed gtkwifi.  Everything installed fine and added it to my panel.  When I open it up, it shows no networks in any of the tabs (I'm about 2 feet from my AP).  When I go to the Wireless Card tab, it shows my card but says that the selected card does not support scanning.  

Is there any way to manually put the information necessary in to the application?

Thanks and sorry for all of the questions, but I would really like to get to use Ubuntu but need the wireless connection since we don't have a wired network in my house.

---

### Post by orbinick on 2005-12-02
Don't be sorry. 

I got to the root of my problems with wireless, I actually found a driver that worked, better than the one in the setup disk for Windows, its not even native, you have to ndiswrapp it.

the problem with the native drivers is that you have to compile it to your kernel. That may be easy, but you really want it to work without fuzz. 

All the editing I did to my config files did nothing. it was all in the driver I used.

Try this link if it helps any:
[http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Orinoco.html]("http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Orinoco.html")

It may have the latest orinoco pcmcia driver supporting scanning that works natively.

---

### Post by tonyw50 on 2005-12-02
crux19,
I haven't tried to follow this whole thread but I'm responding to your original problem where your wireless card appears to be detected and connecting without a WEP but won't operate with a WEP.  Are you sure that the card can support a 26 character WEP?  I have a newer access point that I have to use with lower level encryption in order for one computer using an older card to connect to it.

---

