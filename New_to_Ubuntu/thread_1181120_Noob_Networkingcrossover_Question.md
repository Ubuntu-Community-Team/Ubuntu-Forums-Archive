---
title: "Noob Networking/crossover Question"
date: 2009-06-07
forum: New to Ubuntu
---

### Post by lb4406 on 2009-06-07
Ok I have a laptop running 9.04 and a desktop running 8.10 (as I haven't got round to upgrading it yet)

I also have a network crossover cable and want to link the two machines together to transfer some large files across quicker than using wifi.

I am tearing my hair out!!

I have followed the instructions below which I have found on another thread:

> 

[LIST]
[*]the NIC interface on both machines is called eth0.
[*]Computer A has ip address 192.168.0.1
[*]Computer B has ip address 192.168.0.2
[/LIST]

On Computer A:
     Code:
     /sbin/ifconfig eth0 192.168.0.1 netmask 255.255.255.0 up
/sbin/route add -host 192.168.0.2 eth0 
On Computer B:
     Code:
     /sbin/ifconfig eth0 192.168.0.2 netmask 255.255.255.0 up
/sbin/route add -host 192.168.0.1 eth0 
Now on Computer A you should be able to ping Computer B:
     Code:
     ping 192.168.0.2 
 (And vice versa, B should be able to ping A.)


Note that the ifconfig command assigns the ipaddress 192.168.0.1 to the eth0 interface on Computer A

and that works I can ping the machines. but I still can't view any folders on the other machine, I have right clicked on a folder, clicked sharing and installed the Windows Sharing thingy that comes up automatically when you try to share a file and I still can't see it.

I also tried installing SSH server (I think) which I found on another thread and logged into the other machine using the username an password from that machine and I could view the whole hard disk but then I realised that it was going over my wifi connection to the other machine and not via the crossover cable.

In a nutshell is there a simple guide somewhere that will tell me how to setup a network connection with a crossover cable between two Ubuntu machines and then transfer files between the two ? (because if there is I haven't been able to find it !?!!)

Thanks

---

### Post by Iowan on 2009-06-07
Ubuntu comes with clients for several sharing methodsb-bit can retrieve files from other machines... but to share FROM Ubuntu generally means installing a server of some sort.  Some options include SSH, FTP, NFS, and Samba. 
[https://help.ubuntu.com/community/SSH?action=show&redirect=SSHHowto]("https://help.ubuntu.com/community/SSH?action=show&redirect=SSHHowto") 
[https://help.ubuntu.com/community/SSHFS]("https://help.ubuntu.com/community/SSHFS")
[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/ftp-server.html]("https://help.ubuntu.com/6.06/ubuntu/serverguide/C/ftp-server.html")
[https://help.ubuntu.com/community/SettingUpNFSHowTo]("https://help.ubuntu.com/community/SettingUpNFSHowTo")

---

### Post by superprash2003 on 2009-06-08
NFS is a good option for linux to linux sharing..

---

### Post by Toshubu on 2009-06-08
I have a desktop with Fedora 10 on it; and a laptop with ubuntu 8.04. I use ssh with no problem. If it's not too much trouble, I would disable any wireless interfaces you've got going (temporarily), and I would stay away from the 0 subnet (use 192.168.1, instead). Set up ssh server on the desktop and ssh client on the laptop...(or vice/versa). I'm using a wired router (as a switch) and not a crossover cable...but, that shouldn't make a difference..(if you're sure it's a crossover cable)..

---

### Post by lkraemer on 2009-06-09
Try this:
[http://ubuntuforums.org/showthread.php?t=1031300&page=2](http://ubuntuforums.org/showthread.php?t=1031300&page=2)
Post #15.

lkraemer

---

