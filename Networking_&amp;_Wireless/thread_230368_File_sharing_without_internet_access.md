---
title: "File sharing without internet access"
date: 2006-08-05
forum: Networking &amp; Wireless
---

### Post by Gotou on 2006-08-05
Howdy!
I'm trying to troubleshoot my network settings.  My SSH and NFS connections only work when I turn my modem on (to clarify I'm not confusing it with the router).  My setup is a Motorola cable modem wired to a Linksys router which then connects (hardwired, no wifi) to three computers.  Is there a configuration file(s) somewhere that sets the priority of network connections?  Hosts.allow lists the computers repsectively but not the internet connection.

Thanks!

---

### Post by Gotou on 2006-08-06
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

