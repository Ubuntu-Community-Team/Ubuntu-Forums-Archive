---
title: "NFS is just not working HELP!"
date: 2006-09-09
forum: Networking &amp; Wireless
---

### Post by nanbudh on 2006-09-09
i have two dapper machines on a LAN. i have tried to get NFS working for many days now and i am on the verge of giving up. i went through forums and tried everything but...i have a directory 'shareme' on one machine which is to be mounted at 'mounted' in the other machine.here is what i have tried:

1. installed nfs-common and portmapper thru 'sudo apt-P install nfs-common portmapper'. i copied this command from forums somewhere and donot remember it exactly but it gave an ok response and after that sudo /etc/init.d/portmapper restart and /etc/init.d/nfs-common restart worked ok.
2.made changes to /etc/exports file and added this:
   /home/shavin/shareme   192.168.100.21(rw,no_root_squash,async)
3.created a directory /home/shavin/mounted on the other machine.
4.restarted both machines and restarted the portmapper and nfs-common just to make sure.
5.then on the second machine i wrote 'sudo mount 192.168.100.23:/home/shavin/shareme  /home/shavin/mounted'
6. it gives an error saying nfs could not be mounted.

LAN is ok when i try to ping both machines.
What am i missing here?? Please Help. By the way when i use the command rpcinfo it shows a table but in the second column nfs is not mentioned in any row though portmapper is.

Please answer in detail as i am a complete newcomer to linux from windows.

---

### Post by tbonius on 2006-09-09
From your server machine that is exporting the shared filesystem.. type:

showmount -e

What does it return?  The correct directory you wish to share?  Does that directory exist?

From your NFS client machine... type the same thing

showmount -e (IP address of NFS server)

Of course put in the actual IP address of the NFS server.  Can you see the exported filesystem?

Make sure portmap is started on both machines.  Attempt to mount the remote export to a local directory.. and make sure the local directory exists and has the correct permissions for your user account to access it.


sudo mount (IP address of NFS Server):/(export) (local directory)

WHat happens at this point?  Double check your syslog if you get errors.

Also you dont need to specify just one machine (unless you really want to) in your exports file on the NFS server.  You can specify a range of machines to share the export with:

192.168.0.0/255.255.255.0

T

---

### Post by nanbudh on 2006-09-13
i found out what i was doing wrong. on the server i have to install   nfs-kernel-server and not nfs-common. it is working fine now. Thanks for all the help.

---

### Post by tbonius on 2006-09-13
Awesome.. Im glad its working out for you :)

---

