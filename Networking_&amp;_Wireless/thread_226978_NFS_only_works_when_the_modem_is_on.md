---
title: "NFS only works when the modem is on"
date: 2006-08-01
forum: Networking &amp; Wireless
---

### Post by Gotou on 2006-08-01
I have a NFS LAN setup between 3 computers but it only seems to work when I have the modem turned on.  My computers have cable ethernet connections (no wifi) to the router.  The router is connected to the modem by a fourth cable.  With the modem off I can ping each of the computers but the NFS won't connect.  When I turn the modem on and do a sudo mount -a, then the NFS works and I can send/recieve files between my computers.  So far the router seems to be the problem.  It's a Network Everywhere NR041.  I can access it's settings through a web interface but I don't know which one will allow the NFS network to work without an internet connection constantly on.  I'm also concerned that since my NFS LAN only works with modem accessing the internet that there is a security hole being opened up.

Any ideas how to fix this?

Thanks!

---

### Post by Gotou on 2006-08-06
I posted another question similar to this one.  Since then I solved the problem.  I noticed that more folks have looked at this thread than the other so I thought post my solution here as well.

OK, after much trial and error, googling and swearing](*,)  I figured it out how to make it work!:D 

I had to tweak 3 files in the /etc directory by adding the static IP address of each computer along with some other wording.  I used gedit as the text editor with the sudo command.

These are the 3 files:
/etc/hosts
/etc/hosts.allow
/etc/hosts.deny

First, the "hosts" file.
I fired up the terminal and entered this command:

sudo gedit /etc/hosts



After entering my password gedit opened up the "hosts" file.  There was a bit of a pause on my slowest computer while it loaded gedit.  I could almost hear it grunt and groan.

On my first computer I added these lines to the top of it's "hosts" file:

# Desktop 1
192.168.1.XXX desktop-2
192.168.1.XXX laptop

On my second computer I added these lines to the top of it's "hosts" file:

# Desktop 2
192.168.1.XXX desktop-1
192.168.1.XXX laptop

On my third computer I added these lines to the top of it's "hosts" file:

# Laptop
192.168.1.XXX desktop-1
192.168.1.XXX desktop-2



The "# Desktop 1", "# Desktop 2" and "# Laptop" are notes to myself for clarification.  I highly recommend leaving notes for yourself in configuration files you've tweaked.  The "XXX" in the IP address you'll have to substitute for your own.  "desktop-1", "desktop-2" and "laptop" are the host names of the computers.  If you can't remember what your host name is for a particular computer open another terminal and type in:

less /etc/hostname



Save the "hosts" file and while you're still in your text editor open "hosts.allow" and "hosts.deny".  We'll work on those next.


Moving on to the second file, "hosts.allow".  Remember that each computer has to have the other computers' static IP addresses listed (subtitute "XXX" for your own)

On my first computer I added these lines to it's "hosts.allow" file:

# Desktop 1
ssh: 192.168.1.XXX,192.168.1.XXX
portmap: 192.168.1.XXX,192.168.1.XXX


On my second computer I added these lines to it's "hosts.allow" file:

# Desktop 2
ssh: 192.168.1.XXX,192.168.1.XXX
portmap: 192.168.1.XXX,192.168.1.XXX


On my third computer I added these lines to it's "hosts.allow" file:

# Laptop
ssh: 192.168.1.XXX,192.168.1.XXX
portmap: 192.168.1.XXX,192.168.1.XXX




NFS uses "portmap" and SSH uses "ssh" in the "hosts.allow" file.  Since I'm using both I had to list both.  The IP address for the other two computers can be combined on one line using a "," to seperate them.


The third file, "hosts.deny" has something completely different added to it.  This time each computer had the exact same thing added to their "hosts.deny" files.

Add these following lines to each computers' "host.deny" file:

ALL: PARANOID
portmap:ALL
ssh:ALL



Save the files, reboot and we're done!

This solved my particular problem.  Your's may require more research.  Hopefully this will at least point you in the right direction or save you some of the headaches I went through.

---

### Post by frafu on 2006-09-05
Thanks Gotou; 

That was exactly what the was looking for; and it probably saved me some trouble finding it out. 

However, I think that it is only necessary to edit the hosts, hosts.allow and hosts.deny files on the nfs-server. 

frafu

---

### Post by Gotou on 2006-09-09
Howdy, I'm back again!

Frafu, you're probably right.  I setup all my computers as servers and clients just to cover my bases.  I don't have one computer dedicated as a file server yet.  That's a project to tinker with another day.

Here's another hard lesson learned.  This past weekend I converted all my computers to Ubuntu and went through the nfs setup process all over again.  I got too fancy with the share names (capital letters, apostrophes, spaces and long names) and it caused me alot of headaches.  Especially in the fstab file.  It can be done but it just ain't worth it.

Keep the share names short but meaningful, lowercase, no spaces and no special characters.  The K.I.S.S. principal never fails.

---

