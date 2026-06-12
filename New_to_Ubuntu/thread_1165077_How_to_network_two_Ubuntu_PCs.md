---
title: "How to network two Ubuntu PCs"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by TomFresh on 2009-05-20
I need to network one ubuntu PC to another (for some filesharing and such) and I don't know how to go about it. I edited the connections on both to the IPV4 method 'Shared to other computers'. I created a shared folder on each computer and checked in the Network if they would show up but both computers do not show. They show up when I hook them up using the DHCP mode on a router, but I want to hook them up directly to eachother with my crossover cable. 

One of the computers also gets the error "Unable to mount location: Failed to retrieve share list from server" when trying to get into the Windows Network, if that makes any difference. 

Any help appreciated,


Tom.

---

### Post by mapes12 on 2009-05-20
Try this: [http://ubuntuforums.org/showthread.php?t=793308](http://ubuntuforums.org/showthread.php?t=793308)

---

### Post by lisati on 2009-05-20
If you don't mind using a router, then this might be of some help: [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by mgmiller on 2009-05-20
If you are connecting 2 machines that have gigabit ethernet adapters, you don't use a crossover cable.  You would just use a regular patch cable.  Since they are not connected to a router or other DHCP server, they will need to have static ip addresses and then you can just point the machines at each other using the Places > Connect to server applet.  Or you could put the ip address in the Nautilus address bar after opening Places > Home for example. 

If you are using 10/100 nics, then you would use a crossover cable, but the rest of the instructions above would still apply.

---

### Post by trinidadflores on 2009-05-20
> **mgmiller said:**
> If you are connecting 2 machines that have gigabit ethernet adapters, you don't use a crossover cable.  You would just use a regular patch cable.  Since they are not connected to a router or other DHCP server, they will need to have static ip addresses and then you can just point the machines at each other using the Places > Connect to server applet.  Or you could put the ip address in the Nautilus address bar after opening Places > Home for example. 

Why would you not need a crossover cable? just wondering.

---

### Post by Bölvaður on 2009-05-20
check the link lisati provided.
But.... I recommend doing networking my way.

Btw you probably need to do a tiny bit of googling to help you out, but this is super easy.


Download nfs server and client programs from synaptic package manager

or click on these this link [nfs-kernel-server]("apt:nfs-kernel-server") 

you should then click this link [nfs-common]("apt:nfs-common")  to see if all of the necessary dependency for running nfs client and server are met.

Now press these keys: Alt+F2
Copy and paste : ```
gksu gedit /etc/exports
```
and type in your password (this is a system change, so it requires super user privileges)

Add this line at the bottom of the file. This line allows any local ip connecting to your machine, if you wish to restrict it, you can state exactly which ips you want to allow having access to your computer.
```

/home/george/mySharedFolder	192.168.1.1/24(rw,async)
```
you will have to change the first part of the line to point at the place on this computer where your shared data will be kept. (like changing the user name to something else than george)


When you have done this on both computers you need to let both computers auto mount each other at startup.

Create place for them to mount to:
Open the terminal (Applications &#8594; Accessories &#8594; Terminal)
Copy paste: ```
sudo mkdir /mnt/external
``` note that you can change the name of the directory if you wish, it is the last word in the code called "external", just change it for "bobby" if you wish, just remember to change it accordingly in my instructions further down &#8595;



Now you need to set your computers to static ip.
You might feel comfortable by doing it by point and clicking.. but I have no idea how it looks on your end so you are kind of on your own. Try double clicking or right clicking the network icon if you can find it.




When you have that on both computers lets set it to mount each other at boot
press these buttons: Alt+F2
copy paste : ```
gksu gedit /etc/fstab
```
copy and paste this to the bottom of this file and change the ip so it matches the other pc's ip (the one you are connecting to)
```

192.168.1.200:/home/george/mySharedFolder /mnt/external/ nfs rsize=8192,wsize=8192,timeo=14,intr
```
Change the ip and the path to the shared folder on the other computer accordingly.


you will need to restart your computer for the nfs-kernel-server to take effect, but if you already have you can open the terminal and type```
sudo mount -a
```
then you should be able to see some files be in your /mnt/external directory. Unless if you did some typo



have fun):P

---

### Post by mgmiller on 2009-05-21
> Why would you not need a crossover cable? just wondering.The gigabit ethernet spec allows for direct connections without using a special crossover cable.  I'm not sure, but if you do try to use a crossover cable, it might not work.  My son successfully linked his laptop and my tower with a plain old patch cable.  It only took him a few seconds to get them linked and transfering files.  He's an IT systems professional and he's the one who told me about the gigabit ethernet spec allowing (requiring?) a plain patch cable for direct connections.  For best results the patch cable should be cat5e or cat6.
Here is a link to more info comparing 10/100 with gigabit ethernet and how to direct connect them:
[http://www.sql-server-performance.com/articles/clustering/gigabit_ethernet_networking_p1.aspx](http://www.sql-server-performance.com/articles/clustering/gigabit_ethernet_networking_p1.aspx)

---

### Post by bacardiandwatermelon on 2009-05-21
Are you sure his laptop didn't have Auto-MDIX?
[http://en.wikipedia.org/wiki/Auto-MDIX](http://en.wikipedia.org/wiki/Auto-MDIX)

---

### Post by mgmiller on 2009-05-21
Nope.  Auto MDIX, or something like it has been rolled into the gigabit standard.  If you're using 2 gigabit adapters, you can just wire them together directly without a patch cable.  Here is a quote from the link I sited above.
> Gigabit Ethernet uses a patch cable to connect one adapter to either a switch port or directly to another adapter. This fact appears to be overlooked in much of the publicly available material....So the question remains, what is necessary to connect two Gigabit Ethernet adapters directly? It turns out that the answer is standard Cat 5e or better patch cables!

---

