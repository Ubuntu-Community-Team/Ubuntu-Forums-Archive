---
title: "ifdown: couldn't read interfaces file &quot; /etc/network/interfaces&quot;"
date: 2007-12-05
forum: Networking &amp; Wireless
---

### Post by fullmesh on 2007-12-05
Hi EVERYONE

I have gone through all simillar posts, but non help so far.

My problem started when i tried to change dhcp to inet static using "sudo vi /etc/network /interfaces"

being a newbie with the command in VIM. at first the cursor stucked and i couldn't type a thing not knowing the syntax. anyway i was some how able to make the change and couldn't save the changes I made I've to reboot the server using the start button. there after the network could not come up.
 I use nano since i'm more famillier with it it come up with the following:

# This file describes the network  interfaces available on your system
and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.172.242
netmask 255.255.255.0
network 192.168.172.0
broadcast 192.168.172.255
gateway 192.168.172.1


After I restart the network 

sudo /etc/init.d/networking restart


I got the following error msg

EDIT : Bodhi.zazen ~ reduced size of font. Yikes fullmesh, no need for such a large font.

[B][I]* Reconfiguring network interfaces......
/etc/network/interfaces:2: misplaced option
ifdown: couldn't read interfaces file "/etc/network/interfaces"
/etc/network/interfaces:2: misplace option
ifup: couldn't read interfaces file "/etc/network/interfaces"[/I][/B][SIZE=7]
[/SIZE]
[fail]


PLEASE COULD anyone help bring up this net i'm trying to setup a LAMP server

THANKS

Tanimu
[EMAIL="tambalzar@gmail.com"]tambalzar@gmail.com[/EMAIL]

---

### Post by gazj on 2007-12-05
sounds almost like a permissions problem strange

just post the output from the following command

```
ls -lah /etc/network/interfaces
```

---

### Post by fullmesh on 2007-12-05
Hello Gaz,

this what i got from :

ls -lah /etc/network/interfaces

-rw-r--r-- 1 root 389 2007-12-05 14:03 /etc/network/interfaces

i hope this will help

thanz

regards

fullmesh

---

### Post by gazj on 2007-12-05
just try this

```
sudo chown root:root /etc/network/interfaces
```

then try again

---

### Post by p_quarles on 2007-12-05
Okay, first I would try indenting the list of addresses for the static configuration. It says it's having trouble parsing an option, and I suspect it may just be looking for the indentation that is standard for that file.

Apart from that, I would get rid of the "broadcast" and "network" listings, since these are not required for recent kernels. 

Also try gazj's suggestion. I'm not sure that's the problem, but that file should belong to root:root, as that command will cause it to.

Finally, double check that you're using the correct interface name:
```
ifconfig -a
```
will list the device names for all interfaces available to the system.

---

### Post by MarkusV on 2008-02-01
Hi All

Even as this is a bit an older problem, it just happend to me as well and I think I just found the cure.

The reason for the error is an added linebreak in the file description at the top of the document. I think it's done by Nano when you open the file the first time. 

just add a "#" sign at the beginning of line 2 and all is fine.

HTH
Markus

---

### Post by iCara on 2008-04-22
> **MarkusV said:**
> Hi All

Even as this is a bit an older problem, it just happend to me as well and I think I just found the cure.

The reason for the error is an added linebreak in the file description at the top of the document. I think it's done by Nano when you open the file the first time. 

just add a "#" sign at the beginning of line 2 and all is fine.

HTH
Markus

Thanks!! :)

---

