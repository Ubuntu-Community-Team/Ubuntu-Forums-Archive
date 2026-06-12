---
title: "Fed up of Bluetooth in Linux"
date: 2024-01-24
forum: Networking &amp; Wireless
---

### Post by makem2 on 2024-01-24
[https://pastebin.com/PFcAVsqH](https://pastebin.com/PFcAVsqH)

I have used Linux for many years but have always had a problem with Bluetooth and it is driving me mad. Sometime it works seamlessly, sometimes it does not work and I have to keep trying, uninstalling and generally messing with it, or giving up and using email.

I have just purchased a Samsung A54 as an upgrade to my previous phone and am getting the same problems with Bluetooth.

The A54 is paired and worked once I think. It shows in devices as being paired as a trusted smartphone. I am trying to send a file (.jpg) from the phone to the PC and it shows connected followed immediately by disconnected. This is repeated until it gives up.

If I use the Devices applet to connect to the phone the error given is: Connection Failed: br-connection-profile-unavailable. For me, this is not at all helpful.

Since Covid I have started playing the odd game with family using Windows. In the past I only used Windows if there was no other way via Linux. However, having made more use of Windows I am beginning to wonder why I use Linux.

I can revert to Windows and send the file without a problem. I can do many things easily in Windows and I can understand why when I mention Linux to friends and family they are not interested.

I don't want to use Windows but as I get older I wonder why I struggle with Linux. Anyway, sorry for the diatribe.

Can anyone help permanently fix the issue I am having or show me how to fix it please?

---

### Post by TheFu on 2024-01-24
Friends don't let friends use bluetooth - ever.  Since 2002, I've been hacked only once and it was through bluetooth.

There are 4 possible ways to transfer files, in theory.
[LIST]
[*]USB connection
[*]Bluetooth connection
[*]Wifi connection or any mobile data connection (any IP stack)
[*]Pull the microSD card out, connect it to a real computer, transfer files, then put the microSD back into the phone
[/LIST]

I don't have a Samsung phone, but my Motorola phone refuses to work over the USB connection, I won't use bluetooth, and pulling the microSD out just to load files is a hassle, so that leaves connecting to the local network (and perhaps VPN), to transfer files over the network.

For transferring files over the LAN/WAN there are 50 possible methods.  A few for your consideration:
[LIST]
[*]sftp - Ghost Commander supports sftp. With Linux, you should already have ssh running, so sftp is there too. [https://f-droid.org/en/packages/com.ghostsq.commander/](https://f-droid.org/en/packages/com.ghostsq.commander/)
[*]Magic Wormhole - this is a point-to-point, encrypted, file transfer tool. Perfect when you don't know the other person.   [https://f-droid.org/packages/com.pavelsof.wormhole/](https://f-droid.org/packages/com.pavelsof.wormhole/) - Android Wormhole for send/receive.
[*]Run a 1-line HTTP server, then use the phone's browser to File --> Save As .... The only trick is to change directories into the directory with the files you want to share. There's no authentication for file access, so don't leave this running all the time.
```

# Python 2.x
  $ python -m SimpleHTTPServer 8000

# Python 3.x
  $ python3 -m http.server 8000

# Ruby 1.9.2+
   $ ruby -run -ehttpd . -p8000

# Perl
   $ cpan HTTP::Server::Brick   # install dependency
   $ perl -MHTTP::Server::Brick -e
           '$s=HTTP::Server::Brick->new(port=>8000);
            $s->mount("/"=>{path=>"."});
            $s->start'

# PHP (>= 5.4)
   $ php -S 127.0.0.1:8000
```
[*]Run some sort of personal cloud storage tool on your LAN ... something like nextcloud, seafile, owncloud. These can be handy, especially if you want to avoid untrusted cloudy tools like google, apple, microsoft, dropbox, and others.  Setting up nextcloud has become crazy easy now that it is a snap package.  I can't believe I'm writing that, but I switched to using the nextcloud snap package about 18-24 months ago from a manual install and it has been "better" overall, though not perfect.  [https://snapcraft.io/install/nextcloud/ubuntu](https://snapcraft.io/install/nextcloud/ubuntu)  It is like installing a trivial package these days.
```
root@vps:~# snap install nextcloud
nextcloud 18.0.4snap1 from Nextcloud&#10003; installed

# Now type your IP address in the URL to launch the nextcloud.

http://server_IP

#    Replace the server_IP with your server's actual IP Address.
# You will have to create admin account for NextCloud

```
[/LIST]

There are nextcloud apps on android for all sort of needs - files, calendar, contacts, email reader, RSS feeds, note taking, and literally hundreds of others, but "files" is the default.  Inside the nextcloud webapp, just mount the storage with your files using any of the 5 different external storage access options and Bob's your uncle.  Snaps are automatically updated, so your nextcloud will maintain itself for the most part.  No need to make nextcloud available to the internet, so you don't need to add that risk, but it is nice to have certain files automatically synchronized across devices.  For example, I use a cross-platform password manager and have the password DB file sync'd with my android devices, always.  Nextcloud use on a computer is generally best through a web-browser. That's how it is best accessed.

Anyway, those are some options for your consideration. None use non-secure Bluetooth, however.  I don't think there is any way to fix bluetooth. It is broken, completely, I'm sorry to say. the companies and industry people behind it are 1000x more interested in marketing than security.  

Wifi isn't exactly secure either, so if you are paranoid like my, run a quality VPN whenever you use wifi networking, even at home.  Wireguard makes that fairly seamless, once it is setup.  Everyone has their threshold of convenience vs security.

sftp is good if you will be transferring a few files, but not too many, but still want encryption and authentication involved.

Magic wormhole is good when you want to transfer 1 file or an entire directory system with minimal authentication. The bad part is you need to be able to start the transfer on the source side AND receive it on the target side. At least the data transfer is encrypted too.

1-line http server has the same issue as wormhole and ZERO authentication or encryption.

Nextcloud/Seafile/OwnCloud requires setting up the server, connecting the server to your file storage, setting up account access from the phone (DavX) and the download/sync performance is best started and left to run for some time.  If only used for file transfers, nextcloud and similar tools are a bit overkill. However, if you use them for all the other synchronization things, it can be really nice and a time saver while avoiding cloudy personal data theft by huge internet companies.

I suspect you won't bother with anything I've written, but at least you know it is possible.

---

### Post by makem2 on 2024-01-24
> **TheFu said:**
> Friends don't let friends use bluetooth - ever.  Since 2002, I've been hacked only once and it was through bluetooth.

There are 4 possible ways to transfer files, in theory.
[LIST]
[*]USB connection
[*]Bluetooth connection
[*]Wifi connection or any mobile data connection (any IP stack)
[*]Pull the microSD card out, connect it to a real computer, transfer files, then put the microSD back into the phone
[/LIST]

I don't have a Samsung phone, but my Motorola phone refuses to work over the USB connection, I won't use bluetooth, and pulling the microSD out just to load files is a hassle, so that leaves connecting to the local network (and perhaps VPN), to transfer files over the network.

For transferring files over the LAN/WAN there are 50 possible methods.  A few for your consideration:
[LIST]
[*]sftp - Ghost Commander supports sftp. With Linux, you should already have ssh running, so sftp is there too. [https://f-droid.org/en/packages/com.ghostsq.commander/](https://f-droid.org/en/packages/com.ghostsq.commander/)
[*]Magic Wormhole - this is a point-to-point, encrypted, file transfer tool. Perfect when you don't know the other person.   [https://f-droid.org/packages/com.pavelsof.wormhole/](https://f-droid.org/packages/com.pavelsof.wormhole/) - Android Wormhole for send/receive.
[*]Run a 1-line HTTP server, then use the phone's browser to File --> Save As .... The only trick is to change directories into the directory with the files you want to share. There's no authentication for file access, so don't leave this running all the time.
```

# Python 2.x
  $ python -m SimpleHTTPServer 8000

# Python 3.x
  $ python3 -m http.server 8000

# Ruby 1.9.2+
   $ ruby -run -ehttpd . -p8000

# Perl
   $ cpan HTTP::Server::Brick   # install dependency
   $ perl -MHTTP::Server::Brick -e
           '$s=HTTP::Server::Brick->new(port=>8000);
            $s->mount("/"=>{path=>"."});
            $s->start'

# PHP (>= 5.4)
   $ php -S 127.0.0.1:8000
```
[*]Run some sort of personal cloud storage tool on your LAN ... something like nextcloud, seafile, owncloud. These can be handy, especially if you want to avoid untrusted cloudy tools like google, apple, microsoft, dropbox, and others.  Setting up nextcloud has become crazy easy now that it is a snap package.  I can't believe I'm writing that, but I switched to using the nextcloud snap package about 18-24 months ago from a manual install and it has been "better" overall, though not perfect.  [https://snapcraft.io/install/nextcloud/ubuntu](https://snapcraft.io/install/nextcloud/ubuntu)  It is like installing a trivial package these days.
```
root@vps:~# snap install nextcloud
nextcloud 18.0.4snap1 from Nextcloud&#10003; installed

# Now type your IP address in the URL to launch the nextcloud.

http://server_IP

#    Replace the server_IP with your server's actual IP Address.
# You will have to create admin account for NextCloud

```
[/LIST]

There are nextcloud apps on android for all sort of needs - files, calendar, contacts, email reader, RSS feeds, note taking, and literally hundreds of others, but "files" is the default.  Inside the nextcloud webapp, just mount the storage with your files using any of the 5 different external storage access options and Bob's your uncle.  Snaps are automatically updated, so your nextcloud will maintain itself for the most part.  No need to make nextcloud available to the internet, so you don't need to add that risk, but it is nice to have certain files automatically synchronized across devices.  For example, I use a cross-platform password manager and have the password DB file sync'd with my android devices, always.  Nextcloud use on a computer is generally best through a web-browser. That's how it is best accessed.

Anyway, those are some options for your consideration. None use non-secure Bluetooth, however.  I don't think there is any way to fix bluetooth. It is broken, completely, I'm sorry to say. the companies and industry people behind it are 1000x more interested in marketing than security.  

Wifi isn't exactly secure either, so if you are paranoid like my, run a quality VPN whenever you use wifi networking, even at home.  Wireguard makes that fairly seamless, once it is setup.  Everyone has their threshold of convenience vs security.

sftp is good if you will be transferring a few files, but not too many, but still want encryption and authentication involved.

Magic wormhole is good when you want to transfer 1 file or an entire directory system with minimal authentication. The bad part is you need to be able to start the transfer on the source side AND receive it on the target side. At least the data transfer is encrypted too.

1-line http server has the same issue as wormhole and ZERO authentication or encryption.

Nextcloud/Seafile/OwnCloud requires setting up the server, connecting the server to your file storage, setting up account access from the phone (DavX) and the download/sync performance is best started and left to run for some time.  If only used for file transfers, nextcloud and similar tools are a bit overkill. However, if you use them for all the other synchronization things, it can be really nice and a time saver while avoiding cloudy personal data theft by huge internet companies.

I suspect you won't bother with anything I've written, but at least you know it is possible.

You are most certainly wrong with your statement, "I suspect you won't bother with anything I've written, but at least you know it is possible." You have advised me in the past and I value your input highly. I read every word of your reply and when I arrived at, "Run some sort of personal cloud storage tool on your LAN", I thought, "That's it!". I did continue reading all though.

May I ask a question in respect of the 'nextcloud, seafile, owncloud' suggestion?

They seem to be storing my data on another computer in Germany (owncloud), or elsewhere. For very occasional transferring of files from my phone, my wife's phone or a visitors phone I would prefer to use something which is easy (once set up), convenient, and in which the data stays within my LAN. Which of your suggestions would apply in that case?

It would appear the answer would be nextcloud, but, where is the data stored? I tried to find some instructions/guidance on using nextcloud but failed. perhaps it comes with the install.

I am currently looking into [COLOR=#000000]*Wireguard.*[/COLOR]

---

### Post by TheFu on 2024-01-24
Sorry, I don't remember all the threads and everyone reading my posts.

Nextcloud is something you would install onto your equipment.   The same for the other options.  I suppose there are online "services" which will run those servers for you. I've never used any.  I don't use Google nor Apple nor Microsoft nor Box nor dropbox online stuff.  I self-host most things.  If you choose to install or use anything on someone else's computer, that's your choice.

If you are interested in self hosting, a few links:
[LIST]
[*][https://github.com/awesome-selfhosted/awesome-selfhosted](https://github.com/awesome-selfhosted/awesome-selfhosted)
[*][https://leviwheatcroft.github.io/selfhosted-awesome-unlist/sovereign.html](https://leviwheatcroft.github.io/selfhosted-awesome-unlist/sovereign.html)
[/LIST]

You can run nextcloud on a "server" that you have at home.  I run it inside a linux container (lxd/lxc), but some people run it on a raspberry pi.  Depending on the amount of files involved, a raspberry pi2 could be sufficient, but a pi3 or pi4 would have a longer support period.  I'd expect that a pi2 support period to be ending soon.

Both my "servers" are left running 24/7/366. Also, I try to prevent any drives from spinning down. I think it makes them wear out faster.  A few of my USB HDDs in external enclosures don't allow preventing that spin-down. Sigh.  I have the most issues with them, but they are just for backups, never primary storage.

If you want the snap package install version, which is 100x easier than the manual method, you'll likely want a Pi4 running some sort of Ubuntu. Snaps and Ubuntu are both from Canonical.  I run 
[LIST]
[*][https://snapcraft.io/install/nextcloud/raspbian](https://snapcraft.io/install/nextcloud/raspbian) <---- I block the snapstore and website at the network layer here, so I haven't actually seen that page recently.
[*][https://pimylifeup.com/raspberry-pi-nextcloud-server/](https://pimylifeup.com/raspberry-pi-nextcloud-server/)
[*][https://raspberrytips.com/install-nextcloud-raspberry-pi/](https://raspberrytips.com/install-nextcloud-raspberry-pi/)
[/LIST]

As a point of reference, I use LXC containers for a few things.  Backups, nextcloud, a backup pihole, email gateway, and wallabag (read-it-later clone).
```
$ lxc list
+---------------+---------+---------------------+------+-----------+-----------+
|     NAME      |  STATE  |        IPV4         | IPV6 |   TYPE    | SNAPSHOTS |
+---------------+---------+---------------------+------+-----------+-----------+
| back18        | RUNNING | xxx.xx.xx.7 (eth0)  |      | CONTAINER | 0         |
+---------------+---------+---------------------+------+-----------+-----------+
| deb12         | STOPPED |                     |      | CONTAINER | 0         |
+---------------+---------+---------------------+------+-----------+-----------+
| nextcloud-lxd | RUNNING | xxx.xx.xx.33 (eth0) |      | CONTAINER | 0         |
+---------------+---------+---------------------+------+-----------+-----------+
| pihole2       | RUNNING | xxx.xx.xx.81 (eth0) |      | CONTAINER | 0         |
+---------------+---------+---------------------+------+-----------+-----------+
| publify       | STOPPED |                     |      | CONTAINER | 0         |
+---------------+---------+---------------------+------+-----------+-----------+
| spam2         | RUNNING | xxx.xx.xx.62 (eth0) |      | CONTAINER | 0         |
+---------------+---------+---------------------+------+-----------+-----------+
| wallabag      | RUNNING | xxx.xx.xx.35 (eth0) |      | CONTAINER | 0         |
+---------------+---------+---------------------+------+-----------+-----------+

```
If I used the LXC built-in backup method, there would be snapshots listed.  I don't do backups that way, but it is pretty easy to completely backup any container or snap package+snap data, if you don't mind bloated, non-versioned, backups.

I also run 5-10 virtual machines for things like a reverse proxy, VPN, blog, full email server and even my desktop.  Obviously, these don't run on a raspberry pi. ;) A wee bit more CPU and RAM is needed.  Currently, that system with the containers and VMs is using 22GB of RAM.
```
$ free -hm
              total        used        free      shared  buff/cache   available
Mem:           30Gi        22Gi       3.4Gi       190Mi       5.2Gi       7.9Gi
Swap:         4.1Gi       2.6Gi       1.5Gi

```
But even with all those things on it, generally less than 12% of the total CPU is used.
```
top - 13:31:13 **up 38 days,  5:46**,  6 users,  load average: 0.52, 0.71, 0.77
Tasks: 715 total,   2 running, 711 sleeping,   2 stopped,   0 zombie
%Cpu(s):  9.4 us,  0.2 sy,  0.0 ni, 90.4 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
MiB Mem :  31449.6 total,   3423.2 free,  22738.3 used,   5288.0 buff/cache
MiB Swap:   4200.0 total,   1537.8 free,   2662.2 used.   8078.4 avail Mem 

```
Also, you can see that it is very stable. Up 38+ days and that's with weekly patching. In the last 38 days, no patches have needed a reboot, so I haven't.

---

### Post by SeijiSensei on 2024-01-24
I suggest installing KDEConnect. You can install the computer side of the connection with "sudo apt install kdeconnect". There's an app in the Android store for your phone. Even though it comes from the KDE world, you won't be required to install the full KDE desktop just to run this program. It uses your wifi, not Bluetooth, and lets you do a variety of things including sharing files.

---

### Post by TheFu on 2024-01-24
+1 for 
**KDEConnect** is very popular. 
There's also **GSConnect**. [https://www.omgubuntu.co.uk/2018/11/connect-android-ubuntu-gsconnect](https://www.omgubuntu.co.uk/2018/11/connect-android-ubuntu-gsconnect) for Gnome users.

I've never gotten either to work.  I have used something called **scrcpy** - but I've used it mostly to have a remote desktop into the phone from my Linux computer - some games just need a larger screen than a phone provides.

These are typically the first things people find and try.  If they work for you, fantastic!

---

### Post by makem2 on 2024-01-25
Thank you both for your input. For the immediate future I will transfer the files as and when, using a usb stick from phone to pc. I have a number of pi's including a pi4 which I ran 24/7 for torrents. I will use that as my 'cloud' to which both can connect via wifi when I work out a method. At the moment I host a Chinese professor on her first visit to the UK which takes up a lot of time so will return here later. Thanks again for your time.

---

### Post by TheFu on 2024-01-25
> **makem2 said:**
> Thank you both for your input. For the immediate future I will transfer the files as and when, using a usb stick from phone to pc. I have a number of pi's including a pi4 which I ran 24/7 for torrents. I will use that as my 'cloud' to which both can connect via wifi when I work out a method. At the moment I host a Chinese professor on her first visit to the UK which takes up a lot of time so will return here later. Thanks again for your time.

A Pi4 is a capable platform for running multiple things concurrently.  It can easy host lots of linux containers, assuming you have the 4GB or 8GB version.  However, servers shouldn't use wifi for connectivity. _**Plug that ethernet port in.**_

---

### Post by TheFu on 2024-01-25
duplicate post, somehow.

---

### Post by Claus7 on 2024-01-25
Hello,

bluetooth has received many updates over the years. One of them is that the "send to" option has vanished, since more security was added in the process. I have come across the issues you mention, yet one solution was to keep the bluetooth window under settings always on top. For example: noble requires not only to keep the window on top, yet if I send more than one file from phone to pc, for every single file I have to click the accept option. This has never happened before: sending e.g. 10 files, they were transferred all at once after accepting the first one.

Another option is to try to connect to your mobile device, and then having still on top the settings window to attempt to transfer your files. My suggestions are about ubuntu. Just trying to connect via quick launch menu resulted in disconnections, as you mention.

Regards!

---

### Post by makem2 on 2024-01-25
> **TheFu said:**
> A Pi4 is a capable platform for running multiple things concurrently.  It can easy host lots of linux containers, assuming you have the 4GB or 8GB version.  However, servers shouldn't use wifi for connectivity. _**Plug that ethernet port in.**_

Yes, of course! ethernet is the answer for a server. I have two 1TB ssd drives attached to the pi 4. Not sure if 4 or 8GB version and not used at the moment
.

Linux containers? I've not come across such.

[https://www.redhat.com/en/topics/containers/whats-a-linux-container](https://www.redhat.com/en/topics/containers/whats-a-linux-container)

---

### Post by makem2 on 2024-01-25
A quick question: What is the difference between 1. a 'cloud' and 2. a server?

As far as I can see a cloud is multiple servers hosted on some 'computer system' somewhere. A server is what is says, dedicated software hosted on your own hardware or on hardware elsewhere.

Based on that, all I need is xubuntu on my pi4 in a 'container' (maybe? - to keep it apart from the Pi OS currently installed) and a server installed to which me, my family have access from phones and/or PC.

Or a new SD card with only xubuntu on it with the torrent software installed in it.

---

### Post by makem2 on 2024-01-25
> **TheFu said:**
> Sorry, I don't remember all the threads and everyone reading my posts.

Nextcloud is something you would install onto your equipment.   The same for the other options.  I suppose there are online "services" which will run those servers for you. I've never used any.  I don't use Google nor Apple nor Microsoft nor Box nor dropbox online stuff.  I self-host most things.  If you choose to install or use anything on someone else's computer, that's your choice.

If you are interested in self hosting, a few links:
[LIST]
[*][https://github.com/awesome-selfhosted/awesome-selfhosted](https://github.com/awesome-selfhosted/awesome-selfhosted)
[*][https://leviwheatcroft.github.io/selfhosted-awesome-unlist/sovereign.html](https://leviwheatcroft.github.io/selfhosted-awesome-unlist/sovereign.html)
[/LIST]




Looked at the two links above but sovereign seems ott for my simple purpose and the other has so much to choose from I am lost.

I think I will need to search for a simple guide for my simple requirement as my knowledge of Linux is not up to what I have read.

Thanks again.

---

### Post by TheFu on 2024-01-25
> **makem2 said:**
> A quick question: What is the difference between 1. a 'cloud' and 2. a server?

Context matters.
"cloud" usually is water droplets in the sky that doesn't have a fixed position, though some clouds are always in specific locations due to consistent local conditions that make a "cloud" likely to appear in that same spot over and over.
In computing, "cloud" generally means "someone else's computers" that you don't know where they are, what jurisdiction they reside, how else is on them, or what all the processing they are doing.  There are "cloud services", "cloud computers", "cloud providers", and "cloudy systems".  What they all have in common is that you are paying (somehow) for access.  Google's search tools are "clouds" we pay with our personal data.  Amazon EC2 is a way companies and individuals can pay to rent part of a real server without knowing exactly where the real hardware is located.

OwnCloud, Seafile, Nextcloud are generally self-hosted servers that merge lots of capabilities which used to think of as a big company "cloud" service that is available only to you (in theory), running inside equipment you rent or own.  You can rent part of a computer from someone else - Amazon, Vultr, DigitalOcean, or 100 others around the world, or you can host that software on your own system(s) at your work or home.  

There are pros and cons to each.

For a long time, people rented parts of servers in someone else's data center without a second thought. These can be good people, good businesses, but sometimes they are bad people and bad businesses. Eventually, bad people/businesses get in trouble with the law and the servers they run on are taken.  Sometimes the entire rack of servers - including all the good people who just had bad luck to be in the same rack for their systems are taken too, by law enforcement.  Some well-known, but small, internet companies had their servers taken when neighbor "cloud" systems were arrested by law enforcement.  These companies never recovered and died by a trivial event carried out by the FBI.   Search on this "fbi seized hardware servers" if you want to know more. There are lots and lots of these.  What they often leave off is that nearby people/companies get screwed in these seizures.

> **makem2 said:**
> As far as I can see a cloud is multiple servers hosted on some 'computer system' somewhere. A server is what is says, dedicated software hosted on your own hardware or on hardware elsewhere.

That's one possible definition.  It can be a single computer, running lots of different services.

> **makem2 said:**
> Based on that, all I need is xubuntu on my pi4 in a 'container' (maybe? - to keep it apart from the Pi OS currently installed) and a server installed to which me, my family have access from phones and/or PC.

Not really.  It would be smarter to put the GUI version of Linux on the real hardware, then put your other "services" into either different VMs or different containers.  GUIs don't really work inside containers - well - they can, but it breaks lots of security so it is a bad idea for non-experts.  I would never run a GUI inside a Linux Container. I'm not that smart.

> **makem2 said:**
> Or a new SD card with only xubuntu on it with the torrent software installed in it.

I don't use torrents. They are a huge liability in my part of the world.

---

### Post by makem2 on 2024-01-25
> **TheFu said:**
> Context matters.
"cloud" usually is water droplets in the sky that doesn't have a fixed position, though some clouds are always in specific locations due to consistent local conditions that make a "cloud" likely to appear in that same spot over and over.
In computing, "cloud" generally means "someone else's computers" that you don't know where they are, what jurisdiction they reside, how else is on them, or what all the processing they are doing.  There are "cloud services", "cloud computers", "cloud providers", and "cloudy systems".  What they all have in common is that you are paying (somehow) for access.  Google's search tools are "clouds" we pay with our personal data.  Amazon EC2 is a way companies and individuals can pay to rent part of a real server without knowing exactly where the real hardware is located.

OwnCloud, Seafile, Nextcloud are generally self-hosted servers that merge lots of capabilities which used to think of as a big company "cloud" service that is available only to you (in theory), running inside equipment you rent or own.  You can rent part of a computer from someone else - Amazon, Vultr, DigitalOcean, or 100 others around the world, or you can host that software on your own system(s) at your work or home.  

There are pros and cons to each.

For a long time, people rented parts of servers in someone else's data center without a second thought. These can be good people, good businesses, but sometimes they are bad people and bad businesses. Eventually, bad people/businesses get in trouble with the law and the servers they run on are taken.  Sometimes the entire rack of servers - including all the good people who just had bad luck to be in the same rack for their systems are taken too, by law enforcement.  Some well-known, but small, internet companies had their servers taken when neighbor "cloud" systems were arrested by law enforcement.  These companies never recovered and died by a trivial event carried out by the FBI.   Search on this "fbi seized hardware servers" if you want to know more. There are lots and lots of these.  What they often leave off is that nearby people/companies get screwed in these seizures.



That's one possible definition.  It can be a single computer, running lots of different services.



Not really.  It would be smarter to put the GUI version of Linux on the real hardware, then put your other "services" into either different VMs or different containers.  GUIs don't really work inside containers - well - they can, but it breaks lots of security so it is a bad idea for non-experts.  I would never run a GUI inside a Linux Container. I'm not that smart.



I don't use torrents. They are a huge liability in my part of the world.

Thanks for bearing with me.

You earlier suggested installing ubuntu on a Pi but I am wondering why. Is the Pi software not capable?

Edit: Found the answer:

snip>
[COLOR=#000000]_If you want the snap package install version_, which is 100x easier than the manual method, you'll likely want a Pi4 running some sort of Ubuntu. _Snaps and Ubuntu are both from Canonical_. I run
snip>[/COLOR]

---

