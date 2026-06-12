---
title: "desktop crossover to laptop to wireless router"
date: 2005-10-07
forum: Networking &amp; Wireless
---

### Post by matthew on 2005-10-07
Been searching these forums and Google and haven't had any luck with my specific idea yet so I figured I'd just start a thread.

I just picked up an old desktop for pennies and I'm using it as a testbed for learning linux and experimenting with stuff without risking my main machine's configuration. So far I have tried out several different distros and stuff on it and am having a lot of fun doing installations from cds. This computer is in my home office where I do not have wired ethernet. I would like to be able to download updates and stuff to this test computer.

The easy and obvious answer is just to move the testbed computer to the room where the router is and plug in, but I bought this to test and learn new stuff and that's just too easy.

I do have a wireless router in another room in the house that I connect my laptop to while I am working in my home office where the testbed computer is. It uses wpa and I have a very fast and stable connection between the router and my laptop. My laptop sits on a desk right next to this new testbed computer.

What would I have to do configuration-wise in order to connect from the testbed computer via crossover cable to the laptop ethernet card (eth0) and forward that to the wireless card (eth1) with access to the internet without disrupting the usefulness of the laptop as my main work computer/internet access?

Wow, long sentence.

I want to do this:
testbed->crossover cable->laptop(eth0)->laptop(eth1)->router and internet

What I presume I need to do is continue to use the laptop's eth1 as I am, with DHCP and so on, but configure its eth0 to use a set of static ip addresses and then configure the tester's eth0 to use static ip's as well. However, as a total newbie at this (doing it in order to learn something) I am really not sure what static ips to choose for each and so on.

Any home/office networking tsars out there with ideas that are interested in helping me have a little fun?

---

### Post by mlomker on 2005-10-07
> However, as a total newbie at this (doing it in order to learn something) I am really not sure what static ips to choose for each and so on.


You should use something like 192.168.1.1 and .2 with a mask of 255.255.255.0 (the important thing is that it has to be different than your wireless connection).  You'll need to plug in the real DNS server addresses for your internet provider.

Then install **firestarter** on your laptop and walk through the setup to configure it to perform NAT (network address translation).  It should work fine.

---

### Post by Zelut on 2005-10-07
That is a question I've been wondering about as well.  Under XP I could click 'share internet connection' and not even use a crossover cable.  I would like to be able to do that with my machines too.  If you do get it to work could you put together a HOWTO?  I've got all of my machines near my main modem/router too, just for that reason.  It sure would be easier to be able to use the notebook as a wireless hub for testing.

---

### Post by matthew on 2005-10-08
[quote=mlomker]You should use something like 192.168.1.1 and .2 with a mask of 255.255.255.0 (the important thing is that it has to be different than your wireless connection). You'll need to plug in the real DNS server addresses for your internet provider.

Then install **firestarter** on your laptop and walk through the setup to configure it to perform NAT (network address translation). It should work fine.[/quote] 
Thanks for the response and for your help! I appreciate it.

Here's what I have done:

Laptop config in Network Settings:
  eth0
    Static IP address
    IP address: 192.168.1.102
    Subnet mask: 255.255.255.0
    Gateway mask: 192.168.15.1 (from router status page listed as "Default Gateway")
  eth1 (wireless)
    Configuration: DHCP

Testbed config:
  eth0
    Static IP address
    IP address: 192.168.1.103
    Subnet mask: 255.255.255.0
    Gateway address: 192.168.15.1

Router
  IP address: 192.168.15.100
  Default gateway: 192.168.15.1
Subnet mask: 255.255.255.0
  DNS: xxx.xxx.xxx.xxx
  *for me to log into my router from any computer on the network the address is 192.168.1.1 so I can't use that elsewhere.
  *the router has assigned these addresses to computers using it: 192.168.1.100 and 192.168.1.101

I have been using lokkit to configure my firewall, so I'm not familiar with Firestarter, but I disabled lokkit and installed Firestarter. In Firestarter:
  Edit->Preferences->ICMP filtering
    Enable ICMP filtering
      Echo request (ping)
      Redirection
    Network Settings
      Internet Network Connected Device: eth1
      Local Network Connected Device: eth0
      Enable Internet Connection Sharing
*also opened port 22 as I ssh between the two computers already connecting through the router on a regular basis.

Okay, that's all done. If I ping 192.168.1.101 (desktop in another room connected to router by ethernet cable) from my laptop 192.168.1.100 I get no response (ping is turned of at the firewall). I can login there via ssh as that is turned on.

If I try to ping 192.168.1.102/3 from or to one another I get 100% packet loss with "destination host unreachable."

If I try to ping 192.168.15.1 from the testbed I get "network is unreachable." ping [www.google.com]("http://www.google.com") gives "unknown host www.google.com"

I tried changing the subnet mask on the laptop eth0 from 255.255.255.0 but any other setting causes "could not enable the interface eth0"

Anyway, I may be close, but I'm not yet there. What should I try next?

---

### Post by mlomker on 2005-10-08
> 
    IP address: 192.168.1.103
    Subnet mask: 255.255.255.0
    Gateway address: 192.168.15.1


I can't thoroughly explain TCP/IP without delving into binary math (and I hate math).  The simple thing to keep in mind is that your gateway *always* has to be on the same subnet as one of your interfaces.  On your desktop machine the gateway IP would be the address for your laptop's ethernet port.

> 
  *for me to log into my router from any computer on the network the address is 192.168.1.1 so I can't use that elsewhere.


If your wireless is 192.168.1.x then your ethernet has to be on a different subnet.  Change it to 192.168.2.x instead.

---

### Post by matthew on 2005-10-08
Thank you!! That has brought me closer, though I am still lacking some understanding and coming up a little bit short. I have changed my configuration based on your advice ad can now ping my laptop from the desktop and get a response with no packet loss. That is a big step. The forwarding is not yet working, though.

mlomker, you have been very helpful so far and I appreciate it. If you decide to just give me some ideas of what to search for in Google to learn about the subject that would still be appreciated. After all, I'm just doing this to try to learn something. If you have any specific advice, though, I am all ears.

Here's where I am at specifically:

desktop setup
ip address: 192.168.2.103
subnet mask: 255.255.255.0
Gateway address: 192.168.2.102

laptop setup
eth0
ip address: 192.168.2.102
subnet mask: 255.255.255.0
Gateway address: 192.168.15.100
eth1 (wireless)
DHCP

From the desktop I can now ping the laptop successfully. I can also connect to the laptop via ssh.

From the laptop I have full internet access, but I cannot ping the desktop which probably needs some ports opened--but it doesn't yet have internet access so I can't install firestarter to open them and need to figure out how to do so from the command line...I figure it probably isn't that hard, but I don't know how to do it. I can connect from the laptop to the desktop via ssh.

From the desktop I have no internet access and can't ping anything beyond the laptop...not even my router, so I don't think I have the forwarding set up properly. Redirection is turned on in firestarter, but there must be something I am missing here.

Thanks to any and all for any help/advice/links you might have to keep learning.

---

### Post by mlomker on 2005-10-08
> From the desktop I have no internet access and can't ping anything beyond the laptop...not even my router, so I don't think I have the forwarding set up properly. Redirection is turned on in firestarter, but there must be something I am missing here.


To clarify...firestarter is installed on the laptop, correct?  [Here's a tutorial]("http://www.fs-security.com/docs/connection-sharing.php") with some pictures, which might help

---

### Post by matthew on 2005-10-08
[quote=mlomker]To clarify...firestarter is installed on the laptop, correct?  [Here's a tutorial]("http://www.fs-security.com/docs/connection-sharing.php") with some pictures, which might help[/quote]

I just reread my post and notice I was a little unclear. Sorry about that. Firestarter is installed on the laptop and not on the desktop (no internet access and not on the install cd).

I will take a look at the link after lunch. Thanks!

---

### Post by matthew on 2005-10-08
woo hoo! Closer yet. I can now ping the router from the desktop going through the laptop. This is progress. The only change I made was to install firestarter on the desktop by making an ssh connection to the laptop and copying the .deb from /var/cache/apt/archives and then installing using dpkg -i. I ran and configured firestarter on the desktop to get the right ports open and away we go.

No changes in any of this from before:

 desktop setup
 ip address: 192.168.2.103
 subnet mask: 255.255.255.0
 Gateway address: 192.168.2.102
 
 laptop setup
 eth0
 ip address: 192.168.2.102
 subnet mask: 255.255.255.0
 Gateway address: 192.168.15.100
 eth1 (wireless)
 DHCP

 Router
   IP address: 192.168.15.100
   Default gateway: 192.168.15.1
 Subnet mask: 255.255.255.0
   DNS: xxx.xxx.xxx.xxx
   *for me to log into my router from any computer on the network the address is 192.168.1.1
*the router has assigned these addresses to computers using it: 192.168.1.100 and 192.168.1.101 and has reserved for computers on the network all addresses from 192.168.1.100 to 192.168.1.149

I can successfully ping from the desktop, through the laptop these addresses:
192.168.2.102
192.168.1.1
192.168.15.1
192.168.1.100 (another address for the laptop)
192.168.1.101 (a different desktop in another room connected to the router via ethernet)

I can also ping the 3 DNS addresses assigned to my router from my ISP through DNS. (Found them listed in the router config.)

However, I can't ping anything past my router using names like google.com--I get the output:
ping: unknown host  google.com

After pinging google.com from the laptop I got this:
$ ping -c3 google.com
PING google.com (216.239.37.99) 56(84) bytes of data.
64 bytes from 216.239.37.99: icmp_seq=1 ttl=241 time=101 ms
64 bytes from 216.239.37.99: icmp_seq=2 ttl=241 time=94.2 ms
64 bytes from 216.239.37.99: icmp_seq=3 ttl=241 time=97.3 ms

--- google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 94.242/97.730/101.565/3.021 ms

So from the desktop I chose to ping 216.239.37.99 and got similar successful output.

If I use my browser (firefox) on the desktop to try to connect to google.com I get:
[www.google.com]("http://www.google.com") could not be found. Please check the name and try again.

If I try to connect to 216.239.37.99 using firefox from the laptop it takes me straight to Google's home page. From the desktop it says "connecting to 216.239.37.99..." in the bottom left corner of the browser window for a very long time until it times out.

I really am having fun with this and I am learning some of the inner workings here--so far I am not frustrated at all, but rather hopeful.

Could it be that I need to change something in the router's setup to allow throughput in the 192.168.2.xxx range. I am just taking a ***wild*** guess. My router is a Linksys wrt54g if that helps. 

The other option I am guessing at is maybe ther is a port that still needs to be opened using firestarter on the desktop?

EDIT: I found my problem!! I had set up everything correctly in firestarter on the laptop except for one thing. On the main window, selecting the "Policy" tab, at the bottom I configured "forward service" for inbound traffic as follows:
Forward service DHCP Firewall port 67-68 to 192.168.2.103 port 67-68

EDIT#2: A few minutes later. I spoke a little too soon. This is amusing. I can connect to any web site from the desktop if I know the IP address. For example, I can't connect (firefox or ping is the same) to google.com, but I can connect to 216.239.37.99, I can't connect to ubuntuforums.org, but I can connect to 64.21.33.9

Now I'm really stumped and amused at the same time. It has to be something simple, I just can't see it.

---

### Post by mlomker on 2005-10-08
> Now I'm really stumped and amused at the same time. It has to be something simple, I just can't see it.

Is the desktop configured via DHCP from the laptop, the router, or with a static address?

The answer is in the /etc/resolv.conf file.  The fix is going to vary depending upon how you have it set up.

---

### Post by matthew on 2005-10-08
[quote=mlomker]Is the desktop configured via DHCP from the laptop, the router, or with a static address?

The answer is in the /etc/resolv.conf file.  The fix is going to vary depending upon how you have it set up.[/quote] 
The desktop is configured with a static address (precise location listed above), the laptop with a static for the ethernet and DHCP from the router for the wireless.

I looked at my /etc/resolv.conf from the laptop and found the nameservers listed. The one on the desktop was an empty file. i copied the one from the laptop to the desktop and now it all works!!

That was the final step. Thank you! This has been a fun day.

Huge thanks to mlomker!

For kuyaedz, I will try to do a clear and detailed howto on this soon. Watch for it. If you think of a better title for the howto than what I have used here, let me know.

If anyone wants to try to do what I did, waiting for the howto will help you eliminate a few of the unnecessary steps I did here.

---

### Post by mlomker on 2005-10-08
For your desktop you can install **resolvconf** and add a line to your /etc/network/interfaces file to set your DNS server entries automagically:

```

iface eth0 inet static
  dns-nameservers xxx.xxx.xxx.xxx xxx.xxx.xxx.xxx
  dns-search whatever.com 

```

---

### Post by matthew on 2005-10-08
[quote=mlomker]For your desktop you can install **resolvconf** and add a line to your /etc/network/interfaces file to set your DNS server entries automagically:

```

iface eth0 inet static
  dns-nameservers xxx.xxx.xxx.xxx xxx.xxx.xxx.xxx
  dns-search whatever.com 

```[/quote]

That worked beautifully. Thanks! It would have gotten old quickly to have to re-do resolv.conf every time I rebooted.

---

### Post by Zelut on 2005-10-08
So what configuration do you finally come up with?  I've been following this thread but not sure what the final picture looks like.  Share? ;)

---

### Post by matthew on 2005-10-08
[quote=matthew]For kuyaedz, I will try to do a clear and detailed howto on this soon. Watch for it. If you think of a better title for the howto than what I have used here, let me know.

If anyone wants to try to do what I did, waiting for the howto will help you eliminate a few of the unnecessary steps I did here.[/quote]

[QUOTE=kuyaedz]So what configuration do you finally come up with? I've been following this thread but not sure what the final picture looks like. Share? [/QUOTE]

It is coming shortly...I have some free time tonight and I wll try to write a how-to. I'll post a link in this thread when I get it done.

---

### Post by matthew on 2005-10-09
I wrote a HOWTO for this. It is here: [http://ubuntuforums.org/showthread.php?p=396085](http://ubuntuforums.org/showthread.php?p=396085)

---

