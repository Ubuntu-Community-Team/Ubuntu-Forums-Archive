---
title: "Printer Sharing to XP Clients."
date: 2008-09-21
forum: Networking &amp; Wireless
---

### Post by Roasted on 2008-09-21
Yes, I've searched.
No, nothing helped.
So, here I am with a new thread.

My brothers are running older computers (upgraded enough to run XP Pro) that are out of available USB ports. So, instead, I'm sharing out a spare Lexmark 2500 Series printer I have so they can print school documents and whatnot.

I have a custom built computer that's about 3 years old running Ubuntu Hardy Heron.

My server name is jason-hardy.

I went through the instructions here [https://help.ubuntu.com/community/NetworkPrintingFromWinXP](https://help.ubuntu.com/community/NetworkPrintingFromWinXP) to set up this printer to be shared... but each time my XP Pro laptop that I'm using to test this is coming back saying Windows didn't find it.

The printer is shared. 
The printer is published.
My server name is set up.

Yet I get an error.

What could I be overlooking?

---

### Post by Roasted on 2008-09-23
:confused:

---

### Post by cariboo on 2008-09-24
Are you using Samba to share the printer? If so it could be that you don't have /etc/samba/smb.conf setup properly. Here are the relevant parts of my /etc/samba/smb.conf:

```
# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
   interfaces = lo  eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
   bind interfaces only = true
```

and

```
# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  


   guest account = nobody
```

If you make these changes to /etc/samba/smb.conf your windows computers should see the printer on the network.

Jim

---

### Post by Roasted on 2008-09-24
When I read about printer sharing with samba, I was told ALL I needed was the smbfs plugin, which I have. Besides that, samba should take care of the rest without any need for tinkering with the config file.

I can see the printer now. It just says access denied, unable to connect. *shrug*

---

### Post by superprash2003 on 2008-09-24
its better to do it via samba 
1)Setup samba - [http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html](http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html)
2)setup printing in samba - [http://prash-babu.blogspot.com/2008/05/how-to-setup-network-printer-or-share.html](http://prash-babu.blogspot.com/2008/05/how-to-setup-network-printer-or-share.html)

---

### Post by Roasted on 2008-10-05
I'm trying to share it without samba, even though I have samba running. I just don't see why it doesn't work.

I have a static IP of 192.168.1.111
The printer is shared.
When I go to \\192.168.1.111 on the XP machines, I see the printer.
When I right click and connect, it prompts me for a driver.
I direct it towards the driver.
It installs. I'm connected to the printer.

"Access Denied: Unable to Connect."

What the ****?!

---

### Post by Phosphoric on 2008-10-06
Can't speak for Hardy, but in 7.10 in printer properties, I think there is a tab for global settings?  (not sure, at work on a Windows PC).  Anyway there are two boxes to check share printer and allow connection on the LAN.  Both have to be checked and you get a warning that you've opened up port 631.

Sorry if that's too obvious, I fairly new to networking but this got my Window XP laptop printing via a printer connected to my Ubuntu desktop, wireless router.  Not using Samba.

---

