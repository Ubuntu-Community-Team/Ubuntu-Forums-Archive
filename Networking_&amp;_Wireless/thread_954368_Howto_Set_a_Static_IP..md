---
title: "Howto Set a Static IP."
date: 2008-10-21
forum: Networking &amp; Wireless
---

### Post by theDaveTheRave on 2008-10-21
HowTo: Setup static IP addres on Hardy.

Warning, I know I have set the title of this thread to <howto> but before it gets moved to the <tutorials> section I would appreciate other peoples comments on it... I also need to hunt down a few references... which I seem to have managed to loose!

Some of the information in this file should be helpful for general troubleshooting of network problems, see the list of useful files and commands at the end of this post.

I have not tested this as yet on a wireless card, if there is anyone out there who can say if this works that would be great.

I am not a networking specailist, or Linux Guru, I just needed to get this to work, so as I can get a server where I work to have Linux rather than Windows Vista "ultimate" pretending to be a server!

I have only done this on a single flavour of Ubuntu, namely Hardy...
> 
davem@Dartagnan:~$ uname -a
Linux Dartagnan 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686 GNU/Linux


If this works for you and you are running X, KDE, DEB or any other Linux flavour, please post details (in same format as mine above please) and I will add them to the bottom of this post.

Also if it doesn't work...:oops:... drop in a post and I'll see what I can do.

So why did I need to set up Static IP.

All the terminals where I work are on a static IP system, as there is essential data that need to be shared between the computers.

Before I arrived the team had built a rather nice terminal that was to ultimately become a source for all thier shared data. They attempted to run a variety of Linux flavours on the terminal with the required static IP, so as they would then still be able to easily access from external sites.

I suggested that I examine why they couldn't get a static IP to work on this "soon to be a server" by showing how to do it on my Ubuntu Laptop.

First attempts where a dismal failure, each time the details were entered into Network manager, networking failed immediately! I hunted high and low on the internet for a solution, from my understanding there was either an issue with the connection to the correct DHCP name server or something wrong with the network mask.

Now the strange thing here is that the PC is a windows XP terminal (not for long though if I have my way), and running the <ipconfig> command on this terminal give the following information.

> 
Configuration IP de Windows





        Nom de l'hôte . . . . . . . . . . : Anticlimax


        Suffixe DNS principal . . . . . . : 


        Type de n&#339;ud . . . . . . . . . . : Inconnu


        Routage IP activé . . . . . . . . : Non


        Proxy WINS activé . . . . . . . . : Non





Carte Ethernet Connexion au réseau local:





        Suffixe DNS propre à la connexion : 


        Description . . . . . . . . . . . : Broadcom NetXtreme 57xx Gigabit Controller


        Adresse physique . . . . . . . . .: 00-1D-09-0A-44-8D


        DHCP activé. . . . . . . . . . . : Non


 [color="blue"]       Adresse IP. . . . . . . . .*. . . : 134.157.195.42


        Masque de sous-réseau . . .*. . . : 255.255.255.0


        Passerelle par défaut . . .*. . . : 134.157.195.126


        Serveurs DNS . . . . . . . . . .  : 134.157.0.129
[/color]




As you can probably tell I work in France!

Now running ifconfig on my ubuntu terminal 
> 
davem@Dartagnan:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:19:7d:40:b8:c0  
          inet6 addr: fe80::219:7dff:fe40:b8c0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

[color="blue"]eth0      Link encap:Ethernet  HWaddr 00:16:36:c8:51:d3  
          inet addr:134.157.195.83  Bcast:134.157.195.127  Mask:255.255.255.128
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 
[/color]
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1510 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1510 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:78699 (76.8 KB)  TX bytes:78699 (76.8 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-19-7D-40-B8-C0-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26011 errors:0 dropped:0 overruns:0 frame:16292
          TX packets:6150 errors:35 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:4716117 (4.4 MB)  TX bytes:279792 (273.2 KB)
          Interrupt:18 



now I wasn't entirely sure on the DNS server that I was hooked into, on a further search on the internet (don't you just love google) I found this [site]("http://www.askdavetaylor.com/how_do_i_install_dhcp_on_my_linux_server.html") to be rather helpful with some new files I would have loved to have known existed about 3 months ago!

and it gave me a way to find the required details.

It is apparently hidden in a file that will relate to the dhclient, so we need to have a search for this file with the following

> 
davem@Dartagnan:~$ locate dhclient
/etc/dhcp3/dhclient-enter-hooks.d
/etc/dhcp3/dhclient-exit-hooks.d
/etc/dhcp3/dhclient.conf
/etc/dhcp3/dhclient-enter-hooks.d/avahi-autoipd
/etc/dhcp3/dhclient-enter-hooks.d/debug
/etc/dhcp3/dhclient-enter-hooks.d/samba
/etc/dhcp3/dhclient-exit-hooks.d/debug
/etc/dhcp3/dhclient-exit-hooks.d/ntpdate
/etc/dhcp3/dhclient-exit-hooks.d/whereami
/etc/dhcp3/dhclient-exit-hooks.d/zzz_avahi-autoipd
/etc/dhcp3/dhclient-exit-hooks.d/zzzz_dhcdbd
/lib/dhcp3-client/call-dhclient-script
/sbin/dhclient
/sbin/dhclient-script
/sbin/dhclient3
/usr/share/man/ja/man5/dhclient.conf.5.gz
/usr/share/man/ja/man5/dhclient.leases.5.gz
/usr/share/man/ja/man8/dhclient-script.8.gz
/usr/share/man/ja/man8/dhclient.8.gz
/usr/share/man/man5/dhclient.conf.5.gz
/usr/share/man/man5/dhclient.leases.5.gz
/usr/share/man/man8/dhclient-script.8.gz
/usr/share/man/man8/dhclient.8.gz
/usr/share/man/man8/dhclient3.8.gz
[color="blue"]/var/lib/dhcp3/dhclient.ath0.leases
/var/lib/dhcp3/dhclient.eth0.leases [/color]
/var/lib/dhcp3/dhclient.leases
/var/lib/whereami/dhclient3.ath0
/var/lib/whereami/dhclient3.eth0
davem@Dartagnan:~$ 


we now need to look into the suspect files, in my case the eht0 file (as I am in a hard wired connection - I assume that if I had a wireless router I would look into the ath0, so here is my current file.

> 
davem@Dartagnan:~$ more /var/lib/dhcp3/dhclient.eth0.leases
lease {
  interface "eth0";
  fixed-address 134.157.195.83;
  server-name "";
  option subnet-mask 255.255.255.128;
  option dhcp-lease-time 3564;
  option routers 134.157.195.126;
  option dhcp-message-type 5;
  option dhcp-server-identifier 134.157.195.99;
  option domain-name-servers 134.157.0.129;
  option host-name "Dartagnon";
  option domain-name "local";
  renew 2 2008/10/21 07:15:13;
  rebind 2 2008/10/21 07:37:38;
  expire 2 2008/10/21 07:45:04;
}
lease {
  interface "eth0";
  fixed-address 134.157.195.83;
  server-name "";
  [color="red"]option subnet-mask 255.255.255.128;[/color]
  option dhcp-lease-time 3564;
  option routers 134.157.195.126;
  option dhcp-message-type 5;
  option dhcp-server-identifier 134.157.195.99;
  option domain-name-servers 134.157.0.129;
  option host-name "Dartagnon";
  option domain-name "local";
  renew 2 2008/10/21 06:54:46;
  rebind 2 2008/10/21 06:54:46;
  expire 2 2008/10/21 06:54:46;
}
davem@Dartagnan:~$


Now the important part, and this is where my previous experience caused my internet connection to break, is in red. The subnet mask, this controls the possible IP addresses that the terminal can hold. For some reason the XP terminal has a different mask (admitedly only the last set of digits are changed from ".0" on XP to ".128" on Ubuntu) - if someone can explain why this is I will be truly grateful!

So now we can set out static IP, either via the Network Manager GUI or via the file directly.

Via Network Manager.

Obviously you will have started network manager, unlocked it with your admin password, and selected your eth0 connection. Now you need to click the <properties> button

You now have the options for setting the various IP settings, obviously first off you need to change the <configuration> selection to "Static IP address" and then enter in the details into the required sections as dictated by your </var/lib/dhcp3/dhclient.eth0.leases> file.

Hopefully that should give you success? remember to save the location details, and then whenever you are on this location you will need to change your network location to this location.

Via the file directly.

Nework manager actually causes a change in the </etc/network/interfaces> file that is as the following

> 
davem@Dartagnan:~$ more /etc/network/interfaces
auto lo
iface lo inet loopback




iface ath0 inet dhcp
wireless-key ********
wireless-essid BIBOU





[color="blue"]iface eth0 inet static
address 134.157.195.83
netmask 255.255.255.128
gateway 134.157.195.126[/color]

auto eth0
davem@Dartagnan:~$ 


The important details in this file is the first line stating [color="blue"]iface eth0 inet static[/color]. Appart from that ensuring the details for the address, netmask and gateway are as reported in the </var/lib/dhcp3/dhclient.eth0.leases> file, you will notice that you do not need to have the DHCP server details in the file, I guess the network will automatically ask for this from the DHCP server, wherever it is.

So assuming someone changes the address of the server (eg. an office move causing a new subnet network to be created for the departmet), your system should still ask for the same IP address from the new DHCP server (allthough for all intents this is the "same" machine, its IP address may have changed!).

Proviso to this help file.

I'm no network admin or Linux guru, if you have a problem I will try to help, but I don't know if this will work with wireless cards or not.... although we do have a wireless network here at my office!

a quick recap.

usefull [color="skyBlue"]files[/color] / [color="green"]commands[/color] are:

[color="skyBlue"]/etc/network/interfaces[/color]
[color="skyBlue"]/var/lib/dhcp3/dhclient.eth0.leases[/color] (however this may be different in your system, you will possibly need to do a <locate dhclient> to find your particular file.
[color="green"]ifconfig [/color]- to show all your networking interfaces details.
[color="green"]iwlist scan[/color] - will show all available wireless networks.
[color="green"]route[/color] - will show your routing tables.
[color="green"]traceroute <an IP address>[/color] - show the IP address of the servers that pacets from a [color="green"]ping [/color] of the same IP address will pass through.
<an IP address>

[COLOR="Purple"]
Edit on 22nd October 2008[/COLOR]


OK I've now repeated this excercise on a server! I couldn't get it to function by direcly editing the file, so I had to install a gui and then use the network manager tool to edit the locations. I can however confirm that the server now has a fixed IP.

I'm trying to do the same with wireless.... but so far no luck!

[color="purple"] end edit[/color]

References. - if you know of other good sites / Threads please drop me a note I will add them in.

Setting your linux box as a DHCP, this site gave me a couple of new files to look at.
[http://www.askdavetaylor.com/how_do_i_install_dhcp_on_my_linux_server.html]("http://www.askdavetaylor.com/how_do_i_install_dhcp_on_my_linux_server.html")

I've noticed from the forum that there are plenty of people that have viewed this thread, however none of you have said if it has been usefull or not? Please pm me or drop a note on this forum to say if this has been..

Equally if you are a networking GURU please tell me if this is complete bunkum, I only know what my experience has been and I don't want to give out wrong advice.

Also to the forum modulators,  if you feel that this could / should be in the tutorials section feel free to send it there.

Thanks again to all who have helped me on these forums, I only hope I can give a little bit in return.

Edit 26Nov08:
I've now peromed this action again on another instal, works perfectly for me. I hope it is good for others also. On this occasion I did the edit directly on the /network/interfaces file. I'm a distincly happy bunny today!

David

---

### Post by skowronek on 2009-01-07
=)

Carry on!

---

### Post by ptm on 2009-01-07
I hate to say this, but I have no idea what you mean by Network Manager.  I have edit Network Connections, but that is not resetting anything.  So I still can't get Ubuntu to talk to the network.

---

### Post by theDaveTheRave on 2009-01-12
ptm

sorry for the slow reply, I currently have no internet connection due to having just moved house, and due to my laptop having had a power inlet failure (I'm waiting for the part to be delivered!).

I'll try to give as much help as I can but obviously for the moment I am a little "handicaped" by my high tech failure.... and I am begining to suffer from withdrawl sysptoms! :lolflag:

Ok onto answer your question

Network manager is the GUI method for changing the network connection info.

It should be found in the system | admin | network  menu. (I can't guarantee this at the moment as my laptop has broken), if you want this item then search for it in synaptic under "network manager"

I will do what I can to help out.

firstly are you connecting from home or from a work network? and I guess that you have access to another computer?

You say you can't talk to the network, can you run a couple of commands from the cli and put there output here for me.

so run these.

first send us a copy of your /etc/interfaces/network file by using this comand

```
more etc/network/interfaces
```

 

if you are trying to connect via a hard wired connection

```
ifconfig
```

otherwise
```
iwlist scan
```

The combination of the 2 is prably going to be best if you are trying to connect via wifi.

let us also confirm the network interfaces that you have using

```
lshw |grep network
```

should throw out details of ALL of your network interfaces that are conneted, just in case your hardware isn't playing nice with linux!

If you are trying to use a USB wifi key
```
ls usb
``` will confirm that the key is being found

Do this before and after inserting the key into the port, then the change in the output will be more obvious and we'll know what the card is that you are using.

I have read another thread about some issues where a USB wifi stick isn't being recognised by the system, but we'll worry about that one if you have a stick that causes this problem.

If all of this seems to be as you would expect, have you tried pinging another host? I tend to use google

```
ping www.google.com
```

if you have incorrectly configured the files then the results of ifconfig etc will not make any difference, as the incorrect values in them will kill the connection.

If this is potentially the case then you need to start afresh with a "blank" network connection via a dynamic IP obtained from the server. This is when Network Mangager is usefull, as it is relatively easy to create locations and then have a location set as "zero config" that should work everywhere!

Stupidly I don't know what the "basic" structure of the interfaces file is, as I have it set on network manager as a "zero config" location, and I've broken my laptop and can't check it (did I mention that I had a broken laptop?? ):P )

you could try something along these lines
> 
auto lo
iface lo inet loopback




iface ath0 inet dhcp




iface eth0 inet static


You may even try deleting the file entirely and then re-booting to see if that creates a "general" interfaces file (I have a feeling that it will if you don't have network manager installed).

I'm going to stop now as I could keep going for ever covering all the possible options for you.

Try the above few things and see how they unfold and post the output of those commands.

I'll get back to you as soon as I can.

A quick word of encouragement,

Historically networking via a USB key seems to have been an issue for linux systems, and even some "windows  specific" ethernet cards that use the windows OS as part of thier communication protocol caused issues (particularly in the days of dialup), so if you have an "on board" ethernet card you may be in for some fun and games!

If you have access to an PCI ethernet card you may be best to get that instaled as they mostly work (from what I have read on the forums).

Also if you know the ethernet card that you are using post the details here (although they should show up on the <lshw> or <lsusb> output).

good luck and keep working on the connectivity, we'll get you connected soon enough I'm sure of that!

David
____________ EDIT _______________

Ok did I mention in the first post I'm no Linux GURU?

well I just realised I mad a comand line error...

```

lshw |grep network
```

should in fact be
```

lshw -C network
```

sorry for the bad command

David

---

