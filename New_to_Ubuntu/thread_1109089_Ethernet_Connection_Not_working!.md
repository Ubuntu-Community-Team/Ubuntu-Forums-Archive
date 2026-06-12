---
title: "Ethernet Connection Not working!"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by ehderube on 2009-03-28
Hi,

First off let me say I am fairly new to linux and am not really familar with the way things are organized and am not really interested in recompiling the kernel etc.. I am more interested in seeing if Ubuntu can be used as a viable alternative to Windows.

Ok, I installed Ubuntu 8.10, dual boot with Windows XP, Ubuntu loads fine and even indicates that I have connected to the wired connection but I can not access the internet. I have an onboard ethernet connection its a:

NVIDIA nForce MCP Networking Adapter

Searching on the web I found this:

[http://manpages.ubuntu.com/manpages/intrepid/en/man4/nve.4freebsd.html]("http://manpages.ubuntu.com/manpages/intrepid/en/man4/nve.4freebsd.html")

Does anyone know if this driver is already part of 8.10? I think the driver that is currently loaded is just the default one for nvidia products. If I'm suppose to install this driver can someone in very simple terms explain how to do this or if there's another reason for the problem could you let me know?

I have posted this in the networking section but got no responses, I'm hoping someone can help me out other wise I'm stuck with windows!

Thanks,
Ed

---

### Post by Bucky Ball on 2009-03-28
If it is letting you know you are connected, you are connected ... to the network (lan, not wan obviously). Drivers are installed already for ethernet, nothing additional required. I would say this is happening at the router end perhaps? What is your setup?

---

### Post by SuperSonic4 on 2009-03-28
Mine is ```
Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
``` and mine worked out of the box. I assume the internet is otherwise up and there is no physical reason why it should not work (cable slipped out for example)

This was filed as a bug here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/136836](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/136836)

---

### Post by Delta28 on 2009-03-28
Hey make sure its not just your cable in your computer :P

EDIT: You guys keep beating me lolz

---

### Post by ehderube on 2009-03-28
Hi,

Thanks for getting back to me, answers to your questions:
[LIST]
[*]Yes the cable is plugged in and internet is working fine because I am using it now in XP
[*]I tried that bug fix in the link you provided, after I ran the commands it said "Ignoring unknown interface eth0=eth0" but the network manager showed the connection as back up and running.  When I tried firefox it didn't load
[*]My setup is rather simple I'm connected to an ADSL bridge / router which connects via the phone line to my ISP.  I checked the sudo ifconfig against the numbers in windows (i.e. mapped IP addresses) and its all the same so it must be communicated with the router.
[/LIST]

Any other advice? 

Is it possible that the firewall in ubuntu has completed blocked me out?  How can you tell if the firewall is loaded because I don't think it is?

---

### Post by berksted on 2009-03-28
Have your tried to ping the router? If you get a response then you know your network card is working. At that point, it might be something with the router. Also try a ping a web server - like ubuntu.com and see what happens.

I don't believe there is a firewall loaded from the initial installation, so that's probably not the problem.

---

### Post by ehderube on 2009-03-28
Ok, so I tried
ethtool eth0 -> ethtool not installed....

route -> no gateway present

ping -c 4 [www.google.com](www.google.com) -> unknown host (i think i forgot to write it down)

Any ideas?

---

### Post by m3bik on 2009-03-28
Try

```
sudo ifconfig
```

If you can post the results, that might help us help you?

---

### Post by ehderube on 2009-03-28
Here are the results of ifconfig eth0, by the way the formatting might not be the same as the terminal screen
 
```
edward@edward-desktop:~$ sudo ifconfig eth0
eth0      Link encap:Ethernet  HWaddr  
inet addr:120.111.111.143  Bcast:111.111.111.111  Mask:255.255.255.128
inet6 addr: 1 Scope:Link
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
RX packets:9 errors:0 dropped:0 overruns:0 frame:0
TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:1305 (1.3 KB)  TX bytes:6078 (6.0 KB)
Interrupt:22 Base address:0xe000 
```

---

### Post by berksted on 2009-03-28
Please post the results for 



```
lspci -v 
```

as well.

---

### Post by ehderube on 2009-03-28
I have a modem PCI card but it isn't connected to anything.


[CODE]00:00.0 Host bridge: nVidia Corporation nForce2 IGP2 (rev c1)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 0 (rev c1)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) (prog-if 10)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) (prog-if 10)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) (prog-if 20)
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2) (prog-if 8a [Master SecP PriP])
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
01:07.0 Multimedia audio controller: Creative Labs SB Audigy LS
01:09.0 Communication controller: Conexant Systems, Inc. Device 2f10 (rev 01)
02:00.0 VGA compatible controller: nVidia Corporation NV36.2 [GeForce FX 5700] (rev a1)

---

### Post by m3bik on 2009-03-28
Ok, hang on... If it was connected to a local network, shouldn't the IP be a local IP? 

The reason I ask is because I've actually had one of my computers acquire an odd IP addresses not associated with my lan... Therefore, the computer couldn't navigate through my local network correctly... And thus, no internet. I changed a few settings and got it working, but I'm not sure if that's the case here....

---

### Post by ehderube on 2009-03-28
I don't have a local network (at least I think), I am only connected to the ADSL bridge / router (thats the name the manufacturer of the unit uses) supplied by my ISP.

---

### Post by m3bik on 2009-03-28
Ok, so that should be fine then. With DSL routers that only have one computer attached often just give the computer the internet IP instead of a local ip. So that shouldn't be part of the problem...

---

### Post by berksted on 2009-03-29
For whatever reason it looks like there is no communication with the DSL modem. I would first just try to restart the modem. 

You are directly connected to the modem, no router or switch? 

Then maybe you can try to follow the setup instructions in:

[https://help.ubuntu.com/community/ADSLPPPoE]("https://help.ubuntu.com/community/ADSLPPPoE")



:?

---

### Post by ehderube on 2009-03-29
Tried that link, ran PPPoE and it scanned my system and gave an error related to not being able to find PPPoE device or connection point (sorry I forgot to copy the error message)

if I unplug / plug the ethernet cable from the modem / router it is picked up in the Network Manager so I think this must be some type of setting problem.

---

### Post by ehderube on 2009-03-29
I don't really know why I can't connect to the internet, I  ran sudo dhclient eth0 and it seems that its picking up a DHCP address, it appears that I can communicate with my router / modem (network manager knows it there) but for so reason it won't allow external commication.  I checked the /etc/network/interfaces file it only had information related to the loopback and nothing else.

Anyone have any ideas?  Ubuntu's great but without internet I think I'm going to dump it.


Ed

---

### Post by ehderube on 2009-04-02
Well,

For who ever comes across this page, I figured out the problem.  For some reason whatever program auto generates the /etc/network/interfaces did not have anything related to my eth0 connection.  Since I am using a dhcp client and not static IP  I decided to add the following:

auto eth0
iface eth0 inet dhcp

I saved the file and started the network up again and it worked!  As a side note I did switch from Network Manager to Wicd Manager so that may have an effect as well (Wicd didn't work either until I added the those two lines).

Regards,
Ed

---

### Post by fr0gg on 2009-04-15
Hey ehderube, I'm trying to troubleshoot why my ethernet connection isn't working as well, and was trying to take your advice that got yours going..however, I am a Linux novice and am not sure how to add those lines (wouldn't let me directly, and for some reason using sudo echo "line of code" >> fileName denies me permission as well)..any tips, I'm sure it's something simple, but I'm in the learning curve here heh.
Thank you.

---

### Post by fr0gg on 2009-04-20
Can anyone offer some insight into my problem, I still haven't resolved it and I'm at a loss.
Thank you!

---

### Post by Bucky Ball on 2009-04-20
```
sudo nano /etc/network/interfaces

```
That will get you to the file and you can add the lines, press ctl/X to save.

Log out or restart and see how you go.

---

### Post by ehderube on 2009-04-20
Hey frogg,

If you are not familiar with the terminal and command line as bucky ball has suggested (which works fine) you can try the "windows" method.

1. Go to the task bar at the top of your desktop, find the network connection icon right click and select quit.
2. Go to the task bar at the top of your desktop, select Places
3. Select Home Folder
4. A file browser should open, there is an up arrow button (Open the parent folder) press it twice to see the etc folder, double click the etc folder
5. Double click the network folder
6. You should now see a file called interfaces, double click on it.
7. copy these lines and paste into your file, do not delete anything in the file just paste below existing stuff:

auto eth0
iface eth0 inet dhcp

8. Save and close file.
9. Go to the task bar at the top of your desktop and select Application, Internet and your network manager (I am using Wicd Network Manager) to start it up.

I hope this helps, also I'm sorry if this seems like a dumb down version of what Bucky has stated but I'm not that familiar with the command line and prefer the visual interface to the command line.  Let me know if it works for you.

---

### Post by fr0gg on 2009-04-20
Thank you for the replies, though the reason I was asking about the command line method was because initially, when I couldn't figure it out, I tried the gui direct approach, basically what you wrote ehderube, but it said I didn't have permissions? So thank you bucky for showing me nano. Anyway, using sudo nano I've added those two lines to the file, saved, logged off and back on..still no connection. Any suggestions?
Cheers.

---

### Post by poundjd on 2009-04-20
> **ehderube said:**
> Here are the results of ifconfig eth0, by the way the formatting might not be the same as the terminal screen
 
```
edward@edward-desktop:~$ sudo ifconfig eth0
eth0      Link encap:Ethernet  HWaddr  
inet addr:120.111.111.143  Bcast:111.111.111.111  Mask:255.255.255.128
inet6 addr: 1 Scope:Link
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
RX packets:9 errors:0 dropped:0 overruns:0 frame:0
TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:1305 (1.3 KB)  TX bytes:6078 (6.0 KB)
Interrupt:22 Base address:0xe000 
```
I have one quick question, in hte second line where it says:
```
inet addr:120.111.111.143  Bcast:111.111.111.111 ....
```
is it possible that one of the two address' were retyped wrong?  the first three numbers really should be the same.

Also you don't seam to have a gateway defined on the ubuntu box. check you windows internet connection and see if it has entries for Router or Gateway, and one or more DNS servers.  copy these down and get them entered into the ubuntu box. (sorry but I know where right now)  but try this before you do anything funkey with the kernel or drivers. it may help, and at worst will cause no problem.
-jeff

---

### Post by fr0gg on 2009-04-20
Pound, I believe ehderube got his connection up and running, right mate? Adding the two lines of code to the interface file seemed to do the trick for him, but unfortunately, that's not the case for me..running ifconfig yields the below results.
```
eth0      Link encap:Ethernet  HWaddr 00:1a:92:7d:4d:b5  
          inet6 addr: fe80::21a:92ff:fe7d:4db5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:1 dropped:0 overruns:0 frame:1
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:3952 (3.9 KB)
          Interrupt:215 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 00:1a:92:7d:63:4c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:216 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:258 errors:0 dropped:0 overruns:0 frame:0
          TX packets:258 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16144 (16.1 KB)  TX bytes:16144 (16.1 KB)

```
It appears to be assigning a mac address in place of my ip address possibly? I have everything set to configure and obtain automatically as of now. I'm not sure what's going on, anyone?
Cheers.

---

### Post by ehderube on 2009-04-21
Hey Frogg,

Yes my Internet is working.  I just checked and for some reason unknown to me the default network manager does not work for my setup (I am assuming you have the same network card and are connected via a DSL router / modem?)  you have to also change the network manager to something else I only tried WICD and it worked.

With my problem I was able to get an IP, broadcast and mask it just didn't want to connect (to answer poundid I change my IP and MAC address because I was a little worried about providing too much information).  Can you get a IP address, I would assume you could since you have an IPv6 address but I'm not an expert.

---

### Post by fr0gg on 2009-04-22
I've just installed the wicd package (after removing the network manager package), and now when I try to connect to the "wired network" it detects, it times out trying to obtain an IP address, so to answer your question, I guess i'm not getting and IP address..how should i troubleshoot that?

---

### Post by ehderube on 2009-04-22
frogg,

Are you dual booting?  If so can you connect to the internet in windows?

Do you know if you are using a static IP or dhcp?  If you have a static IP try this: 
[http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html]("http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html")

you can try "sudo dhclient" to see if you can connect to any dhcp servers

---

### Post by fr0gg on 2009-04-22
I am dual booting XP and Ubuntu..and I have a static IP in XP currently, so I followed the directions in that tutorial and:
Find and remove dhcp entry:
```
iface eth0 inet dhcp

```
and then..
Append new network settings:
```

iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.254

```
but the next step, for adding the nameservers (i think) to the /etc/resolv.conf file, nano opens up a brand new file (implying there is no existing file to edit, right)..I'm having trouble finding what i should actually have in this file, would you mind running yours and showing me?
Thank you!

EDIT: hmm intersting wicd is showing i'm connected at 1% (IP:0) now? I'm pretty sure if i get that resolv.conf properly set up i would be getting an IP, any hints?

---

### Post by nandemonai on 2009-04-22
> **fr0gg said:**
> I am dual booting XP and Ubuntu..and I have a static IP in XP currently, so I followed the directions in that tutorial and:
Find and remove dhcp entry:
```
iface eth0 inet dhcp

```
and then..
Append new network settings:
```

iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.254

```
but the next step, for adding the nameservers (i think) to the /etc/resolv.conf file, nano opens up a brand new file (implying there is no existing file to edit, right)..I'm having trouble finding what i should actually have in this file, would you mind running yours and showing me?
Thank you!

EDIT: hmm intersting wicd is showing i'm connected at 1% (IP:0) now? I'm pretty sure if i get that resolv.conf properly set up i would be getting an IP, any hints?

Boot back into Windows and 'Start -> run -> cmd'

Once in the windows 'terminal' type:

```
ipconfig /all
```

This should list all the IP settings including your DNS server(s).

Copy the DNS server(s) down somewhere and then boot back into Ubuntu and edit your /etc/resolv.conf file like so:

```
nameserver xxx.xxx.xxx.xxx
```

xxx.xxx.xxx.xxx being the IP address. If more than one (there is usually a primary and secondary) just add two lines.

```
nameserver xxx.xxx.xxx.xxx
nameserver xxx.xxx.xxx.xxx
```

---

### Post by fr0gg on 2009-04-22
Alright, so I'm only adding the two DNS servers then, nothing else? I tried just this, and then configured the custom settings(static IP) for the wired connection in wicd, and it says connected! But..it won't load a site..
I have a few questions, just to make sure I entered the right information in the /etc/network/interfaces file.
First of all, from the turotial, in 
Append new network settings:
```

iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.254

```
what do the network and broadcast addresses refer to, right now i just have my network set as my router's ip (192.168.1.1) and my broadcast set as my static IP. I'm not sure this is correct. Also, I should still have the following lines of code at the start of my file, right?
```
auto lo
iface lo inet loopback
auto eth0

```
Thanks for the help guys..I've not gotten the internet working on ubuntu and it's frustrating me.

---

### Post by alphacrucis2 on 2009-04-22
> **fr0gg said:**
> Alright, so I'm only adding the two DNS servers then, nothing else? I tried just this, and then configured the custom settings(static IP) for the wired connection in wicd, and it says connected! But..it won't load a site..
I have a few questions, just to make sure I entered the right information in the /etc/network/interfaces file.
First of all, from the turotial, in 
Append new network settings:
```

iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.254

```
what do the network and broadcast addresses refer to, right now i just have my network set as my router's ip (192.168.1.1) and my broadcast set as my static IP. I'm not sure this is correct. Also, I should still have the following lines of code at the start of my file, right?
```
auto lo
iface lo inet loopback
auto eth0

```
Thanks for the help guys..I've not gotten the internet working on ubuntu and it's frustrating me.

The network address defines the starting address of the local subnet. You can't assign the network address itself to a host. The network address combined with the netmask define the range of addresses belonging to the subnet. In this case the network has a 24 bit mask (255.255.255.0) which means the subnet range is
192.168.1.0 - 192.168.1.255. The last address is reserved as a broadcast address and can't be assigned to a host, so hosts have to be in the range 192.168.1.1 - 192.168.1.254. Hosts in that subnet range that are physically connected can all talk to each other directly without needing a router. The default gateway is the address of a router on the subnet that knows how to get to other subnets that aren't explicitly specified (such as the internet :)). 


You can do all this through the network manager gui. Right click on the NM icon somewhere on the right hand end of the bar at the top of the screen. Select Edit Connections. It will probably list one connection "Auto eth0". Select it and click edit. It will ask for the admin password. Click the IPv4 Settings tab. To enter a static address, change the method to manual and add your static address mask and default gateway and DNS server ip's.

---

### Post by fr0gg on 2009-04-22
Ok cool, that kind of clears things up..
so the default gateway shouldn't be the address of my router-192.168.1.1, it should be the upper limit of what the host can assign? I have wicd, because ehderube said that after editing the files, he had to use wicd rather than NM to get connected..but i've still configured it manually, to where it says it's connected but i'm not getting anything.

---

### Post by alphacrucis2 on 2009-04-22
> **fr0gg said:**
> Ok cool, that kind of clears things up..
so the default gateway shouldn't be the address of my router-192.168.1.1, it should be the upper limit of what the host can assign? I have wicd, because ehderube said that after editing the files, he had to use wicd rather than NM to get connected..but i've still configured it manually, to where it says it's connected but i'm not getting anything.

The default gateway should indeed be the address of the router.

---

### Post by nandemonai on 2009-04-23
> **fr0gg said:**
> Alright, so I'm only adding the two DNS servers then, nothing else? I tried just this, and then configured the custom settings(static IP) for the wired connection in wicd, and it says connected! But..it won't load a site..
I have a few questions, just to make sure I entered the right information in the /etc/network/interfaces file.
First of all, from the turotial, in 
Append new network settings:
```

iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.254

```
what do the network and broadcast addresses refer to, right now i just have my network set as my router's ip (192.168.1.1) and my broadcast set as my static IP. I'm not sure this is correct. Also, I should still have the following lines of code at the start of my file, right?
```
auto lo
iface lo inet loopback
auto eth0

```
Thanks for the help guys..I've not gotten the internet working on ubuntu and it's frustrating me.

I'm not familiar with wicd myself and am hoping it's not rewriting your file or disabling it like network manager in 8.10 tends to.

That said I'll try my best to explain as this really seems like incorrect configuration.

Here is an example of my servers /etc/network/interfaces files I'll use to explain with.

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 10.1.1.15
        netmask 255.255.255.0
        network 10.1.1.0
        broadcast 10.1.1.255
        gateway 10.1.1.254
```

Now in my example the auto lo section (which is mandatory you must have it) is the loopback device. It's a virtual local only networking thing. Without going into great detail you need it and it will always be the same as above so you can safely copy and paste that section.

Now as for eth0.

```
auto eth0
iface eth0 inet static
```

The auto bit tells the system to automatically bring the interface up. The static bit tells the system to manually set the IP settings and not use the DHCP protocol to try and automatically aquire an IP address.

This bit you can also copy and paste.

```
  
address 10.1.1.15
netmask 255.255.255.0
network 10.1.1.0
broadcast 10.1.1.255
gateway 10.1.1.254
```

Here is where you're getting confused.

address = the IP address you want for your machine. It has to be one on your local range and not in use by another machine. Based on your posts the address you're using should be fine as long as no other system is using it.

netmask = the subnet. I'm not going to attempt to explain what a subnet is because it's just going to confuse you. Ultimately subnets are used to segregate networks. The setting 255.255.255.0 is fine for your purposes.

network = is exactly that. The network address. It ties in with the subnet but assuming the settings you're using and the address of your router then your network address would be 192.168.1.0.

broadcast = is essentially the address that ALL machines on the local network use to do exactly what it sounds like, broadcast stuff. 'Where is X machine?' That kind of thing.
192.168.1.255 is fine in your case.

gateway = the device by which the system tries to access stuff outside your local network. Ala a router. So your router address of 192.168.1.1 must go here for you to get outside access.

Save the file then check your /etc/resolv.conf

```
nameserver 192.231.203.132
nameserver 192.231.203.3

```

As you can see from my example I've used the IP address of the 2 DNS servers that my ISP runs.

Provided your Windows machine can browse the net fine, using the addresses from windows via the instructions from my previous post should be fine.

You could use your router address in most cases as most of them will forward the DNS request to the DNS server within it's own tables but for the sake of getting you online just copy the ones from your Windows install. If it turns out one of them was your router address don't worry that's in some cases normal. (Just thought I'd explain that just in case because it can be confusing)

DNS essentially converts names like google.com to IP addresses.

Now, once you have edited both files and saved them, within terminal do this:

```
sudo ifdown eth0 && ifup eth0
```

This will take the network down then bring it up again with the fresh settings.

If you still cannot browse the Internet please try a few tests for me.

From terminal:

```
ifconfig -a
```
```
route
```

Then paste the results.

```
ping 192.168.1.1 -c 3
```

```
ping 91.189.94.156 -c 3
```

```
ping ubuntu.com -c 3
```

Then paste the results.

---

### Post by ehderube on 2009-04-23
frogg,

I switched to wicd because as nandemonai eluded to the default network manager can do some weird things at least with my configuration (8.10, nforce MCP integrated NIC) I couldn't get it to work.  Also I use the atuo dhcp client and get assigned an IP which is different than your setup.

To be honest with you your problem is completely different than my problem  was (although you could argue that they are the same incorrect configuration) so I don't think any thing in my original post will help you but it seems that nandemonai knows his stuff and should lead you down the right path.

So what I'm getting at is maybe wicd isn't right for you and maybe the default network manager would be OK or maybe it won't matter once you get the configuration correct. Only trial and error will tell you.

---

### Post by fr0gg on 2009-04-23
Alright, yea I also considered what you wrote ehderube, but thought trying a different connection manager might be useful, thanks though.

nandemonai, thanks for the clarification, the only thing i had different was my network, which when changed still didn't solve my issue.
when i run  sudo ifdown eth0, not sure why, but it tells me
RTNETLINK answers: No such process
SIOCDELRT: No such process
ifup says eth0 has already been configured..

here is the output for the commands you suggested:
```
$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1a:92:7d:4d:b5  
          inet addr:192.168.1.121  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:92ff:fe7d:4db5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:1 dropped:0 overruns:0 frame:1
          TX packets:0 errors:0 dropped:12 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:4076 (4.0 KB)
          Interrupt:216 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 00:1a:92:7d:63:4c  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:179 errors:0 dropped:0 overruns:0 frame:0
          TX packets:179 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12864 (12.8 KB)  TX bytes:12864 (12.8 KB)

pan0      Link encap:Ethernet  HWaddr ce:28:dc:bb:2b:ed  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0

$ ping 192.168.1.1 -c 3
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.121 icmp_seq=1 Destination Host Unreachable
From 192.168.1.121 icmp_seq=2 Destination Host Unreachable
From 192.168.1.121 icmp_seq=3 Destination Host Unreachable

$ ping 91.189.156 -c 3
PING 91.189.156 (91.189.0.156) 56(84) bytes of data.
From 192.168.1.121 icmp_seq=1 Destination Host Unreachable
From 192.168.1.121 icmp_seq=2 Destination Host Unreachable
From 192.168.1.121 icmp_seq=3 Destination Host Unreachable

--- 91.189.156 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2013ms
, pipe 3


```
thanks for your patience and help by the way mate!

---

### Post by nandemonai on 2009-04-23
> **fr0gg said:**
> Alright, yea I also considered what you wrote ehderube, but thought trying a different connection manager might be useful, thanks though.

nandemonai, thanks for the clarification, the only thing i had different was my network, which when changed still didn't solve my issue.
when i run  sudo ifdown eth0, not sure why, but it tells me
RTNETLINK answers: No such process
SIOCDELRT: No such process
ifup says eth0 has already been configured..

here is the output for the commands you suggested:
```
$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1a:92:7d:4d:b5  
          inet addr:192.168.1.121  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:92ff:fe7d:4db5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:1 dropped:0 overruns:0 frame:1
          TX packets:0 errors:0 dropped:12 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:4076 (4.0 KB)
          Interrupt:216 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 00:1a:92:7d:63:4c  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:179 errors:0 dropped:0 overruns:0 frame:0
          TX packets:179 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12864 (12.8 KB)  TX bytes:12864 (12.8 KB)

pan0      Link encap:Ethernet  HWaddr ce:28:dc:bb:2b:ed  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0

$ ping 192.168.1.1 -c 3
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.121 icmp_seq=1 Destination Host Unreachable
From 192.168.1.121 icmp_seq=2 Destination Host Unreachable
From 192.168.1.121 icmp_seq=3 Destination Host Unreachable

$ ping 91.189.156 -c 3
PING 91.189.156 (91.189.0.156) 56(84) bytes of data.
From 192.168.1.121 icmp_seq=1 Destination Host Unreachable
From 192.168.1.121 icmp_seq=2 Destination Host Unreachable
From 192.168.1.121 icmp_seq=3 Destination Host Unreachable

--- 91.189.156 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2013ms
, pipe 3


```
thanks for your patience and help by the way mate!

Hmm, this isn't hopeful. You can't seem to access your router.

Can you please post your updated /etc/network/interfaces and /etc/resolv.conf files again please?

The only other thing I'm thinking is that perhaps you actually have the cable attached to eth1 rather than eth0 as I just noticed you have two interfaces, ie two network cards / ports.

---

### Post by alphacrucis2 on 2009-04-23
[QUOTE=fr0gg;7131058]Alright, yea I also considered what you wrote ehderube, but thought trying a different connection manager might be useful, thanks though.

nandemonai, thanks for the clarification, the only thing i had different was my network, which when changed still didn't solve my issue.
when i run  sudo ifdown eth0, not sure why, but it tells me
RTNETLINK answers: No such process
SIOCDELRT: No such process
ifup says eth0 has already been configured..

here is the output for the commands you suggested:
```


$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
```

That is telling you that you don't have a gateway. If the gateway was set up, there should be another line something like:

```
default     192.168.1.1      0.0.0.0          UG    0     0      0 eth0
```

```
$ ping 192.168.1.1 -c 3
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.121 icmp_seq=1 Destination Host Unreachable
From 192.168.1.121 icmp_seq=2 Destination Host Unreachable
From 192.168.1.121 icmp_seq=3 Destination Host Unreachable
```

A bad sign. Do the above ping again and then immediately type:

```
arp
```

Post output.

---

### Post by alphacrucis2 on 2009-04-23
I forgot. Post output of 


> sudo ethtool eth0

---

### Post by fr0gg on 2009-04-23
I don't think that it is the other port, because when i try switching the wired connection name to eth1 in wicd, it says no connection found.

```
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
address 192.168.1.121
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

nameserver 192.168.1.1
nameserver 192.168.1.18

after ping(got same results)
$ arp

Address   HWtype  HWaddress           Flags Mask            Iface
192.168.1.1                          
                  (incomplete)                              eth1
192.168.1.1                      
                  (incomplete)                              eth1

```
but after seeing this, i'm not sure..what exactly does arp do..shouldn't it be displaying eth0? I tried switching the eth0 with eth1 in the interfaces file, switching out the ethernet cable to the other port, and then changing wicd to connect to eth1, but still same issue. It said it couldn't find the ethtool package, so no luck there.

---

### Post by alphacrucis2 on 2009-04-23
> **fr0gg said:**
> I don't think that it is the other port, because when i try switching the wired connection name to eth1 in wicd, it says no connection found.

```
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
address 192.168.1.121
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

nameserver 192.168.1.1
nameserver 192.168.1.18

after ping(got same results)
$ arp

Address   HWtype  HWaddress           Flags Mask            Iface
192.168.1.1                          
                  (incomplete)                              eth1
192.168.1.1                      
                  (incomplete)                              eth1

```
but after seeing this, i'm not sure..what exactly does arp do..shouldn't it be displaying eth0? I tried switching the eth0 with eth1 in the interfaces file, switching out the ethernet cable to the other port, and then changing wicd to connect to eth1, but still same issue. It said it couldn't find the ethtool package, so no luck there.

It is very strange that arp resolution seems to be trying eth1!

arp stands for address resolution protocol. When your PC tries to send a message to an IP address within the same ip subnet and it is not an address local to your PC then it sends out an arp broadcast saying in effect "who has ip address x.x.x.x". All devices on your local lan will see the broadcast and with luck one of them will respond via the source mac address of the broadcast with its' own mac address saying "hey that's me". Your PC then adds the mac address - ip address pairing to the local arp cache (it remembers so it doesn't have to ask again until the arp cache entry expires). The arp command allows you to display and manipulate to arp cache. Your arp cache is saying incomplete which proably means it tried an arp broadcast but received no response. Are you certain that the address of the router is 192.168.1.1 ?

A pity about ethtool as it will tell you the status of your ethernet transceiver - useful stuff such as link detected y/n, link speed, duplex, negotiation etc.

---

### Post by fr0gg on 2009-04-23
Ah, I see. Yes, I am sure, that's the address I type in my browswer to assign static IP's and forward ports and what not..and when i ping it in XP I get full response and no packets dropped..
Is there a way I can download the ethtool package and install it manually?

---

### Post by nandemonai on 2009-04-24
I think you should attempt using eth0 first then eth1 in your config files. Bringing the interface down and then back up each time you change it. Leave the cable in the same port you usually use but try both eth0 and eth1.

If that's not the issue then perhaps we need to look at bugs with your particular Ethernet controller.

```
lspci | grep Ethernet
```

That should list what controllers you're using.

---

### Post by alphacrucis2 on 2009-04-24
> **fr0gg said:**
> Ah, I see. Yes, I am sure, that's the address I type in my browswer to assign static IP's and forward ports and what not..and when i ping it in XP I get full response and no packets dropped..
Is there a way I can download the ethtool package and install it manually?

You could download the deb using windows and copy it to a usb thumb drive. Then just double click on the deb file from nautilus.

The deb for Jaunty is here:

[http://packages.ubuntu.com/jaunty/utils/ethtool](http://packages.ubuntu.com/jaunty/utils/ethtool)

select either i386 or AMD 64

If you aren't running jaunty then change as appropriate for hardy, intrepid etc.

---

### Post by fr0gg on 2009-04-24
Yea, but like I've said, when I then try to change the wired connection in wicd to eth1, it says cannot find connection, which tells me the port should be eth0..

here's the grep command's output
```
00:11:0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:12:0 Bridge: nVidia Corrporation MCP55 Ethernet (rev a2)
```

---

### Post by alphacrucis2 on 2009-04-24
> **fr0gg said:**
> Yea, but like I've said, when I then try to change the wired connection in wicd to eth1, it says cannot find connection, which tells me the port should be eth0..

here's the grep command's output
```
00:11:0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:12:0 Bridge: nVidia Corrporation MCP55 Ethernet (rev a2)
```

Do you see anything in dmesg

This is what I get with my e1000e ethernet card:

```
[   19.420320] e1000e 0000:00:19.0: irq 2297 for MSI/MSI-X
[   19.478051] e1000e 0000:00:19.0: irq 2297 for MSI/MSI-X
[   19.478345] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.240774] 0000:00:19.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   21.240777] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   21.240959] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready


```

Look through your dmesg output and see if your driver is logging any problems.

---

### Post by fr0gg on 2009-04-24
I get a whole mess of output, then many lines of eth1: no link during initialization and ADDRCONF(NETDEV_UP): eth1: link is not ready
I still don't understand why it's trying to use eth1, when I'm fairly certain the port I have the cable plugged into is eth0, that's the only way wicd will detect a connection..

---

### Post by alphacrucis2 on 2009-04-24
> **fr0gg said:**
> I get a whole mess of output, then many lines of eth1: no link during initialization and ADDRCONF(NETDEV_UP): eth1: link is not ready
I still don't understand why it's trying to use eth1, when I'm fairly certain the port I have the cable plugged into is eth0, that's the only way wicd will detect a connection..


Very odd. Are there actually two ethernet cards or is it a single dual port card?

---

### Post by nandemonai on 2009-04-24
I found this post that seems related though there was no resolution of the problem for them (unless they figured it out and never posted again).

[http://ubuntuforums.org/showthread.php?t=829709](http://ubuntuforums.org/showthread.php?t=829709)

I'm wondering if this is a driver issue perhaps. Experience would indicate a bad cable but since you have no issues in XP that's likely not the case.

If you can follow the instructions to get ethtool installed and then run it on both eth0 and eth1 then that would really help the cause.

I realise this is a frustrating problem and you're being a champ about it by having to dual boot for all of this. Which really makes me want to help you get this figured out ;)

One other option I'd suggest is getting a copy of the Jaunty live CD and trying to setup your connection within the live session with network manager. I'm reading many issues with this controller on various Linux distros which again would hint at driver problems. I suggest Jaunty because it has a newer kernel.

That would be a last resort though in my opinion.

---

### Post by SnaveDogg on 2009-04-24
> **fr0gg said:**
> Can anyone offer some insight into my problem, I still haven't resolved it and I'm at a loss.
Thank you!

I'm in roughly the same boat. I have no clue what I'm doing either.
I worked with it for about 2 hours last night to no avail. Getting really frustrated with Xubuntu.

---

### Post by nandemonai on 2009-04-24
> **SnaveDogg said:**
> I'm in roughly the same boat. I have no clue what I'm doing either.
I worked with it for about 2 hours last night to no avail. Getting really frustrated with Xubuntu.

Same network controller?

---

### Post by fr0gg on 2009-04-24
> **alphacrucis2 said:**
> Very odd. Are there actually two ethernet cards or is it a single dual port card?

It's a single dual port card. I'll work on getting ethtool going shortly, I'm currently tied up. When I do get it up, post output of the below command right?
```
ethtool eth0
```

Again, thanks for the help nandemonai alpha, and ehderube, it's nice to know someone cares enough to look after my issue!

---

### Post by nandemonai on 2009-04-24
> **fr0gg said:**
> It's a single dual port card. I'll work on getting ethtool going shortly, I'm currently tied up. When I do get it up, post output of the below command right?
```
ethtool eth0
```

Again, thanks for the help nandemonai alpha, and ehderube, it's nice to know someone cares enough to look after my issue!

Both would be handy.

```
ethtool eth0
```
```
ethtool eth1
```

I'm off to bed now myself but will check on your progress later on ;)

---

### Post by fr0gg on 2009-04-24
Alright, I'm having trouble even finding the right .deb file for eth0 to work in intrepid..all of the ones I've tried so far (even the one located here:[https://launchpad.net/ubuntu/intrepid/lpia/ethtool/6-0](https://launchpad.net/ubuntu/intrepid/lpia/ethtool/6-0), which says it is for intrepid..), tell me Error:Incorrect architecture.
I tried extracting the .tar, but where should I extract to, and what is the command to do so?

---

### Post by nandemonai on 2009-04-24
> **fr0gg said:**
> Alright, I'm having trouble even finding the right .deb file for eth0 to work in intrepid..all of the ones I've tried so far (even the one located here:[https://launchpad.net/ubuntu/intrepid/lpia/ethtool/6-0](https://launchpad.net/ubuntu/intrepid/lpia/ethtool/6-0), which says it is for intrepid..), tell me Error:Incorrect architecture.
I tried extracting the .tar, but where should I extract to, and what is the command to do so?

Don't bother with the tar.gz, that's source you have to compile.

```
uname -a
```

Will tell you your running kernel and architecture, either 32bit or 64bit.

```
Linux brownbox 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux
```

```
Linux blackbox 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux
```

The first example is 32bit (i686) the second 64bit (x86_64). Anything but x86_64 is 32bit (i386, i486, i586, i686 etc).

So depending which you have you'll need the correct architecture.

[http://packages.ubuntu.com/intrepid/ethtool](http://packages.ubuntu.com/intrepid/ethtool)

---

### Post by fr0gg on 2009-04-25
Alright, thanks got that sorted..heh.

```
Settings for eth0:
	Supported ports: [ MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 1
	Transceiver: external
	Auto-negotiation: on
	Supports Wake-on: g
	Wake-on: d
	Link detected: yes

Settings for eth1:
	Supported ports: [ MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: Unknown! (65535)
	Duplex: Unknown! (255)
	Port: MII
	PHYAD: 1
	Transceiver: external
	Auto-negotiation: on
	Supports Wake-on: g
	Wake-on: d
	Link detected: no


```So the fact that the speed and duplex is showing up for eth0, as well as that the link is detected says that the port is indeed eth0 I'd assume?

---

### Post by nandemonai on 2009-04-26
After some more searching I came across another bug report that seems to be like it could be your issue fr0gg.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/136836](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/136836)

Give this a try (from the bug report):

```
##########################################
 Networking Solution for nVIDIA MCP55 Ethernet - Ubuntu 8.10 Interpid
##########################################

Step 1, open a terminal.

a) become superuser
$ sudo su

b) remove forcedeth kernel module (it's the ethernet's driver)
# rmmod forcedeth

c) load forcedeth kernel module again with new parameters
# modprobe forcedeth msi=0 msix=0

d) restart networking
# /etc/init.d/networking restart

You should be able to connect to your network now.

Step 2, configure the system to do this automatically from now on when it starts
(otherwise you'll need to do the above steps every time you boot).

Open a terminal and become root with
$ sudo su

a) go to /etc/modprobe.d/
# cd /etc/modprobe.d/

b) edit the options file
# gedit options

c) go to end of file and add the following lines (without the quotes)
"#nVIDIA Corporation MCP55 Ethernet"
"options forcedeth msi=0 msix=0"

d) save the changes and close gedit

e) you'll need to rebuild your boot image, in the same terminal type:
# update-initramfs -u

Reboot and you're done.

Hope this helps.

```

For clarification the $ and # just indicate which user you're working with (user/root). You do not need to type the $/# in your commands. It's just a way to show you who you should be running the commands as. Rather than use sudo su you could just use sudo in front of each command that requires root (#). It's probably easier to just follow the example above but be careful. When you're done using root type exit to get back to your user ($).

If this fixes your issue you may want to add to the bug report yourself to confirm it for your hardware.

Good luck buddy ;)

---

### Post by fr0gg on 2009-04-26
haha crap, i didn't even get past the first command,
```
ERROR: Module forcedeth does not exist in /proc/modules
```

---

### Post by nandemonai on 2009-04-26
> **fr0gg said:**
> haha crap, i didn't even get past the first command,
```
ERROR: Module forcedeth does not exist in /proc/modules
```

That's weird.. It's not using the kernel module I thought it would or should..

Please post the complete output of:

```
lspci -knn
```

That way we can see what module it is using.

This just gets weirder and weirder :P

What model motherboard out of interest?

---

### Post by fr0gg on 2009-04-26
Ah great..yea, I've had nothing but problems since day 1 trying to get ubuntu working hah, just want to get this sorted. Looks like that fix worked for multiple people though, shame.

```
$ lspci -knn
00:00.0 Host bridge [0600]: nVidia Corporation C55 Host Bridge [10de:03a1] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03ac] (rev a1)
00:00.2 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03aa] (rev a1)
00:00.3 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03a9] (rev a1)
00:00.4 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03ab] (rev a1)
00:00.5 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03a8] (rev a2)
00:00.6 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b5] (rev a1)
00:00.7 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b4] (rev a1)
00:01.0 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03ad] (rev a1)
00:01.1 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03ae] (rev a1)
00:01.2 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03af] (rev a1)
00:01.3 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b0] (rev a1)
00:01.4 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b1] (rev a1)
00:01.5 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b2] (rev a1)
00:01.6 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b3] (rev a1)
00:02.0 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b6] (rev a1)
00:02.1 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03bc] (rev a1)
00:02.2 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03ba] (rev a1)
00:03.0 PCI bridge [0604]: nVidia Corporation C55 PCI Express bridge [10de:03b7] (rev a1)
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp
00:09.0 RAM memory [0500]: nVidia Corporation MCP55 Memory Controller [10de:0369] (rev a1)
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP55 LPC Bridge [10de:0360] (rev a2)
	Kernel modules: ck804xrom
00:0a.1 SMBus [0c05]: nVidia Corporation MCP55 SMBus [10de:0368] (rev a2)
	Kernel driver in use: nForce2_smbus
	Kernel modules: i2c-nforce2
00:0a.2 RAM memory [0500]: nVidia Corporation MCP55 Memory Controller [10de:036a] (rev a2)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP55 USB Controller [10de:036c] (rev a1)
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP55 USB Controller [10de:036d] (rev a2)
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd


```
It's an Asus p5n32-e SLI motherboard.

---

### Post by nandemonai on 2009-04-26
> **fr0gg said:**
> Ah great..yea, I've had nothing but problems since day 1 trying to get ubuntu working hah, just want to get this sorted. Looks like that fix worked for multiple people though, shame.

```
$ lspci -knn
00:00.0 Host bridge [0600]: nVidia Corporation C55 Host Bridge [10de:03a1] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03ac] (rev a1)
00:00.2 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03aa] (rev a1)
00:00.3 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03a9] (rev a1)
00:00.4 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03ab] (rev a1)
00:00.5 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03a8] (rev a2)
00:00.6 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b5] (rev a1)
00:00.7 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b4] (rev a1)
00:01.0 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03ad] (rev a1)
00:01.1 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03ae] (rev a1)
00:01.2 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03af] (rev a1)
00:01.3 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b0] (rev a1)
00:01.4 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b1] (rev a1)
00:01.5 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b2] (rev a1)
00:01.6 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b3] (rev a1)
00:02.0 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b6] (rev a1)
00:02.1 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03bc] (rev a1)
00:02.2 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03ba] (rev a1)
00:03.0 PCI bridge [0604]: nVidia Corporation C55 PCI Express bridge [10de:03b7] (rev a1)
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp
00:09.0 RAM memory [0500]: nVidia Corporation MCP55 Memory Controller [10de:0369] (rev a1)
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP55 LPC Bridge [10de:0360] (rev a2)
	Kernel modules: ck804xrom
00:0a.1 SMBus [0c05]: nVidia Corporation MCP55 SMBus [10de:0368] (rev a2)
	Kernel driver in use: nForce2_smbus
	Kernel modules: i2c-nforce2
00:0a.2 RAM memory [0500]: nVidia Corporation MCP55 Memory Controller [10de:036a] (rev a2)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP55 USB Controller [10de:036c] (rev a1)
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP55 USB Controller [10de:036d] (rev a2)
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd


```
It's an Asus p5n32-e SLI motherboard.

Are you sure that's all of it? I don't see the ethernet controller there...

---

### Post by fr0gg on 2009-04-27
Holy crap..it worked!! I guess it was displaying that the module wasn't in the directory after the second time I entered it..nothing was displayed the first time so I wasn't sure anything happened..but today I thought I'd just run through the rest of those steps and see what happened.
Thanks a lot nandemonai, you not only helped me fix my solution but taught me quite a lot!
Now..to find out how to get my x-fi sound card working..haha I seem to have all the hardware that isn't fully supported in linux yet..any tips with that in your experience?

---

### Post by nandemonai on 2009-04-27
> **fr0gg said:**
> Holy crap..it worked!! I guess it was displaying that the module wasn't in the directory after the second time I entered it..nothing was displayed the first time so I wasn't sure anything happened..but today I thought I'd just run through the rest of those steps and see what happened.
Thanks a lot nandemonai, you not only helped me fix my solution but taught me quite a lot!
Now..to find out how to get my x-fi sound card working..haha I seem to have all the hardware that isn't fully supported in linux yet..any tips with that in your experience?

Fantastic, glad to be of assistance then :)

As far as the x-fi card, not my forte I'm afraid. Looks like you're right about having non Linux friendly hardware though unfortunately.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63352](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63352)

Best of luck with it, my advice would be to use internal sound if your motherboard has it or get yourself another card. Creative are know for their lack of Linux support.

---

### Post by fr0gg on 2009-04-27
Brilliant..heh..
as for my graphics card (8800gts), I was trying to enable desktop effects and the package won't install..I've tried just letting it auto-detect by enabling the effecs, that tells me they cannot be enabled. Also tried hardware drivers, but after clicking Activate, it searches..does nothing, then still says "this driver is not activated.." any suggestions?

---

### Post by nandemonai on 2009-04-27
> **fr0gg said:**
> Brilliant..heh..
as for my graphics card (8800gts, I was trying to enable desktop effects and the package won't install..I've tried just letting it auto-detect by enabling the effecs, that tells me they cannot be enabled. Also tried hardware drivers, but after clicking Activate, it searches..does nothing, then still says "this driver is not activated.." any suggestions?

Hmm, the restricted drivers should be fine with that card. Make sure you're online when you enable them.

If it won't work through there you could always grab the installer from the nvidia site. Instructions should be up there. Just make sure you grab the right architecture.

---

### Post by fr0gg on 2009-04-27
Yes, I was online while trying..
I've also tried to visiting the nVidia site [http://www.nvidia.com/object/unix.html]("http://www.nvidia.com/object/unix.html") but those are all x86 drivers..

---

### Post by nandemonai on 2009-04-27
> **fr0gg said:**
> Yes, I was online while trying..
I've also tried to visiting the nVidia site [http://www.nvidia.com/object/unix.html]("http://www.nvidia.com/object/unix.html") but those are all x86 drivers..

[http://www.nvidia.com/object/linux_display_amd64_180.51.html](http://www.nvidia.com/object/linux_display_amd64_180.51.html)

Should probably move this to another thread now :P

---

### Post by fr0gg on 2009-04-27
ahah yea, was just thinking the same.
cheers though!

---

