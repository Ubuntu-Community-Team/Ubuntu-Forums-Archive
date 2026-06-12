---
title: "How do you manually allocate an IP address?"
date: 2011-03-07
forum: New to Ubuntu
---

### Post by nickdc on 2011-03-07
I'm trying to get a recalcitrant second wireless AP up and running on my network, which requires disabling auto DHCP on my laptop and specifying an IP address manually when I need to go back into the web admin pages of the AP. I only know how to do this in Windows so have had to keep booting back into same. Pathetic ! This morning decided I need to learn another step with Ubuntu, but surprised it hasn't come up straight away in searching documentation (or at least in a form I can understand). Presumably there's a simple terminal command? Can someone please enlighten me? (And the command to restore back to auto!) Thanks!

---

### Post by wizard10000 on 2011-03-07
> **nickdc said:**
> I'm trying to get a recalcitrant second wireless AP up and running on my network, which requires disabling auto DHCP on my laptop and specifying an IP address manually when I need to go back into the web admin pages of the AP. I only know how to do this in Windows so have had to keep booting back into same. Pathetic ! This morning decided I need to learn another step with Ubuntu, but surprised it hasn't come up straight away in searching documentation (or at least in a form I can understand). Presumably there's a simple terminal command? Can someone please enlighten me? (And the command to restore back to auto!) Thanks!

Here's how I do it.  The information you want is stored in /etc/network/interfaces and I keep a couple different copies around so I can just rename them and restart networking if I need a static IP or to change back to DHCP.  My /etc/network/interfaces looks like this -

```
auto lo
iface lo inet loopback

```

but I also have a text file in /etc/network that looks like this -

```
auto lo
iface lo inet loopback
#
auto eth0
iface eth0 inet static
address 192.168.1.101
network 192.168.1.0
netmask 255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.1
```

and what I do is just copy /etc/network/interfaces to something else and copy the file above to /etc/network/interfaces then restart networking and everything works.

You can also do this on a command line with ifconfig like this -

```
sudo ifconfig eth0 192.168.1.101 netmask 255.255.255.0 up
```

substituting the IP you want for the one I put in there.

---

### Post by nickdc on 2011-03-07
Thanks. Looks like the ifconfig command is simplest. What's the equivalent command to set it back to auto?

---

### Post by migs73 on 2011-03-07
You can do this in the GUI as well. Disable you wireless first. Right click on your network manager (the wireless sign in the panel), click on edit connections, select edit, select the IPv4 tab  and then click on the drop down with 'Auto' in it, change it to manual, click on add in the table below and set your IP address in the boxes.

I think this is right, I'm on an XP machine just now so can't check.

To change it back to Auto just change the dropdown back to auto.

---

### Post by wizard10000 on 2011-03-07
> **nickdc said:**
> Thanks. Looks like the ifconfig command is simplest. What's the equivalent command to set it back to auto?

```
sudo dhclient eth0
```

will have the machine contact a DHCP server and obtain an IP address.

Hope this helps -

edit:  Your wireless adapter is most likely eth1, not eth0 - so remember to adjust the commands above accordingly.  cheers -

---

### Post by nickdc on 2011-03-07
Sorted! Thank you both very much. :)

---

### Post by migs73 on 2011-03-07
Your welcome (I know you asked for a terminal way to do it but thought others might want to know how to do it in GUI).

Could you please mark your thread as solved (above the first post, click on thread tools and select markas solved)

:)  Mike

Looks like you marked it as solved as I was typing, thank you!

---

