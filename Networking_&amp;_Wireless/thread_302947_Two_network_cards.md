---
title: "Two network cards"
date: 2006-11-19
forum: Networking &amp; Wireless
---

### Post by Bill007 on 2006-11-19
Kia Ora 

I have two network cards 

eth0 for the dhcp

eth1 for networking  

But the default interface is set to eth0 so I cant seem to reach the lan as every thing is defaulting thru thru eth0 how to change or remove the default any suggestions  


Regards

---

### Post by spd106 on 2006-11-19
I don't quite understand the set up, but you can change the default route using **ip route** at a terminal. Add it to your /etc/network/interfaces file after 'post-up' to make it run each time on start-up. Check the man page for details.

---

### Post by Bill007 on 2006-11-19
Kia Ora from Wet New Zealand

I have set up a server for production ubuntu 5.10 base system

after installing all the neccasry packages

One of them being Webmin which I want to configure thru a remote machine

the server has
two network cards

eth0 set for dhcp {working on the net fine}

eth1 for networking (not working)

The default interface is set to eth0 which is working fine

checked it on the command line with the command **route**

How ever I cant seem to reach the lan on eth1 as every thing is defaulting thru thru eth0 (I think)

how to change or remove the default interface so i can reach the lan and router

is it thru the command sudo nano /etc/network/interfaces

and if so what should be written to the file 

any suggestions Confused


Regards
Edit/Delete Message

---

### Post by lloyd_b on 2006-11-19
It would simplify things for us if you would post the following information:

The output of the "ifconfig" command (so we can see what IP's are being given to each card).

The ouput the of "route" command (so we can see what routes are being defined).

I *suspect* you've got a conflict between the routes for eth0 and eth1, but without seeing that information it's tough to define the problem any further.

Lloyd B.

---

### Post by Bill007 on 2006-11-19
Pew What A Mission Typing that

Here are results I dont even see eth1

$ ifconfig

eth0 

Link encap:Ethernet HWaddr 00:14:85:D5:18:6F
inet addr:192.168.1.5 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 :fe80::214:85ff:fed5:186f/64 scope:link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:282 errors:0 dropped:0 overruns:0 frame:0
TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:31713 (38.9 KiB) TX bytes:2430 (2.3 KiB)
Interrupt:23 Base address:0xc400

 
lo
    
Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/126 scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0 KiB) TX bytes:0 (0.0 KiB)

$ route 
Kernel IP routing table
Destination Gateway    Genmask       Flags Metric Ref Use Iface
192.168.1.0 *           255.255.255.0  U      0     0   0  eth0
default     192.168.1.1 0.0.0.0       UG      0     0   0  eth0

Regards Bill

---

### Post by harrysales on 2006-11-19
Just curious as I got an issue with iptables (i think that the -i has no effect in the filter table) but I tried  "ifconfig -a" and i got the what I expected with two network cards.
I will be about for 15 minutes.
I wonder about the contents of your /etc/network/interfaces file.
PS in bash you can high light text with a mouse edit-> copy and paste into anything. See below

        inet addr:xxx.xxx.xxx.xxx  Bcast:xxx.xxx.xxx.xxx  Mask:xxx.xxx.xxx.xxx
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1667 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1120 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:157652 (153.9 KiB)  TX bytes:152211 (148.6 KiB)
          Interrupt:11 Base address:0x2080 Memory:40300000-40300038

eth1      Link encap:Ethernet  HWaddr 
          inet addr:xxx.xxx.xxx.xxx  Bcast:xxx.xxx.xxx.xxx  Mask:xxx.xxx.xxx.xxx.xxx
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:53 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5450 (5.3 KiB)  TX bytes:940 (940.0 b)
          Interrupt:11 Base address:0x2400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by Bill007 on 2006-11-19
I cant copy anywhere as im on another remote machine from my server with no access to the server 

Writting down what i see and typing this stuff is the only way for me

Im running only the base server system system of ubantu on the box


my contents of sudo nano /etc/network/interfaces

auto lo
iface lo inet loopback

mapping hotplug
script grep 
map eth0

#the primary network interface

inface eth0 inet  dhcp


auto eth1
iface eth1 inet static
address 192.168.2.100
netmask 255.255.255.0
network 192.168.2.0
broadcast 192.168.2.255
gateway 192.168.2.1
 

Regards

---

### Post by lloyd_b on 2006-11-19
First off: If "ifconfig" doesn't show eth1, then as far as Ubuntu is concerned it doesn't exist.  This by itself could explain your problem.

Run the following, and note any errors that result:
```

[B]ifdown eth1
ifup eth1
[/B]
```
Most likely you'll get a "doesn't exist" type error on the first.  The error from the second one is what I'm interested in.

Another question:  Two network cards - both PCI (inside the computer)?  If so, run the command
```
**[FONT="Arial"]lspci -v [/FONT]**
```

(don't try to post all of it unless you want to stress-test your keyboard and/or fingers - just look for the entries that mention "Ethernet").  I just want to make sure that your computer knows it has two network cards, and what type it thinks they are. 

Final note: Do NOT add a gateway command on eth1 unless you actually have a gateway (router) at 192.168.2.1.  DHCP will set a default route for eth0, and this command may very well reset it for eth1 (if and when eth1 is recognized).  This would result in the opposite of what you have now - everything going via eth1, when you want *most* of it to go via eth0. A gateway command is only needed if you want to connect to networks outside of 192.168.2.x via that network card. 

Lloyd B.

---

### Post by Bill007 on 2006-11-19
Here it is could nt help my self
 
all so I have an onboard network card eth0
and one PCI network card eth1
[B]
ifdown eth1[/B]
Failed to open stat interface eth1 not configured

**ifup eth1**
error while getting interface flags nosuch device
SIOCIFNETMASK No such device
192.168.2.255 Uknown Host

Failed to bring up device
[B]
lspci -v[/B] 

0000: 00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge 
flags:fast devsel
capabilities: <available only to root>

0000: 00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge 
flags:fast devsel

0000: 00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge 
flags:fast devsel

0000: 00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge 
flags:fast devsel

0000:01:00.0 VGA Compatable controller :via Technologies, Inc :: Unknowen dvice 3 108 (rev 01(prog if 00 [VGA])
Sub system:Giga-byte Technology:device unknowen d000
flags:bus master, 66MHZ, medium devsel,latency 32 IRQ 10
memory at e4000000 (32-bit prefetchable)[size=64M]
memory at e8000000 (32-bit non prefetchable)[size=16M]
capabilities:<available only to root>

Bill

---

### Post by lloyd_b on 2006-11-20
First off, the "ifdown/ifup" commands should have been run with "sudo" - my goof.  But the results are pretty much what I expected - it appears that no device driver is being loaded for eth1.

The "lspci" output does not list ANY ethernet controllers, which is weird.  Exactly what type of machine is that?  Could the "onboard" ethernet actually be connected via USB or something? (unusual in a desktop system, but not impossible).

What type of ethernet card did you install for eth1?  We need to identify the card type, and get a driver loaded for it.  At that point, eth1 should become available.   

Here's another command (with a ton of output, of course :-))

```
sudo lshw
```

This will list all detected hardware, regardless of whether it's PCI or not.  Hopefully both ethernet devices will be listed here.

Lloyd B.

---

### Post by trubblemaker on 2006-11-20
yeah, dmesg would also be helpful.  funny I don't see an auto eth0 in your interfaces file but it's loading and eth1 isn't.  I don't see Ethernet controllers in your lspci, but those 'bridges' listed might be ethernet controllers.  I got to say you outputs got me scrachting my head.

---

### Post by Bill007 on 2006-11-20
Good Morning from New Zealand
and thank you so much for your help

I did use sudo **ifdown/up eth1 **

**Computor**

AMD Sempron SOCKET 754 PROCESSOR MOTHERBOARD its a new box not super grunty but should be up to spec for production server duties
On board Fast ethernet Lan VIA 6103L chip (10/100 Mbit IRJ 45 PORT)

PCI NETWORK CARD IS Realtek RTL8169S-32 Chipset

After entering **sudo lshw** there is a ton of info but can't scroll to see all that is there from the command line how can see all this info

---

### Post by Bill007 on 2006-11-20
One would now think that I have know drivers for the network card

I guess what I now need to know is where to install the network card Drivers once i have them

What directory do unzip the drivers into 

I havnt found the drivers yet but should nt be too hard to find them on line I do have a disk but dont how to do this method

---

### Post by lloyd_b on 2006-11-20
> After entering sudo lshw there is a ton of info but can't scroll to see all that is there from the command line how can see all this info

Two choices:

```
sudo lshw | more
```

will display the info one page at a time (that "|" character is the "pipe" symbol - on most keyboards <SHIFT><BACKSLASH>.  <BACKSLASH> is usually right above the <ENTER> key).

Second option:

```
sudo lshw > hw.txt
```

Will create a file in the current directory called "hw.txt", which you can view/edit via the editor of your choice ("vi", "nano", "gedit", etc.).

Another command:
```

sudo modprobe -v r1000
```

I believe that "r1000" is the correct module for the Realtek card, so this should install the driver for that card.  If the module loads without errors, you should be able to run "sudo ifup eth1" without getting errors.

If this works, edit the file "/etc/modules" (with "vi", "nano", whatever) and add a line that reads "r1000".  This file contains a list of modules to  automatically load when the system restarts.

Lloyd B.

---

### Post by lloyd_b on 2006-11-20
> One would now think that I have know drivers for the network card

I guess what I now need to know is where to install the network card Drivers once i have them

What directory do unzip the drivers into

I havnt found the drivers yet but should nt be too hard to find them on line I do have a disk but dont how to do this method

Looks like we were both posting at the same time :-)

You shouldn't need to download any drivers for that card.  A standard install should have already put them on your machine.  It's just a matter of telling the system to actually LOAD the driver.  My previous post (with the "modprobe") command contains the instructions for doing this.

Lloyd B.

---

### Post by Bill007 on 2006-11-20
"UUGH"

**sudo modprobe -v r1000**

FATAL: module r1000 not found

I was getting excited about that I guess that module is not there

---

### Post by lloyd_b on 2006-11-20
> UUGH"

sudo modprobe -v r1000

FATAL: module r1000 not found

I was getting excited about that I guess that module is not there

Ouch.  I read back through the thread, and realized that you're using a fairly old verions of Ubuntu.  Which means that there may not BE drivers for that card with that version.

The "r1000" driver appears to be a fairly recent addition to the Linux kernel (as of Feb 2006).

Any chance of switching to a more recent version of Ubuntu?  Edgy (6.10) definitely has the support for that card, and I suspect Dapper (6.06) does as well (could somebody running Dapper confirm that the "r1000.ko" module exists in that release?).

At least we've identified the problem.  That counts as progress (though I'm sure you'd rather have the problem *solved* than *identified*).

FYI: Drivers *are* available from the manufacturer's website, but they have to be compiled.  That means installing a lot of other things onto that machine just to be able to compile the driver....

Lloyd B.

---

### Post by trubblemaker on 2006-11-20
upside to upgrade is that it should be minimal work for you. Server install is really quick and it would have all the modules pre-installed. Not pushing it on you put happen to have the [link to the server-disk right here.]("http://us.releases.ubuntu.com/6.10/ubuntu-6.10-server-i386.iso")

course an upgrade is also possible, also you could hunt out some old docs on getting your driver up and running as I'm sure people have already battled that battle. it helps that you already know the driver.

---

### Post by Bill007 on 2006-11-20
Iwould love to Now

I had a funny feeling about ubuntu 5.10 I had it lying around and thought I would give it a go

whats the best way to get the latest

Ive tried down loading the latest lamp server but for the life of me cant get the cd to boot once burnt 

Ive extracted the files from the iso but still no go maybe i should get a cd posted   

Suggetions  

Bill

---

### Post by Bill007 on 2006-11-20
Im a little frustrated On the ISO IMAGE as i have not been able to get the extracted files to boot on start up

and no i have not just burnt the image on to disk

whats the trick here  

ISO Frustration

Oh and thanks sooooo much  trubblemaker and lloyd_b i have learnt so much with  your advice much appreciated

LOVE THAT LEARNING CURVE

[NEW PLYMOUTH MOTEL]("http://newplymouthmotel.co.nz")

---

### Post by trubblemaker on 2006-11-20
check your bios settings, when the computer is 'just' started, you'll see press F10 or 'del' to go into bios, it's only on the screen for 2 seconds just after powering on. then look for boot order make sure it's selected to boot from cdrom first.

It does occur to me that you installed 5.10 so you should be able to boot.... Is it comeing up at all or just boots into normal ubuntu?

---

### Post by Bill007 on 2006-11-21
Hey you Guys I sorted that problem with the ISO Image i was burning it wrong :-? 

And the best advice given I have to say was to upgrade to 6.10 server, lamp and all yehaaaaa saved a lot of configuring

I have located both cards now so thats  a great advance thought I was going insane on that one but learnt a hell of lot 

you are the best  trubblemaker lloyd B thank you 

I still have a ways to go but thats one hurdle jumped

 I know its not the right forum but whats your advice on webmin

I feel I need some user friendly interface to lessen the steepness of the command line learning curve

Stoked Bill007:p :p :p

---

### Post by Bill007 on 2006-11-21
My Results from command

**sudo ifconfig |more**


eth0 

Link encap:Ethernet HWaddr 00:E0:4C:E9:39:F7
inet addr:192.168.1.5 Bcast:192.168.1.255 Mask:255.255.255.0
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:24 errors:0 dropped:0 overruns:0 frame:0
TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:3365 (3.2 KiB) TX bytes:1026 (1.0 KiB)
Interrupt:185 Base address:0xa000

 

eth1 

Link encap:Ethernet HWaddr 00:14:85:D5:18:6F
inet addr:192.168.2.5 Bcast:192.168.2.255 Mask:255.255.255.0
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:36 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:4425 (4.3 KiB) TX bytes:0 (0.0 B)
Interrupt:193 Base address:0xc400


lo
    
Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0 KiB) TX bytes:0 (0.0 KiB)

so now I have this working or at least configured

Webmin says go [http://production:10000/](http://production:10000/)

so I go to a remote machine and try to put in this new address so I can configure webmin 

you guessed nothing "Gotta laugh at this point"

cant ping from a remote machine or see the server in any way

Any Ideas:confused:

---

### Post by trubblemaker on 2006-11-21
not sure, but you have to type [http://production:10000/](http://production:10000/) from the machine (your server) that has that installed on it. it won't work from the other machines.  

You probably forgot to install something that will respond.  Remeber this ain't no windows box.  THe server is probably locked down.

why don't you try installing open-ssh on the computer then you can command line into it with ssh <ip> although I know you don't like commandline.  first setup from the server with [http://production:10000/](http://production:10000/) then after you can probably do it remotely.

---

### Post by Bill007 on 2006-11-21
to set up the server with
[http://production:10000/](http://production:10000/)
 
is this the command

**wget [http://production:10000/](http://production:10000/)**

I since 
have installed 

ssh 
synaptic 
webmin

on the server 


and have putty on this windows Machine

Im of with command line Im just new to it and dont zip on the commands allthough im learning fast Thanks to you guys  

Just found a book on setting up a linix server using apache from sitepoint

Ill be back tomorrow its been a big day going around and around around and around

cheers guys for sticking it out this is probably a useful thread for others as well

Over and untill tomorrow

PS do you guys not sleep either

---

