---
title: "Sharing folders should be simpler than this?"
date: 2007-06-04
forum: Networking &amp; Wireless
---

### Post by vertigo1980 on 2007-06-04
hi all, i want to share a folder between 2 computers, both running feisty. let's say there is PC1 and PC2. i want to have a folder on PC2 and for PC1 to have full access to it. 

so i created a folder in /home/user in PC2, right-clicked it, selected sharing. i installed nfs, as prompted, and created an nfs share, with a permission by "hostname" (which is just the "name" of PC1, right?)

i rebooted both PCs, went into PC1, places>network, and it's empty. shouldn't i see the share in there somewhere? what am i doing wrong? both pcs have the "nfs" stuff installed as prompted when trying to share folders

thanks! :)

---

### Post by vertigo1980 on 2007-06-04
anybody?

---

### Post by blitzer on 2007-06-04
This[ Link]("http://ubuntuguide.org/wiki/Ubuntu:Feisty") should provide all the info you need  :D

---

### Post by vertigo1980 on 2007-06-04
thanks, but i've seen thos guides, and all they do is give a bunch of commands, and "assume the network is configured properly". i don't really know what i'm doing, and i need it to be easy enough (with a gui) so that my dad knows how to do it

---

### Post by fdrake on 2007-06-04
i had the same problem when i try to share a folder through unix network. don't know why but in windows network works.

---

### Post by vertigo1980 on 2007-06-05
yeah it works here through samba too, but i'd much rather use nfs.

---

### Post by vertigo1980 on 2007-06-06
nobody knows how to use nfs to share folders between 2 ubuntu boxes? :confused:

---

### Post by vertigo1980 on 2007-06-07
still looking for a solution to this :(

---

### Post by vertigo1980 on 2007-06-08
........

---

### Post by vertigo1980 on 2007-06-09
Sex!

---

### Post by vertigo1980 on 2007-06-10
is it getting better, or do you feel the same

---

### Post by eentonig on 2007-06-10
Ah! Sex!

Let me help you now! :mrgreen:

Did you try to change the export to the IP address in stead of Hostname? If you want to do it by hostname, you'll need a local name resolution in place. Either via static hosts definition r by bind.

I always define my subnet in the exports.

---

### Post by vertigo1980 on 2007-06-10
thanks eentonig, i thought posting "sex" might get someone's attention. :p

i'll gladly try it out, but how do i find out my pc's ip? :)

---

### Post by dmizer on 2007-06-10
ifconfig will show you your ip address.

you didn't want a command line solution.  but unfortunately, the commandline solution is the easiest solution.  just a few lines of code to copy and paste and you'd be up and running.  check the 4th link in my sig if you're willing to make a small commitment of time in the command line.

if you configure your share to be mounted via fstab, your dad will never have to do anything but click on the folder to open the share.

---

### Post by imon9 on 2007-06-10
maybe you both does not connect to the same local domain?
it could be the case!

---

### Post by vertigo1980 on 2007-06-14
i went away for a bit, back now so i'll try again today and let you know how it goes.

thanks everyone! :D

---

### Post by vertigo1980 on 2007-06-14
> ifconfig will show you your ip address.

i get a bunch of categories like eth0, lo, vmnet1, etc. and each of them have several ip addresses. which one should i use?

dmizer, i will try your guide if i can't get it working through the gui. looks easy enough :)

---

### Post by dmizer on 2007-06-14
the vmnet is for your vmware virtual machine, so you can ignore those.  your ip address will be labeled as "inet addr:".  i've highlighted mine in red.
```
eth0      Link encap:Ethernet  HWaddr 00:C0:9F:76:86:1E  
          [COLOR="Red"]inet addr:192.168.0.101[/COLOR]  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2816753 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2594434 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1714537962 (1.5 GiB)  TX bytes:426972195 (407.1 MiB)
          Interrupt:10 Base address:0x800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:108 errors:0 dropped:0 overruns:0 frame:0
          TX packets:108 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8092 (7.9 KiB)  TX bytes:8092 (7.9 KiB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:172.16.37.1  Bcast:172.16.37.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2049 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:192.168.245.1  Bcast:192.168.245.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2049 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

---

### Post by vertigo1980 on 2007-06-14
thanks dmizer,

mine is "10.1.1.6", and i entered it in the folder sharing dialog. still not there when i go into menu/places/network.

my ip is very different from yours and a few others i've seen while searching for a solution, maybe that's the problem?

my setup goes like this: i have a hub, and there is a dsl modem and 2 ubuntu pc's connected to it via ethernet.

the pc that will be the server pc has an ip 10.1.1.2, and the client (my pc) has 10.1.1.6

---

### Post by dmizer on 2007-06-14
nothing wrong with those ip addresses.  it's just built on a different subnet than most, but there's absolutely nothing wrong with that.

do you have firestarter installed on either of  your ubuntu boxes?

---

### Post by vertigo1980 on 2007-06-14
> 
do you have firestarter installed on either of your ubuntu boxes?

no

---

### Post by BLTicklemonster on 2007-06-14
Good luck. I've been messing with Ubuntu for a while now, and pretty much gave up any hope of using windows to browse folders on my ubuntu machine.

Thank God for window's networking, though. I just use the ubuntu machine to get to a shared folder on a windows machine and drop what I want into the folder, then go upstairs to retrieve what I should have been able to get to easily from the windows box in the first place.

Why is networking in ubuntu not simple and straight forward?

You ever notice that when you share a folder, you're never asked specifically if you want to create a user name and password to gain access to the folder? I have yet to see that occur, but by golly, when you share a folder, then go to a windows machine to view it, you're asked for a user name and password. Why in the name of all that's barbecue is this like this? What useful purpose could this possibly serve? Security? Yes, I want to secure my folders from me viewing them!!!! Score one for the security turds!!!! Wheeee!!!! *pant pant pant* (nothing gets me going more than the retarded networking garbage one must deal with when using ubuntu. Yes, I know "edit this: " .  Riiiiight)

Networking in Ubuntu is one thing that needs some real serious attention.

---

### Post by dmizer on 2007-06-15
> **BLTicklemonster said:**
> You ever notice that when you share a folder, you're never asked specifically if you want to create a user name and password to gain access to the folder?

this password prompt is not for access to the folder.  you are being prompted for a password because you haven't added your ubuntu user to the samba user group.  to correct this, you need to add your ubuntu username to the samba group like so:
```
sudo smbpasswd -L -a your_ubuntu_username
sudo smbpasswd -L -e your_ubuntu_username
```

i have zero problem with ubuntu hosting shares out to windows computers.  it was a pain to get working correctly, but no more painful than doing the same thing in windows when i configured file sharing for the first time.

but the OP (if you had read closely) is wanting to share between two linux boxes, not a linux box and a windows box.

---

### Post by dmizer on 2007-06-15
> **vertigo1980 said:**
> no

the only thing i personally have left for you then is to configure it by command line because i have no idea how to make the gui work.  that doesn't mean the gui can't work.  it just means that i don't know how to make it work.

---

### Post by vertigo1980 on 2007-06-15
alright thanks guys, i'll give it a shot soon and let you know how it goes :)

---

### Post by jocheem67 on 2007-06-15
Here's my story, looks quite similar to vertigo's hazzles:

Got two feisty boxes, and wanted my desktop /home shared to my laptop. First I've been searching the forums, the official and community documentation, really not knowing anything 'bout networking.

Both my comps are connected through a wifi connection, separately, via a speedtouch wireless modem. Both working through dhcp, desktop with a atheros restricted driver, the laptop with ndiswrapper....both working fine.

well, first I made sure that the comps see each other's ip. I just pinged them through 'network tools' .....they do see each other. No problem there ( so no probs with firewalling  I assumed.)

Used several howto's to make this /home folder shared, initially with no succes. But to be honest, this is mainly due to the fact that I'm an n00b regarding networking.

Now in the end I've got it running. My method:

On the server-machine; 

installed through synaptic:nfs-common , nfs-kernel-server, portmap.

I used this howto: [http://nfs.sourceforge.net/nfs-howto/](http://nfs.sourceforge.net/nfs-howto/)
It's the official nfs howto. in fact only two chapters are actually  needed; setting up a nfs server, and setting up a nfs client.
It's important to understand the /etx/exports file and to configure this one correctly, some example are given but I'll give you mine:

/home/******    192.1**.1.**(rw,no_root_squash,async) 
This line is to be filled in uncommented at the end of the file and it gotta be the ip of the remote machine ( the client in my case my laptop. You can find your ip on the remote machine in the right upper corner under the network connections icon )

Next ther's editing /etc/hosts.allow and /etc/hosts.deny ... in fact this is merely a matter of some good reading of  the howto and some plain old copying and pasting....examples again are given and i think, easy to follow.

getting your services started, just reboot.

Next ther's the client stuff of nfs. I just followed the same howto:

installed nfs-common and portmap ( the server stuff is not necessary on the client machine )....next, and this is crucial, i made a new folder under /mnt ; /mnt/home ( use alt-f2 --- gksudo nautilus -- go to filesystem and to /mnt and create the /home folder there ). The howto is not very clear on this, only a small note is present.

here's how the howto states it:

With portmap, lockd, and statd running, you should now be able to mount the remote directory from your server just the way you mount a local hard drive, with the mount command. Continuing our example from the previous section, suppose our server above is called master.foo.com,and we want to mount the /home directory on slave1.foo.com. Then, all we have to do, from the root prompt on slave1.foo.com, is type:

# mount master.foo.com:/home /mnt/home

and the directory /home on master will appear as the directory /mnt/home on slave1. (Note that this assumes we have created the directory /mnt/home as an empty mount point beforehand.)

If this does not work, see Section 7, “Troubleshooting”.

You can get unmount the file system by typing:

# umount /mnt/home

So I tried to mount my /home folder which is on the server machine, from the client:

here's the command, it's a bit an intimidating one:

sudo mount 192.1**.1.**:/home/****** /mnt/home

Note that the /mnt/home part makes the client think that the mounted folder is actually a local folder with an entry under /mnt ....

well this works for me now, goping to my filesystem --- /mnt/home, I can actually browse my home folder on the server machine. Ofcourse the sudo mount ip has to be the ip of the server machine....

Then next ther's the option to make an entry in fstab to automatically mount at bootup. But okay , let me first know if this has been of any help????

It sure is my longest post here, hope it's not a totally **(&*($%ône......

cheers.

---

### Post by Sand Lee on 2007-06-15
NFS sharing is supposed to be faster than SMB sharing. To use NFS, you must know the IP address of the PC you are trying to connect to (PC1) and you must have a mock copy of the folder that is being shared (PC2). 

**Step 1. ** Create a directory in PC2 to "hold" the shared files.
.....Example: I created the directory /mnt/vault on PC2 to connect to /vault on PC1 using ```
mkdir /mnt/vault
```

**Step 2. ** Make sure you've specified who can access the NFS-shared files.
.....Example: I allowed every computer on the network to access /vault on PC1 by doing the following: ```
sudo shares-admin
``` , going to the properties of the folder, and at the allowed hosts section clicking add, specifying the network, then adding the ip address of my network (maybe 192.168.2.1 if you have a Belkin) and the subnet mask, entering 255.255.255.0.

**Step 3. ** Mount the NFS-shared folder to the folder in PC2
.....Example: In the terminal of PC2 enter: ```
sudo mount 192.168.2.2:/vault /mnt/vault
```
Where 192.168.2.2 is the ip address of PC1.

**Step 4. ** Automount the NFS share on startup
.....Example: Enter ```
gksudo gedit /etc/fstab
``` in PC2 then add the line you've used for Step 3 +" nfs rsize=8192,wsize=8192,timeo=14,intr", and it should look something like
```
192.168.2.2:/vault /mnt/vault nfs rsize=8192,wsize=8192,timeo=14,intr
```

**Step 5. ** Congratulations you're done! Now sit back, relax, and feel accomplished.

For more information in a terse format, visit: [[COLOR="DeepSkyBlue"]Ubuntu Guide : NFS[/COLOR]]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Mounting_Automatically")

---

### Post by vertigo1980 on 2007-06-15
thanks guys, i've had some success :). i can "see" the share now, but i cannot write to it, even though i added:

```
/home/Shared 10.1.1.4 (rw,no_root_squash,async)
```

to the server's /etc/exports. can't write to it with sudo either.

---

### Post by jocheem67 on 2007-06-16
Are you having the same user and passwords on both machines?

There could be the trap......

---

### Post by Sand Lee on 2007-06-16
it's probably be cause you have the read only option selected on PC1. Go to the properties section of your shared folder and see if "Read Only" is checked off under the allowed hosts section..

---

### Post by Robin T Cox on 2007-06-16
Here's how I set up file sharing on a home network using Zeroconf(Avahi) between a PC using Feisty (7.04) and another PC using Dapper (6.06) which are linked via a Netgear WG834 router. Note that Feisty has Avahi installed by default, whereas Dapper does not. I am running KDE (Kubuntu).

My grateful thanks to the authors whose posts are referenced below. :KS They have shown how easy it is nowadays to set up a simple network, and this was my first.

### Setting up File Sharing on a Local Network using Zeroconf ###

## References:
[http://ubuntuforums.org/showthread.php?t=218630]("http://ubuntuforums.org/showthread.php?t=218630")
[https://help.ubuntu.com/community/HowToZeroconf]("https://help.ubuntu.com/community/HowToZeroconf")
[https://wiki.kubuntu.org/KubuntuZeroconf]("https://wiki.kubuntu.org/KubuntuZeroconf")

SERVER MACHINE (Feisty)

## Set up FTP daemon ##
(Using FTP for file sharing)

Install vsftpd to set up a file server:

> sudo apt-get install vsftpd

Edit vsftpd config file:

> sudo kate /etc/vsftpd.conf

Change or uncomment (remove the #) the follg parameters in the vsftpd.conf file:

	> local_enable=YES
    	write_enable=YES
    	anonymous_enable=NO
    	chroot_local_user=YES

Start vsftpd:

> sudo /etc/init.d/vsftpd restart

Vsftpd will now always start automatically when your computer starts.

## Install zeroconf (avahi)

> sudo apt-get install avahi-daemon avahi-discover avahi-utils libnss-mdns service-discovery-applet mdns-scan

(Yes, I know I don't need all of this on the Feisty machine)

## Install nmap

> sudo apt-get install nmap

## Check for services

> nmap localhost

On my Feisty machine this gives:

> cox@Kubuntu:~$ nmap localhost

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2007-06-16 18:54 BST
Interesting ports on localhost (127.0.0.1):
Not shown: 1694 closed ports
PORT    STATE SERVICE
21/tcp  open  ftp
25/tcp  open  smtp
631/tcp open  ipp

Nmap finished: 1 IP address (1 host up) scanned in 0.338 seconds


Note the port numbers etc.

## Publish services on network

Create /etc/avahi/services/ftp.service:
(copy and insert the following)

> <?xml version="1.0" standalone='no'?>
    <!DOCTYPE service-group SYSTEM "avahi-service.dtd">

    <service-group>
    <name>FTP file sharing</name>
    <service>
    <type>_ftp._tcp</type>
    <port>21</port>
    </service>
    </service-group>

## Turn on avahi-daemon
In /etc/default/avahi-daemon, set:

> AVAHI_DAEMON_START=1


## Restart avahi-daemon
> sudo /etc/init.d/avahi-daemon restart


## Avahi Zeroconf Browser ##
You will find this available in Start/Utilities. It will show you what services are available, and what workstations are on the LAN.

CLIENT MACHINE (Dapper)

## Install zeroconf
> sudo apt-get install avahi-daemon avahi-discover avahi-utils libnss-mdns service-discovery-applet mdns-scan


(I do need all of this on the Dapper machine)

## Turn on avahi-daemon
In /etc/default/avahi-daemon, set:

> AVAHI_DAEMON_START=1

## Restart avahi-daemon
> sudo /etc/init.d/avahi-daemon restart

## Avahi Zeroconf Browser ##
Available in Start/Utilities.

## Clients login to Network ##
Via System Network/Remote Places/Network Services, or via Konqueror entering URL 'zeroconf:/'.

To login to FTP service, enter the username and password of the *server machine*.

---

### Post by dmizer on 2007-06-16
> **vertigo1980 said:**
> thanks guys, i've had some success :). i can "see" the share now, but i cannot write to it, even though i added:

```
/home/Shared 10.1.1.4 (rw,no_root_squash,async)
```

to the server's /etc/exports. can't write to it with sudo either.

the ip address in the /etc/exports line should be the ip address of the machine allowed to view the share, not the ip address of the machine hosting the share.

in this post: [http://ubuntuforums.org/showpost.php?p=2846304&postcount=19](http://ubuntuforums.org/showpost.php?p=2846304&postcount=19) you said your two computer ip addresses were as follows:
the server: 10.1.1.2
the client: 10.2.2.6

so, to configure your server machine to host shares to your client computer, you must have a folder on your server called /home/Shared (make sure that it does indeed have a capital s because linux IS case sensitive).  then, you must configure /etc/exports as follows:
```
/home/Shared 10.1.1.6 (rw,no_root_squash,async)
```
your server setup is now complete.


now, on your client machine (the machine with the 10.1.1.6 ip address), let's make sure you have all the client support installed correctly:
```
sudo aptitude install portmap nfs-common
```
then, you will need to create a place to mount the server.  usually in the /media directory, this way it will appear on your desktop.
```
sudo mkdir /media/server
```
then ... edit fstab as root:
```
sudo gedit /etc/fstab
```
and add this line to the end:
```
10.1.1.2:/home/Shared /media/server nfs rsize=8192,wsize=8192,timeo=14,intr
```
save the file, and close gedit.
type this command to mount the share:
```
sudo mount -a
```
and you should get a folder on your client's desktop, and your client should be able to read and write to that folder.

---

### Post by vertigo1980 on 2007-06-17
guess i'm not the only one whose had troubles with this. thanks for the suggestions everyone, i'll get on it soon :D

---

### Post by DSK on 2007-06-17
I really wanted to be a Linux user.. I have tried many distro's and all the ubuntu versions since 5.10.  I too wanted to setup a server,share files between clients, host FTP, a website, and a game server.

I read that ubuntu and networking is so easy but yet I was unable to get it working.   I broke down and got windows 2003 and my progess and ease of setup far surpassed what Linux has to offer IMHO.  After all what is wrong if with having a server with a GUI for a noob.  Why cant I have a Ubuntu ISO that is like Windows 2003 (A gui and a graphical interface for each progarm)?

I still plan to conquer this Linux mountain some day but for now to get things up and running I have reverted back to windows. :(

---

### Post by Sand Lee on 2007-06-17
well it is possible to do it graphically with samba, however this method using NFS requires terminal usage. Through networking with windows and ubuntu, i've personally found ubuntu to be way easier.

---

### Post by dmizer on 2007-06-17
> **DSK said:**
>  After all what is wrong if with having a server with a GUI for a noob.  Why cant I have a Ubuntu ISO that is like Windows 2003 (A gui and a graphical interface for each progarm)?

well, first of all ... as a windows noob, did you try to set up a dedicated ftp or file sharing server?  was one of the first things you did in windows to try to set up an IIS server?  how many years had you honestly used windows before you even considered attempting such tasks?

second, having a gui interface for a server is a waste of cpu cycles and memory.  the command line is more powerful and more useful for dedicated server deployment.

finally, next time install webmin: [http://www.webmin.com/](http://www.webmin.com/) for a graphical web interface to your dedicated linux server.

---

### Post by DSK on 2007-06-19
Sry I did not want to flame.  I do love Ubuntu and hope to be a  full Linux user in the future.  Was the first time I ever used IIS and I setup an FTP with it in no time at all.

With my Ubuntu server experience  tried using samba and could not get webmin to install properly, even tried to use zpanel and a few others.

For me to run a server at home with an FTP,local file sharing,  website and TeamSpeak on it I have no worries about clock cycle do to a GUI.  afer all for someone like me it would be great to have a gui at install then the option to remove it after setup is done.  much easier than trying to figure out how to the gui on my own.

I plan on setting up Ubuntu server on a different box after I am done setting up my windows server.  I am sure at that time I will realize how much better ubuntu is.  after all $500 for M$ server is not something I enjoy for my at home use.  I even considered talking that money and spending it to have have someone teach me ubuntu server but then again that would defeat the purpose of me using ubuntu.

---

### Post by vertigo1980 on 2007-06-20
ok guys it seems to be working now. thanks for all your help! :D

though as the title says, it really should be simpler than this. here's hopes for gutsy ;)

---

