---
title: "netgear wg111v1 and feisty"
date: 2007-04-15
forum: Networking &amp; Wireless
---

### Post by jiaz1 on 2007-04-15
i've read a bunch of posts, etc, and ended up with conflicting posts.

i just upgraded from edgy and now there's no longer a wireless profile in my networks preferences.

how should i get my wireless usb adapter working?

wait until the official release of feisty?

---

### Post by willz06jw on 2007-04-22
I have noticed that the WG111v1 will work with WEP in Feisty with ndiswrapper.  It used to work with WPA, but there is some problem ([https://bugs.launchpad.net/ubuntu/+bug/105977)](https://bugs.launchpad.net/ubuntu/+bug/105977)).  

I have to also blacklist both bcm43xx and prism54usb in /etc/modprobe.d/blacklist

I am just hoping that they will add support for this adapter in the future and we won't have to struggle through all of this just to get the internet working.

Hope that helped,
William

---

### Post by willz06jw on 2007-04-23
OK I got the ndiswrapper and WG111v1 w/ Feisty working with both WPA and WEP.  

All you have to do is install the newest version of ndiswrapper from the source as I found out from Kevin Oberle in Launchpad ([https://bugs.launchpad.net/ubuntu/+bug/105977](https://bugs.launchpad.net/ubuntu/+bug/105977))

Here is the download
[http://sourceforge.net/projects/ndiswrapper](http://sourceforge.net/projects/ndiswrapper)

and here is the wiki describing how to do the install -- kind of
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

I have to let you know it is a little of a pain for someone unused to installing programs from source (me).

Before d/ling I had to:
Remove ndiswrapper using Synaptic
I had to then use sudo rm -r to remove all of the files and directories that had ndiswrapper in their name
I then had to remove my old wireless profile
I then had to remove any files with loadndisdriver in the name
(Note: I used slocate to find the files)

Then I installed using the wiki above

---Of course the make installer put something in the wrong directory and I had to move it:
It put the ndiswrapper.ko in the /lib/modules/2.6.20-15-generic/misc/ directory so I had to move (sudo mv) ndiswrapper.ko to the /lib/modules/2.6.20-15-generic/kernel/ubuntu/misc/ndiswrapper/ directory.
I think the code would be: 
```
sudo mkdir /lib/modules/2.6.20-15-generic/kernel/ubuntu/misc/ndiswrapper/
sudo mv /lib/modules/2.6.20-15-generic/misc/ /lib/modules/2.6.20-15-generic/kernel/ubuntu/misc/ndiswrapper/
```

I then used the Ubuntu Help to load the driver in the OS and keep it there
Ubuntu Help documentation said do the following:

1.  Open Applications &#8594; Accessories &#8594; Terminal and type: 

```
sudo ndiswrapper -i ~/Desktop/drivername.inf
```

The above command assumes that your .INF file is named drivername.inf and was copied to your Desktop. Replace these values if necessary.

2.  To check if it is working correctly, type: 
```
ndiswrapper -l
```

If it is working correctly, you should see:
      		Installed ndis drivers:
      		{name of driver}  driver present, hardware present
3.  For ndiswrapper to function, you need to load a module. To do this, type:
```
sudo depmod -a
      		sudo modprobe ndiswrapper

```

4.  To ensure that the module is loaded each time you boot the computer, type:

```
sudo ndiswrapper -m
```


Hope this help you fellow WG111v1 users.

Will

---

