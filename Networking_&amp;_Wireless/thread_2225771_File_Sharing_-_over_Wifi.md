---
title: "File Sharing - over Wifi"
date: 2014-05-23
forum: Networking &amp; Wireless
---

### Post by bazsound on 2014-05-23
This is probbaly the 5th or 6th time i have looked into and tried to setup but after many wasted days of searching and reading i usually give up. There is so much different information out there and most of it usually does not quite fit with my setup.

I already have file sharing setup which works over ethernet on both a ubuntu laptop and a windows laptop using samba. But i just cant work out from the many posts and guides how to do this via wireless.

I dont have a wireless router, but i do have 2 wireless interfaces. 1 is a broadcome USB adapter and that uses ndiswrapper. it works fine when connecting to a wifi hotspot.

Also i have a broadcome pci card (airforce one) which is working fine with the linux provided driver.

for internet i use my phone for tethering, so i can use 1 interface for connecting to my phone, and want to setup my other interface to share over a network, pretty much what im doing over ethernet.

Or maybe its possible to do it through my tethered wifi phone? who knows its all confusing.

---

### Post by tgalati4 on 2014-05-23
Normally you would have router with 4 wired, ethernet ports and a wifi antenna.  Then your router becomes an Access Point (AP) using Infrastructure mode--one main antenna and everybody in your household talks to it.  Then you can use SAMBA and freely share files from wired and wireless devices.

What you are trying to do is use your wireless antenna on your laptop and create an AP (which then shares your internet connection) and then have your laptop act as a gateway for other computers connected to it to be able to share files.  Although this can be done, it is quite difficult in practice, as you have discovered.

For the amount of time that you have spend trying to make this happen, you could have spent $20 (used) to $100 (new) for a decent wifi router.

To continue your pain you would do the following:

1.  Select a PC that is on most of the time and install the USB wireless adapter on it.  Ndiswrapper means you are using Windows, binary drivers, and you may have limited functionality.
2.  Set up the wireless radio as "Infrastructure".
3.  Read up on connection sharing:  [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)
4.  Attempt to share your wireless connection with your wired connection so that they share the same network (for example 192.168.1.XX).
5.  Set up a shared folder and give it guest read privileges.
6.  Use a laptop to connect to your wireless AP and see if you see the shared directory.
7.  Check craigslist for a used wireless router.

---

### Post by bazsound on 2014-06-08
ok i found an easier solution, it turns out that my phone acts as a wireless AP

If i turn on wifi protable hotspot to share my phones internet and connect my desktop and laptop computer to the phone, i can ping both computers,

I setup SSH and was able to connect to my desktop and browse the entire computer.

however it was painfully slow and unreliable.

So i then under the sugestion of my friend use NFS which is designed for this kind of thing.

well when i tried to start nfs and connect it via the guides instructions.

unable to resolve host

---

### Post by bazsound on 2014-06-08
Right so im going with nfs but the documentation is ot very helpfull

# /etc/exports: the access control list for filesystems which may be exported
#        to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#

/home/bazsound     192.168.43.2(rw)

this is my exports file, the ubuntu guide states to use a specific hostname, but does not detail what the hostname should be and where it comes from.

after some various trys of stuff, the best i can get is access denied from the server while trying to mount

or it sits there doing nothing for a whle

---

### Post by bazsound on 2014-06-08
Ok i got it working, error in mount specifying wrong path.

Now i just need to figure out how to share my external drive which is mounted at /media/TOSHIBA EXT.

puting /media/TOSHIBA\EXT

doesnt work

exportfs: Failed to stat /media/TOSHIBA\EXT: No such file or directory

---

