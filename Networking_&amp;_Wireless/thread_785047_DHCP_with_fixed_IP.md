---
title: "DHCP with fixed IP?"
date: 2008-05-07
forum: Networking &amp; Wireless
---

### Post by ign on 2008-05-07
I have a home network with a PC running Xubuntu and 2 laptops running Mac OSX. The PC is connected via ethernet and the laptops use wireless connection, the router is set to DHCP. I use the PC as a media server, so it would be very nice if I could have the same IP assigned every time I turn it on. Mac OSX has an "DHCP with fixed IP" on its network configuration that accomplishes this, but I can't find a way to do the same on my Linux machine.
Any tips?

---

### Post by subzero316 on 2008-05-07
open the /etc/network/interfaces file.

```
sudo gedit /etc/network/interfaces
```

you will see the following lines

auto eth0
iface eth0 inet dhcp

Itz using DHCP right now.  to change dhcp to static

auto eth0
iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1


All these can be configured for your preferences.
Restart the neworking service using the following command

```
sudo /etc/init.d/networking restart
```

---

### Post by jetsam on 2008-05-07
I'm not aware of an easy way to do this on the linux client, but you should be able to configure the router so that you can have a fixed ip on the desktop.  The exact details depend on your router.

If the router supports it (many, but not all do), you can reserve an ip address on the router for your pc's mac address.  This is usually fairly easy to set up in the router admin pages, and it's nice because it makes a central administration point for the ips on your network.  You then just use standard dhcp when you configure networking on the linux desktop and it will always get the same ip address.  

If your router doesn't support that, you can usually limit the range of ip addresses it assigns through dhcp.  As an example-- you can tell your router to only assign dhcp addresses in the range between 192.168.1.1 and 192.168.1.100.  Then you configure your desktop to have a static ip outside that range but still within the same subnet--  i.e. 192.168.1.101.  Doing this ensures you never get conflicting dual assignments of the same ip address.  

Hope that helps.  A lot of the details have more to do with your router model than with Xubuntu.

---

### Post by ign on 2008-05-08
Thanks for the help :)

@subzero316: The problem is that I want to keep having DHCP, but I want the linux box always gettin the same IP (now I see that my post wasn't clear explaining this).

@jetsam: That's what I've read elsewhere, apparently it's only doable through the router config, my Belkin router doesn't seem to have that possibility. I already limit the IP range in order to keep the MacBooks IP's separated, but everytime I restart the linux pc I get a different IP, the router seems to reserve for a very long time the IPs that it has assigned, but apparently not tied to the mac address(?). 

I'll post the solution here if I get to find it.

By the way, my router model is: Belkin F5D7633-4

---

### Post by chili555 on 2008-05-08
I don't believe having your router set to DHCP prevents, in any way, static addresses being used, as well. I have both on my Linksys WRT54G. The only caution is you do not want the statics and DHCPs to run over each other. So you might configure the router to issue a maximum of ten DHCP addresses, starting at 192.168.1.100. Then assign your static IPs, in your *interfaces* file, as outlined above, at, say, 192.168.1.115 and higher.

---

### Post by panda29 on 2008-05-18
You can accomplish this by placing the following configuration in [FONT="Courier New"]/etc/dhcp3/dhclient.conf[/FONT]:

```
alias {
  interface "eth0";
  fixed-address 192.168.1.5;
}
```

Obviously you should modify the interface and address values as required.

After running [FONT="Courier New"]/etc/init.d/networking restart[/FONT], ubuntu will be listening on two IP addresses, one assigned by DHCP as usual, and the other as specified in the dhclient alias configuration.

Note that you should probably make sure the address used in the alias block is outside the address range used by your DHCP server, in order to ensure it's always available for ubuntu.

There's no need to alter the /etc/network/interfaces file from the default shipped with ubuntu for this to work - in fact you should make sure it is unmodified.

---

### Post by dmizer on 2008-05-19
> **chili555 said:**
> I don't believe having your router set to DHCP prevents, in any way, static addresses being used, as well.
it does cause problems with local network name resolution and packet forwarding.  if you assign a static ip on a dhcp network, the router doesn't register the mac and packets are dropped.  not in all situations, but it does happen.

> **panda29 said:**
> You can accomplish this by placing the following configuration in [FONT="Courier New"]/etc/dhcp3/dhclient.conf[/FONT]:

```
alias {
  interface "eth0";
  fixed-address 192.168.1.5;
}
```

Obviously you should modify the interface and address values as required.

After running [FONT="Courier New"]/etc/init.d/networking restart[/FONT], ubuntu will be listening on two IP addresses, one assigned by DHCP as usual, and the other as specified in the dhclient alias configuration.

Note that you should probably make sure the address used in the alias block is outside the address range used by your DHCP server, in order to ensure it's always available for ubuntu.

There's no need to alter the /etc/network/interfaces file from the default shipped with ubuntu for this to work - in fact you should make sure it is unmodified.

this is a solution i've been searching for for a very long time.  thank you very much for this post.

---

