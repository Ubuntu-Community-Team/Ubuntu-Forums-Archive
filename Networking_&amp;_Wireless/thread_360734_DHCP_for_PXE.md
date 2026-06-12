---
title: "DHCP for PXE"
date: 2007-02-13
forum: Networking &amp; Wireless
---

### Post by a5benwillis on 2007-02-13
I am trying to put together a pilot in my school district to set up an Edubuntu computer lab but have ran into a problem. Hopefully someone out there can help me introduce Ubuntu to these kids.

I run in a Netware/Windows/Linux environment with a Netware server running DHCP(amoung other things) at each of my schools. I am trying to configure the existing DHCP server to hand out IP's and image file path/locations to the PXE clients instead of setting up a separate subnet. The main reason for this is to allow the users to access their existing home directories on the Netware servers as well as be authenticated via LDAP.

Can anyone help me out with what options to set in DHCP to allow the clints to:

1. Get an IP ( I already have this working
2. Point to the Edubuntu server and boot from the image.

Thanks for any help!!!

Ben 
Anderson School District #5
Anderson, SC

---

### Post by a5benwillis on 2007-02-13
Ok, so I got the client to boot. SHEW!

For anyone else looking for an answer to this you have to go to 'subnet options' and enable 'Set Boot Parameter Option' and set the ip address, name and Boot File name to '/ltsp/i386/pxelinux.0'


I get the Ubuntusplash screen but then I get this error:

```
BusyBox v1.1.3 (Debian1:1.1.3-2ubuntu3) Built-in shell (ash)

/bin/sh: can't access tty; job control turnedoff
(initramfs
```)


Anyone have an idea about this error?

Thanks!

Ben

---

