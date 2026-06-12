---
title: "ssh and router configuration?"
date: 2006-08-08
forum: Networking &amp; Wireless
---

### Post by cypher35 on 2006-08-08
I've recently set up an ubuntu server on an old hp pavilion machine that was just collecting dust in my closet.

I installed a basic LAMP server and then installed ssh.

Here's the setup:
**192.168.1.60** - my powerbook running osx
**192.168.1.40** - ubuntu server
**123.45.67.89** - the external ip address for both

The router (192.168.1.1) is set up to forward port 22 to 192.168.1.40.

Now from my powerbook, i cannot connect directly to the ubuntu server using the command
**~$ *ssh mike@192.168.1.40***

however, strangely, i can connect to it using the external ip address by using
**~$ *ssh mike@123.45.67.89***

is there some sort of setting on the server end that prevents local ip addresses from connecting?  does anyone have any ideas as to why this might be happening?

---

### Post by tagra123 on 2006-08-09
Try pinging that same 192.168.1.40.

Make sure the firewall is allowing connections. It seems to be doing that already.

You might try adding 192.168.1.40 hpserver (or whatever you named the machine) to your alias -- on both machines.

192.168.1.60 OSXlaptop
192.168.1.40 hpserver

You can add the alias in MENU: System-Administration-Networking   TAB Hosts

after doing that you can  type ssh mike@hpserver

I know this worked with two ubuntu machines.

I had to do this once with a Belkin to get NFS to work.

---

