---
title: "Sharing connection with 2 PCs"
date: 2005-09-15
forum: Networking &amp; Wireless
---

### Post by damu on 2005-09-15
First, I'd like to thanks all the guys here which gave some many answers to my questions!

Here is my configuaration:
. laptop 1 with Kubuntu Hoary installed. This laptop is connected to broadband  with a usb modem through ppp0.
Another connection eth0 with DHCP enabled is configured.
Firestarter is installed on this laptop , so that I can share the connection with the laptop 2 through the router.

. I have a Netgear router and, a Netgear MA521 cardbus plugged to the laptop 2. 

.a laptop 2 with dual boot to Windows XP and Studio to Go! (linux system dedicated to music and sound production based on a knoopix).

Here are my problems  ;-) ! :

1) I usually can't access the configuration of  eth0 through control center/network settings. KDE asks me to log in administrator mode. It asks me my password and then go back to the home page of the control center. I f I go to the network settings again , I am still not log as administrator and therefore can't edit/modify eth0.
Twice since Kubuntu , the administrator thinggy worked and I could modify eth0. I still don't know how and why, at a particular time it worked!

2)When I was lucky to be logged successfully in administrator mode, I chose DHCP for eth0, and tried to enable the connection. Each time the connection fails and goes back to disable mode.
Of course, when I start Firestarter, it tells me that eth0 is not ready!

3) When the problems 1 & 2 will be sorted, the connection in between the 2 computers through the router should work fine...till I boot on Win XP on laptop2. I can't find any drivers for the Netgear MA521, and didn't find any obvious way to make it work on the net

When this 3 problems will be solved , I might be the happiest newbbie linuxian in the world ! O:)

---

### Post by spd106 on 2005-09-16
I'll have a go at these problems

1) You could try maually editing the configuation from the command line. This involves opening a terminal and issueing commands with sudo then entering your password. The file to look at first is /etc/network/interfaces. You might also want to check out the man pages for reference. Also use ifconfig, ping and route to check it's working.

2) As far as i know the dhcp server should be set with a static ip address then your laptop 2 will broadcast a dhcp request on the network and get a response. You will set firestarter to enable internet sharing and enable dhcp for the local network. Set the local device to eth0 and internet device to ppp0. Then on laptop 2 set eth0 to dhcp. 
This is a bit of overkill for such a small network. It may be easier to set static ip addresses all round. Then it least you know who to ping when troubleshooting. I would set up laptop 1 eth0 as 192.168.1.1 w/ subnet mask 255.255.255.0 and laptop 2 eth0 as 192.168.1.2 w/ 255.255.255.0 and 192.168.1.1 as the default gateway.

3) What's wrong with the netgear website? You should bring up the page to download the driver in less than ten secs. [http://kbserver.netgear.com/release_notes/d102418.asp](http://kbserver.netgear.com/release_notes/d102418.asp)
Just make sure you check it's for the right model and region.

Good luck

---

### Post by damu on 2005-09-18
Thanks for the answers!...I'm not sorted though! eth0 is still disabled and I can't manage to change it to enable state.

1) Here are some informations I managed to get,if it can help:

> When I do ifconfig in a Konsole, I get :

eth0      Link encap:Ethernet  HWaddr 00:90:F5:13:20:7C
          inet6 addr: fe80::290:f5ff:fe13:207c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:125 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:41418 (40.4 KiB)
          Interrupt:10 Base address:0x3200

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:223 errors:0 dropped:0 overruns:0 frame:0
          TX packets:223 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:7297 (7.1 KiB)  TX bytes:7297 (7.1 KiB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:87.242.141.165  P-t-P:212.67.121.53  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:2828 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3037 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:1850625 (1.7 MiB)  TX bytes:379565 (370.6 KiB)







>When I open the file Interface with Kate, here is what it gives :

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

iface eth0 inet dhcp

auto eth0






>I read in some threads that the ip_forward should be allowed, so I changed it in /etc/network/options to ip_forward=yes

It didn't change anything though...eth0 is still s=disabled 




2) From I read in other threads, this second point should be ok if we managed to sort out the problem 1.

3) Thanks for the link to Netgear. I checked it already...they provide drivers for Windows only.
I've been browsing to find a way for my MA521 to be recognised on a knoppix based system...could find few attempts...not many results and no obvious ways to go through that. But hey! if we can manage to sort out the problem that would be already a major step. I could connect with XP on the laptop2!

---

### Post by spd106 on 2005-09-19
1) Let's try static ip addresses.
As root (sudo): 
- On laptop 1 run ifdown eth0. Ignore any errors.
- Open the interfaces file with kate then add these lines

iface eth0 inet static
address 192.168.2.1
netmask 255.255.255.0

- Save and exit.
- Now do ifup eth0.
- ifconfig should now contain the line inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0.
- Go to laptop 2 and repeat using

iface eth0 inet static
address 192.168.2.2
netmask 255.255.255.0
gateway 192.168.2.1

- now ping 192.168.2.1  from laptop 2.
- To access the internet you will need to change the firestarter preferences to reflect the static addresses.

3) Sorry, i assumed you would be using ndiswrapper which uses the windows drivers. Check out this wiki page for a useful guide.
[https://wiki.ubuntu.com/SetupNdiswrapperHowto](https://wiki.ubuntu.com/SetupNdiswrapperHowto)
I suggest you start with apt-get install ndiswrapper-utils the if this doesn't work move on to building from source. It is a rather confusing process if you've not been through it before.  

Good luck
Steve

---

### Post by damu on 2005-09-19
Thanks Steve for ur help. O:) That's sooo great for a newbie like me to find some help on this quite technical subject!

1)I am not yet connected with laptop2 through wireless, but, hey, I guess it is learning process. Here are the results:


ppp0: unknown hardware address type 512
sit0: unknown hardware address type 776
ppp0: unknown hardware address type 512
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:90:f5:13:20:7c
Sending on   LPF/eth0/00:90:f5:13:20:7c
Sending on   Socket/fallback


mamta@do:~$ sudo cp /home/mamta/NEW_COMPILATION/Damu/eth0connection/interfaces* /etc/network


mamta@do:~$ ifup eth0
/etc/network/interfaces:18: duplicate interface
ifup: couldn't read interfaces file "/etc/network/interfaces"


mamta@do:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1371 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1371 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:40589 (39.6 KiB)  TX bytes:40589 (39.6 KiB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:87.242.156.121  P-t-P:212.67.121.44  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:35301 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31904 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:33149253 (31.6 MiB)  TX bytes:4584613 (4.3 MiB)





Of course, if I start Firestarter, I have the same answer than before :
Internal network device eth0 is not ready. Aborting..

         
3)Thanks for the wiki link. Will try that as soon as the laptop1 connection thinggy is sorted. Hopefully, the Ubuntu tutorial will also work on a knoopix as they are both debian...

Damu

---

### Post by kianziack on 2005-09-20
[QUOTE=damu]Thanks Steve for ur help. O:) That's sooo great for a newbie like me to find some help on this quite technical subject!

1)I am not yet connected with laptop2 through wireless, but, hey, I guess it is learning process. Here are the results:


ppp0: unknown hardware address type 512
sit0: unknown hardware address type 776
ppp0: unknown hardware address type 512
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:90:f5:13:20:7c
Sending on   LPF/eth0/00:90:f5:13:20:7c
Sending on   Socket/fallback


mamta@do:~$ sudo cp /home/mamta/NEW_COMPILATION/Damu/eth0connection/interfaces* /etc/network


mamta@do:~$ ifup eth0
/etc/network/interfaces:18: duplicate interface
ifup: couldn't read interfaces file "/etc/network/interfaces"


mamta@do:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1371 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1371 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:40589 (39.6 KiB)  TX bytes:40589 (39.6 KiB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:87.242.156.121  P-t-P:212.67.121.44  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:35301 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31904 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:33149253 (31.6 MiB)  TX bytes:4584613 (4.3 MiB)





Of course, if I start Firestarter, I have the same answer than before :
Internal network device eth0 is not ready. Aborting..

         
3)Thanks for the wiki link. Will try that as soon as the laptop1 connection thinggy is sorted. Hopefully, the Ubuntu tutorial will also work on a knoopix as they are both debian...

Damu[/QUOTE]
 hi! i'm having same trouble to and i try it, will it works but my problem is i dont know to how to download  firestarter :D thy say i can have it using apt_get <--- err what is this? plz help T_T

---

### Post by spd106 on 2005-09-21
> mamta@do:~$ ifup eth0
/etc/network/interfaces:18: duplicate interface
ifup: couldn't read interfaces file "/etc/network/interfaces"
It sounds like you have duplicate entries in the interfaces file. Make sure there is only one stanza per inet, if you are unsure please post it here.

I should have mentioned that in a manually configured network every device will need to be on the same subnet. This means you will need to check that the netgear router  has an ip address like the other two. eg 192.168.2.3

Does the netgear router have a built-in broadband modem? If so it would be easier to use this. I often get frustrated by these usb modems. If not don't worry we'll get it working.

When you get the wireless card up and running the best thing to do is to test it by scanning for nearby access points. **sudo iwlist wlan0 scan**, if this works you should be ok to fill in the details.

There is a wifi howto in the wiki [WiFiHowto](https://wiki.ubuntu.com/WiFiHowto)

>  hi! i'm having same trouble to and i try it, will it works but my problem is i dont know to how to download firestarter  thy say i can have it using apt_get <--- err what is this? plz help T_T
kianziack you can use apt-get, but the user-friendly way is through synaptic. Open system->administration->synaptic package manager
then open settings->repositories and add the hoary universe repos.
Then reload and look for firestarter.
I would also point you to the ubuntu [unofficial starter guide](http://www.ubuntuguide.org/) but it doesn't seem to be there at the moment.

---

### Post by damu on 2005-09-22
Many thanks Steve for ur help!

Following your advices I erased  the auto dhcp thinggy in the interfaces file.
Then I did ifup in a Konsole and now the eth0 is enabled!
Seems like a nice achievement to me  :smile: !

The adress given with ifconfig is different from what is was supposed to be (192.168.2.1 instead of 192.168.2.3)
I guess it's not a big deal but I don't know what to put on laptop2 under Win XP to share the connection. I tried a few things hoping that I could guess, but...

So here is the result of ifconfig :


>mamta@do:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:90:F5:13:20:7C
          inet addr:192.168.2.1  Bcast:192.168.2.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:193 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:28174 (27.5 KiB)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0x3200

ppp0      Link encap:Point-to-Point Protocol
          inet addr:87.242.139.11  P-t-P:212.67.121.53  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:22011 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21946 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:20639518 (19.6 MiB)  TX bytes:2757304 (2.6 MiB)

There are not many options in firestarter for the connection settings. So I just disabled DHCP. 

To answer to ur question about the router, unfortunately it is not a modem router. That's why I struggled to create a connection with a usb modem with laptop1 and Kubuntu and that we struggle now to share this connection with laptop2!...and, yep, I should have look twice before purchasing this router!!

Damu

---

### Post by damu on 2005-09-22
On laptop1, in Firestarter I allowed connections from host 192.168.2.1  and 192.168.2.2 and 192.168.2.3
One host would probably enough but I didn't want firestarter to be a possible source of problem during the testing period!

I then configured TCP/ip this way on laptop2 in WinXP:

  IP Address      192.168.2.2
   Subnet mask     255.255.255.0
   Default gateway 192.168.2.1

Now the funny thing is that Skype detected the connection on laptop2 (yehh...one thing connected...I can at least receive my phonecalls!  ;-) , but I can't find any way to settle the connexion in firefox or IE . Neither automatic proxy or fix IP ( 192.168.2.2) works!... :neutral: 

What do u reckon?

---

### Post by spd106 on 2005-09-24
Sorry I took so long to get back, the internet line's been down for the last few days. :mad: 
First of all can you ping your gateway(laptop1), from command prompt **ping 192.168.2.1**? Chances are this will work fine. What's the ip address of your router? It usually defaults to 192.168.2.1, but it can change. There are often guides and help on the router start page if you direct your browser to it's ip address. You should have done this already when configuring the security settings ;-) 
On the the old repeating hubs you didn't need to do much, just plug it in and away it goes. These intelligent routers need more configuring.

It might be that you're not resolving dns properly. Try pinging a remote server by name and then by ip address. eg **ping -C 2 [www.whitehouse.gov](www.whitehouse.gov)** if that doesn't work then try **ping -C 2 194.109.192.9**

If you get a result from the second attempt but not the first then you need to add a nameserver to the /etc/resolv.conf. If you're in windows then you need to configure the tcp/ip properties by adding a dns server. This should be provided by your ISP, it's best to check their website, though there are many free ones available.

Steve

---

### Post by Baby on 2005-09-28
I checked on the net , and it seems the default ip of the Netgear MR814 is 192.168.0.1
I tried this ip in Konqueror, hoping it would give me an access to the control panel of the router, but no, nothing...can't access thinggy message.

Then I changed the ip in ect/network/interfaces to 192.168.0.1
In the inbound connections of Firestarter, I allowed the ip 192.168.0.1 ,192.168.0.2 , 192.168.0.3

I rebooted

But for now, no results...I start to wonder if trying to share a net connection from an Ubuntu based system to another computer is not too ambitious for a linux newbie like me!

I work on Studio to Go (linux distrib for audio production)  on a daily basis. My partner use Kubuntu on this laptop...we wouldn't go back for anything on a Win system...but I must say that setting an internet connection and standart connection on linux is a real pain in...for a non programmer...mean, if the purpose of the next version of Ubuntu is to challenge Win systems, nearly everything looks fine to me, but this major problems of connections! 

Thanks for ur support and understanding!

---

### Post by damu on 2005-10-01
Hi,

I realised I posted the previous post with the loggin of my partner! Well, now you know that Babby and Damu are part of the same team!! ;) 

When I want to reconnect on laptop1 (we have to swap many times a day  from a laptop to the other and I must say it's just mad to have to work this way!), I open a Konsole and do: sudo /etc/init.d/dial.
It works, I'm connected, and it gives some more informations about proxy. I guess it could perhaps help to solve my problem :

mamta@do:~$ sudo /etc/init.d/dial

Plugin pppoatm.so loaded.
PPPoATM plugin_init
PPPoATM setdevname - remove unwanted options
PPPoATM setdevname_pppoatm - SUCCESS:0.38
Using interface ppp0
Connect: ppp0 <--> 0.38
CHAP authentication succeeded
Cannot determine ethernet address for proxy ARP
local  IP address 84.43.119.80
remote IP address 212.67.121.48
primary   DNS address 212.67.120.148


Thanks for ur help!

---

