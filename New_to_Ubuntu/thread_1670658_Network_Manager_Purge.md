---
title: "Network Manager Purge"
date: 2011-01-19
forum: New to Ubuntu
---

### Post by Linkpark1 on 2011-01-19
Hi,
I'm a complete noob/newb. I have no idea what I am doing and I try to avoid sudo in terminal at all times. I have no idea what I was doing and put in *sudo purge network-manager* and now I have no internet on Ubuntu 10.10

SOMEONE PLEASE HELP ME GET INTERNET BACK BECAUSE I FAIL.

Thank you.

P.S - I love you! Peace! :popcorn:

---

### Post by Frogs Hair on 2011-01-19
Try this in the terminal .```
sudo apt-get install network-manager-gnome
```

Sorry , it's hard to download a package with no internet .

---

### Post by ajgreeny on 2011-01-19
With no network manager I don't think the command will work; it's a bit of a catch 22 situation.  If you have another computer, or even can run the live CD, you should be able to navigate to and download the missing packages from [http://packages.ubuntu.com/](http://packages.ubuntu.com/).

Make sure you choose the correct ubuntu version, download the packages to a USB flash drive, then boot back to your installed version, plugin the flash drive and use terminal command ```
sudo dpkg -i /path/to/flash/drive/*.deb
```

---

### Post by Paqman on 2011-01-19
> **ajgreeny said:**
> then boot back to your installed version, plugin the flash drive and use terminal command ```
sudo dpkg -i /path/to/flash/drive/*.deb
```

You can also just double-click on the file ;)

---

### Post by Laysan_A on 2011-01-19
Hey, can't he just add the live cd to his sources and install it with synaptic? I mean networkmanager is on the cd, isn't it?

---

### Post by cek on 2011-01-19
What do you use for your internet connection?  If you have a router that assigns you an IP address via DHCP, it's trivially easy to get internet back, then I would suggest installing network manager again as described above.

From a terminal, assuming you use eth0 and DHCP
```

sudo ifconfig eth0 up
sudo dhcpcd eth0

```

After this you should have internet access, now reinstall network manager.

---

### Post by cek on 2011-01-19
What do you use for your internet connection?  If you have a router that assigns you an IP address via DHCP, it's trivially easy to get internet back, then I would suggest installing network manager again as described above.

From a terminal, assuming you use eth0 and DHCP
```

sudo ifconfig eth0 up
sudo dhcpcd eth0

```

After this you should have internet access, now reinstall network manager.

---

### Post by cek on 2011-01-19
What do you use for your internet connection?  If you have a router that assigns you an IP address via DHCP, it's trivially easy to get internet back, then I would suggest installing network manager again as described above.

From a terminal, assuming you use eth0 and DHCP
```

sudo ifconfig eth0 up
sudo dhcpcd eth0

```

After this you should have internet access, now reinstall network manager.

---

### Post by cek on 2011-01-19
What do you use for your internet connection?  If you have a router that assigns you an IP address via DHCP, it's trivially easy to get internet back, then I would suggest installing network manager again as described above.

From a terminal, assuming you use eth0 and DHCP
```

sudo ifconfig eth0 up
sudo dhcpcd eth0

```

After this you should have internet access, now reinstall network manager.

---

### Post by cek on 2011-01-19
What do you use for your internet connection?  If you have a router that assigns you an IP address via DHCP, it's trivially easy to get internet back, then I would suggest installing network manager again as described above.

From a terminal, assuming you use eth0 and DHCP
```

sudo ifconfig eth0 up
sudo dhcpcd eth0

```

After this you should have internet access, now reinstall network manager.

---

### Post by cek on 2011-01-19
.

---

### Post by cek on 2011-01-19
Sorry -- Had some problems with my proxy, resulting in a multipost.

---

### Post by mattman85 on 2011-01-19
> **Linkpark1 said:**
> Hi,
I'm a complete noob/newb. I have no idea what I am doing and I try to avoid sudo in terminal at all times. I have no idea what I was doing and put in *sudo purge network-manager* and now I have no internet on Ubuntu 10.10

SOMEONE PLEASE HELP ME GET INTERNET BACK BECAUSE I FAIL.

Thank you.

P.S - I love you! Peace! :popcorn:

Linkpark1, did your question get solved? If not, use Layson_A's approach. Put in your LiveCD, and set it as a package source in Software Sources (open Synaptic Package Manager and clicking on Settings, and then Repositories). There should be an area with the liveCD listed, with a checkbox next to it. Check that and click ok. reload, and then in Synaptic, search for network-manager. Install it and all dependencies.

then let us know what happens.

---

### Post by Linkpark1 on 2011-01-19
How to delete this message?

---

### Post by Linkpark1 on 2011-01-19
Sorry for the repost. Computer obviously dislikes me

---

### Post by Linkpark1 on 2011-01-19
Need to learn how to delete messages

---

### Post by Linkpark1 on 2011-01-19
> Linkpark1, did your question get solved? If not, use Layson_A's approach. Put in your LiveCD, and set it as a package source in Software Sources (open Synaptic Package Manager and clicking on Settings, and then Repositories). There should be an area with the liveCD listed, with a checkbox next to it. Check that and click ok. reload, and then in Synaptic, search for network-manager. Install it and all dependencies.

So when i put the liveCD in, i open Synaptic, go into Repositories and check the liveCD. But when i go to reload, it throws some errors at me =(

Basically heaps of W:Failed to fetch ...<input url> Could not resolve

then these:

> 

W: Failed to fetch cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/dists/maverick/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/dists/maverick/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Some index files failed to download, they have been ignored, or old ones used instead.


---

### Post by Laysan_A on 2011-01-19
Apparently you need to use the terminal and do:

apt-cdrom add

first, so the system can recognize it (don't know why it's not done automatically).

There also appears to be an old bug - don't know if it applies anymore - but if after you've done that you can't get the cd to mount, open etc/fstab in gedit (you'll need to use gksu "gksu gedit" without the quotes) and change the entry for /cdrom to /cdrom/ and you should be able to mount it.

---

### Post by Linkpark1 on 2011-01-19
I did a search for fstab and found it in the /etc folder. Although the file doesnt mention cd Rom at all. There are fstab examples though which do. But they are read only. What should I do?

---

### Post by Laysan_A on 2011-01-19
Hi Linkpark1,

It's very important that you read the instructions people (myself included) give you and consider them carefully before taking any action.

Now, did you run the apt-cdrom add command? What was the result? Did you open synaptic, place a check in the box where it says to add a source from cd? Did you then reload the package information, then search for networkmanager, select and install it?

Now, I know you didn't get as far as this, but we need to know just what you've done, and what happened when you did it, as specifically as possible.:)

Oh, one more thing...I noticed when you wrote cdrom, you wrote cd Rom. In Linux it is very important to get the case and spacing correct when doing anything with the command line (just in case you weren't aware).

As to your question about etc/fstab, no. Don't do anything with it unless someone who knows what they're doing tells you you should. I don't know why I didn't remember this, but I tried to add an entry for cdrom in my Lucid installation a few weeks ago, and the OS didn't like it. I don't know what (K)Ubuntu is doing now to recognize and mount cdrom, but I couldn't find an entry for it in the places there would've been an entry for it in Karmic. I'm sorry I made that recommendation about etc/fstab, now. Just try to forget I said anything.

---

### Post by Linkpark1 on 2011-01-20
OK. i did

inserted live CD
apt-cdrom add

> 
Using CD-ROM mount point /media/apt/
Identifying.. 
E: Unable to stat the mount point /media/apt/ - stat (13: Permission denied)
W: Failed to mount '/dev/sr0' to '/media/apt/'


Opened Synaptic
Checked installable from CD
Clicked Reload

> 
W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg)  Could not resolve 'au.archive.ubuntu.com'

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2](http://au.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2)  Could not resolve 'au.archive.ubuntu.com'

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en_AU.bz2)  Could not resolve 'au.archive.ubuntu.com'

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2](http://au.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2)  Could not resolve 'au.archive.ubuntu.com'

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en_AU.bz2)  Could not resolve 'au.archive.ubuntu.com'

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2](http://au.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2)  Could not resolve 'au.archive.ubuntu.com'

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en_AU.bz2)  Could not resolve 'au.archive.ubuntu.com'

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2](http://au.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2)  Could not resolve 'au.archive.ubuntu.com'

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en_AU.bz2)  Could not resolve 'au.archive.ubuntu.com'

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg)  Could not resolve 'extras.ubuntu.com'

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Could not resolve 'extras.ubuntu.com'

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_AU.bz2](http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_AU.bz2)  Could not resolve 'extras.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en_AU.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en_AU.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en_AU.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en_AU.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en_AU.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en_AU.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en_AU.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en_AU.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_AU.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_AU.bz2)  Could not resolve 'archive.ubuntu.com'


---

### Post by Laysan_A on 2011-01-20
Okay, I wondered about that when I read the original sources for that command in the forum - it looks like you need to use sudo to add a new source.

sudo apt-cdrom add

Then it should accept it.

Don't worry about all those error messages. They just tell you what you already know, that apt is unable to reach the repos. You were correct in your earlier post that the important errors have to do with the cd.

---

### Post by Linkpark1 on 2011-01-20
Opened terminal
Typed sudo apt-cdrom add

> 
Using CD-ROM mount point /media/apt/
Identifying.. [e6fbe1571743a7752d144a427af01351-2]
Scanning disc for index files..
Found 2 package indexes, 0 source indexes, 0 translation indexes and 1 signatures
This disc is called: 
'Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)'
Copying package lists...gpgv: Signature made Fri 08 Oct 2010 02:24:55 EST using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Reading Package Indexes... Done
Writing new source list
Source list entries for this disc are:
deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
Repeat this process for the rest of the CDs in your set.
W: Skipping nonexistent file /media/apt/dists/maverick/main/binary-i386/Packages
W: Skipping nonexistent file /media/apt/dists/maverick/restricted/binary-i386/Packages


---

### Post by Paqman on 2011-01-20
Ok, so ow can you reinstall Network Manager?

---

### Post by ajgreeny on 2011-01-20
In the past, and if things have not changed, it is impossible to use the live CD as a package source; it needs the Alternate Install CD.

My apologies if the live CD now does work in that way, but I believe you will find things are still the same, hence the errors at the end of your post:-
> W: Skipping nonexistent file /media/apt/dists/maverick/main/binary-i386/Packages
W: Skipping nonexistent file /media/apt/dists/maverick/restricted/binary-i386/PackagesThose folders simply are not there on the live CD.

---

### Post by Laysan_A on 2011-01-21
> In the past, and if things have not changed, it is impossible to use the  live CD as a package source; it needs the Alternate Install CD.

Well...that certainly sucks!

My apologies, Linkpark1...

---

