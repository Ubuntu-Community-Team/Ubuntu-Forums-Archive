---
title: "iPhone and PdaNet"
date: 2008-10-19
forum: Networking &amp; Wireless
---

### Post by iblanken on 2008-10-19
For those with an iPhone who want to utilize it as a tethered modem [June Fabrics]("http://www.junefabrics.com/iphone/index.php") has an app for jail broken iPhones.

The application is a wireless router with DHCP support so you don't have to use static addresses or proxy servers.

The instructions only cover Windows and Mac, but it is possible to make pdanet work with Ubuntu, Hardy in my case. Basically, the steps are:
Configure an ad-hoc wireless network 
Connect the iPhone to the wireless network
Start pdanet, ensure that the router functionality is on
Use acquire an IP Address from pdanet

Since network manager does not support ad-hoc networks you have to configure  the wireless device via the command line (the script I use is posted below). 

At first things seemed to be going well. Pdanet informed me that my laptop was connected and had acquired an IP address. But I could not browse the web.. I could ping the iPhone's wireless IP address and the phones IP address on AT&T's network, so routing appeared to be working. I could ssh by IP to a remote host, but DNS queries always timed out with dig reporting that no servers could be reached. DHCP updated my /etc/resolve.conf as expected but nothing could resolve. 

I tried pdanet with a Windows system and a Mac, and both worked without a hitch. So I figured there must be an issue with my Ubuntu configuration.

It seems I had to “prime the pump.”  

Once I was assigned my IP address, I checked /etc/resolv.conf:
search localdomain
nameserver 68.28.114.91


Then executed dig @68.28.114.91 [www.google.com](www.google.com)

It worked.. and from then on I could resolve normally.  Any ideas why this could be the case?

This is the script I use to start using pdanet:
#!/bin/sh
# pdanet_on
sudo /etc/dbus-1/event.d/25NetworkManager stop
sudo ifconfig eth1 down
sudo iwconfig eth1 mode ad-hoc
sudo iwconfig eth1 channel 4
sudo iwconfig eth1 essid 'iPhone 3G'
sudo iwconfig eth1 key somekey
sudo ifconfig eth1 up
echo Press Enter when iPhone is connected to Network and PDANet is started
read foo
sudo dhclient eth1
DNS=`grep nameserver /etc/resolv.conf | head -1 | awk '{print $2}'`
dig @$DNS [www.google.com](www.google.com)


When I am done with pdanet I run this script (Network Manager does not put your wireless back into “managed” state):
#!/bin/sh
# pdanet_off
sudo ifconfig eth1 down
sudo iwconfig eth1 mode managed
sudo ifconfig eth1 up
sudo /etc/dbus-1/event.d/25NetworkManager start


I hope this helps anyone looking to use pdanet with Ubuntu.

For those interested, I have an Windows XP SP3 VMWare image running in Player 2.5.0 build-118166 and it sees the iPhone with no problem. I was able to jailbreak the phone using the VM. My music lives  on Ubuntu so I use VMWare's shared folder capability and [iTunes Library Updater]("http://itlu.ownz.ch/wordpress/") to keep iTunes current.

---

### Post by gozala on 2008-11-04
Do you know how to do this trick with Ibex???

I guess you can create ah-hock network from GUI in Ibex but it never connects. I can see the connection from PDA NET but connection is not seen in Ubuntu I can only see it's trying to connect

As I guess there is no /etc/dbus-1/event.d/25NetworkManager
in Ibex so I'm kind of confused :confused:

---

### Post by klauslanza on 2008-11-14
I'm having mixed results in Intrepid Ibex.

Since there is no /etc/dbus-1/event.d/25NetworkManager, usually i just killall NetworkManager and then goes with the oters commands. Sometimes the connection with pdanet goes ok, but most of the times I just keep upping and downing interface and sometimes I get the right way.... problem is, I don't know which is the correct and easiest way, assuming the gui way is broken.

PLEASE HELP!

---

### Post by Plecebo on 2008-11-14
In Ibex I was having trouble getting the laptop to connect to the ad-hoc network. So I had to change the ipv4 settings to DHCP
[LIST]
[*]right click on the network manger and choose edit connections
[*]On the wireless tab choose the ad-hoc network and select edit
[*]On the IPv4 Settings tab change the method dropdown to "Automatic (DHCP)"
[/LIST]

I imagine this was because Ibex was not getting any IP address from the network, so if you assigned a static IP using "Manual" rather then "Automatic (DHCP)" you would have success as well. 

This worked for me.

---

### Post by SnowflakeRV7 on 2008-11-26
I'm struggling with the ad-hoc network settings on my Dell XPS 1330.  I'm trying to get my jailbroken iPhone 3G connected.

I took the scripts above and turned them into a single script that can be called with the options "start" or "stop" to start or stop the ad-hoc network... I'll attach it to the end of this post.
The problem is that it still doesn't work right.

My Network Manager stops as requested, and the ifconfig and iwconfig commands all complete without any complaints.  But when it gets to the "connect the iPhone to the [ad-hoc] network" setting, my iPhone can't find any new networks.

Any help appreciated...

Here's my script (~/pdanet):

```
#!/bin/sh -e
# script to start/stop wireless in ad-hoc mode for iPhone

case "$1" in
    start)
	sudo /etc/init.d/NetworkManager stop
	sudo ifconfig eth1 down
	sudo iwconfig eth1 mode ad-hoc
	sudo iwconfig eth1 channel 4
	sudo iwconfig eth1 essid 'iPhone 3G'
#	sudo iwconfig eth1 key somekey
	sudo ifconfig eth1 up
	echo Press Enter when iPhone is connected to Network and PDANet is started
	read foo
	sudo dhclient eth1
	DNS=`grep nameserver /etc/resolv.conf | head -1 | awk '{print $2}'`
	dig @$DNS [www.google.com](www.google.com)
	;;
    stop)
	sudo ifconfig eth1 down
	sudo iwconfig eth1 mode managed
	sudo ifconfig eth1 up
	sudo /etc/init.d/NetworkManager start
	;;
    *)
	echo "Usage: /etc/init.d/pdanet {start|stop}"
	exit 1
	;;
esac

exit 0
```

---

### Post by JamesLaugesen on 2008-11-26
> **SnowflakeRV7 said:**
> I'm struggling with the ad-hoc network settings on my Dell XPS 1330.  I'm trying to get my jailbroken iPhone 3G connected.

Hi mate, I just recently got my M1330 (with 8.10 64bit) connecting to iPhone with PdaNet.

My problem was that the M1330 wouldn't connect to any ad-hoc networks.
M1330's have the Intel 3945ABG wireless adapter, so I switched to the old ipw3945 driver (instead of iwl3945) and now connect to ad-hoc networks fine.

However, now with ipw3945 I have terrible performance with encrypted networks... but I'm treating that as a new issue hahah.

Your situation sounds different, since my m1330 would still create the ad-hoc network, visible to the iPhone, and would these hang when trying to actually establish an IP on the network.

Sounds like you're not even able to create the ad-hoc network.
What do you get from iwevent while your 'up' script runs?

Ps - this is a good post regarding the iwl3945 driver: [http://www.ubuntugeek.com/using-ipw3945-instead-iwl3945-in-hardy.html](http://www.ubuntugeek.com/using-ipw3945-instead-iwl3945-in-hardy.html)

---

### Post by marcog42 on 2008-12-17
Just as a warning, the latest kernel update broke this method of connecting to PdaNet on the iPhone 3G.  I switched back to kernel 2.6.24-22 and everything works as expected.  Tomorrow I'll post the error the script gives, but essentially it's not creating an Ad Hoc network, as one never shows up for the iPhone to connect to.  I'm using a Dell XPS M1530 with the Intel 3945ABG Wireless adapter.  I'll post more once I've delved into the problem a bit more.

---

### Post by shrubman on 2009-01-01
Hi all,

Just figured it might help others to state I just had success connecting the ad-hoc network.

My hardware is: 

[INDENT]iPhone 3G, jailbroken, firmware 2.2 (modified by pwnage tool)
HP Pavilion dv4 laptop with Broadcom BCM4312 Wireless[/INDENT]

Software is:
[INDENT]Ubuntu 8.10[/INDENT]

Things I did:
[INDENT]Used killall NetworkManager
replaced the essid and key entries with network name and key of my choosing (probably obvious to most of you)[/INDENT]

I still got an error involving SET (forgot exactly what after closing terminal) but I was able to ignore it and complete the rest of the script.

Good luck!

---

### Post by wonderfullyrich on 2009-03-20
> **marcog42 said:**
> Just as a warning, the latest kernel update broke this method of connecting to PdaNet on the iPhone 3G.  I switched back to kernel 2.6.24-22 and everything works as expected.  Tomorrow I'll post the error the script gives, but essentially it's not creating an Ad Hoc network, as one never shows up for the iPhone to connect to.  I'm using a Dell XPS M1530 with the Intel 3945ABG Wireless adapter.  I'll post more once I've delved into the problem a bit more.


I have to second this experience of PdaNet failing on 2.6.24-23.  It works fine on on 2.6.24-22. I've got a Dell Latitude D420 using the same Intel 3945ABG Wireless Adapter.  I posted the same script as SnowflakeRV7, which I slightly modified for my Dell hardware.  

When I run this script, I get 2 seconds of connection on PdaNet and then it disconnects.  Not sure what's happening.

If anyone can figure it out I'd be very appreciative.

```
#!/bin/sh -e
# script to start/stop wireless in ad-hoc mode for iPhone

case "$1" in
    start)
#	sudo /etc/init.d/NetworkManager stop
	sudo /etc/dbus-1/event.d/25NetworkManager stop
	sudo ifconfig wlan0 down
	sudo iwconfig wlan0 mode ad-hoc
	sudo iwconfig wlan0 channel 4
	sudo iwconfig wlan0 essid 'iphone3g'
#	sudo iwconfig wlan0 key abadbadbad
	sudo ifconfig wlan0 up
	echo Press Enter when iPhone is connected to Network and PDANet is started
	read foo
	sudo dhclient wlan0
	DNS=`grep nameserver /etc/resolv.conf | head -1 | awk '{print $2}'`
	echo $DNS
	dig @$DNS www.google.com
	;;
    stop)
	sudo ifconfig wlan0 down
	sudo iwconfig wlan0 mode managed
	sudo ifconfig wlan0 up
	sudo /etc/dbus-1/event.d/25NetworkManager start
	;;
    *)
	echo "Usage: /etc/init.d/pdanet {start|stop}"
	exit 1
	;;
esac

exit 0
```

---

### Post by Bad Penguin on 2009-03-27
> **wonderfullyrich said:**
> I have to second this experience of PdaNet failing on 2.6.24-23.  It works fine on on 2.6.24-22. I've got a Dell Latitude D420 using the same Intel 3945ABG Wireless Adapter.  I posted the same script as SnowflakeRV7, which I slightly modified for my Dell hardware.
I am also having difficulty getting it to work.  I am running a dell xps m1530 with a Broadcom BCM4312 on 2.4.24-23.

Just a FYI, I believe the correct syntax is:
```
iwconfig whatever mode Ad-Hoc
```

At least on my box, the Ad-Hoc is case sensitive.  It also seems iwconfig is particularly finicky with my broadcom chipset.  It fails if I do not stack all of the iwconfig arguments together, for example this works for me:

```
iwconfig eth1 essid mynet channel 4 key aaaaaaaaaa mode Ad-Hoc
```

But this doesn't:

```
iwconfig eth1 essid mynet
iwconfig eth1 channel 4
iwconfig key aaaaaaaaaa
iwconfig eth1 mode Ad-Hoc

```

Go figure ;)

PDANet will work perfectly for me if I do not use encryption:

```
iwconfig eth1 essid mynet enc off mode Ad-Hoc
```

However, if I try with encryption, pdanet never sees or responds to my dhcp requests.  I know encryption is working, I can statically assign ip addresses to the connection on both sides and ssh back and forth.  It just seems pdanet does not like something about wep encryption and dhcp in my case.

I have contacted pdanet (I registered my copy) and they are of no help whatsoever.

Has anyone had any luck getting it to work, with encryption?

---

### Post by wonderfullyrich on 2009-03-28
Thanks Bad Penguin.  You lead me to try a few things and figure out that PDANet will work with 2.4.24-23

It turned out that it didn't like the quote in my ssid.  (i.e. essid mynet is good as opposed to essid 'mynet')

This is the line that i'm now using in my previously posted script. 

```
    sudo iwconfig wlan0 essid iphone3g channel 4 enc off mode Ad-Hoc
``` 

I also tried it with WEP encryption and had the same experience as you did.  PDANet doesn't respond, but the computer-iPhone connection seems to be up and working.  I'm curious if WPA or WPA2 as encryption would work or would cause similar problems, but as WPA is slightly more complicated to script, I haven't tested it.

---

### Post by ump001 on 2009-04-01
i've tried the above recommendation on my macbook also, but no joy. Why is setting up a ad-hoc network so difficult in Ubuntu?

Am very new to ubuntu...

---

### Post by ivanmladek on 2009-04-05
Success! It seems the catch is only on the Ubuntu wifi side:
I have 2.6.27-12-generic #1 SMP Thu Feb 5 09:26:42 UTC 2009 x86_64 GNU/Linux and I installed WICD (from here [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)) and then there is a simple button to setup an ad hoc netowrk which works well:

1) set up an adhoc network on Ubuntu 
2) connect to the network on your iphone
3) launch PDAnet and you should be good to go)

Troubleshooting:
Initially I had to turn off 3G for the PDANet to connect to the adhoc wifi, once it was connected I went back and turned it back on and now I get 1Mb/s on a wireless IPhone tether.

[[IMG]http://www.speedtest.net/result/445766378.png[/IMG]](http://www.speedtest.net)

---

### Post by ump001 on 2009-04-12
hi,

thanks for the above info.
I have got as far as creating an a-hoc network, once created, my iphone doesnt seem to see the network, all other wifi networks can be seen. 

I can see that the network has been created and the laptop is connected via 169.x.x.x network.

Anything i might be missing.

---

### Post by ivanmladek on 2009-04-13
> **ump001 said:**
> hi,

thanks for the above info.
I have got as far as creating an a-hoc network, once created, my iphone doesnt seem to see the network, all other wifi networks can be seen. 

I can see that the network has been created and the laptop is connected via 169.x.x.x network.

Anything i might be missing.

Hi, 
I am not sure. I remember the iphone definitely saw the ad hoc network created by the laptop. Try restarting both iphone and laptop and try again. Even when iphone sees the adhoc network, getting connected can be tricky: turn off 3g, connect to the ad hoc nework on the phone thenrun pdanet and verify connection. Only then turn 3g back on and itshould work. Good luck.

---

### Post by ahmadynejad on 2009-04-20
Hi to every one;
My PDANET 1.5 works fine, :( almost. I can get connect to my iphone 3g with Laptop XP preo/Vista through USB/ad-hoc and get on the internet no problem. I can get my VPN get connected to my work network no problem (my vpn is cisco client with ipsec) but for some reason the remote desktop can not get connect to the remote computer nor I can not ping the remote computer. Does anybody has any idea what the problem might be?
Thanks:

---

### Post by joebuntu_2 on 2009-05-10
Just a quick note for anyone else having issues getting Pdanet running on Jaunty. I couldn't connect mine, whereas worked fine on XP. The script and normal instructions didn't work.

I tried the normal network-manager based solutions but it never seemed to get an IP from the phone. I modified the ad-hoc network to use:

Automatic (DHCP Addresses Only)

Rather than:

Automatic (DHCP)

Once done, I connected to it on Ubuntu (use connect to hidden if not showing). Then connected to it on the iPhone and opened PDANet. 

Lo and behold, both sides showed as connected and I'm writing this reply using it.

Cheers.

---

### Post by bmclauser on 2009-05-14
> I tried the normal network-manager based solutions but it never seemed to get an IP from the phone. I modified the ad-hoc network to use:

Automatic (DHCP Addresses Only)

Rather than:

Automatic (DHCP)

How did you modify the script to get the network to use DHCP Addresses Only?

Thanks

Bryan

---

### Post by KennyHAA on 2009-05-19
> **bmclauser said:**
> How did you modify the script to get the network to use DHCP Addresses Only?

Thanks

Bryan

I think Joe was using the NetworkManager applet interface.  You need to have NetworkManager 0.7.* to create and configure ad-hoc networks.  Once you create the ad-hoc network, you can right click on the applet, and select "Edit Connections" and change the settings of your connections, such as, Automatic (DHCP addresses only).  I think NM 0.7.0 comes packaged with Jaunty (9.04) and newer.  Hope this helps.

Side note: I have a similar problem with my laptop connecting to an ad-hoc network I've created for only 1 or 2 seconds before dropping the connection.  I'm trying to get 3G connectivity through PDANet on my Dell Mini 9 and I'm kicking myself in the *** for not ordering it with the optional WWAN card installed!

I haven't yet tried the Automatic (DHCP addresses only) option yet, I'll give it a shot and get back to you guys.

---

### Post by KennyHAA on 2009-05-23
Update: the Automatic (DHCP Addresses Only) setting didn't help.  

I think it's a problem with my system, my laptop doesn't even seem be broadcasting the ad-hoc network I create.  Any suggestions?

---

### Post by Bad Penguin on 2009-06-16
> **ivanmladek said:**
> 
1) set up an adhoc network on Ubuntu 
2) connect to the network on your iphone
3) launch PDAnet and you should be good to go)


Is your ad-hoc network encrypted?

---

### Post by theborisx on 2009-07-11
I'm curious if anyone else is experiencing my issue. The network is created, and my phone connects fine. The problem is that it wont ever switch over to the 3g connection once its connected to the iphone; it is stuck on the adhoc network. Pdanet sees the connection to the computer, but reports that it doesn't see an internet connection. My phone connects corretly to my brother's PC fine so its not an issue with the phone. It seems to be an issue with ubuntu causeing the iphone not to flip over to the 3g. Any thoughts?

---

### Post by ump001 on 2009-07-12
hi,

i followed this guide to get my ad-hoc networking up and running correctly:

[http://www.ubuntugeek.com/creating-an-adhoc-host-with-ubuntu.html](http://www.ubuntugeek.com/creating-an-adhoc-host-with-ubuntu.html)

But only up to the following section:

Editing the UbuntAhoc network

Dont add in the manual IP settings basically. Leave it all on auto.
Then thats is, iPhone picked up the network, started PDAnet and all working :)

---

### Post by subsity on 2009-10-18
Ok before I upgraded to the new Ubuntu 9.10 this script worked with pdanet to tether my iphone. I was wondering if anyone out there can help me get it working again. Please this is my first post so be gentle. Thanks and I have used linux since 8.04 version and I love it!

I am going to post both scripts. Thanks to All the people who have contributed to the success of Ubuntu!
**This is the first script that allows me to get it working. **

 	Quote:
 	 	 		 			 				#!/bin/sh
# pdanet_on
sudo /etc/init.d/NetworkManager stop
sudo ifconfig eth1 down
sudo iwconfig eth1 mode ad-hoc
sudo iwconfig eth1 channel 4
sudo iwconfig eth1 essid 'laphone'
sudo iwconfig eth1 key cA1158tO
sudo ifconfig eth1 up
echo Press Enter when iPhone is connected to Network and PDANet is started
read foo
sudo dhclient eth1
DNS=`grep nameserver /etc/resolv.conf | head -1 | awk '{print $2}'`
dig @$DNS [www.google.com]("http://www.google.com/") 			 		 	 	 
[B]This is the second script to bring my network manager back and running
[/B] 
 	Quote:
 	 	 		 			 				#!/bin/sh
# pdanet_off
sudo ifconfig eth1 down
sudo iwconfig eth1 mode managed
sudo ifconfig eth1 up
sudo /etc/init.d/NetworkManager start 			 		 	 	 
**[COLOR=Black]Here are the errors I get now when I run this script[/COLOR]**

 	Quote:
 	 	 		 			 				sudo: /etc/init.d/NetworkManager: command not found
eth1: ERROR while getting interface flags: No such device
Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth1 ; No such device.
Error for wireless request "Set Frequency" (8B04) :
    SET failed on device eth1 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth1 ; No such device.
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "cA1158tO".
eth1: ERROR while getting interface flags: No such device
Press Enter when iPhone is connected to Network and PDANet is started

---

### Post by tampax on 2010-01-12
:popcorn:

goood stuff... on ubuntu 9.10 i had to kill the script, and afterwards using the network manager app connect to the iphone 3g adhoc network and it works..

---

