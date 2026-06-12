---
title: "Trying server, need many recommendations"
date: 2009-12-20
forum: New to Ubuntu
---

### Post by DArtagnon on 2009-12-20
I've just come into possession of a free tower and my first thought is to make it a file-server for me and my roommates (mostly as a media & backup center).  I could just turn on file sharing in WinXP, but I want a more robust solution.

The only problem is that my roomies are not techno-savvy and don't like wading through muck trying to solve networking issues (weird, right?)

So, I'm thinking of installing Ubuntu server, setting up Samba, ftp, ssh, and any other cool software you can suggest.  I need for it to be easy, and preferably have simple solutions for me to implement and my roommates not to have to research.

What kind of pitfalls should I be looking out for?  I'm thinking of just attacking it trial-by-fire style, but from experience I know there's a smarter way.

---

### Post by Temposs on 2009-12-20
If you are not comfortable with command line, you may want to just install the standard Ubuntu Desktop edition. You can do the same server stuff, but you'll have a GUI by default.

Ubuntu Server has no GUI by default, so you'll have to know command line from the beginning if you want to be effective with it.

Setting up Samba is definitely something to do. You can even share Printers and the CD-ROM through Samba.

If you install the Server edition, there is no USB auto-mounting by default. So, you need to install the usbmount package in order to get that support. You'll need that if you'll have an external drive attached or something.

---

### Post by audiomick on 2009-12-20
+1 Temposs
I'm no server expert, but from what I have read, the main reason for leaving out the gui on the server version is to cut down on resource usage. 

On a server in a business where maybe 40 or 50 users or even a couple of hundred are accessing it at the same time, that is relevant. For you and a couple of room mates, it shouldn't be an issue.

If you use the standard Ubuntu, you will have something that behaves like a "normal" computer, and should be easier to deal with.

---

### Post by lukeiamyourfather on 2009-12-20
If your roommates use Windows they can mount a Samba (CIFS) share on their systems as a network drive. So if the server is always on, when they boot up it'll connect as a drive (like drive R:\ for remote or something like that if you like). To applications and users the mounted drive is transparent. Cheers!

---

### Post by undecim on 2009-12-20
> **lukeiamyourfather said:**
> If your roommates use Windows they can mount a Samba (CIFS) share on their systems as a network drive. So if the server is always on, when they boot up it'll connect as a drive (like drive R:\ for remote or something like that if you like). To applications and users the mounted drive is transparent. Cheers!

To set up a shared folder like this in windows, right click on the shared folder you would like to mount and select "Map Network Drive"

---

### Post by Cheesemill on 2009-12-20
You may want to take a look at humphreybc's thread [here]("http://ubuntuforums.org/showthread.php?t=1349394") that I've been helping him with.
We've not got round to Samba yet but it has some good beginners info on Servers.

---

### Post by audiomick on 2009-12-20
If you have any trouble with samba, it seems the guru is here:
[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

It is a monster thread, but if one follows the steps in the links in dmizers signature, it seems that all ills can be cured...;)

---

### Post by holastickboy on 2009-12-20
I agree with the posters here, I think Ubuntu Desktop will be the right choice for you.  I currently run two servers in my house, one is my more powerful webserver which looks after my website.  The other is a Ubuntu (running desktop edition) file server.  It runs Samba, and I have it sharing files to all of the computers in the house.  My wife is the only other user, but she is very computer illiterate, and has no problem using it.  I set up the share, then I went to the other computers running windows and "mapped" the share so that it appeared in "My Computer" as a normal hard drive.  On the iMac, I connected to the server, then placed it into logon items so that the mac connects to the drive on startup.  That way, all your users have to worry about is copying and pasting files to the drive.  No setup required!

---

### Post by DArtagnon on 2009-12-21
Thanks for the many replies.  I'm fairly confident in my cli skills.  At least enough so to edit config files to set up networking and a basic apache server.

I was thinking about server version because the computer is going to be remote anyway.  I'll be using my own monitor and keyboard to set it up, but once it's running, I'll be accessing it via ssh.

I guess I'd like to take this opportunity to make more than just a file server... I want to introduce the roomies to cool server stuff (and try and convert them to techies).  I just want to know if you guys know of any neat stuff already out there.  For example, I'm thinking of using an email server w/ a bash script to take emails, parse youtube webaddresses & download the flvs, and reencode them & put them in a shared folder.

I'm no gnu wizard, but I feel like a few parlor tricks might be within my power.

As a side note:  I can't seem to find apache in the 9.10 desktop repositories.  Am I not being thorough?

EDIT: And @ Cheesemill & audiomick: Thanks, those links are quite helpful.  I've bookmarked them, and I'll be referencing them as I make my preparations.

---

### Post by Temposs on 2009-12-21
apache is in the repositories. Go to System->Administration->Synaptic Package Manager and do a search for "apache" by Name. It's definitely there.

Another thing you might try with your server is to setup automatic regular remote backups of your home directory to the server over ssh :-) 

I recommend you try the backup program called **Deja-Dup**. Just install it on a client machine that has Ubuntu on it and set up the Preferences. It's the most active GUI-based backup project for Linux going on right now, I think. I've made a couple contributions to it myself. I think it will become included by default in GNOME and maybe even in Ubuntu.

EDIT: fyi: deja-dup is in the repositories

---

### Post by DArtagnon on 2009-12-21
Alright, I'm started and have encountered my first roadblock.

I got ubuserver installed, which went smoothly.  I got ssh up and running.

For a reason unknown to me, the network seems to be spontaneously quitting from the server.  It's a wired connection, and I think I set up the static IP properly, since it will work for a few minutes before dropping.  My router should auto-assign x.x.x.1/99 and the static is x.x.x.107 so I don't think it's a conflict.

Any ideas?  I guess this could go under a different thread title, but I think it's relevant to what I'm doing.

---

### Post by lukeiamyourfather on 2009-12-21
> **DArtagnon said:**
> Alright, I'm started and have encountered my first roadblock.

I got ubuserver installed, which went smoothly.  I got ssh up and running.

For a reason unknown to me, the network seems to be spontaneously quitting from the server.  It's a wired connection, and I think I set up the static IP properly, since it will work for a few minutes before dropping.  My router should auto-assign x.x.x.1/99 and the static is x.x.x.107 so I don't think it's a conflict.

Any ideas?  I guess this could go under a different thread title, but I think it's relevant to what I'm doing.

Why the static IP? Just let it get a IP address from the DHCP server, assuming there's a router in the house/apartment.

---

### Post by audiomick on 2009-12-21
Ok, it is a bit out of my league, but simple problem solving first.

Try a different cable. It may have an intermittent contact. (Likewise the connector on the machinne)

This may not be a likely cause, by my 25 years as a sound tech have taught me to exclude the simple things first... ;)

Next thing, when the connection breaks down, can you ping the other machine?

```
ping *target IP address*
```

Edit:
As far as static IP addresses goes, I do that by reserving addresses in the router for my computers. Easy to do, and means you can leave the computer on DHCP and don't have to change it if you are using the laptop somewhere else to get into the net, mostly.

---

### Post by DArtagnon on 2009-12-22
Tried a couple different things.  Tried a new network cable, another port on the router and the same thing happened both times.

My interfaces file is very basic, and works for the first few minutes after a reboot.  I can ping the machine and ssh into it.  From the server, I can ping back to my pc, as well as [www.google.com](www.google.com).

Then, without warning, ssh client becomes unresponsive, I can't ping the server machine, and my router lists it as 'disconnected.'

As for static vs dhcp, it's my understanding that doing server stuff is much easier w/ a static.  Especially port forwarding.  My pc is dhcp, for ease of use, but the serverbox is just going to sit in one place so a little rigidity is fine.

Any more ideas?  I'd hate to have to give up so soon.  If it helps I can post my /etc/network/interfaces and /etc/resolv.conf, but they seriously only have about 6 lines combined, and I think they're right.

---

### Post by Temposs on 2009-12-22
It really is just as easy to do server stuff with dhcp. And it's easier to setup. Well, it doesn't require setup at all, as was my experience...was just plug and play dhcp with my router to my server.

---

### Post by audiomick on 2009-12-22
ok, so your network connection itself is breaking down. That gets out of range of my experience pretty quick if I am not sitting in front of the machine myself....:(

Try doing as I suggested with reserving an IP in the router for the server.
This allows you to leave the server on DHCP, which is pretty robust and painless, whilst still allowing a constant IP for the server.

It should be possible, look around a bit in the setup thing. You will need the MAC address of the ethernet connection. If you right click on the network icon in the task bar and choose properties, you can see that on the second tab.

---

### Post by DArtagnon on 2009-12-22
Thanks for your guys' input.

Hmm, I've been searching around in my router and I can't find anything that seems to let me do what you're suggesting.  What are some keywords that I should look for?  I have the MAC address.

My router is a Verizon Modem/router "Ultra Line Series3 Model 9100EM"

---

### Post by audiomick on 2009-12-22
I went here and looked in the manual you can get there:
[http://www.westell.com/index.php?option=com_content&task=view&id=952&arcsection=support](http://www.westell.com/index.php?option=com_content&task=view&id=952&arcsection=support)
I think this is for yours.

Anyway, on a quick look through, I didn't see anything promising...:(

Maybe you can have a look, if you haven't already.

If you are just using samba shares, I don't think it is too tragic if your server doesn't have a static ip, but I think for other stuff it becomes important.

The other thing that occurs to me is that there must be a network log somewhere on the server. I'll see if I can find it on my machine.

edit: no not where I thought, anyway. I guess I am running out of ideas... :(

---

### Post by t0p on 2009-12-22
You said that the connection works okay for a few minutes, then it goes. Right?  Well, is the server's IP address the same when it's working and when it stops?  You can find that out by typing into a terminal

```
ifconfig
```

---

### Post by The Real Dave on 2009-12-22
Can I make a suggestion? [FreeNAS]("www.freenas.org"). Its a BSD based network attached storage distro. Can be installed to a harddrive, or run from a live disk, taking a config from a flash drive or floppy. Its extremely lightweight, but also very easy to use, because after the CLI install is finished, everything thing else is controlled using a WebGUI. It'll do Samba, NFS, AFS, Media Streaming, Webserver, Torrents, and quite a bit more. Software RAID and the like are easily set up, even encryption if you want. And all this is done though a WebGUI, or SSH if you want. It'll run with very minimal requirements, but with alot of features. Its a great OS, and I highly recommend it. I've been using it for quite a while now, and its very stable too :)

Its incredibly easy to set up static IP, its done during the install. Give it a shot, remember, you can always just boot up the disk (live) and see what its like without touching your install of Ubuntu :)

---

### Post by audiomick on 2009-12-22
Something just occurred to me:
When your router has a DHCP server running and you want to assign a fixed ip to something, I think it has to be outside the range of ips that the router is allowed to assign. That can be set in the router setup.

I have to go to bed now, it is after 2 a.m. here. I'll look back in tomorrow.

---

### Post by bodhi.zazen on 2009-12-22
To throw out a dissenting opinion =)

Install Ubuntu server edition, if you wish a graphical interface to manage it, look at webmin.

---

### Post by The Real Dave on 2009-12-23
> **audiomick said:**
> Something just occurred to me:
When your router has a DHCP server running and you want to assign a fixed ip to something, I think it has to be outside the range of ips that the router is allowed to assign. That can be set in the router setup.

I have to go to bed now, it is after 2 a.m. here. I'll look back in tomorrow.

Nope, well, not for my router anyway, a Netopia 2247NWG. Works fine within DHCP. Setting it on the server's side, not router.

---

### Post by audiomick on 2009-12-23
> **The Real Dave said:**
> Nope, well, not for my router anyway, a Netopia 2247NWG. Works fine within DHCP. Setting it on the server's side, not router.

OK, good to know. The tip is from my brother, but my router (SMC) doesn't seem to like any static IPs in the system at all.

---

### Post by The Real Dave on 2009-12-23
> **audiomick said:**
> OK, good to know. The tip is from my brother, but my router (SMC) doesn't seem to like any static IPs in the system at all.

Are you setting it from the router's side or the server's? There might be an option to set static IPs from within your router's console. 

Also, are you sure the info in your /etc/network/interfaces is correct? Here's mine for my 9.10 server just as an example

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet static
        address 192.168.1.150
        netmask 255.255.255.0
        network 192.168.1.0
        gateway 192.168.1.254


```

---

### Post by audiomick on 2009-12-23
> **The Real Dave said:**
> There might be an option to set static IPs from within your router's console. 


Hi Dave. Been through that with the OP, and I had a look in a manual which I think is the right one for his router. I don't think it can do IP reservations.:(

---

### Post by The Real Dave on 2009-12-23
> **audiomick said:**
> Hi Dave. Been through that with the OP, and I had a look in a manual which I think is the right one for his router. I don't think it can do IP reservations.:(

Ah apologies, I must have missed that :) Mine can't either, but that should cause such a problem :confused:

---

