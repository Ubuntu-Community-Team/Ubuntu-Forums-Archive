---
title: "Wired network not configured on install (hardy)"
date: 2008-06-13
forum: Networking &amp; Wireless
---

### Post by NastyT23 on 2008-06-13
Ok so Im trying to get my wired connection working on my little sisters desktop pc. When i installed ubuntu, during the network configuration it said it couldn't configure it and asked me if i wanted to manually configure the network myself, i selected no not at this time. when ubuntu loaded up i went to the top of the screen with the 2 little cpu's and clicked on it to see what it would give me for network connections and it gave me these 2 choices:

[I]wired network (unknown usb communications interface)
wired network (hewlett-packard company j2585b hp 10/100vg pci lan adapter)[/I]

Im assuming the second one would be eth0 and my internal ethernet card...
I plug the cable into the card but nothing happens...(im typing this post on my laptop using the same cable)(oh and when xp was on the desktop pc the wired network connection worked fine so i know the hardware is good) I went to eth0 properties and selected automatic configuration (DHCP) hoping that would automatically detect everything but it didn't...and now when i go up top and click on the 2 cpu's for my network options it doesn't show me:
[I]wired network (unknown usb communications interface)
wired network (hewlett-packard company j2585b hp 10/100vg pci lan adapter)[/I]
Instead all it has now is *Wired Network* 

I did a search for a solution but couldn't come up with anything, i could be searching for the wrong thing. But if anyone could help me it would be greatly appreciated.
Thanks

---

### Post by nickdbliss on 2008-06-13
ok give the output of #ifconfig -a

---

### Post by NastyT23 on 2008-06-13
kasha@kasha:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 08:00:09:fa:9f:16  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:9 Base address:0x3000 DMA chan:4 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:632 errors:0 dropped:0 overruns:0 frame:0
          TX packets:632 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:38288 (37.3 KB)  TX bytes:38288 (37.3 KB)

kasha@kasha:~$

---

### Post by nickdbliss on 2008-06-13
Try leaving it to roaming mode and then try to connect.Lemme know if it works that way.

---

### Post by NastyT23 on 2008-06-13
how do i put it back in roaming mode?  It was in roaming mode when i first installed and it wouldn't connect....i don't know how to put it back in roaming mode though.

---

### Post by rlzyoner on 2008-06-13
System -> Administration -> Network -> Wired Connection -> Properties 

Now tick enable roaming mode

---

### Post by NastyT23 on 2008-06-13
okay when i restarted the desktop it was already back in roaming mode....but it still doesn't even show my ethernet card, all it says is wired connection....i still can't connect to the internet.
here's is what *ifconfig -a* tells me now:

[I]kasha@kasha:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 08:00:09:fa:9f:16  
          inet6 addr: fe80::a00:9ff:fefa:9f16/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:393 errors:500 dropped:0 overruns:0 frame:0
          TX packets:6 errors:500 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24708 (24.1 KB)  TX bytes:468 (468.0 B)
          Interrupt:9 Base address:0x3000 DMA chan:4 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:502 errors:0 dropped:0 overruns:0 frame:0
          TX packets:502 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:25100 (24.5 KB)  TX bytes:25100 (24.5 KB)

kasha@kasha:~$ [/I]

---

### Post by NastyT23 on 2008-06-13
can anyone help me?

---

### Post by nickdbliss on 2008-06-14
ok right click on the two monitors or Cpus u see and see if networking is enabled.If not tick to enable it n see if it works. Moreover from the above result u have posted, i can see ur ethernet adapter actually sent n received data.

*RX bytes:24708 (24.1 KB) TX bytes:468 (468.0 B)*

And also try renabling the card.
Code:
#sudo ifconfig eth0 down
#sudo ifconfig eth0 up
again give result of #ifconfig  (without -a). 

Are you having some other external ethernet card too? It might be causing the problem.

---

### Post by NastyT23 on 2008-06-15
When i right clicked on the 2 cpus the enable networking box was already checked. So i ran the commands you asked me to try and still nothing. Here's the results:

[I]kasha@kasha:~$ sudo ifconfig eth0 down
kasha@kasha:~$ sudo ifconfig eth0 up
kasha@kasha:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 08:00:09:fa:9f:16  
          inet6 addr: fe80::a00:9ff:fefa:9f16/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4599 errors:507 dropped:0 overruns:0 frame:0
          TX packets:45 errors:507 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:282646 (276.0 KB)  TX bytes:5797 (5.6 KB)
          Interrupt:9 Base address:0x3000 DMA chan:4 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:590 errors:0 dropped:0 overruns:0 frame:0
          TX packets:590 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:32140 (31.3 KB)  TX bytes:32140 (31.3 KB)

kasha@kasha:~$ 
[/I]

---

### Post by NastyT23 on 2008-06-15
and theres no other external ethernet card...i dont know why it says unknown usb communication interface? After i set my network connections to DHCP, the 2 interfaces aren't even listed when i left click on the 2 cpu's...all it says is wired connection. Even after it being set back to roaming mode. I also unplugged any usb cables in case that was causing any confusion.

---

### Post by nickdbliss on 2008-06-15
Ok give the output of the following. 
#sudo ping [www.google.com](www.google.com) -c 5
#sudo ping 209.85.153.104 -c 5

Also this file
#sudo gedit /etc/network/interfaces.

I am thinking i know what is the problem.

---

### Post by NastyT23 on 2008-06-15
Okay here are the outputs:
[I]
kasha@kasha:~$ sudo ping [www.google.com](www.google.com) -c 5
ping: unknown host [www.google.com](www.google.com)
kasha@kasha:~$ sudo ping 209.85.153.104 -c 5
connect: Network is unreachable
kasha@kasha:~$ sudo ping [www.google.com](www.google.com) -c 5
ping: unknown host [www.google.com](www.google.com)
kasha@kasha:~$ sudo ping [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)
kasha@kasha:~$ sudo ping 209.85.153.104
connect: Network is unreachable
kasha@kasha:~$ sudo gedit /etc/network/interfaces[/I]






[I]
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback[/I]

---

### Post by nickdbliss on 2008-06-15
ok try installing wicd. tell me if that works for you. 
For installing it:
Go to system>Administration>Software Sources - Third party software
Click to add the following one by one

deb [http://apt.wicd.net](http://apt.wicd.net) hardy extras
deb [http://apt.wicd.net](http://apt.wicd.net) hardy all

(i forgot to ask u which version do u have? hardy or gutsy anyways replace hardy with gutsy if u have gutsy.)

Close it and let it reload. After that open synaptic package manager
system>administration>synaptic package manager.

Search for wicd and install it.Once it is done open it from applications>internet>Wicd

Hit refresh and u will see your wireless network. Go to preference and tick to enable Always show wired connection. Hope that will work. If it doesnt or mess up revert back to network manager. For that in synaptic package manager uninstall wicd and install network-manager and network-manager-gnome

---

### Post by NastyT23 on 2008-06-15
how do i install wicd if i cant connect to the net through that desktop?

---

### Post by nickdbliss on 2008-06-15
> **NastyT23 said:**
> how do i install wicd if i cant connect to the net through that desktop?

Before installing wicd i would like u to disable ipv6 and then see if it works,if doesnt then try the following procedure to install wicd and keep ipv6 disabled. Code:

Open file
#sudo gedit /etc/modprobe.d/aliases

find the line:

alias net-pf-10 ipv6

and replace with:

alias net-pf-10 off #ipv6
save and exit. Restart

[I]
INSTALLING WICD[/I]
Ok first go to synaptic package manager and remove the files named:
network manager and network-manager-gnome
And then,
Type the following from the terminal: sudo dpkg -i /path_to_the_package/name_of_the_package_to_install.deb

(Wicd deb file attached)

---

### Post by NastyT23 on 2008-06-16
Alright so i removed network manager and network manager gnome because disabling ipv6 didn't do anything for me.
I installed wicd and after installation i recieved an error: *The NetworkManager applet could not find some required resources. It cannot continue.*

And when i ran wicd, nothing happend, it just says: *No wireless networks found.*

now what? why is this such a headache! Im thinking of just reinstalling xp...

---

### Post by NastyT23 on 2008-06-17
Anyone else have some idea's why it's still not connecting?

---

### Post by nickdbliss on 2008-06-18
That error was for network manager thats ok. Just disable it on startup  by going to Session(under preferences) and startup programs. find it n delete.

ok for wicd. Go to preferences and tick the option which says always show wired interface. It will show the wired connection on the front page and then try clicking connect. Is your router having dhcp enabled?

---

### Post by NastyT23 on 2008-06-18
Okay i ticked that box to always show wired network, and hit refresh. but the connect is like a bluish purple color and doesn't do anything when i click on it...
As for dhcp... i have no idea. When i plug my laptop in through the router it just automatically connects, i was hoping for the same thing with the desktop.

---

### Post by nickdbliss on 2008-06-18
> **NastyT23 said:**
> Okay i ticked that box to always show wired network, and hit refresh. but the connect is like a bluish purple color and doesn't do anything when i click on it...
As for dhcp... i have no idea. When i plug my laptop in through the router it just automatically connects, i was hoping for the same thing with the desktop.

Ok go to terminal and do this
#sudo gedit /etc/network/interfaces

In that file paste this

auto eth0
iface eth0 inet dhcp

save and exit. Restart

That should solve your problem now. Thanks

---

### Post by NastyT23 on 2008-06-19
Okay when i did all that wicd actually allowed me to click the connect button but...it didn't get past the *Obtaining ip address...* step. It says connecting, it tries for about a minute straight then it just says not connected.

---

### Post by nickdbliss on 2008-06-20
> **NastyT23 said:**
> Okay when i did all that wicd actually allowed me to click the connect button but...it didn't get past the *Obtaining ip address...* step. It says connecting, it tries for about a minute straight then it just says not connected.

Seems like ur router doesnt has dhcp enabled. You have to manually give ip address, subnet mask and default gateway etc.

---

