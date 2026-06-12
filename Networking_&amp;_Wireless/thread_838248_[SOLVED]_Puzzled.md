---
title: "[SOLVED] Puzzled"
date: 2008-06-23
forum: Networking &amp; Wireless
---

### Post by daggerx on 2008-06-23
I connect to every network that I attempt to connect to accept for my church network. My church network is verizon DSL. As the admin of my church, its weird that everyone can connect via windows (wifi) and I can to but when I try to use my ubuntu to connect it cycles and does not connect at all.

so here's what I got, I'm gonna assume as a noob that is information is what you need to see if my card is setup properly. Since I can connect everywhere else, this is weird to me:

```
*-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: BCM4310 USB Controller
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:0b:00.0
                logical name: eth1
                version: 01
                serial: 00:1f:e1:0f:ea:5c
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
```

If not I attached the lshw results (I feel like I know what I'm talking about right now :))

At home, I have a hidden ssid and running WPA2+AES for my laptop (1525). Open school networks (I connect no problem). 

Would an IP conflict cause me to "not connect" even though the church is DHCP. Please advise and thanks.

---

### Post by plewisfdx on 2008-06-23
I think since you can connect at home using wpa2 on ubuntu (correct?) that your card is setup properly.

Re-check your wifi settings on the ubuntu side at your church.  

Ubuntu & Vista both work at home.

Vista works / Ubuntu doesn't work at church.  Right?

What router, wep/wpa, at church?

What wifi manager are you using on ubuntu?  wireless-manager is default.

---

### Post by daggerx on 2008-06-23
> **plewisfdx said:**
> I think since you can connect at home using wpa2 on ubuntu (correct?) that your card is setup properly.

Re-check your wifi settings on the ubuntu side at your church.  

Ubuntu & Vista both work at home.

Vista works / Ubuntu doesn't work at church.  Right?

What router, wep/wpa, at church?

What wifi manager are you using on ubuntu?  wireless-manager is default.

**Yes** - Ubuntu & Vista both work at home.

Vista works / Ubuntu doesn't work at church.  Right? **Correct.**


What router, wep/wpa, at church? **WPA**

What wifi manager are you using on ubuntu?  wireless-manager is default. **Default**, is there a better one?

Thanks.

---

### Post by daggerx on 2008-06-26
The router is a Westell 327W, not sure if there is an firmware upgrade for it or anything. I recently ( May 2008 ) setup someone's home with wifi and they also have a 327W and I connected via linux no problem. Could this be a firmware issue?

---

### Post by plewisfdx on 2008-06-26
> **daggerx said:**
> The router is a Westell 327W, not sure if there is an firmware upgrade for it or anything. I recently ( May 2008 ) setup someone's home with wifi and they also have a 327W and I connected via linux no problem. Could this be a firmware issue?

Probably not, I wanted to know so I could look into the settings for that router.

In your original post you asked "would an IP conflict cause problems," and the answer is yes.  If your ubuntu is set to a static IP that is already issued to someone, it would either not connect, or cause connection/packet problems.

I asked which wifi manager you used because your /etc/network/interfaces will be nearly blank if you use network manager or similar.  I just switched to wicd ([http://wicd.sourceforge.net/wiki/doku.php?id=faq&DokuWiki=7cb26d9d88e07d3559b53cd52d123af4](http://wicd.sourceforge.net/wiki/doku.php?id=faq&DokuWiki=7cb26d9d88e07d3559b53cd52d123af4)) if you want to try another one.  I was sick of the prompts for keyring password.

You said it "cycles and doesn't connect" so that means you can "see" the network, but not connect, right?

Try this at church in a terminal:
```
sudo /etc/init.d/networking restart
```

and watch the dhcp and paste the output.

---

### Post by daggerx on 2008-06-30
I should be there on wednesday, and I will try this (I hope I remember) still no go with linux at the church but I will try that in the terminal and save it to paste it here...

I concluded that it is the router since i can connect everywhere else - including a router identical to the one at the church.

---

