---
title: "Broke my ubuntu server!"
date: 2010-05-21
forum: New to Ubuntu
---

### Post by kiwixboxer on 2010-05-21
Hey there,
I am sooo... frustrated. Been mucking with this os for about 24 hours and still not getting anywhere.

all I wanted to achieve was a simple print and file server that could connect my windows machines to for serving files and printers.

So... I went about setting up VMware as a test base first! (glad I did not go full monty and commit to the change of OS)
no matter what info I read about changing the DHCP config in the /etc/network/interfaces file.... I could not get the settings to work.

the VM ware assigned a virtual network card that windows could see ... and all worked well on dhcp.... (could browse and ping in the ubuntu client).... when ever I changed the settings on the interfaces file .... internet connectivity was lost. change it back to DHCP ... and all good. 

then I deleted some DHCP client (i think it was dhcp3) as I was installing ebox kit - they said it was easy!!!

now I am unable to re install a dhcp client as ther is no connection to the net anymore :O(
pretty much over it now .... so will simply move away from this so called powerful txt based os ... and just go dumbo mode with the masses on win 7

any help?

---

### Post by The Cog on 2010-05-21
My guess is that you didn't configure the DNS server when you manually configured the interfaces. DNS is configured in /etc/resolv.conf. As an example, I have a server configured statically with these two files:

/etc/network/interfaces:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.101
netmask 255.255.255.0
gateway 192.168.1.1
```
/etc/resolv/conf:```
nameserver 192.168.1.1
```
Try configuring the DNS server and rebooting.

Next time, don't uninstall the DHCP server, just configure the machine not to use it. That way you're not burning bridges behind you. The above config disables the DHCP client, or rather, doesn't start it.

If you're just learning the OS, you are probably better off installing the desktop version. You'll find configuring that much easier. Unless ebox does that for you - I don't jnow what ebox is.

---

### Post by Locke_99GS on 2010-05-21
> **kiwixboxer said:**
> so will simply move away from this so called powerful txt based os ... and just go dumbo mode with the masses on win 7

OK. :rolleyes:

---

### Post by kiwixboxer on 2010-05-21
Ok thanks ... will try that. although when I was restarting my interfaces with anything other than dhcp.... the restart would say something like no such service or service failed??

I did try adding the nameserver lines 
namerserver 192.168.1.1
nameserver 192.168.1.140 (the virtual network card)

but still no joy :o(
I will give you a dump of the actual error if you like?

---

### Post by The Cog on 2010-05-21
You could post the config files and the error message. That would help.

Can you confirm that you can ping things by IP address but not by name? If that is the case then I'm sure it's a DNS resolution problem. Do you actually know the IP address of your DNS server? If not, try 8.8.8.8 which is a Google public DNS server.

---

### Post by kiwixboxer on 2010-05-21
yep know my DNS server ip ... and they are in the list of nameservers.

---

### Post by Nythain on 2010-05-21
is much easier to do outside of a VM, try a real install, so you're not dealing with virtual network adapters and bridged addresses and stuffs.

---

### Post by jerome1232 on 2010-05-21
> **Nythain said:**
> is much easier to do outside of a VM, try a real install, so you're not dealing with virtual network adapters and bridged addresses and stuffs.

+1

But unfamiliar territory is unfamiliar territory. Expect learning a new OS to be a bit rough.

Btw Windows Server has a cli only version now too.

---

### Post by KdotJ on 2010-05-21
You can set up the file server etc with out doing all that DNS stuff you mentioned. I did it, using samba. I can connect to the server form within my network no problems, from windows too.

---

### Post by Nythain on 2010-05-21
> **KdotJ said:**
> You can set up the file server etc with out doing all that DNS stuff you mentioned. I did it, using samba. I can connect to the server form within my network no problems, from windows too.
Just suggested that to OP yesterday in a different thread :)

---

