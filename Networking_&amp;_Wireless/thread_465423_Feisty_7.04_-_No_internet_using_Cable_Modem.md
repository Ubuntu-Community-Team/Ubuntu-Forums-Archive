---
title: "Feisty 7.04 - No internet using Cable Modem"
date: 2007-06-05
forum: Networking &amp; Wireless
---

### Post by Astraion on 2007-06-05
Ok, i've installed Ubuntu 7.04 Feisty ...everything went smooth ....except my freaking internet....
I also have Motorola SB5101 and i use automatic configuration assigned by DHCP to connect to my cable ISP.
I don't use any router, it's direct connection, with static IP.
When i start the net tools and select from the dropdown menu on the first tab...the eth0 is connected and receiving packets from the net (gets all the config from the DHCP).
When i ping my ISP's DNS - it's pinging, but when i ping yahoo or google - unknown host.
I start FF but nothing is loading....
I really want to start using Ubuntu...but with this "main" problem i start to lose my patience...

BTW, i didn't know what else to do...i've read in some post ....to try uninstalling the network manager so it could auto connect to internet, uninstalled it, but no progress.

Any help would be gratefull.

Thanks in advance.

---

### Post by clyrrad on 2007-06-05
Check what you have in /etc/resolv.conf

It should be something like this:

search local
nameserver [your isp's gateway ip here]

**So for example:**

search local
nameserver 74.100.200.100

Hope it helps.

---

### Post by Astraion on 2007-06-06
i did all this but i think that its of no use man....what help from this should i have...

Checkout the files:

---

### Post by tturrisi on 2007-06-06
reboot the cable modem (power off for 30 sec), it likeley is still storing the mac address & system id's from previous op sys, then reboot comp.

---

### Post by Astraion on 2007-06-06
> **tturrisi said:**
> reboot the cable modem (power off for 30 sec), it likeley is still storing the mac address & system id's from previous op sys, then reboot comp.

Thanks for the reply mate but maybe my Ubuntu is very stubborn...nothing really happens when i do that...
I dont know anymore what else to do....i am trying to solve this "problem" almost for a week so far...
I think that the only solution is format/uninstall Ubuntu.... and transfer to Fedora ...
I expected so much from ubuntu, but this connection issues really changed my opinion about Ubuntu...

So if anyone knows how to solve this problem...i'll be watching this topic for some time in case there is SOME other option to solve this freaking connection problem.
Thanks.

---

### Post by NeoLithium on 2007-06-06
Can you open up a terminal window and copy & paste the results of this command:
```

cat /etc/network/interfaces

```

---

### Post by Astraion on 2007-06-06
> auto lo
iface lo inet loopback


iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp



iface eth0 inet dhcp

What's next...?

---

### Post by NeoLithium on 2007-06-06
Ok, I think we can fix this rather easily.  Open up a terminal, and type:
```

gksu gedit /etc/network/interfaces

```
Then change the file to look like this:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```
Save the file, and then type (in a terminal) 
```
sudo etc/init.d/networking restart
```

Hopefully that will work for you.

---

### Post by Astraion on 2007-06-06
No progress so far mate...still the same:
> Listening on LPF/eth0/00:11:09:dc:59:97
Sending on   LPF/eth0/00:11:09:dc:59:97
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 89.185.192.3 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416

Listening on LPF/eth0/00:11:09:dc:59:97
Sending on   LPF/eth0/00:11:09:dc:59:97
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 89.185.192.3
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 89.185.192.3
SIOCADDRT: Network is unreachable
bound to 89.185.193.223 -- renewal in 34025 seconds.

and from the sudo ifconifg we can see clearly that i receive packets from the net...
> eth0      Link encap:Ethernet  HWaddr 00:11:09: DC:59:97  
          inet addr:89.185.193.223  Bcast:89.185.193.255  Mask:255.255.255.0
          inet6 addr: fe80::211:9ff:fedc:5997/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12807 errors:0 dropped:0 overruns:0 frame:0
          TX packets:94 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1166166 (1.1 MiB)  TX bytes:19170 (18.7 KiB)
          Interrupt:17 Base address:0x2000 

I am on Dual Boot WinXP/Ubuntu... and everything is going just fine in XP...

---

### Post by tturrisi on 2007-06-06
This does not make sense:
> I also have Motorola SB5101 and i use automatic configuration assigned by DHCP to connect to my cable ISP.
I don't use any router, it's direct connection, with static IP
You cannot use DHCP if have a static ip from your isp UNLESS you also use a router.
how do you want to connect, wired or wireless?

---

### Post by Astraion on 2007-06-06
> **tturrisi said:**
> This does not make sense:

You cannot use DHCP if have a ststic ip from your isp UNLESS you also use a router.
how do you want to connect, wired or wireless?

Look the hierarchy mate....i have motorola and i dont make any settings ...auto config by DHCP and i am connected to the net....
From the DHCP my ISP gives me Real/static IP (it doesnt change) i dont have any idea how they work...router or whatever...

and yes i wanna connect wired...

---

### Post by tturrisi on 2007-06-06
I understand all that!
If your isp gives you a static ip then it is NOT DHCP, it can't be.  An ip is either static or dynamic.  If yours is static then you have to config your connection as static!

Open net-admin and enter the connection info manually.  You will need to know:
isp dns servers
static ip assigned by isp
etc, etc

You can get all of this needed info in Windows by using the command prompt and typing:
ipconfig /all

copy+paste to save thjat info for use in ubuntu.

---

### Post by NeoLithium on 2007-06-06
> **tturrisi said:**
> I understand all that!
If your isp gives you a static ip then it is NOT DHCP, it can't be.  An ip is either static or dynamic.  If yours is static then you have to config your connection as static!

Open net-admin and enter the connection info manually.  You will need to know:
isp dns servers
static ip assigned by isp
etc, etc

You can get all of this needed info in Windows by using the command prompt and typing:
ipconfig /all

copy+paste to save thjat info for use in ubuntu.

Ok, that makes a bit more sense now, I wish I'd thought of that a few posts ago, to let him know.

---

### Post by Astraion on 2007-06-06
lol guys :)
ok, doing this stuff, brb in 5-10mins with the result.
thanks for the fast replies.
I appreciate that.

---

### Post by Astraion on 2007-06-06
OK i set to Static IP, entered everything, but still nothing...where i go wrong here i dont have any idea...

sudo etc/init.d/networking restart
> Failed to bring up eth0.

sudo ifconfig
> eth0      Link encap:Ethernet  HWaddr 00:11:09: DC:59:97  
          inet addr:89.185.193.223  Bcast:89.185.193.255  Mask:255.255.255.0
          inet6 addr: fe80::211:9ff:fedc:5997/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:46218 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3257217 (3.1 MiB)  TX bytes:3765 (3.6 KiB)
          Interrupt:17 Base address:0x2000

---

### Post by NeoLithium on 2007-06-06
Did you switch the DHCP option for Eth0 to Static in /etc/network/interfaces?

---

### Post by Astraion on 2007-06-06
I did that through the network admin

---

### Post by rudedude_96 on 2007-06-06
Hi there everyone, i have only just signed up to the forums, so im sorry if i have jumped in a bit late in this thread. I am having similar issues with Ubuntu 7.04 server, i installed Ubuntu correctly and it boots up and everything seems to work great, apart from one thing. I have a Motorola Cable modem connected to Paradise.net Cable internet, i have configured all the correct IP addresses, gateways, DNS servers etc etc, but can only ping the actual network cards address, as soon as i try to ping the gateway address, i get a destination host unreachable error. The server i am using is a old Pentium 433MHz, 128mb ram, 4GB Hdd, 2 Realtek 100Mbs network cards (model 8139 i believe) I want Eth0 to be connected to the cable modem for the internet and eth1 to be connected to a switch (as i have 5 pcs including the server in my flat and all need the net) i also want eth1 to be the DHCP server. But nothing seems to work, i have re-installed ubuntu twice, still nothing, and eth1 is not even up yet, any ideas??????

---

### Post by tturrisi on 2007-06-06
> **Astraion said:**
> OK i set to Static IP, entered everything, but still nothing...where i go wrong here i dont have any idea...

sudo etc/init.d/networking restart


sudo ifconfig

post contents of /etc/network/interfaces again & also  /etc/network/resolv.conf
as a test, boot from the live cd & see if have connectivity & if do then compare those 2 files to the live files.

---

### Post by Astraion on 2007-06-07
Guys ... finally i managed to set the network settings for my connection...
The problem was in my ISP - i changed my subnet mask from 255.255.255.0 -> 255.255.248.0 and everything is going smoothly ....i am writing this reply from my ubuntu. :)
Anyway, i would like to thank you for the kind support you gave me in this post: NeoLithium & tturrisi - thanks guys... at least i have learned the basics of networking in ubuntu lol.
Now its time to pimp my Ubuntu :)

---

### Post by tturrisi on 2007-06-07
very well done!
now get busy & tweak it up.
tt

---

### Post by stchman on 2007-06-07
> **Astraion said:**
> Guys ... finally i managed to set the network settings for my connection...
The problem was in my ISP - i changed my subnet mask from 255.255.255.0 -> 255.255.248.0 and everything is going smoothly ....i am writing this reply from my ubuntu. :)
Anyway, i would like to thank you for the kind support you gave me in this post: NeoLithium & tturrisi - thanks guys... at least i have learned the basics of networking in ubuntu lol.
Now its time to pimp my Ubuntu :)

My recommendation is to get a router (preferably wireless is you plan on getting a laptop).  They allow you to share the connection and they are pretty inexpensive (~$30).  You can then enter the static IP and the subnet mask in the router software.  This way if you ever get another PC you can just hook it up.

---

### Post by Astraion on 2007-06-07
I don't need a router mate...i am @ home, i have pci wireless + BT adapter...the wireless also has option to switch it in Access Point Mode...so if i plan to connect another pc or laptop i can use my access point.. buying a router is just wasting money..in my case here...but thanks for the input. :)

Man this ubuntu is Rocking..i've DLed the nVidia drivers...and those Desktop Effects are so cool.

Now, since i know whats the fuss with my connection, i wanna try the Linux Mint (Cassandra) Distro...i read a review about it on softpedia and its promising...all that look & feel, the windows like interface.
Gotta try it too.

OK, one more question from me.... this is not the right forum for this question, but since i've made this topic...in context...can you give me some tips how to uninstall ubuntu and do i have to remove The Grub too (how?) so I can make a fresh install with the Mint Distro?

Thanks :)

---

### Post by tturrisi on 2007-06-07
The next distro you use should give the option during install to re-partition the disk & if so, the boot record will be gone and later during the install it should give the option to install grub or whatever bootloader it provides.

re routers:
The advantage of a router at home is to secure the home network.  Even one comp, connected to a cable or dsl modem directly is networked...it's networked to all tghe other comps & routers connected to that isp network!  A router will block all incoming requests UNLESS the local comp has asked for something to be sent to it.  Some comps have opened ports, listening, just waiting for a request from the outside, making the comp open to attacks, exploits, certain network viruses, criminal hackers, etc.  All that is needed to attempt an exploit is your ip address that is assigned by your isp.  This is easily obtained by viewing email headers, web page scripts, social engineering tricks., network scanners. Post your ip address & I'll tell you how secure you really are.  (don't post it, I was only trying to make a point).  Spend 30 bucks, if anything, you may sleep better!

BTW, this is your IP address  [posted here]("http://www.idealorg.com/ip.php").

---

### Post by stchman on 2007-06-07
I could not agree more.  Routers provide a firewall to protect your computers from hackers.  Granted Ubuntu being Linux is pretty resistant to hackers.

Routers are just really nice things to have and very inexpensive as well.  A router is also useful if you want to run many PCs and some network printers.  I have 5 PCs and 2 network printers at my home.

The best way to remove Ubuntu IMO is to just delete the partition.  If you dual boot then remove the partition that Ubuntu resides on.  You can then use the Windows command fdisk /mbr to clear out GRUB.  You will need to get a hold of a Win98 boot disk to do this.

---

### Post by Astraion on 2007-06-07
I found a post when searching thru the net about uninstalling. Check it out:
> Boot into Windows Recovery Console via your XP CD and run fixmbr to clear the master boot record (this is where Lilo or Grub is kept). Windows doesn't boot from the master boot record, it simply boots to the first active partition and loads boot.ini.

Once you do this and boot straight into Windows, simply right click My Computer, select Manage, go to Disk Management, and delete the Linux partitions. Then use those partititions for whatever you want or merge them back into your Windows partition with Acronis Disk Director or Partition Magic.

U gotta go with the 98 disk or i can do it this way?

---

### Post by tturrisi on 2007-06-07
That will work.
What I do is delete the partitions & create a new one in fat32 or ntfs, then do a full format (not a quick format) so all files get removed.  Then I delete the partition again giving a "truer" free space on the disk.

---

### Post by cdewalt on 2007-06-10
I had the same problem on a Dell Dimension when I upgraded from 6.06 to 6.10 then to 7.04.  

I am concerned that my install which ran through the night might not have gone smoothly.  

When I first reboot after installing fiesty eth0 was fine and was able to connect.

next day, eth0 was not able to connect.  

here is my work-around.

I ended up loading a previous version of linux kernel in grub loader (the one before 2.20 i believe) and now i am connecting fine.  but this didnt really solve the problem.

I think my problem was related to an install that did not complete properly.  When i run update manager it seems to be caught in a loop and tries to downloand files 36 of 36 but then it doesnt complete it just goes back to system is up to date.

i plan to do a clean install and if i get same issue again report as bug in fiesty as config issue with ethernet eth0.

---

