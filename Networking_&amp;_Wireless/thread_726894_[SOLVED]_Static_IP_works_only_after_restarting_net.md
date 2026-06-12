---
title: "[SOLVED] Static IP works only after restarting networking, not after boot"
date: 2008-03-17
forum: Networking &amp; Wireless
---

### Post by bronkeydain on 2008-03-17
I have this strange problem... I have re-configured my Gutsy machine for static ip address by updating /etc/network/interfaces as below. The strange part is it works only when I restart networking, but not after a reboot. :confused:

--------- /etc/network/interfaces ------------------------------
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.0.0.2
netmask 255.255.255.0
gateway 10.0.0.1

---

### Post by bronkeydain on 2008-03-17
In case I did not make myself clear, when I reboot I get an address from DHCP. when I type /etc/init.d/networking restart, it works on static again. My machine is put away in a corner without a screen, and I access through ssh only so static IP would be handy....

---

### Post by Eiríkr on 2008-03-17
I am baffled why your machine would even attempt to get a DHCP lease with this interfaces file.  Anyone else have any clues what's up with this?

That aside, one workaround in the meantime would be to mimic a static IP config by setting up your DHCP server (likely your router?) to grant set IP addresses on the basis of the requesting machine's MAC address.  I could be wrong, but I think most consumer routers include something along these lines; my old D-Link DI-524 had this, and my replacement D-Link WBR-2310 also does.  

Cheers,

Eiríkr

---

### Post by wieman01 on 2008-03-17
Which version of Ubuntu do you run? Have you removed network manager? Or is it the server version?

---

### Post by Iowan on 2008-03-17
> **Eiríkr said:**
> I am baffled why your machine would even attempt to get a DHCP lease with this interfaces file.  Anyone else have any clues what's up with this?
I've seen threads where **dhclient** runs anyway - updates static addresses w/ dynamic ones - or resets DNS addresses.  Unfortunately, I don't remember how to "shut it off".

---

### Post by Eiríkr on 2008-03-17
Thanks for the lead, Iowan -- your post reminded me of Network Manager's odd behaviour.  

@bronkeydain --

Following on Wieman's and Iowan's comments, your trouble might be due to Network Manager, if you've got it installed.  NM has a bad habit of ignoring any changes to /etc/network/interfaces and overwriting the file with NM's own configuration data (though I have no idea where this is stored).  My memory has been slow to engage today, but I now recall that I had similar issues a while back when trying to switch to a static IP address, and found I had to make the change in NM or it wouldn't work (or, I suppose you could uninstall NM instead).  

If you do indeed have NM on your server machine, either remove it, or find some way of opening it up (it's a GUI app), select the Connections tab, click the appropriate connection, hit the Properties button, and make sure the Configuration dropdown is set to "Static IP address", with the fields below filled in as apporpriate.  

HTH,

Eiríkr

---

### Post by wieman01 on 2008-03-17
If you happen to use NM then static IP addresses won't work. NM can only handle DHCP. So removing NM entirely will help.

---

### Post by Eiríkr on 2008-03-17
@Wieman --

That's odd, as I've got NM with a static IP address...?

---

### Post by bronkeydain on 2008-03-17
Hi peeps,

Thanks for all your replies, I appreciate it.

I have Ubuntu Gutsy 7.10 desktop. But I use it as a server and have removed X11 and a lot more (long story, but yes I could have used ubuntu server :)

After removing network manager all works fine now. Thanks Wieman01 and Eiríkr and Iowan too.

---

### Post by wieman01 on 2008-03-18
> **Eiríkr said:**
> @Wieman --

That's odd, as I've got NM with a static IP address...?
Probably not the NM I am referring to. There are 2 networking applets. One can handle static IP addresses, but fails when it comes to WPA security for wireless networking. The other one does WPA but only using DHCP. Hardy will fix that.

---

