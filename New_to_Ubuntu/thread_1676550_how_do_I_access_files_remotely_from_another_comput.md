---
title: "how do I access files remotely from another computer?"
date: 2011-01-27
forum: New to Ubuntu
---

### Post by nick24 on 2011-01-27
Hi :P 
I am running Ubuntu 10.10 as a guest through VirtualBox on Windows 7 machine. I have almost all my music and other files on my Windows machine, and I was wondering if I can access those files from my Ubuntu machine. What are the various available ways to do that? Any help is of course like always, greatly appreciated.

---

### Post by bioterror on 2011-01-27
Using LAN you should
> sudo apt-get install samba
[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/configuring-samba.html]("https://help.ubuntu.com/6.06/ubuntu/serverguide/C/configuring-samba.html")

From WAN I suggest to use WINSCP or what ever sftp based client which uses sshd for getting in your computer.

---

### Post by tdapower on 2011-01-27
You have to create a network share in ubuntu. so it can be accessed from windows. otherwise you can browse windows files from ubuntu easily. You just need to make the ip address of ubuntu to same range as windows machine.

---

### Post by nick24 on 2011-01-27
thanks for the reply folks. Since I am running it virtually I can't access my windows files by simply going to file system and browse thru. Bioterror I am reading about samba and see what I can do with that. Ideally I want the server in Wondowws and the client in Ubuntu so I can remotely log in and be able to access/transfer the files from there. I don't even know if that's possible. I will keep reading. Thanks again

---

### Post by JKyleOKC on 2011-01-27
My VBox host system is Xubuntu and my guest VMs are Windows, just the reverse of your installation, so these suggestions may not apply to your problem. However:

If you have at the bottom of the VBox "frame" around the guest display a number of icons for HDD, CD, USB, network, and one that looks like a file folder, click that file folder icon which should lead you to a dialog for dealing with "shared folders."

If that works, click the "+" button in that dialog window and select "other" in order to open a browser dialog that will let you select which folder(s) on your host system you want to share with the guest. You can select only one at a time but can repeat as often as you like to share more folders, and when you share a folder, all of its sub-folders will come along with it.

This makes the folders available for sharing but does NOT automatically mount them. In my Windows guests I have to go to "My Network Places" and create connections for each of them. I don't know what you will need to do but I would start with the Gigolo program and tell it to connect as "Windows shares."

You don't need to install Samba in order to access the Windows folders from Linux, only if you want to go the other way. The default installations of Ubuntu install enough of the Samba package to allow reading from Windows boxes. Neither is it necessary to set up network sharing (although it will work). The whole purpose of VBox's "shared folders" capability is to do what you want!

---

### Post by bodhi.zazen on 2011-01-27
Either use the "shared folders" feature built into VBox (read the user manual to set it up ;) ) or samba.

[http://blogs.sun.com/tao/entry/virtual_box_shared_folder_between](http://blogs.sun.com/tao/entry/virtual_box_shared_folder_between)

---

### Post by nick24 on 2011-01-28
Thank you JkyleOKC. You pretty much nailed what I am trying to do. I will give it a shot.

---

### Post by nick24 on 2011-01-28
> **bodhi.zazen said:**
> Either use the "shared folders" feature built into VBox (read the user manual to set it up ;) ) or samba.

[http://blogs.sun.com/tao/entry/virtual_box_shared_folder_between](http://blogs.sun.com/tao/entry/virtual_box_shared_folder_between)


Thanks for the link.

---

