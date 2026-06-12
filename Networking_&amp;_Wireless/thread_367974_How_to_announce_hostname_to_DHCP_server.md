---
title: "How to announce hostname to DHCP server?"
date: 2007-02-22
forum: Networking &amp; Wireless
---

### Post by Dave / Mosaic on 2007-02-22
Xubuntu newly running here; tricky to get the installer to work right, but Ubuntu is GREAT...

Q:  When the machine boots and obtains its IP address from my DHCP server (all of which is working fine) it somehow isn't informing the DHCP server of its own hostname, whereas all of the other machines on my subnet do, including another (Yellow Dog) linux box.  The Ubuntu machine only broadcasts it's name as a "*", so what I get in my DHCP server's table looks like this:

Compaq-5280	192.168.0.100	00:40:D0:0E:5D:48	1 day 00:00:00	
Compaq-M2005	192.168.0.125	00:80:C8:AE:61:B0	1 day 00:00:00	
YellowDog-G5	192.168.0.126	00:80:C8:AE:61:B0	1 day 00:00:00	
*	192.168.0.139	00:50:E4:BA:F0:27	1 day 00:00:00

I assume that the Ubuntu machine, which knows its own name as Ubuntu-G3, isn't broadcasting it's name along with its DHCP request...  Is there any way to get it to?

BTW, the DHCP server / router / wireless bridge is itself running embedded linux - DD-WRT v23 SP2, running on a Buffalo WHR-HP-G54 off-the-shelf consumer wireless access point.

Thanks--

--dave

---

### Post by RandomJoe on 2007-02-22
I haven't used Xubuntu, I'm assuming it uses dhclient just like Ubuntu...!

Edit the file /etc/dhcp3/dhclient.conf.  The first commented configuration line sets the hostname.  Uncomment it (remove the #) then change the hostname.  I have found I don't need a fully-qualified name (like is there by default), just the name of the computer itself.  The machine I'm on looks like this:
```
send host-name "robin";
```

Save the file, and get dhclient to restart.  (Simplest way is just to reboot, but that's a Windows answer so... ;) )

Edit:  Okay, I just saw the "newly running" part.  To edit that file, you will need to use sudo.  Do this:
```
sudo gedit /etc/dhcp3/dhclient.conf
```
Of course, gedit is Gnome...  You may not have that...  I use 'vim', but that's pretty tough to use if you haven't before!  Not sure what Xubuntu uses for a text editor...

---

### Post by Dave / Mosaic on 2007-02-23
Hey, wow - thanks; that worked exactly like you said.

Now all I am wondering, is if there is some environment variable, like $HOSTNAME or something, that I could use in place of the hardcoded host-name in dhclient.conf.  If anybody knows that, I'd be happy to hear - I'm not sure exactly where or how Linux keeps it's own name, etc.

(Xubuntu ends up installing a simple text editor called mousepad, I've found, which is okay, at least where X is running...  Hopefully I'll get emacs or something else usable over a remote terminal installed soon - I never did learn vi, even though I was a pretty heavy duty unix user back about 15 years ago...)

Thanks--

--dave

---

### Post by RandomJoe on 2007-02-24
The system's current hostname is stored in /etc/hostname.  The trick of course is getting dhclient to use it directly - I don't know that.  (I almost never change the hostname of a machine once it's set up.)

I suppose you could cobble together a shell script that replaces the appropriate spot in dhclient.conf right before dhclient gets run - but I'm not sure where it gets run at!  I've tried doing a little searching through the various rc scripts and I'm just not finding it.  Not sure yet how Ubuntu is doing that!

---

### Post by MaleqAlhaq on 2007-03-15
Hi!
I have the problem, that I have the appropriate settings in my /etc/dhcp3/dhclient.conf but my router still doesn't know my PC. Pinging doesn't work, which is uncool. 

Does anybody have an idea what I can do to announce myself / my PC to the router?

Tanks in advance!

Cheers

---

### Post by koenn on 2007-03-15
> **MaleqAlhaq said:**
> Hi!
I have the problem, that I have the appropriate settings in my /etc/dhcp3/dhclient.conf but my router still doesn't know my PC. Pinging doesn't work, which is uncool. 


Your problem is completely different from the OP. The OP was about a minor glitch in dhcp config. You don't even have a functional network. Better create e separate thread for this.

---

### Post by MaleqAlhaq on 2007-03-17
I do have a functioning ntwork... it works flawlessly, except that hostname thing... 
But I think, I will open a new thread, that might attract some more attention...

Cheers

---

### Post by koenn on 2007-03-17
> **MaleqAlhaq said:**
>  Pinging doesn't work, 
That indicates network problems - not just dhcp

---

### Post by MaleqAlhaq on 2007-03-18
It seems, that I missed to include, that networking works great. What does not work is pinging one of the KUbuntu Boxes on my network. 
Internet, filesharing (with IP) and everything else works quite well, just not when I try to do it with a Linux hostname. Windows hostnames are resolved fine...

Any ideas?

Cheers

---

### Post by koenn on 2007-03-18
you need DNS, probably. That's not the same as dhcp  :)
I remember a thread about the same problem, I'll see if I can find it

---

### Post by koenn on 2007-03-18
[http://ubuntuforums.org/showthread.php?t=356034](http://ubuntuforums.org/showthread.php?t=356034)
[http://ubuntuforums.org/showthread.php?t=364232](http://ubuntuforums.org/showthread.php?t=364232)
[http://ubuntuforums.org/showthread.php?t=315488](http://ubuntuforums.org/showthread.php?t=315488)

the first one should give you an idea of what's involved & get you going. 
The rest are more of the same with some additional info here and there

---

