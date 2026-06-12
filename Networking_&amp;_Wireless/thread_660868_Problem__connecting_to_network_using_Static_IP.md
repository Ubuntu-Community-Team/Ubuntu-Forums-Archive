---
title: "Problem  connecting to network using Static IP"
date: 2008-01-07
forum: Networking &amp; Wireless
---

### Post by bellurashwin on 2008-01-07
hi,
I can cannot to the network in windows but in the same machine and with the same network configuration, i cannot connect to the network, i cannot ping to the gateway, and i cannot ping to other systems in the network also. 

Can anyone help me fix this issue.
Thanks in advance

Bellur Ashwin

---

### Post by stalker145 on 2008-01-07
> **bellurashwin said:**
> hi,
I can cannot to the network in windows but in the same machine and with the same network configuration, i cannot connect to the network, i cannot ping to the gateway, and i cannot ping to other systems in the network also. 

Can anyone help me fix this issue.
Thanks in advance

Bellur Ashwin

What kind of hardware are we dealing with here? Type ```
lshw
```into the terminal and post the output here. Also, if you would like to post the general make/model of computer, we can try to help you out.

There are a lot of network cards that work fine in Windows but need some TLC when running in Linux. Don't despair.

---

### Post by mips on 2008-01-07
You are not supplying enough info.

1. Please post output of **ifconfig eth0  ** (Depends on your interface number)
 2. Please post output of **lspci | grep Eth**
 3. Please post output of **route -n**
 4. Please post output of **cat /etc/resolv.conf**
 5. Please post output of **cat /etc/network/interfaces**
 6. Please post output of **cat /etc/dhcp3/dhclient.conf**
 7. Please copy entire output of **windows ipconfig /all **command here

---

### Post by bellurashwin on 2008-01-08
Hi all,
Thanks for the replies. I have attached the outputs of all the commands you asked.
Outputs of all the linux related commands are in dhclient.txt.
Windows configuration is in windows.txt
 Kindly help me.

[ATTACH]55694[/ATTACH]

[ATTACH]55695[/ATTACH]

---

### Post by stalker145 on 2008-01-08
> **bellurashwin said:**
> Hi all,
Thanks for the replies. I have attached the outputs of all the commands you asked.
Outputs of all the linux related commands are in dhclient.txt.
Windows configuration is in windows.txt
 Kindly help me.

[ATTACH]55694[/ATTACH]

[ATTACH]55695[/ATTACH]

OK, I don't know if this could be causing a problem (probably not) but in your interfaces for lo, you have ```
auto lo

iface lo inet loopback

address 127.0.0.1

netmask 255.0.0.0
```which I don't believe is strictly necessary. At least, mine doesn't have it and it works without issue```
auto lo
iface lo inet loopback

```

Your ethernet card (RTL-8139/8139C/8139C+) shows up in the [Hardware Compatibility list]("https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCardsRealtek") as working without issue, so that's *obviously* not the problem.

I would suggest, unless someone else has a brighter idea, to back up your interfaces file and remove the address and netmask from your loopback interface and give that a shot... I'm kinda at a loss.

Worst case scenario, if my idea doesn't work, you can always replace the newer interfaces file with the backup and be back where you are now.

---

### Post by polybius on 2008-01-08
I have a very similar problem, and static IP address seems to be part of it.  The internet connection works fine with this cable when I attach to my Mac laptop, so I'm sure it's working.  (Of course I have to configure the ip address in the Mac.)

I just bought a Dell Dimension second hand.  Before buying it, I ran the Ubuntu 7.10 liveCD.  At that time the machine was connected to a DHCP server.  Ubuntu found the internet connection just fine in that case.  Now I take t his computer to my work where I have the static ip address, I installed Ubuntu from the same CD, and no internet connection.

To try to diagnose the problem,  I opened the Network item under Administration.  It lists 2 connections:  Wired Connection and Modem Connection, but no ethernet.

So I opened Network Tools.  It shows 3 network devices:  Loopback, Ethernet interface (eth0), and Ethernet interface (eth0:avahi).  If I select eth0, it says iPv6, and configure button is not operational so I can't do anything.  If I select eth0:avahi, it say iPv4, and when I click Configure it says, "Interface does not exist".

Next I opened Hardware Information.  It says
82801DB PRO/100 VE (LOM) Ethernet Controller (Intel)
Networking Interface "net","net.80203"

Here is content of /etc/network/interfaces:
auto lo
iface lo inet loopback

This is not the same as interfaces file of the original poster, so maybe the problems are not the same.  I haven't run all the other commands requested because I have to copy them by hand, but I can do that if it will help.

Any help would be appreciated.

---

### Post by polybius on 2008-01-08
I solved my problem by following instructions at
[http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html](http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html)

Is it possible that I could have taken care of this problem by clicking on "Wired connection" under the Network tool?  It's too late to find out now, but my recollection is that I tried that and it didn't work.  

I hope I haven't muddied the waters here...but thanks for your tolerance.

---

### Post by bellurashwin on 2008-01-09
I tried removing address and netmask for the loopback (lo). Now when i restart network using /etc/init.d/networking restart command, i get the error message "SIOCDELRT no such process".

I am stuck up here dont know how to restore the network connection.

---

