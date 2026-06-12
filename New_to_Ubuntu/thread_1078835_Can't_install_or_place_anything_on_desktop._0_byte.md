---
title: "Can't install or place anything on desktop. 0 bytes available"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by paulkruger on 2009-02-23
I am having a lot of problems with Ubuntu errors related to available space for files.  I have two drives each of which has over 15 GB empty space. Several problems seem related.

1) try to place a link on desktop. error says requires 38 bytes, 0 available.
2) tried to install package getting error no space on device.
3) trying updates, same types of error...no space available.
4) cannot set preference in Firefox. will not remember any changes to settings. Always errors on start then asks if I want to restart old session or start a new session. Suspect can't write to config files.
5) cannot download files. I downloaded Opera to another machine on network and could transfer the file over ok. Seemed to install. I have the icon but nothing happens when I click it.

Ideas why all this empty space is invisible to ubuntu?:(

---

### Post by taurus on 2009-02-23
Have a look at your disk space first to make sure it is not 100% used.

Applications -> Accessories -> Terminal
```
df -h
```

---

### Post by Rolcol on 2009-02-23
> **taurus said:**
> Have a look at your disk space first to make sure it is not 100% used.

Applications -> Accessories -> Terminal
```
df -h
```
You can use the Disk Usage Analyzer utility in Applications > Accessories > Disk Usage Analyzer to see what files (if any) are taking up that space.  My brother's machine had logging problems and the some log files grew to 1.5GB.

---

### Post by Bölvaður on 2009-02-23
Before we can help we will need to know everything about your harddisk and it's partitions.


First send us your partition scheme... an easy way would be sending screenshot of gparted (gnome partition editor).
That can be done by pressing Alt+F4 and type in "sudo gparted" and then press "Print Scrn" button often next to F12 on standard keyboards. Note that if you have many harddisk drives you will also need to send screenshots of those.

Also you should open up the terminal (Applications &#8594; Accessories &#8594; Terminal) and type in : "cat /etc/fstab" 

When you post the screenshot you set it under attachment but you have to copy and paste the output of cat /etc/fstab into the post but with [C[SIZE="1"] [/SIZE]ODE] and [/COD[SIZE="1"] [/SIZE]E]


> **paulkruger said:**
> ... I have two drives each of which has over 15 GB empty space. Several problems seem related.

[... things that obviusly fail if you dont have enough free space on the / partition ...]

Ideas why all this empty space is invisible to ubuntu?:(

There are 2 possibilities:

1. Those drives or partitions are not mounted
2. You have all your data on / partition but not the empty partitions and therefore you end up with what you got :)

Solutions :

1. mount the empty partitions and move all your data onto them
2. move all your data onto the empty partitions

---

### Post by paulkruger on 2009-02-24
> **taurus said:**
> Have a look at your disk space first to make sure it is not 100% used.

Applications -> Accessories -> Terminal
```
df -h
```

Not in that way but viewing in partition manager says I have all this free space. I even re-arranged the two partitions to open up gobs of space? :mad:

---

### Post by paulkruger on 2009-02-24
Filesystem............Size...Used..Avail.Use%.Mounted on
/host/ubuntu/disks/root.disk
                      3.5G  3.5G     0 100% /
tmpfs.................251M.....0...251M   0% /lib/init/rw
varrun................251M...328K..251M   1% /var/run
varlock...............251M.....0...251M   0% /var/lock
udev..................251M..2.7M...249M   2% /dev
tmpfs.................251M..240K...251M   1% /dev/shm
/dev/sda5.............16G...5.8G...11G  36% /host
lrm...................251M...2.0M...249M   1% /lib/modules/2.6.27-11-generic/volatile
overflow              1.0M   36K  988K   4% /tmp
----

I had to create a file on a windows machine on the network and paste this into that text file because I cannot save anything on the Ubuntu machine.

---

### Post by taurus on 2009-02-24
> **paulkruger said:**
> Filesystem            Size  Used Avail Use% Mounted on
[B][COLOR="Red"]/host/ubuntu/disks/root.disk
                      3.5G  3.5G     0 100% /[/COLOR][/B]
tmpfs                 251M     0  251M   0% /lib/init/rw
varrun                251M  328K  251M   1% /var/run
varlock               251M     0  251M   0% /var/lock
udev                  251M  2.7M  249M   2% /dev
tmpfs                 251M  240K  251M   1% /dev/shm
/dev/sda5              16G  5.8G   11G  36% /host
lrm                   251M  2.0M  249M   1% /lib/modules/2.6.27-11-generic/volatile
overflow              1.0M   36K  988K   4% /tmp
----

I had to create a file on a windows machine on the network and paste this into that text file because I cannot save anything on the Ubuntu machine.
Wubi!

---

### Post by paulkruger on 2009-02-24
Problem with getting info to the forum is I am switching between Windows machine where I am viewing the forum and the linux box where I can't save anything to post here.

---

### Post by paulkruger on 2009-02-24
> **Bölvaður said:**
> 

1. mount the empty partitions and move all your data onto them
2. move all your data onto the empty partitions

--

I had an earlier post about mounting because I could not view data in the other drives.  I never found out how to mount them?

They are NTFS partitions. Ubuntu is also able to see the C: drive data ( is also NTFS ) which has the Windows OS on it so I assume that one is mounted?  I can read-write over the network and open a text file on the other networked machine but I can't create a file over then network with Ubuntu on the Windows machine.

---

### Post by avtolle on 2009-02-24
It looks like when the Wubi install was done, the OP allocated only 3.5 GB for the Ubuntu system, which appears to be full. The options available are to use LVPM to enlarge the Ubuntu install, or to add additional partitions to the Wubi installation. See [https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?) for some information.

---

### Post by Bölvaður on 2009-02-24
*edit*
according to avtolle I may be doing too much for too little. but still the problem is that wubi is not setting up a good partition scheme where your data are not on the / partition.
*/edit*


What you will need to do is have one of the ntfs partition auto mounted every time you start up your system and move all your data onto it.

To do that you add the physical address of the (ntfs) partition in this file : /etc/fstab

First we need to know the physical address.
I already told you to post a screenshot of your gparted (gnome partition editor) where it is 

Fire up the terminal (Applications &#8594; Accessories &#8594; Terminal)
type : ```
sudo fdisk -l
```
_post us the output please._


btw if you want to save some space you can uninstall some applications with System &#8594; Administrator &#8594; Synaptic package manager. You may be able to get enough space for making ubuntu usable by uninstalling applications like pidgin, rythmbox, gnome-games, gimp, open-office. Then later when you got your system up you will be able to install it again.

---

### Post by paulkruger on 2009-02-28
> **avtolle said:**
> It looks like when the Wubi install was done, the OP allocated only 3.5 GB for the Ubuntu system, which appears to be full. The options available are to use LVPM to enlarge the Ubuntu install, or to add additional partitions to the Wubi installation. See [https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?) for some information.

I can not boot Ubuntu any longer. It says it does not have enough disk space to do so.  How do I fix this so I can fix the other installation errors or should I just delete it all and try again?

I was at first impressed with the Ubuntu install but never saw anything about Wubi unless that is the default installer on the disks I downloaded.  

I did not expect this much trouble. It appeared to correctly recognize and  install drivers, network etc. then some how not know to mount any extra space to function in the process. The C drive is not where Ubuntu is installed yet that is what it displays as the only visible NTFS drive. The partition Ubuntu installed to has a lot of free space, over 15GB empty so why would it deny itself enough space to function in the first place?

Paul

EDIT:  Another problem I had after installing.  My TCP/IP on the Windows 2k boot was damaged when Ubuntu installed.  I did not really notice this because when I was working on the linux boot the net access is fine and I just used the KVM switch to the other computer for windows and internet.  But when I boot the dual boot to windows, I can no longer access anything via internet. I note the date it stopped from the anti virus waring and the last date it was able to update is the same day I installed the Ubuntu.

---

