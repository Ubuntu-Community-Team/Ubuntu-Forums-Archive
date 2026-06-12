---
title: "Is there anything for Ubuntu like this?"
date: 2010-07-26
forum: New to Ubuntu
---

### Post by adamjkok on 2010-07-26
I've used this really handy program on Windows called [Connectify]("http://connectify.me"). Basically, it makes use of Microsoft's virtual Wi-Fi adapter to rebroadcast your Internet connection, regardless of whether or not that connection was also wireless. This is useful, for example, if you're at a hotel that charges for Wi-Fi, and it does not require MAC spoofing. Can someone visit the link and read about this and tell me if there's something similar for Ubuntu? It needs to be able to rebroadcast a Wi-Fi connection. Thanks!

---

### Post by viralmeme on 2010-07-26
Couldn't you turn on IP-Forwarding and get the same results?

[Configuring a Linux Wireless Router]("http://martybugs.net/wireless/router.cgi")

---

### Post by aeiah on 2010-07-26
nothing as automatic, but its possible. most well-supported wireless cards in linux can be put into access point mode, and then its just a matter of routing incoming traffic. i suspect the easiest wireless cards are ones supported by madwifi.

---

### Post by adamjkok on 2010-07-26
> **viralmeme said:**
> Couldn't you turn on IP-Forwarding and get the same results?

[Configuring a Linux Wireless Router]("http://martybugs.net/wireless/router.cgi")
:confused:

---

### Post by NFblaze on 2010-07-26
> **adamjkok said:**
> This is useful, for example, if you're at a hotel that charges for Wi-Fi, and it does not require MAC spoofing.

Huh?

---

### Post by mbsullivan on 2010-07-26
To be perfectly clear, you have a free hardwired connection, connected to a laptop (running Ubuntu) with a wireless NIC. You want to be able to share the free connection with OTHER wireless enabled devices, in order to avoid the wifi service which you must pay for. Right?

If your wifi card supports it then [master mode]("https://help.ubuntu.com/community/WifiDocs/MasterMode") can do it, though it's non trivial. After running the following command:

```
sudo iwconfig [wireless interface] mode master
```

You'll then want to bridge the wireless interface to the wired one (see [here]("http://www.linux.com/archive/feed/55617") and [here]("http://www.ibm.com/developerworks/library/l-wap.html")). 

You can also get some tips from [here]("http://ubuntuforums.org/showthread.php?t=376283")... In your case, it doesn't need to be fancy, so you can go WITHOUT things like encryption and a firewall. DHCP might actually be easier, since it won't require any changes on the client side.

It's DEFINITELY not as easy as a GUI-based program, like under Windows. It might take 10 minutes, or could turn into an all day thrashing, I'm not sure.

If your wireless NIC doesn't support master mode, you're stuck with ad hoc networking or other trickery (SSH/HTML tunneling or maybe mac address hackery to get past the pay-for service).

Mike```

```

---

### Post by adamjkok on 2010-07-26
> **mbsullivan said:**
> To be perfectly clear, you have a free hardwired connection, connected to a laptop (running Ubuntu) with a wireless NIC. You want to be able to share the connection with OTHER wireless enabled devices, in order to circumvent the service which you must pay for. Right?

If your wifi card supports it then [master mode]("https://help.ubuntu.com/community/WifiDocs/MasterMode") can do it, though it's non trivial. After running the following command:

```
sudo iwconfig [wireless interface] mode master
```You'll then want to bridge the wireless interface to the wired one (see [here]("http://www.linux.com/archive/feed/55617") and [here]("http://www.ibm.com/developerworks/library/l-wap.html")). 

You can also get some tips from [here]("http://ubuntuforums.org/showthread.php?t=376283")... In your case, it doesn't need to be fancy, so you can go WITHOUT things like encryption and a firewall. DHCP might actually be easier, since it won't require any changes on the client side.

It's DEFINITELY not as easy as a GUI-based program, like under Windows. It might take 10 minutes, or could turn into an all day thrashing, I'm not sure.

If your wireless NIC doesn't support master mode, you're stuck with ad hoc networking or other trickery (SSH/HTML tunneling or maybe mac address hackery to get past the pay-for service).

Mike
So, about the HTML tunneling, would it be possible to connect to, for example, HHONORS (Hilton's default SSID), and then run an ad-hoc network at the same time with the SSID set to INSPIRON1545, and then share it via a proxy? If so, how? Which proxy would be best to use and how do I install it? I would also want to set a WPA key on the ad-hoc network.

---

### Post by mbsullivan on 2010-07-26
> 
So, about the HTML tunneling, would it be possible to connect to, for example, HHONORS (Hilton's default SSID), and then run an ad-hoc network at the same time with the SSID set to INSPIRON1545, and then share it via a proxy? If so, how? Which proxy would be best to use and how do I install it? I would also want to set a WPA key on the ad-hoc network. 

Some sort of tunnelling would be more of a direct solution: you connect all of the wifi devices to Hilton's Wifi network, use SSH/DNS tunneling to send their traffic through an external computer, which is not on the network. Depending on how the wifi is set up, you might have to go through contortions. You'll need to figure out which (if any) destination ports are allowed through the firewall in this case.

There are some material limitations here, though. Each (and every) computer must have an SSH/DNS tunnelling client. Also, you'll need some computer OUTSIDE of the network, with a publically accessible IP address (if it's behind a NAT, you'll need to forward ports). This is also probably against the network usage policy (though since the companies set those policies, creating an access point may also be). In part because of the ethical concerns, I don't necessarily think this is a good solution for you. However, it's useful to mention it here, because it may be a viable solution for somebody in a different situation.

I something like Ad-Hoc + proxy server, which should also be possible, as a completely separate solution. In this case, you'd set the computer which is hooked up to the Ethernet jack as a proxy server, and ad-hoc the networks together. Set the address of the proxy server in Firefox and you should be able to surf the web.

Ad-hoc networking is a pain, in my experience. I've set up a proxy server though, it's easy.

```
sudo aptitude install squid
vi /etc/squid/squid.conf
```

You need to make some changes in squid.conf to allow a range of IP addresses access, and to tell it the right interface to listen on. See [here]("http://en.kioskea.net/faq/804-ubuntu-installing-an-http-proxy-server-squid") for details, they seem pretty solid.

Mike

PS: On second thought, if you get the ad-hoc network working between the computers WITHOUT encryption, you should be able to use SSH tunnels BETWEEN the computers. This has two advantages:

[INDENT](1) You get secure communication without the need for WPA nastiness
(2) You don't have to set up a proxy server[/INDENT]

And one disadvantage:

[INDENT](1) You need an SSH client on all of the computers.[/INDENT]

It seems like a good overall solution, though. It assumes an ad-hoc network to begin with, though. Also, there may be unseen interface routing ugliness, but you'll risk that with any fix which shares the Ethernet connection.

---

### Post by adamjkok on 2010-07-27
How about if I brought along a spare USB Wi-Fi adapter to use as the ad-hoc access point and used the internal card on HHONORS?

---

### Post by adamjkok on 2010-07-27
> **mbsullivan said:**
> Some sort of tunnelling would be more of a direct solution: you connect all of the wifi devices to Hilton's Wifi network, use SSH/DNS tunneling to send their traffic through an external computer, which is not on the network. Depending on how the wifi is set up, you might have to go through contortions. You'll need to figure out which (if any) destination ports are allowed through the firewall in this case.

There are some material limitations here, though. Each (and every) computer must have an SSH/DNS tunnelling client. Also, you'll need some computer OUTSIDE of the network, with a publically accessible IP address (if it's behind a NAT, you'll need to forward ports). This is also probably against the network usage policy (though since the companies set those policies, creating an access point may also be). In part because of the ethical concerns, I don't necessarily think this is a good solution for you. However, it's useful to mention it here, because it may be a viable solution for somebody in a different situation.

I something like Ad-Hoc + proxy server, which should also be possible, as a completely separate solution. In this case, you'd set the computer which is hooked up to the Ethernet jack as a proxy server, and ad-hoc the networks together. Set the address of the proxy server in Firefox and you should be able to surf the web.

Ad-hoc networking is a pain, in my experience. I've set up a proxy server though, it's easy.

```
sudo aptitude install squid
vi /etc/squid/squid.conf
```You need to make some changes in squid.conf to allow a range of IP addresses access, and to tell it the right interface to listen on. See [here]("http://en.kioskea.net/faq/804-ubuntu-installing-an-http-proxy-server-squid") for details, they seem pretty solid.

Mike

PS: On second thought, if you get the ad-hoc network working between the computers WITHOUT encryption, you should be able to use SSH tunnels BETWEEN the computers. This has two advantages:
[INDENT](1) You get secure communication without the need for WPA nastiness
(2) You don't have to set up a proxy server[/INDENT]And one disadvantage:
[INDENT](1) You need an SSH client on all of the computers.[/INDENT]It seems like a good overall solution, though. It assumes an ad-hoc network to begin with, though. Also, there may be unseen interface routing ugliness, but you'll risk that with any fix which shares the Ethernet connection.
Here's why WPA is still important:

[LIST]
[*]Someone could use the network to illegally download stuff like copyrighted music and movies and/or child pornography. Provided the connection could be traced (which is pretty much not even a question in the United States or pretty much any country with the money to find you) back to the "originating" laptop, *I* would be held responsible.
[*]Someone could also use the network to *send* stuff, like spam and threats. Not to mention if they *distrubuted* any of the above-mentioned legal trouble.
[*]The majority of the clients will be iPods. Even though it *is* indirectly UNIX-based, Apple has everything so locked down that it's not even funny. Sure, there's iPod Linux (not to mention jailbreaking) and stuff like that, but only one of the iPods will be *my* iPod. Because of this, standard WPA (*possibly* WEP) is neccessary.
[/LIST]

---

