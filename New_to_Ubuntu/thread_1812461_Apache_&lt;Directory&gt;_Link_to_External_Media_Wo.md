---
title: "Apache &lt;Directory&gt; Link to External Media Woes"
date: 2011-07-26
forum: New to Ubuntu
---

### Post by Bushido89 on 2011-07-26
Hi All,

Firstly, thanks for taking the time to read.

I've got a number of DvDs ripped to an external HDD, connected to my Desktop (Box A). I have since lost most of these DvDs, and I would like to watch them on Box B (a thin client, connected to a wide-screen).

These two machines are networked via wireless, through a BT Home Hub. Windows 7 flat out refuses to share files between nodes natively. This appears to be due to the Home Hub (as neither node can ping each other, and Samba is pulling a blank also), though I am unsure.

I happened to be playing about with Apache2, and (upon testing outside of localhost) realised that this might solve my problem. Files copied to /var/www work like a dream, and (with additions to the /etc/Apache2/<config>) so do files from /home/me.

There is however not enough space on my Ubuntu partition to throw everything into /www/var, or /home/me. I have added:

```
Alias /home/ "/dev/sdb1/Films"
<Directory "/dev/sdb1/Films">
	Options +Indexes FollowSymLinks +ExecCGI
	AllowOverride AuthConfig FileInfo
        Order allow,deny
	Allow from all
</Directory>
```

to the apache config, and believe that the server is linking to it okay as it's throwing a 403 error. I have used

```
sudo nautilus
``` and ```
sudo chown
``` 

to attempt to modify permissions in both /dev/sdb + /dev/sdb1 and /media/ratherlonghexaddress, the former has (seemingly) worked, the latter has not.

Ubuntu Version is 11.04, FileSystem on sdb is NTFS, Apache is the latest version (as of yesterday), and as LAMP. I've searched a number of related threads, however none seem to pertain to 11.04, which I am rather new to (along with Linux in general)

Have I gone about this the right way? Is there something crucial I've missed?

---

### Post by androssofer on 2011-07-26
> **Bushido89 said:**
> Hi All,

Firstly, thanks for taking the time to read.

I've got a number of DvDs ripped to an external HDD, connected to my Desktop (Box A). I have since lost most of these DvDs, and I would like to watch them on Box B (a thin client, connected to a wide-screen).

These two machines are networked via wireless, through a BT Home Hub. Windows 7 flat out refuses to share files between nodes natively. This appears to be due to the Home Hub (as neither node can ping each other, and Samba is pulling a blank also), though I am unsure.

I happened to be playing about with Apache2, and (upon testing outside of localhost) realised that this might solve my problem. Files copied to /var/www work like a dream, and (with additions to the /etc/Apache2/<config>) so do files from /home/me.

There is however not enough space on my Ubuntu partition to throw everything into /www/var, or /home/me. I have added:

```
Alias /home/ "/dev/sdb1/Films"
<Directory "/dev/sdb1/Films">
	Options +Indexes FollowSymLinks +ExecCGI
	AllowOverride AuthConfig FileInfo
        Order allow,deny
	Allow from all
</Directory>
```

to the apache config, and believe that the server is linking to it okay as it's throwing a 403 error. I have used

```
sudo nautilus
``` and ```
sudo chown
``` 

to attempt to modify permissions in both /dev/sdb + /dev/sdb1 and /media/ratherlonghexaddress, the former has (seemingly) worked, the latter has not.

Ubuntu Version is 11.04, FileSystem on sdb is NTFS, Apache is the latest version (as of yesterday), and as LAMP. I've searched a number of related threads, however none seem to pertain to 11.04, which I am rather new to (along with Linux in general)

Have I gone about this the right way? Is there something crucial I've missed?

not quite sure about the appache config, but could you do:

```
cd /var/www

mkdir films

cd films

ln -s /dev/sdb1 hardDrive
```

tht will create a symbolic link in /var/www/films called hardDrive tht links to your Hard Drive...? ***mite need to use sudo on some of those commands

---

### Post by Bushido89 on 2011-07-26
> **androssofer said:**
> not quite sure about the appache config, but could you do:

```
cd /var/www

mkdir films

cd films

ln -s /dev/sdb1 hardDrive
```

tht will create a symbolic link in /var/www/films called hardDrive tht links to your Hard Drive...? ***mite need to use sudo on some of those commands

Thank you kindly for the swift reply. I've tried adding it, but my browser is still throwing the 403...I think it might be to do with not being able to set permissions on the drive itself (or any directories therein), only in /dev/sdb*

Thanks once again though ^_^.

---

### Post by androssofer on 2011-07-26
> **Bushido89 said:**
> Thank you kindly for the swift reply. I've tried adding it, but my browser is still throwing the 403...I think it might be to do with not being able to set permissions on the drive itself (or any directories therein), only in /dev/sdb*

Thanks once again though ^_^.

ratz...

ntfs doesnt suport permissions, so like u said, once it hits the harddrive its gna just keep complaining about it... unless u give appache root permissions, which i wudnt do... as its not safe... 

is this for a network share btw? can u forward ports on the bt homehub? nvr used 1...

if so try forwarding these ports to ur samba server and see wot comes up then:

137
138
139
445
389
901
(the first 4 are the main 1s, last 2 are for gd measure :-) )
assuming u havent played about with port forwarding on ur router etc yet...

---

### Post by Bushido89 on 2011-07-26
> **androssofer said:**
> ratz...

ntfs doesnt suport permissions, so like u said, once it hits the harddrive its gna just keep complaining about it... unless u give appache root permissions, which i wudnt do... as its not safe... 

is this for a network share btw? can u forward ports on the bt homehub? nvr used 1...

if so try forwarding these ports to ur samba server and see wot comes up then:

137
138
139
445
389
901
(the first 4 are the main 1s, last 2 are for gd measure :-) )
assuming u havent played about with port forwarding on ur router etc yet...

I've played a little, I know what ports are & why they exist; most I've ever used it for is throwing 80 from hub to 80 on my node to allow incoming connections.

I'll try forwarding those ports for sure, see what happens. Sadly my family for some reason doesn't understand my grim fascination with such matters and is dragging me from my cave.

Thanks a bunch for your help - soon as I throw off the yoke of having my dinner paid for; I'll keep you posted :).

---

### Post by androssofer on 2011-07-26
> **Bushido89 said:**
> I've played a little, I know what ports are & why they exist; most I've ever used it for is throwing 80 from hub to 80 on my node to allow incoming connections.

I'll try forwarding those ports for sure, see what happens. Sadly my family for some reason doesn't understand my grim fascination with such matters and is dragging me from my cave.

Thanks a bunch for your help - soon as I throw off the yoke of having my dinner paid for; I'll keep you posted :).

no worries..

haha. call them the fun police and run off! thts wot i'd do... haha. btw if ur router asks are the forwards: tcp, udp or both. pick both. as i'm not sure which ports r what..

---

### Post by Bushido89 on 2011-07-28
> **androssofer said:**
> no worries..

haha. call them the fun police and run off! thts wot i'd do... haha. btw if ur router asks are the forwards: tcp, udp or both. pick both. as i'm not sure which ports r what..

I have set the forwards to the Desktop with Samba set up, unfortunately BoxA still cannot see BoxB and vice versa. Thanks a bunch for the assistance though ^_^, I'll see if I can't find a way to convince Ubuntu that it's fine for 'Everyone' to have Read Only on this drive.

---

### Post by androssofer on 2011-07-28
> **Bushido89 said:**
> I have set the forwards to the Desktop with Samba set up, unfortunately BoxA still cannot see BoxB and vice versa. Thanks a bunch for the assistance though ^_^, I'll see if I can't find a way to convince Ubuntu that it's fine for 'Everyone' to have Read Only on this drive.

install firestarter on your ubuntu box and make sure it can accept incomming connections on those ports aswell...


click [here]("https://help.ubuntu.com/community/Firestarter") for the documentation on it (should you need it)

it might b blocking them and tht cud b y u cant see it..

---

### Post by Bushido89 on 2011-07-31
Thanks a bunch for all the help chum, I've tried FireStarter, but things still seem bleak. I'll find another way to approach the problem.

---

