---
title: "All I want to do is copy some big files."
date: 2007-07-01
forum: Networking &amp; Wireless
---

### Post by xmastree on 2007-07-01
I have a laptop running Edgy, and I have about 12GB worth of files I would like to transfer to my wife's XP desktop.
I've tried samba, and I can copy them but only at 300kbps... Searching the forums it seems I'm not alone there.
So, I tried setting up an FTP server on this machine, but the windows one couldn't see it (and using gproftpd I managed to change my root password, which was weird...).

So, apart from using my flash drive, is there a better way?

---

### Post by darkog on 2007-07-01
Samba and FTP speeds should be similar. Samba is an easier setup. 

The XP machine should see the FTP server.[ Are you sure you set it up]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#FTP_Server")? try to telnet from the XP machine to the Ubu/FTP server on port 21..

telnet <ip_addy_of_ubu> 21


you should get a response.

Disable firewalls on both hosts to make sure it's not a protocol block.

If you have a cross cable -- you should be able to set dummy ip addy's on both and transfer straight and bypassing your other devices in the chain. 

connect them to each other. disable f/w. and ping each other. 

ubu machine ip=10.1.1.10

xp machine ip = 10.1.1.12

---

### Post by xmastree on 2007-07-01
> **darkog said:**
> Samba and FTP speeds should be similar. Samba is an easier setup. 
[this thread](http://ubuntuforums.org/showthread.php?t=424063) would indicate otherwise...

> The XP machine should see the FTP server.[ Are you sure you set it up]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#FTP_Server")? try to telnet from the XP machine to the Ubu/FTP server on port 21..
I followed [this](http://ubuntuforums.org/showthread.php?t=79588), the first section (GUI/beginners) and it didn't work.

```
chris@chris-laptop:~$ sudo /etc/init.d/proftpd restart
 * Stopping ftp server proftpd                                           [ ok ] 
 * Starting ftp server proftpd                                                  
 - no such group 'nobody'
 - Fatal: Group: Unknown group 'nobody' on line 24 of '/etc/proftpd/proftpd.conf'                       [fail]
chris@chris-laptop:~$ sudo gedit /etc/proftpd/proftpd.conf
[COLOR="Red"]comment out the references to 'nobody'[/COLOR]
chris@chris-laptop:~$ sudo /etc/init.d/proftpd restart
 * Stopping ftp server proftpd                                           [ ok ] 
 * Starting ftp server proftpd                                                  
 - Fatal: TLSRSACertificateFile: '/etc/gproftpd/gproftpd.pem' does not exist on line 51 of '/etc/proftpd/proftpd.conf'                     [fail]


```
> If you have a cross cable -- you should be able to set dummy ip addy's on both and transfer straight and bypassing your other devices in the chain. Forgot to mention, they're both wireless, connected to a router.

I am a complete numpty when it comes to networking, haven't a clue really. All this host & domain stuff confuses the hell out of me. :confused:

---

### Post by darkog on 2007-07-01
> Generally, you should find that Samba performs similarly to ftp at raw transfer speed. It should perform quite a bit faster than NFS, although this depends on your system.

[http://us4.samba.org/samba/docs/man/Samba-HOWTO-Collection/speed.html]("http://us4.samba.org/samba/docs/man/Samba-HOWTO-Collection/speed.html")


> **xmastree said:**
> Forgot to mention, they're both wireless, connected to a router.


wi-fi is gonna to be slower than wired for sure. are you on b or g? you will want to rule out the possiblilty that the router is the bottleneck. is there another host on the network that perfoems/transfers data faster?

---

### Post by xmastree on 2007-07-02
> **darkog said:**
>  is there another host on the network that perfoems/transfers data faster?
I'm not sure what you mean there. There are three computers here, one cabled to the router running Win98, my ubuntu laptop, and one XP desktop, both are wireless. No data transfer has ever taken place between any of them until now.

At some point I would also like to share the printer on the XP box, to print directly from the laptop.

Another host? what's that?

Anyway, the above error stuff was after my attempt at configuring using the graphical tool, so I removed proftpd and deleted the config file, then started over as per the guide.

I now get this error:
```
~$ sudo /etc/init.d/proftpd restart
 * Stopping ftp server proftpd                                           [ ok ] 
 * Starting ftp server proftpd                                                  
 - IPv4 getaddrinfo 'chris-laptop' error: Name or service not known
 - warning: unable to determine IP address of 'chris-laptop'
 - error: no valid servers configured
 - Fatal: error processing configuration file '/etc/proftpd/proftpd.conf'       [fail]
chris@chris-laptop:~$

```

So, there's something up with getaddrinfo then...

---

### Post by xmastree on 2007-07-05
Still struggling with this one...

Any ideas about that getaddrinfo thing?

---

### Post by fredj on 2007-07-05
If they are both connected by wireless to the router then this speed may be all you can expect.
Wireless speed depend on the quality of the signal and the distance from the router. It is usually 
good enough for the internet but makes a slow network compared to using network cables.

---

### Post by xmastree on 2007-07-06
Possibly, although I get much faster speeds to and from the internet. Of course, these are one way through the router.

I'll try connecting to the one PC which is wired to the router instead, if that works well then I know what the problem is.

Thanks

---

### Post by fredj on 2007-07-07
Try the transfer between two computers that are both wired to the network. Also keep this in mind, network
speeds both wired and wireless are specified in megabits per second. In terms of bytes transferred 10 bits
equals 1 byte. 

So in theory a wireless network with an 8mb connection can transfer data at a maximum speed of 800k bytes
per second. In practice you will be lucky to realise half this speed.

---

### Post by xmastree on 2007-07-07
Well, I set up the other pc (my dad's, just don't tell him) which is wired to the router, and it's much faster, so I guess that's the problem. Next thing would be to take this laptop in there and plug it in too.

Thanks for the advice all.

---

### Post by xmastree on 2007-07-07
Hmm... this is getting strange.

I just tried again. Initially, I had a target directory on dad's, called shared, with full (r/w) access. I copied some files into it from my laptop.

I've just tried again, and all I can find shared on that computer is what appears to be a replica of the directory from which I copied the files. IOW, I'm looking at my own computer, not Dad's...

If I try to access mine from dad's, I'm asked for a password. I didn't set one up anywhere, and my usual login password doesn't work.

:confused:

---

