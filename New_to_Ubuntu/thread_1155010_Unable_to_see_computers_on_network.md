---
title: "Unable to see computers on network"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by parkinrg on 2009-05-10
Hi 
I have a desktop PC running Ubuntu 8.04 ,which I successfully networked with a Vista laptop,and was able to share files and a printer.
Today I installed Ubuntu 9.04 on the laptop with WUBI, but I am unable to see the desktop PC from the laptop or vice versa. Both are connected to the same network, and I can access the internet OK from both. There are folders on the desktop that have sharing enabled. Both machines have the same username and password.  Can anyone help , I get the feeling I am missing something very basic

---

### Post by roger_1960 on 2009-05-10
Hi

Not sure if this is the problem but have you installed smbfs or smbclient in the wubi install on the laptop?  Perhaps try it.

---

### Post by parkinrg on 2009-05-10
Thanks for the reply, SMBclient was installed,but not SMBFS  . I have installed this , but I still can not see the either Ubuntu machine from the other one. If I reboot the laptop with Vista , I can share files OK. 
I thought sharing files with 2 Ubunt machines was just a matter of connecting to the network and enabling sharing on the required folders.

---

### Post by Peter09 on 2009-05-10
If you go to Places-> Connect to Server

and setup the Windows Share Option what happens.

---

### Post by roger_1960 on 2009-05-10
Hi

You should be able to see the IP address ( eg 192.168.0.8 ) of each machine by right clicking the network manager icon and selecting connection information.  Then try, in the location entry box in Nautilus, entering 

smb://IPadress/sharename

or smb://machinename/sharename

I find this works where I cant browse the network directly

---

### Post by AClark on 2009-05-10
I have found NFS to be the simplest way to share files between my Ubuntu computers. 

This howto got me started.
[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

To make it as simple as possible I have static IPs on all my machines so after setting up NFS and configuring /etc/exports the command to mount one of the desktops so that I can access it from the laptop looks like this:

sudo mount 192.168.11.12:/home/awc /media/NewHomeOffice

This gives me access to the home folder on the desktop in the /media/NewHomeOffice folder on the laptop

Hope this helps - Good Luck

---

### Post by parkinrg on 2009-05-10
> If you go to Places-> Connect to Server

and setup the Windows Share Option what happens.

I am not sure what the server name should be !

---

### Post by Peter09 on 2009-05-10
You can use its IP address

---

### Post by parkinrg on 2009-05-10
Thanks Peter09
I have tried putting the IP adress of the desktop pc in the servername ,I have also tried its IP address , but the error messsage always  says can not display location.
 am doing something wrong . Where would I find what the server name should be

---

### Post by roger_1960 on 2009-05-10
Hi

Have you tried the

smb://machinename/sharename

method in Nautilus, noting that its case sensitive?  I get the "canot display location" message with Peter09's method (although it should work!)

---

### Post by parkinrg on 2009-05-10
Yes I tried that , not sure that I understand the results. I just get 2 drop down menus "location" and "root" in the Nautilus window,then if I click on the "root" drop down , the name of the share folder is there but I can't do anything with it

---

### Post by roger_1960 on 2009-05-10
Hi again

I can only think that this problem has something to do with using WUBI, but I don't know what!

---

### Post by parkinrg on 2009-05-10
Yes maybe it is to do with WUBI, Perhaps I will try a proper install , dual booting with Vista , or ditch windows all together !!

---

### Post by parkinrg on 2009-05-12
Still struggling with this !
This may be a daft question , but if I am trying to share files between two Ubuntu machines ,Do I need Samba ? or is Samba just for sharing Linux with Windows

I have a workgroup called "workgroup" on both machines ,  I can see this workgroup in --places / network/ windows network from both machines , but when I try to open it from the laptop I get "unbale to mount location" "failed to retrieve share list from server"

---

### Post by AClark on 2009-05-12
Samba is needed to network with Windows.  

You certainly can use Samba to share files between 2 Linux machines but in my opinion if that is what you want to do using Samba introduces an unnecessary level of complexity.

As I said in my prior post I find using NFS to be much simpler and more reliable.

[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

---

### Post by parkinrg on 2009-05-12
Thanks Aclark

I will certainly give it a go. It might take a bit of head scratching due to my lack of knowledge about such basic things as mountpoints etc, but that's how we learn !

---

### Post by AClark on 2009-05-12
A mount point is just a folder that you create on your computer

After you have mounted a drive or a shared folder to that point then the files and/or folders on that drive or folder will be accessible through that folder or "mount point" 

As I said before I find it simpler to use the IP address of the remote machine in the mount command - of course there are other options.

The more things don't go smoothly the more we learn

Have fun

---

### Post by parkinrg on 2009-05-12
Thanks again , even that little bit of knowledge makes it clearer

---

### Post by Miljet on 2009-05-12
Disclaimer: I am by no means an expert so take any advice with a grain of salt.

I have always had problems accessing files on a mounted partition or drive. Here are a few things that I have learned by experimenting.

The mount point is critical. If you make a mount point using sudo, the mount point will belong to "root." Since you can make a mount point anywhere, I created a mount point in my home directory (without using sudo.) That way the mount point belonged to me and I could access, and modify, the files.

Next, I tried creating a mount point using sudo. Then before actually mounting anything there, I used sudo chown to change ownership to myself. That worked also.

One final note. The permissions of a directory must be executable in order to use "cd" to move into that directory.

---

### Post by NHArticleTen on 2009-05-12
Please let us know how you're coming along with this.

---

### Post by parkinrg on 2009-05-14
OK , I am trying to follow AClarks instructions , and I think I am making progress, everything seems to go well untill I try to mount the share using
"sudo mount dad-desktop:/files /files" ( the desktop pc is called dad-desktop)
The terminal tells me "mount point nfs does not exist".   I notice I have an empty folder called "files"  in the root directory of both machines. There is obviously something I am not doing correctly Any ideas ?

---

### Post by AClark on 2009-05-14
I am assuming you have installed: 

1. nfs-kernel-server 
2. nfs-common 
3. portmap

on _Both_ machines.

and that you modified the /etc/exports file on "dad-desktop" .

Could you please post the contents of the /etc/exports file on dad-desktop ?

Just to be clear the purpose of the /etc/exports file is to specify what files to share, who to share them with and what they are allowed to do with them (Read Only, Read Write Etc.)

I have the best luck assigning static IP addresses and using them to specify who is who.  It helps to avoid typos in names and mistakes in case when mounting.

The following line in /etc/exports shares the /home/awc folder with the machine at IP address 192.168.11.11 allowing read/write access to the files in that folder.

/home/awc 192.168.11.11(rw,async)

The following line would allow sharing with all machines on the .11 network
/home/awc 192.168.11.1/24(rw,async)

---

### Post by parkinrg on 2009-05-15
Thanks AClark
I have managed to get it working .The problem was my lack of basic knowledge, but once I stumbled on the right way to do things ,it all became quite clear. Your suggestion of using the IP address was a great help. I havent got it to mount at boot up yet . I will play with that later . I am just pleased to have got a shared folder working 
Thanks again AClark and anyone else who posted replys , they all help.

---

### Post by AClark on 2009-05-15
Glad to hear of your success.  

I never got around to putting the commands in fstab to automount.  Since I don't need the shares all the time I just created a launcher on the desktop and pasted the mount command into it.

When I need access to my share I just double click the launcher.  Did the same for the umount command.

I seem to remember some issue with wireless networking not being established when fstab is executed causing problems with automounting remote folders.

That was back on 7.04 so things may have changed by now.

Or more likely I just didn't know what I was doing :)

---

### Post by toypilot on 2009-05-19
> **parkinrg said:**
> Hi 
I have a desktop PC running Ubuntu 8.04 ,which I successfully networked with a Vista laptop,and was able to share files and a printer.
Today I installed Ubuntu 9.04 on the laptop with WUBI, but I am unable to see the desktop PC from the laptop or vice versa. Both are connected to the same network, and I can access the internet OK from both. There are folders on the desktop that have sharing enabled. Both machines have the same username and password.  Can anyone help , I get the feeling I am missing something very basic

Similar thread: The something simple turned out to be firewall for a few people...

---

