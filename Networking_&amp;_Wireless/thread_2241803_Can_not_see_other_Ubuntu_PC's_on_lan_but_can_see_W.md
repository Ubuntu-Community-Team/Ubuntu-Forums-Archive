---
title: "Can not see other Ubuntu PC's on lan but can see Windows PC'c"
date: 2014-08-28
forum: Networking &amp; Wireless
---

### Post by Martin_McGlensey on 2014-08-28
Running a clean install on Ubuntu 14.04 LTS. Have this pc, one running 12.04 LTS and several Windows (8.1) and devices on a modem/router LAN. On both Ubuntu PC's I do not see them displayed on the network panel. They do not appear on the Windows network as well. I have been able to connect to the windows machine from 12.04 by selecting "Network" and opening the proper pc/drive. My internet connection is working properly.

Now I want to connect from one Linux pc to the other Linux pc to move files. I cannot connect to them because they are not listed. I'd like to see all pc's on the LAN displayed when I look at the network and be able to connect to them from the network option in the file manager. What am I missing

OBTW I'm not a Linux guru so please keep it to simple steps and include all steps. Thanks. All replies are appreciated!

Marty

---

### Post by TheFu on 2014-08-28
You need to setup DNS or manage the IP to hostname table some other way - /etc/hosts is common.  It is customary to do this with static IPs.  It may be easier to do it with your router in control using "DHCP Reservations" - [http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management](http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management) tries to explain.

I use a centrally managed /etc/hosts file and push any updates out to all the linux systems with Ansible.

---

### Post by Martin_McGlensey on 2014-08-28
My /etc/hosts file shows only 127.0.1 Local Host. Added the ip address of the other pc to hosts file. Restarted PC. Clicked on network in the files menu and see only Windows network. I did not see a MAC address in the hosts file only an ip for the local host. both PC's can see the internet but not each other. The secont method is way above my pay grade. I do not know where those options are located on the modem.


Got  to be a simpler way.

Marty

---

### Post by bab1 on 2014-08-28
> **Martin_McGlensey said:**
> My /etc/hosts file shows only 127.0.1 Local Host. Added the ip address of the other pc to hosts file. Restarted PC. Clicked on network in the files menu and see only Windows network. I did not see a MAC address in the hosts file only an ip for the local host. both PC's can see the internet but not each other. The secont method is way above my pay grade. I do not know where those options are located on the modem.


Got  to be a simpler way.

Marty
DNS does not allow you to "browse" for available hosts on the LAN.  Only Windows file sharing and Samba allow for that.  If you can't see the Windows machines then you have to turn on NETBIOS over TCP on those hosts.  If you want to see the Linux hosts you need to install and configure Samba server.

On the other hand you don't really need to "see" the other machines to access the files.  If you install OpenSSH server on your Linux machines you can access them via sFTP.  You can also access the Linux machines using sFTP from the Windows machines via [WIN-scp]("http://winscp.net/eng/index.php").   You must know the IP address or have some form of DNS name resolution to locate them by hostname (i.e. /etc/hosts or DNS server).

---

### Post by Martin_McGlensey on 2014-08-30
For give my ignorance. Are we talking about the same samba that allows connection to a Windows printer? I have done that and it works.  Looked at the samba site. Think I need both server and client on each Linux pc. Am  I correct?  Could you post an example samba server config file?

Thanks,
Marty

---

### Post by TheFu on 2014-08-30
> **Martin_McGlensey said:**
> For give my ignorance. Are we talking about the same samba that allows connection to a Windows printer? I have done that and it works.  Looked at the samba site. Think I need both server and client on each Linux pc. Am  I correct?  Could you post an example samba server config file?

Thanks,
Marty

I've never heard of samba connecting to printers.
I have heard of Windows machines using Samba to automatically load printer drivers for Linux-connected printers, however.

The easy way (if a GUI is installed): [http://www.howtogeek.com/74459/how-to-create-samba-windows-shares-in-linux-the-easy-way/](http://www.howtogeek.com/74459/how-to-create-samba-windows-shares-in-linux-the-easy-way/)

The harder way (perhaps not really harder): [http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/)

There are far too many options to get into them here.  Samba-server is for sharing linux storage with Windows systems.  There are many, many, many, many examples in these forums if you need more help.  At least 10 in the last month alone.

---

### Post by Martin_McGlensey on 2014-08-30
Maybe I have not explained the problem clearly. I want to share between the Linux pc's not Linux to Windows. The way my system is setup now I can share with the Windows system using the file manager on the Linux pc. I just go to network, select the Windows pc and follow the prompts to connect. Then I can move files between the Windows PC and the Linux PC. Now if I want to move a file between Linux PC's I first move it to the Windows PC. Then from the Windows PC to the target Linux PC. I connect from the target Linux pc to the Windows PC then move the file.

Thanks for bearing with me. 

Marty

---

### Post by TheFu on 2014-08-30
Why mention windows at all?

For linux to linux file sharing, the best answer is to use NFS.
NFS - Network File System.
With nfs, you mount the storage after "exporting" it from the storage server. On the client machine, it appears like any local disk - users, groups, full file permissions all work as expected.  It is also very fast.  NFS has many different features based on the requirements and those are addressed by both the server half options and the client half mounting options.  If using non-wired ethernet, NFS may not be the best choice. It uses lazy writes and buffers. If a remote mount goes away (reboot) - the client machine may lock up until the storage is back. There are options to get around this, but they have trade-offs.  3 of my systems are NFS servers to the other 20 systems here.  So - you can mount NFS storage in /etc/fstab or through autofs.  I always use autofs - find it more convenient.

So - all of this applies when there isn't ANY Windows involved.  Windows does have NFS clients and NFS servers, but doing the userid/groupid mapping and the general lack of security on most non-Server Windows systems makes this a less-than-great idea - most of the time.

Anyway - google (nfs ubuntu) found these instructions: [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

