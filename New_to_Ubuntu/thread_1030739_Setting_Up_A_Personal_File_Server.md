---
title: "Setting Up A Personal File Server"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by cfree220 on 2009-01-04
I'm really new to Linux and to configuring servers and was hoping that someone could point me in the right direction based on what I'm trying to do.

First off, let me prefix this post with the fact that I am a broke college student (which is one of the reasons why free, open source software is so great :) ). Cost is a pretty big concern... I'd like to keep it under a hundred, preferably free.

My personal computer is a Dell XPS M1530 laptop running 32-bit Vista Ultimate. I also have an 8-9 y/o Dell Desktop, one from way back when Dell still made it's few USB ports inaccessible under that stupid plastic flap.

Right now I have Ubuntu 8.10 up and running with ProFTPD installed and more or less configured how I want it. As I worked on that project, however, I began to realize some of the limitations of the setup, and decided I needed help in determining what exactly I'm trying to create (in terms of the means to an end).

I'd like to set up something that will allow me to synchronize the hard disk in my laptop with a hard disk in the Dell box. In addition, I'd like to be able to gain remote access to the files on the Dell HDD remotely, perhaps via FTPS. Security is important to me.

I've already done some Google-ing to see if I could find anything useful. One page that I came across (thanks to jimmy the saint) detailed how to set up a simple home file server using Ubuntu Server 7.10. Based on the description, it sounds more or less like what I'm trying to accomplish. I have the .iso 's for 8.10 and 8.04 and would like to use one of the two. 

The tutorial is here: [Simple Home File Server (Based on Ubuntu)]("http://www.howtoforge.com/ubuntu-home-fileserver")

In general, or (if you have time) based on the content of the tutorial)  should I be able to more or less follow those instructions using 8.04 LTS or 8.10? Or am I headed in the completely wrong direction and, if so, does anyone know of any good resources that would help me accomplish this task?

In case there are any hardware considerations, the dell box does not have USB 2.0 and is not SATA compatible. Also, I need to try and track down a much larger hard drive(s). The original 40GB drive died, so I replaced it with an even smaller 10GB drive. Obviously, that's not going to work too well, as I have over 10x that much data to store on it.

Thanks in advance!

---

### Post by DGortze380 on 2009-01-04
All I have time for right now.

[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010150014%201035907789&name=IDE%20Ultra%20ATA100](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010150014%201035907789&name=IDE%20Ultra%20ATA100)

---

### Post by albinootje on 2009-01-04
> **cfree220 said:**
> 
I'd like to set up something that will allow me to synchronize the hard disk in my laptop with a hard disk in the Dell box. In addition, I'd like to be able to gain remote access to the files on the Dell HDD remotely, perhaps via FTPS. Security is important to me.


A quick answer :
To synchronise data, look at Unison
[https://help.ubuntu.com/community/Unison](https://help.ubuntu.com/community/Unison)
or grsync :
```

sudo apt-get install grsync

```

If you want something much more secure by design than ftp, then use ssh.

to run a ssh-server on the dell laptop :
```

sudo apt-get install ssh

```

Install winscp from [http://winscp.sf.net/](http://winscp.sf.net/) on the Windows machine.

---

### Post by crazyness003 on 2009-01-04
The tutoorial you provided will set up a simple *home network* file sever. Meaning you can only access it when your laptop is within the home network realm (basically only when you connect via wifi or wired to your router).

If you wanna access your files over the internet, you'll need a different approach. FTP wound not be a bad option, but im not too familiar with launching an internet based file-server. As a matter of fact, i was gonna do the same thing you just outlined, only i could care less for the backup part. i just wanna be able to access my files from any internet connected box.

Sorry im not that much helpful. But once i do start on my project, i will drop back to see if you need any additional help. 
What you outiled can be done, but there's different ways to implement it. Depending on the user, you may get different responses.

Good luck

---

### Post by ken22 on 2009-01-04
Firstly if you set up an ssh server, sftp will be available. Then, give your server box static IP. Forward port 22 from the server box to the router.

All you need now is to be able to locate your box from the internet. Go to [http://www.dyndns.com/]("http://www.dyndns.com/") and setup a free dynamic dns account.

When all this is done you can just sftp to your box by

```
sftp username@hostname
```

where hostname is whatever domain you got from dyndns. 

For syncronizing, I recommend rsync tunneled over ssh.

I hope this was helpful.

---

### Post by DGortze380 on 2009-01-04
> **crazyness003 said:**
> 
If you wanna access your files over the internet, you'll need a different approach. 

True

> **crazyness003 said:**
> 
FTP wound not be a bad option, but im not too familiar with launching an internet based file-server...

Not so true...

ssh and sftp or a VPN are your best option. FTP is inherently insecure and IS a bad option.

---

### Post by ken22 on 2009-01-04
> **DGortze380 said:**
> 
ssh and sftp or a VPN are your best option. FTP is inherently insecure and IS a bad option.

Agreed, in ftp passwords are passed as plaintext.

---

### Post by crazyness003 on 2009-01-04
See, i didnt know that. Good thing there are people who know this stuff to point people like me to the dunce corner :P

NO FTP! Hear that.
I was gonna suggest ssh, but i have NO IDEA how to set up or use it. yet.

---

### Post by cfree220 on 2009-01-04
Thanks! Unison looks like it will probably do the trick. One thing, though.... In the page you posted, it said that it requires Samba in order to work between the Linux box and my Windows laptop, and that Samba is designed for server distributions. I currently have the desktop version installed, and was wondering if I would be able to install Samba on that version, or if I have to/would be better off changing the OS over to the server edition.

Also, would I have to do anything to the Windows machine to allow synchronisation? I imagine I'd have to adjust the permissions, but will I have to install any additional software for sync to be coordinated?

And last of all, I've been using a portable FileZilla client for FTPing. It supports SSL/TLS for FTPS. Would I still be better off using SSH?

---

### Post by cfree220 on 2009-01-04
If I follow the tutorial and setup a home file server, will I be able to add an FTP or SSH server to extend access to any computer with an internet connection?

---

### Post by cfree220 on 2009-01-04
I have the box set up with a DynDNS Update Client (which I imagine could also be added to any other configuration?) and forward the ports through to it. When you say assign it a static IP, I imagine you mean on the home network? If the server is behind a DHCP enabled router, is there any way for me to do this, or should I just let the update client run and use port forwarding? Also, for the synchronization... do I need to have it encrypted if it's on a secure private network? My school imposes and enforces bandwidth limits, so I don't want to be synchronizing remotely. I was thinking I could put a router in my room and create a miniature home network and do my transfers over my own local connection, as opposed to the school network.

---

### Post by albinootje on 2009-01-04
> **cfree220 said:**
> If I follow the tutorial and setup a home file server, will I be able to add an FTP or SSH server to extend access to any computer with an internet connection?

The home server setup howto you've mentioned in your original posting sets up a ssh-server and samba on Ubuntu Gutsy.

In your set up with your two machines you can just install the ssh-server on your server machine and then you're done for the LAN part.
You can even run a local ssh-server on your Window-machine, which makes it possible for your server machine to use rsync/scp/sftp to/from that.

Someone else in another comment already mentioned how to set it up for the remote access part via the internet.

---

### Post by achianese on 2009-01-04
FileZilla will talk to your server if sshd is running; just choose SFTP and connect on port 22.

WinSCP does about the same thing, but I've liked it better for automating backups, e.g. syncing Documents to a folder on the server using a batch file:

[http://winscp.net/eng/docs/scripting](http://winscp.net/eng/docs/scripting)

---

### Post by ken22 on 2009-01-04
> **cfree220 said:**
> When you say assign it a static IP, I imagine you mean on the home network?

Yes, I mean on the home network. DynDNS will update itself as your external (WAN) IP changes.

---

### Post by ken22 on 2009-01-04
> **crazyness003 said:**
> See, i didnt know that. Good thing there are people who know this stuff to point people like me to the dunce corner :P

NO FTP! Hear that.
I was gonna suggest ssh, but i have NO IDEA how to set up or use it. yet.

I've written a little about this. If you want to use rsync over ssh or be able to ssh to a machine without having to give a password use keys. This is as strongly encrypted as using a password. Here is my [tutorial]("http://kenobrien.org/ssh.html").

To install ssh server
```
sudo apt-get install openssh-server

```

---

### Post by crazyness003 on 2009-01-10
I noticed this thread wasnt solved, so i decided to take a loot at it again.
For the record i got ssh up and running and its phenomenal! Its not that slow to access files. I even set up a dynDNS account and can access my desktop from anywhere on the net! w00t!
File Sharing is also a breese thru ssh. You can just run
ssh X name@domain
then
nautilus&
And you get a gui window of your remote computer. Access anything your server (desktop at home) can access...on your client (the computer you're currently on).
I really never have tried backup...so i have no comment on that.

Thats all i have. Im a n00b and found this to be an extremely easy talk to complete!
shwing!

---

### Post by ken22 on 2009-01-11
awesome :)

---

### Post by cfree220 on 2009-01-11
Ok, so I have the box up and running with Open-SSH and a Samba server. What I still need to do is install and configure Unison to synchronize the files between my Laptop HDD and the HDD in the Linux box. I'm looking through all the Unison documentation and manual material and, despite their claims that it's supposed to be easy to set up, I'm a little baffled. To begin, how do I install it on the server from command line (no GUI)?

---

### Post by albinootje on 2009-01-11
> **cfree220 said:**
> Ok, so I have the box up and running with Open-SSH and a Samba server. What I still need to do is install and configure Unison to synchronize the files between my Laptop HDD and the HDD in the Linux box. I'm looking through all the Unison documentation and manual material and, despite their claims that it's supposed to be easy to set up, I'm a little baffled. To begin, how do I install it on the server from command line (no GUI)?

```

sudo apt-get install unison
zless /usr/share/doc/unison/README.Debian.gz  ("q" to quit)

```

That text file talks about two different versions of unison.
On your laptop you can install the GUI version of unison then.

---

### Post by computermacgyver on 2009-01-11
```

sudo apt-get install unison

```

Will install unison on the linux box.

You have two conceptual options in terms of file syncing:
1) Manually initiate a sync (from the Windows or linux box)
2) Script something to sync ever so often (probably easiest to script on the linux box with cron)

To start with option 1 (which is a bit simpler). You will need to install unison on the windows box and I believe you can complete all the configuration there through Unison's gui. You will just tell unison to connect to the linux box via SSH on port 22.

---

### Post by cfree220 on 2009-01-11
OK, I tried sudo apt-get install unison, but there was some sort of error:
```

Err http://us.archive.ubuntu.com intrepid/universe unison 2.27.57-1ubuntu1
  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/u/unison/unison_2.27.57-1ubuntu1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

I assume this has something to do with how I have the network configured... any suggestions?

---

### Post by crazyness003 on 2009-01-11
i think maybe the server might have been down for a bit. Always perform a "sudo apt-get update" after that happens, then try again. The repo system is not 100% perfect (but its still 100% better than manually downloading and updating etc.)
If it still fails to work, a number of problems may have occured. But since you mentioned your network, have you done any special modifications to it? 
By default, it should "just work" (about 99% of the time)

---

### Post by albinootje on 2009-01-11
> **cfree220 said:**
> OK, I tried sudo apt-get install unison, but there was some sort of error:


Does your server have internet connection now ?
```

sudo dhclient
sudo apt-get update
sudo apt-get install unison

```

By the way, if you want to use your server from the outside, it is recommended to give it a static ip-address, because you cannot completely rely on a dhcp-server giving your machine the same ip-address each time.

---

### Post by computermacgyver on 2009-01-11
Yeah. This is usally the error when the mirror is down (rarely, and I just accessed it from my computer) or the computer cannot connect to the internet. The exact error relates to DNS problems: the computer cannot convert us.archive.ubuntu.com into an IP address to access it.

Have you been able to access the Internet before? How is your Windows box configured? DHCP? Manual DNS Addresses? Proxy settings?

If you have followed the suggestions above and changed the linux box to a static ip address (from previously being DHCP) we will probably have to add DNS server information.

If you do have a manual ip address, look up your DNS servers in windows "ipconfig /all" (I think) and then add them to /etc/resolv.conf .
The conent of the file should be:
```

nameserver <IP address of first DNS server>
nameserver <IP address of second DNS server>

```

---

### Post by cfree220 on 2009-01-11
To the last three posts:

I'm not surprised that I'm having some issues with connectivity. I just returned to school and brought my server with me. I had to register the comp on the network, so I booted with a live CD and followed the instructions etc. The school issues a DHCP IP to registered computers (the issues ip address = external IP) which is static. In the network interfaces file, I changed eth0 from DHCP to my issued IP address. I know this much is functioning, because I am able to connect to the server via SSH.

I can't run apt-get update... I get the same error.

Would there be any issues if the hostname (?) [cfreeman.homeftp.net) does not match the school issued domain of dhcp-my-i-p-address.dorm.brandeis.edu?

Also, I should note that I am able to access my Samba shares... it seems that the only problem is in accessing the mirror. When I was booted in using the LiveCD, I was able to navigate to other, off-location sites.... but then, perhaps the configuration issue is specific to the server install.

---

### Post by cfree220 on 2009-01-11
Ok, I just got it working. What was the first bit of code you gave me for?

Thanks!

---

### Post by computermacgyver on 2009-01-12
Which bit of code? Posts 22-25 should no longer be relevant as you have the repository/internet working.

For reference:
sudo dhclient <== installs a dhcp client to get a dhcp address from the network
sudo apt-get update <== refreshes the local repository cache, downloads new info about packages, etc.
sudo apt-get install unison <== downloads,installs,configures unison 

/etc/resolv.conf <== holds your DNS addresses for machines with static ip addresses/manual DNS entries

sudo, of course, in front of any command runs the command as a privileged user (e.g. root)

---

### Post by albinootje on 2009-01-12
> **computermacgyver said:**
>  For reference:
sudo dhclient <== installs a dhcp client to get a dhcp address from the network

[nitpick-mode off, information-mode on]
Make that : the dhcp client goes asking on the network for an ip-address for all network interfaces on the local machine.

---

### Post by cfree220 on 2009-01-13
Ok, so here is how the project stands:

**Installed new HDD:** I bought and installed a 320GB internal HDD which mounts on boot and is/will be used for all files managed by the server.

**Samba Server:** Done. Functions properly with the exception that I am not able to access on of the share folders when using the administrative account on the client computer.

**Open-SSH:** Done. Has been working since day 1.

**DynDNS Update Client (ddclient):** Done. Appears to function, although have not rebooted system or restarted networking since initial configuration (Not sure if that could hide a problem...)

**FTP (w/support for SSL/TLS):** Pending

**Unison:** Managed to install, but have not yet gotten to work as desired. I'm a little confused on how to configure it. The preference file on the Windows machine looks like this:
```

#Unison Preferences File

root = D:\ 
root = ssh://muse.dyndns.ws//muse/

# Ignore certain directories and files
ignore = Name Thumbs.db
ignore = Name Desktop.ini

# Helps out a lot on Windows
fastcheck = true

# Don't synchronize permission bits
perms = 0

# Place new files at the top of the list
sortnewfirst = true

backup = Name *.doc *.pdf *.xls *.txt

```

I'm not sure what, if any, configuration changes must be made on the Linux box.

When I try to sync from the Windows machine, I get the following error message:

Uncaught exception Unix.Unix_error(20, "create_process", "ssh")

I'm able to connect by setting the second root to the local network address (\\MUSE\Muse), however the program seems to run EXTREMELY slowly (click on a menu and wait five seconds for it to drop down; try and drag the window and wait for it to move). Aside from the responsiveness of the program, this configuration should work fine for me as long as I only want to sync over the local network. Ideally, however, it should run over SSH for security and for remote sync-ing.

I want the Unison sync to originate from the server. That is to say, I want the server to synchronize itself with my laptop over SSH and on a schedule, without being prompted by the user (me). Part of what is confusing me is in determining which machine is the client and which is the server. In my mind, if the Linux box is providing backup services to the laptop, then it is the server. At the same time, however, my laptop is serving files to the Linux box.

Does anyone know what I've done wrong that is preventing Unison to work over SSH? Also, if anyone has any insight as to why it is running so sluggishly. I also have some more complex and specific questions regarding configuration, but I'll save those for after I get this puppy up and working.

Thanks in advance!

---

### Post by cfree220 on 2009-01-14
I'm at somewhat of a standstill, so I'm going to bump this up a little. I haven't been able to find many helpful resources on how to set up an SSH sync between a Windows machine and a Linux machine. Also, I had a question about the PC speaker. In the tutorial that I used for building a simple home file server (see link on first page of thread), it goes over how to make the PC speaker beep when the system loads and when again as the servers load. I followed these instructions, but they did not have any effect. Does anyone know how to get it going? The program is "beep," btw.

Thanks!

---

### Post by DGortze380 on 2009-01-14
> **cfree220 said:**
> I'm at somewhat of a standstill, so I'm going to bump this up a little. I haven't been able to find many helpful resources on how to set up an SSH sync between a Windows machine and a Linux machine. Also, I had a question about the PC speaker. In the tutorial that I used for building a simple home file server (see link on first page of thread), it goes over how to make the PC speaker beep when the system loads and when again as the servers load. I followed these instructions, but they did not have any effect. Does anyone know how to get it going? The program is "beep," btw.

Thanks!

Look into the rsync command (man rsync) it will do various types of backups over ssh.

---

### Post by cfree220 on 2009-01-14
Sorry, I should have included more details from the post previous to my last. I'm using Unison for synchronization and have it installed on both client and server, but don't know how to make it work over SSH.

---

### Post by albinootje on 2009-01-14
> **cfree220 said:**
> I'm at somewhat of a standstill, so I'm going to bump this up a little. I haven't been able to find many helpful resources on how to set up an SSH sync between a Windows machine and a Linux machine. 

Between a Linux and a Linux machine, you only need the ssh server running on both machines and have rsync (client) installed on the client.
With a windows machine I bet it's the same.
You can install a ssh server on Windows through cygwin, not that easy as on Ubuntu, but i can be done :)

---

### Post by albinootje on 2009-01-14
This should get you started with installing ssh server on windows :
[http://pigtail.net/LRP/printsrv/cygwin-sshd.html](http://pigtail.net/LRP/printsrv/cygwin-sshd.html)
[http://erdelynet.com/2004/08/30/cygwin/see-cygwincom-for-cygwin-ssh-docs/](http://erdelynet.com/2004/08/30/cygwin/see-cygwincom-for-cygwin-ssh-docs/)

Make sure you do a bit of reading on security, because as far as I'm concerned MS-Windows and Internet are two things which I prefer to keep separated for my users :)

Just my 2 cents.

---

### Post by cfree220 on 2009-01-14
I was wondering if, based on my descriptions of how I want it set up (i.e. the Linux machine syncs with the Windows on a schedule), you could identify which machine I should consider the server and which the client. In general, is the server the machine that initiates the sync, or is it the machine that provides the files?

Thanks for all the help you've given me with this project! I wouldn't have gotten beyond installing the server OS without it.

---

### Post by morningboat on 2009-01-14
> **cfree220 said:**
> 
**FTP (w/support for SSL/TLS):** Pending


The use of the age old and mature FTP protocol is still my preferred way since the client's configuration is almost zero on Linux, Windows, and Mac.
As to the security, Auth SSL/TLS is of same or higher level of security than SSH. The configuration for FTPS supported server:
[LIST]
[*]Approach 1: ProFTPD w/support SSL/TLS: [http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)
[*]Approach 2: vsftpd w/support SSL/TLS: [http://ubuntuforums.org/showthread.php?t=518293](http://ubuntuforums.org/showthread.php?t=518293)
[*]Approach 3: CrossFTP Server w/support SSL/TLS: [http://www.ubuntugeek.com/how-to-setup-file-sharingsftp-for-machines-by-newbie-in-5-minutes.html](http://www.ubuntugeek.com/how-to-setup-file-sharingsftp-for-machines-by-newbie-in-5-minutes.html)
[/LIST]

---

### Post by albinootje on 2009-01-14
> **morningboat said:**
> The use of the age old and mature FTP protocol is still my preferred way since the client's configuration is almost zero on Linux, Windows, and Mac.

Thanks your posting, interesting to read.
I do disagree however with FTP being easy to use, it can cause enormous headaches depending on the several firewall setups in between the client and server.
> 
As to the security, Auth SSL/TLS is of same or higher level of security than SSH.
In my opinion Openssh encryption is to be preferred over SSL any time. 
Especially SSL with a 1024 bit key.
Also with Openssh there's not the CA vs. handmade SSL certificates problem, and it's imho much easier to restrict on ip-addresses, restrict on usernames, and there's scponly (with or without chroot).

It is possible however that some setups at schools or companies have port 22 closed while port 21 is open, but you might need port 20 open for your ftp session to work too.

---

### Post by albinootje on 2009-01-14
> **cfree220 said:**
> I was wondering if, based on my descriptions of how I want it set up (i.e. the Linux machine syncs with the Windows on a schedule), you could identify which machine I should consider the server and which the client. In general, is the server the machine that initiates the sync, or is it the machine that provides the files?

Thanks for all the help you've given me with this project! I wouldn't have gotten beyond installing the server OS without it.

With ssh server installed on both, and with rsync as client installed on both, there's not a server or client side anymore.
It all depends where you want to have the backups.. could be on both even.

In the rsync syntax, just like the scp syntax, there's source and destination.
For example :
```

rsync -auzv 192.168.1.111:/usr /home/backup/usr

```
There it is "source" vs. "destination", where /home/backup/usr is the destination, the place where the backup will reside.

---

### Post by compiledkernel on 2009-01-14
Im sure no one has said it yet but, here you go. 

[http://howtoforge.net/disk_based_backups_amanda_debian_etch](http://howtoforge.net/disk_based_backups_amanda_debian_etch)

should be fairly simple to duplicate on an Ubuntu machine. 

the only consideration here otherwise would be the use of win32 amanda client -- [http://wiki.zmanda.com/index.php/Windows_client](http://wiki.zmanda.com/index.php/Windows_client)

---

### Post by cfree220 on 2009-01-14
[Insert Frustrated Noise Here]!!!!

The initial Unison scan had been running for the past 23 hours. It was about 8 video files away from being done when my computer blue screened.

SKLHG';SILWEUohSKKLDH

Any idea what went wrong? I'm going to try and sync the other way, and see if I have better luck.

EDIT: I can't seem to get the configuration right on the Linux end. I might just go ahead and try rsync... Unison just seems way too slow.

---

### Post by cfree220 on 2009-01-24
Ok, so I've modified my setup slightly. I just got a new roommate, so I had to give up the second active Ethernet port. Instead of paying the school 50 bucks a year to activate another one, I bought a 25 dollar switch (10/100 mbits/s). After putting both computers behind it, I ran Unison again. This time, it ran substantially faster for scanning the local machine, but was still excruciatingly slow when scanning the remote machine. I assume some of this is probably do to a slow network card in the ten year old machine, but either way.... it doesn't make for a particularly practical setup if each sync is going to take more than 24 hours to complete. It's too bad that Windows backup doesn't just back up using folder hierarchies. Then I could just do my backups over the network. Does anyone have any experience with alternatives to Unison for file sync or even just hierarchical backup?

---

### Post by ken22 on 2009-01-24
have you tried rsync?

---

### Post by albinootje on 2009-01-24
> **cfree220 said:**
> it doesn't make for a particularly practical setup if each sync is going to take more than 24 hours to complete.

I suggested you to try unison and grsync.
And I'm sorry to hear that it is not working well :(
Can you please try rsync and see how that goes ?

---

### Post by cfree220 on 2009-01-26
OK, so I'm working on setting up rsync. I have cygwin installed on my windows machine. I have yet to download and install the rsync packages for the linux box. Before I continue, I have a question. I'm still confused as to whether or not the Linux box should be the server or client. If I configure rsync as a server on the Linux machine, does that mean it will mirror the hard drive in my laptop, or does that mean that it will attempt to make my laptop HDD a mirror of whatever is on the server HDD?

---

### Post by cfree220 on 2009-01-26
UPDATE: APparently rsync IS installe don the linux box as well.... though I don't remember doing so.

---

### Post by albinootje on 2009-01-26
> **cfree220 said:**
> I'm still confused as to whether or not the Linux box should be the server or client. If I configure rsync as a server on the Linux machine, does that mean it will mirror the hard drive in my laptop, or does that mean that it will attempt to make my laptop HDD a mirror of whatever is on the server HDD?

There are two different approaches to use rsync.

One is the use rsyncd (server) on one machine. I've never used that.
The other approach is to have rsync and ssh on both machines, and then use the rsync command wherever you prefer.

What will end up where is again up to you.
If you would for example do :
```

rsync -avuz your_other_machine:/data ~/backup

```
on the laptop, then the laptop will have the backup.
And if you would do a command like that on the other machine, then the other machine would have a backup of the data from your laptop.

---

### Post by albinootje on 2009-01-26
See also :
```

man rsync

```
the section "Usage" and "Examples". That has examples and text about the examples.

---

### Post by cfree220 on 2009-01-26
I'm not entirely sure on the syntax for the rsync command. I want to backup the D:\ drive on my windows laptop on the HDD in the server. I still don't understand drive designation in Linux. When I was configuring the system, I had to install the second HDD by making it auto-mount at /media/store. I manually synced the drives before running unison for the first time, so, for example, D:\CFreeman is found at /media/store/CFreeman. I'm not sure how I would incorporate both hostname and specific path in the command...

---

### Post by albinootje on 2009-01-26
> **cfree220 said:**
> I'm not entirely sure on the syntax for the rsync command. I want to backup the D:\ drive on my windows laptop on the HDD in the server.

You did install rsync and ssh through cygwin on the MS-Windows machine, no ?
Try ssh-ing in to your MS-Windows machine, then do :
```

ls -la /

```
There should be a (cygwin) directory visible which points to the C: drive.
I forgot the name, but it should be obvious.

> 
I still don't understand drive designation in Linux.

There's / for everything.
Then there's /media/ for anything else which gets attached/mounted.

---

### Post by albinootje on 2009-01-26
Just looked it up, it's /cygdrive/ in cygwin which should show the other drives.
Here's an example for your setup :
```

sudo mkdir -p /home/backup/d/
sudo chmod 750 /home/backup/d/
sudo rsync -azuv your_admin_name@your_laptop_ip:/cygdrive/d/ /home/backup/d/

```

---

### Post by cfree220 on 2009-01-27
Is there a section for people less knowledgeable than absolute beginner? I'm not really sure how to command line SSH into Windows. When I SSH to my server from Windows, I use an SSH client. No clue how to do the reverse using a text interface.

I'm wondering if I should upgrade the NIC in the Linux box before totally giving up on Unison. If I get a gigabit card, it's not too late for me to return the switch and buy a gigabit switch and some Cat6 cable. I suspect that the 10 Mbit/s NIC in the server is responsible for the 27 hour sync time.

Another thing I might consider doing in the near future (after I understand the software end of things) is to replace the system entirely. My current setup is running at just about minimum requirements. When new, the Dimension 8200 cost about $2k. Today, for $200, I can buy the Shuttle K4500. Investing in a newer system (even a low end one) will save eliminate immediate concern for hardware failure, and would make upgrading components such as the USB PCI card and NIC unnecessary. It would also add support for SATA and SATA2, as opposed to being limited to IDE.

---

### Post by cfree220 on 2009-01-27
Oh yeah, I also went ahead and installed ProFTPD. It was partially successful. One problem is that I can list directories, but it doesn't seem to want to display individual files. I also cannot login using my non-administrative account. Interestingly, I could not SSH into the server using my non-admin account.... the PuTTY window just closed itself. I noticed that this user did not have a home directory, so I created one for it on the second hard drive, so as to allow home directory caging for the user.

---

### Post by albinootje on 2009-01-28
> **cfree220 said:**
> Is there a section for people less knowledgeable than absolute beginner? I'm not really sure how to command line SSH into Windows. When I SSH to my server from Windows, I use an SSH client. No clue how to do the reverse using a text interface.


Installing ssh server on MS-Windows :

[http://pigtail.net/LRP/printsrv/cygwin-sshd.html](http://pigtail.net/LRP/printsrv/cygwin-sshd.html)

let's assume you're using MS-Windows XP, here's a quick howto taken from that (and I've tried this before, and it works!) :

1) install cygwin, and install ssh from within cygwin

2) 
> 
(3)  Right click My Computer, Properties, Advanced, Environment Variables
See this illustration (red dots)
Click the "New" new button to add a new entry to System variables:
variable name is CYGWIN
variable value is ntsec tty

(4) Right click My Computer, Properties, Advanced, Environment Variables
See this illustration (green dots)
Select the Path variable and click the "Edit" edit button:
append  ;c:\cygwin\bin   to the end of the existing variable string.

For Windows XP  , open a cygwin window by double clicking theg icon; a black screen pops open,

Then :
```

chmod +r  /etc/passwd
chmod +r  /etc/group
chmod  777  /var

ssh-host-config  -y

```
> 
(6) While you are still in the (black) cygwin screen, start the sshd service, type
net start sshd
or
cygrunsrv  --start  sshd

and test it from your Ubuntu box ..

---

### Post by albinootje on 2009-01-28
> **cfree220 said:**
> Oh yeah, I also went ahead and installed ProFTPD. It was partially successful. 

Please try rsync first.
FTP is insecure by default, and can be a real pain with firewalls in between.

---

### Post by cfree220 on 2009-01-28
I'll try out the suggestions above when I get back to my dorm. The FTP server is not intended as a replacement for rsync, but rather as a complement to it. I don't plan on using for FTP, but rather FTPS or SFTP. I just need to get the login for my non-administrative account to work first.

---

### Post by albinootje on 2009-01-28
> **cfree220 said:**
> I'll try out the suggestions above when I get back to my dorm. The FTP server is not intended as a replacement for rsync, but rather as a complement to it. I don't plan on using for FTP, 

Okay :). Plain FTP in a LAN with only trusted users would be fine by the way, but using it over the internet wouldn't.
> but rather FTPS or SFTP. I just need to get the login for my non-administrative account to work first.

> 
the PuTTY window just closed itself. I noticed that this user did not have a home directory, so I created one for it on the second hard drive, so as to allow home directory caging for the user.

And after creating that home dir and setting the ownership for that dir it did work ?
If not, you can double-click on the cygwin icon, and then type :
```

ssh -v username@ip-address-ubuntu-box

```
Not sure whether the ssh client in cygwin is installed by default, but if not, install "ssh" from the cygwin collection.

This approach might reveal more information about this problem.

---

### Post by cfree220 on 2009-01-28
Hmmm..... I'm not really sure I understand what exactly Cygwin does. Is it basically a Linux emulation for Windows?

I was able to login to the non-admin account using Cygwin (dunno why the same won't work from PuTTY). Interestingly, when I type in the path to the second HDD (/media/store), it returns no such file or directory. It is finding a directory @ /home/cfreeman

I am able to connect to the FTP server using my admin credentials, but when I enter cfreeman + password it returns Error 530 Login Incorrect. The account DOES exist on the server... I created it when I set up Samba.

Just out of curiosity, for local connections, is it best to go with the IP address, or can I use the DynDNS hostname? Also, my school assigns long-term DHCP addresses to network computers. The IP assigned my computer on the network is also my external IP address. As such, am I still able to connect over FTP using the server's IP address, or might there be external traffic associated with such a connection?

---

### Post by albinootje on 2009-01-28
> **cfree220 said:**
> Hmmm..... I'm not really sure I understand what exactly Cygwin does. Is it basically a Linux emulation for Windows?

No, cygwin is basically GNU (and the like) applications for MS-Windows.
There's no emulation, the cygwin applications are native MS-Windows binaries.

> 
I was able to login to the non-admin account using Cygwin (dunno why the same won't work from PuTTY). Interestingly, when I type in the path to the second HDD (/media/store), it returns no such file or directory. It is finding a directory @ /home/cfreeman

I am able to connect to the FTP server using my admin credentials, but when I enter cfreeman + password it returns Error 530 Login Incorrect. The account DOES exist on the server... I created it when I set up Samba.

To create a samba user the linux system user with exactly the same name should exist.
The password of the linux system user, and the password of the samba user (with the same username) can be different.
It could be possible that your linux system user doesn't have a password yet, while the samba user (with the same user name) doesn't.
> 
Just out of curiosity, for local connections, is it best to go with the IP address, or can I use the DynDNS hostname? Also, my school assigns long-term DHCP addresses to network computers. 

Hmm, well, ip address should always work, but hostnames are easier to remember and type :)
> 
The IP assigned my computer on the network is also my external IP address. 

In that case, with your external ip address being also your local address it is really recommended to have a firewall on your Ubuntu machine.
> As such, am I still able to connect over FTP using the server's IP address, or might there be external traffic associated with such a connection?
The possible theoretical attacker has to be somewhere in your network traffic.
Try :
```

mtr your_school_ip

```
and see what the route of the network traffic looks like.
But you already wrote that you didn't want to plain ftp, but ftp with SSL, so.. that should be fine.

---

### Post by FerociousTwig on 2009-01-28
I've been silently following this thread with interest for a bit now. My desires are somewhat simpler than cfree. What I want to do is set up a webhosting server at home which I can edit from school.   So from what I understand this is what I need to do:

1) Install Ubuntu on my home computer.
2) Install open-ssh on my ubuntu machine at home.
3) The ubuntu machine should come with both apache and php pre-installed correct?
4) Write down my home external IP address so that when I set up my dynDNS account I can tell it where to go


So what I'm wondering is if cfree could post a quick tutorial on what you did with the ssh part because you mentioned you got that working quickly? Sorry I can't help with your rsync problems because I'm pretty new to linux myself.

P.S. my laptop at school is dual booting vista/ubuntu -- would it be better to ssh from ubuntu to my ubuntu machine on home or to install putty on my vista partition and use that to ssh?

Thanks for the help.

---

### Post by albinootje on 2009-01-28
> **FerociousTwig said:**
>  3) The ubuntu machine should come with both apache and php pre-installed correct?

No, even when you use the Ubuntu server installatio cdrom you would have to choose for that to be installed.
Here's a howto :
[http://maketecheasier.com/setting-up-a-lamp-server-in-ubuntu-hardy-heron/2008/08/06](http://maketecheasier.com/setting-up-a-lamp-server-in-ubuntu-hardy-heron/2008/08/06)
> 
4) Write down my home external IP address so that when I set up my dynDNS account I can tell it where to go

Don't forget to set up the port forwarding to port 22 and 80 inside your DSL-router or cable-modem.

---

### Post by cfree220 on 2009-01-28
FerociousTwig,
The way you wil install Open-SSH can depend on which version of Ubuntu you plan on using. My Linux box is running Ubuntu 8.10 Server Edition. During the installation, you are given the option of a few different servers to install with the OS, including open-ssh and, if my memory serves me right, Apache (don't quote me on that, though). If you're planning on running a server out of Ubuntu desktop, you can open a terminal and type in ```
sudo apt-get install ssh
```
I don't think I had to do any configuration to make it work... you just use your regular credentials from some sort of SSH client (e.g. PuTTY).

As a note on accessing the server, both remotely and locally, you may have to make some configuration changes to the server's networking configuration. If you have a router, chances are it is acting as a DHCP server. This means that the router assigns an internal IP address to computers as they connect to the network. I'd recommend configuring the server with a static IP of 192.168.1.XXX, where XXX is a number higher than the total count of all computers on the network. The reason for this is that, if the server is using, say, 192.168.1.103, and then becomes disconnected from the network, the router may then assign 192.168.1.103 to the next device that connects to the network. If the server tries to connect to the network using 192.168.1.103 in this situation, you will likely encounter an internal network error (two machines claiming one IP address).

No matter what you do, you're going to need to have the server hooked up to a monitor during installation. Once open-ssh is installed, you can hide the server somewhere out of site and administer it via SSH.

I don't really know anything about setting up and configuring your web server. At this point, I'd recommend setting up your DynDNS account for the home machine. When you set up your account, it will give you the option to use your current IP address. Remember that this is the address for your home network, and not for a computer on the network (Which would probably start with 192.168...). 

Since your external IP address changes periodically, simply having a DynDNS account and hostname is not enough. To keep the hostname up to date, you need to have some way of updating your external IP. There are two ways that you can do this:

1. If you are behind a router, you may have the configuration option of automatically updating your hostname. On Linksys routers, the configuration pages can be accessed through your browser at [http://192.168.1.1;](http://192.168.1.1;) If you look around, there should be a section that has options for updating your hostname. All you have to do is select DynDNS.com from the drop down menu, enter in the username and password of your DynDNS account, and indicate which hostname to update.

2. Alternatively, you can install an update client on a machine behind the router. The DynDNS website has several update clients for a variety of operating systems ([DynDNS Update Clients]("http://www.dyndns.com/support/clients/"). For ease of use and reliability, not to mention an unusually attractive GUI, you might try installing the Windows Update Client (if you have a Windows machine on your network). For Linux, try installing ddclient:
```

sudo apt-get install ddclient

```
The installer will prompt you for the same details as with the router configuration (username, password, and hostname to update).

Finally, as you probably noted earlier in the thread, you will have set up port forwarding to your server through the router. If you want to remotely administer it over SSH, you have to forward port 22 to the internal IP of your server.

---

### Post by cfree220 on 2009-01-28
hmmmm.... I've tried changing existing accounts and creating new accounts and nothing is working. I changed the passwd on my existing non-admin account (entered in the same password I thought I had previously setup). Before I did this, I was able to SSH into the Linux box through cygwin, but not through PuTTY. After I "added" the password, I was not able to login through either (with the PuTTY window returning access denied, as opposed to just closing itself). I know that I'm entering the correct credentials. Is there somewhere that I can modify who is allowed to login remotely? Maybe it is not the FTP server that is returning invalid login, but the system itself?

---

### Post by albinootje on 2009-01-28
> **cfree220 said:**
>  Is there somewhere that I can modify who is allowed to login remotely?

This is getting a bit out of hand :| ;-)

For the openssh server it's /etc/ssh/sshd_config where you can limit access to users (or groups).

---

### Post by cfree220 on 2009-01-28
I checked in there, and didn't see anything that should be limiting access. When creating the new user:
```

useradd -d /home/binary_muse/ -m -p XXXXXXXX binary_muse

```
Anything in there (or, more likely, missing) that would cause a problem?

---

### Post by albinootje on 2009-01-28
> **cfree220 said:**
> I checked in there, and didn't see anything that should be limiting access. When creating the new user:
```

useradd -d /home/binary_muse/ -m -p XXXXXXXX binary_muse

```
Anything in there (or, more likely, missing) that would cause a problem?

why not use :
```

adduser binary_muse

```
? ... 

The underscore is a little bit of a problem :
> 
adduser binary_muse
adduser: Please enter a username matching the regular expression configured
via the NAME_REGEX[_SYSTEM] configuration variable.  Use the `--force-badname'
option to relax this check or reconfigure NAME_REGEX or NAME_REGEX_SYSTEM.

but apart from the "badname" it should work.

What happens when you do :
```

su - binary_muse

``` ?

And what shows :
```

tail -f -n50 /var/log/auth.log

```

---

### Post by cfree220 on 2009-01-28
I got the FTP server working. I created an ftpuser group and added an account to it, then modified the allow permissions in the config file. I also changed the user at which the server operates form proftp to nobody.

Now I just need to figure out how to do this over a secure protocol.

---

### Post by cfree220 on 2009-01-28
Ok, I have no clue how to configure it for SSL/TLS, but I did manage to FTP over SSH. It is my understanding that the drawback to this is that only the command channel is encrypted. For me, that should be fine.... I'm really only concerned with keeping my credentials safe, as I don't have any sensitive files to move around.

The only thing that seemed off, though, was that when I connected to the FTP server using SSH, I was not longer jailed to /media/store. Just wondering what I need to do to fix that.

Also, will it be easier on the CPU if it only has to encrypt the control channel?

---

### Post by albinootje on 2009-01-28
> **cfree220 said:**
> Ok, I have no clue how to configure it for SSL/TLS, but I did manage to FTP over SSH.
How did you do ftp over ssh ? Just wondering.

Here are some howtos (you used protftpd, no ?) :

[http://www.howtoforge.com/setting-up-proftpd-tls-on-ubuntu-8.10](http://www.howtoforge.com/setting-up-proftpd-tls-on-ubuntu-8.10)
[http://www.howtoforge.com/proftpd-tls-debian-etch](http://www.howtoforge.com/proftpd-tls-debian-etch)

---

### Post by cfree220 on 2009-01-28
I use the FileZilla FTP client, which has support for FTP over SSH. YOu just use port 22 instead of 21.

That first article looks like it might be a winner. I'll try it out and get back to you.

---

### Post by albinootje on 2009-01-28
> **cfree220 said:**
> I use the FileZilla FTP client, which has support for FTP over SSH. YOu just use port 22 instead of 21.


Okay, I see what you mean. 
But that's simply sftp (just like scp it's included with ssh), which should still work after removing the ftp-server software.

---

### Post by cfree220 on 2009-01-28
OK, so I followed the instructions from the first link. Technically speaking it solved the problem. In reality, it turns out that proftpd does not properly shutdown the TLS connection, which causes FileZilla to abort the connection.

---

### Post by FerociousTwig on 2009-01-28
So for the SSH I'm still a wee bit confused. I've never used SSH before so I don't have any credentials, does that mean I can just make them up or what. . . This is my first foray into anything of this sort so I'm sorry you have to be so detailed in your responses. Thanks again.

---

### Post by cfree220 on 2009-01-28
Assuming you've already downloaded and installed an SSH client (such as PuTTY) and have open-ssh installed on your server, you should be able to connect by entering the hostname into PuTTY's hostname field. MAke sure that the port is set to 22, and that the SSH radio button is selected. Click open, and a black window (looks like a command prompt or terminal) pops up and prompts you for a username. Enter in the username that you created when you installed the operating system and press enter. It will then ask you for your password. Again, this is the value that you entered during installation of the OS. Hit enter again, and it should log you in.

---

### Post by cfree220 on 2009-01-28
To get around the problem I was having with TLS shutdown, I downloaded the most recent version of proftpd. I had to compile it first, and when I installed it, it was to a completely different directory than the original (the new one was installed to /usr/local/proftpd). I'm just a little confused as to what I have to do to get rid of the old and be able to handle the new with the same commands and directories as the old one.

---

### Post by albinootje on 2009-01-29
> **cfree220 said:**
> To get around the problem I was having with TLS shutdown, I downloaded the most recent version of proftpd. I had to compile it first, and when I installed it, it was to a completely different directory than the original (the new one was installed to /usr/local/proftpd). I'm just a little confused as to what I have to do to get rid of the old and be able to handle the new with the same commands and directories as the old one.

/usr/local is the default PREFIX for installations from source (compiling).
You can remove the old one with Synaptic package manager.
Since you compiled from source that new installation will not be in that list of installed applications.

---

### Post by FerociousTwig on 2009-01-29
Last question (i think/hope). . .

If I use the ubuntu server edition, how do I know what my hostname is that I'm supposed to enter during the installation?

---

### Post by compiledkernel on 2009-01-29
by either doing a 

cat /etc/hostname 

or by simply typing

hostname

---

### Post by albinootje on 2009-01-29
> **FerociousTwig said:**
> Last question (i think/hope). . .

If I use the ubuntu server edition, how do I know what my hostname is that I'm supposed to enter during the installation?

The hostname is something that you can choose.

Do you need proper resolving of your hostname for certain services on your server ?
If not, then just a simple name will do, like ubuntu-desktop for example :
```

# example of the first 2 lines of /etc/hosts
#
127.0.0.1	localhost
127.0.1.1	ubuntu-desktop

# example /etc/hostname
ubuntu-desktop

```

---

### Post by cfree220 on 2009-01-29
> **albinootje said:**
> /usr/local is the default PREFIX for installations from source (compiling).
You can remove the old one with Synaptic package manager.
Since you compiled from source that new installation will not be in that list of installed applications.
Ok, teensy bit confused. Does that mean that I won't be able to use commands like /etc/init.d/proftpd resart? I'm wondering if I would be better off simply using a different FTP client until the final compiled release of ProFTPD is released.

I I do choose to, or need to, go that direction, how do I go about uninstalling the newly compiled version?

Also.... how do I use the Synaptic Package MAnager from command line? I know how to do it with the GUI, but I'm running text-only.

---

### Post by albinootje on 2009-01-29
> **cfree220 said:**
> Ok, teensy bit confused. Does that mean that I won't be able to use commands like /etc/init.d/proftpd resart? 
> 
It's possible that the compilation from source did not supply that.

I'm wondering if I would be better off simply using a different FTP client until the final compiled release of ProFTPD is released.

I I do choose to, or need to, go that direction, how do I go about uninstalling the newly compiled version?

That's a bit of a difficult question, uninstalling from source could be done if a "make uninstall" is provided.
Using "checkinstall" to install the compiled source as a deb package makes it possible for you to uninstall it much easier.
> 
Also.... how do I use the Synaptic Package MAnager from command line? I know how to do it with the GUI, but I'm running text-only.

There's only apt-get, aptitude, and dpkg for the text console, no Synaptic package manager.

---

### Post by cfree220 on 2009-01-29
Ok, so checkinstall basically turns a compiled source into a packeage that can be handled like any other package? I googled it up for more info. I guess it uses something called installwatch to keep track of what files have been changed. If I download and install checkinstall, can I use that to package-ify a previously compiled source? And, if so, can I use this to make a package without installing it as a compiled source?

Oh man, Linux really isn't Windows.

---

### Post by albinootje on 2009-01-29
> **cfree220 said:**
> Ok, so checkinstall basically turns a compiled source into a packeage that can be handled like any other package? I googled it up for more info. I guess it uses something called installwatch to keep track of what files have been changed. If I download and install checkinstall, can I use that to package-ify a previously compiled source? And, if so, can I use this to make a package without installing it as a compiled source?

Oh man, Linux really isn't Windows.

You would use checkinstall as following.
```

./configure
make
sudo checkinstall

```
See also : [http://ubuntuforums.org/showthread.php?p=6638456#post6638456](http://ubuntuforums.org/showthread.php?p=6638456#post6638456)

---

### Post by cfree220 on 2009-01-29
I think I understand. Is this the bit I was supposed to see?

> **mc4man said:**
> It's not always possible to use checkinstall. Using this will increase your chances (there is a bug in checkinstall this addresses

```
sudo checkinstall --fstrans=no
```

Also sometimes if you had to do a make install but would like to get rid of the build folder you can cd back to your build folder and run this
```
sudo checkinstall --fstrans=no --install=no
```

If successful then run from build folder
 
sudo make uninstall

Then use your .deb to install and afterwards delete the build folder

So, theoretically, even though I don't have a record of what files were changed, I should still be able to remove it?

---

