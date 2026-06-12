---
title: "[SOLVED] setting up a Mac/Linux network"
date: 2008-07-21
forum: Networking &amp; Wireless
---

### Post by DarchAengel on 2008-07-21
I have a G4 Mac and my gf has a Linux box in the other room.  What is the best way to 1) connect so that we can access each-other's computer (i.e. send eachother sound/video files, etc) and 2) set it up so that I can print to her computer where the printer is hooked up.  When we were living apart I used to use chicken of the VNC but now that we are in the same apartment on the same router I am hoping there is a simpler more secure solution.

---

### Post by DarchAengel on 2008-07-21
Please guys, I'm at a loss as to how to fix this problem.  I got to the point where I was trying to set up samba and it won't let me add passwords to the users that I make/add.  Any help would be greatly appreciated.  Thank you all in advance.

---

### Post by fmartinez on 2008-07-21
I'm in the same situation. I have a Linux file server and a new/old Powerbook G4. I'm going the route of NFS with MAC. This will mount which ever directory on my server to any location i want. You can set up a "Public" folder on each others computers and mount them respectively. then when she copies files to it, it will show up on your G4 and when you copy to yours it will show on her Linux box...
Still doing some research on how MACs handle NFS, but it's the best option for me. I don't want to do SAMBA just because no i guess. no particular reason for me.

---

### Post by ktrnka on 2008-07-21
If you're trying to share files using samba and samba users, then you need to add your linux users to samba.

```
sudo smbpasswd -a username
``` It will then prompt for a samba password.

---

### Post by ktrnka on 2008-07-21
To set up an NFS server on ubuntu, first install nfs-kernel-server.

```
sudo apt-get install nfs-kernel-server
```

Then add the directory you wish to share in /etc/exports
Something like this:

/home/username/sharedfolder 192.168.1.0/24(rw,sync)

This will share the directory with the entire 192.168.1 network.
Restart the NFS daemon.

```
sudo /etc/init.d/nfs-kernel-server restart
```


Then all you need to do on your Mac is access the Terminal and pick a folder to mount the NFS share.
I don't have a Mac but this should work.

On the Mac:
```
sudo mount IPaddressofNFSserver:/home/username/sharedfolder /private/mnt
```

---

### Post by ktrnka on 2008-07-21
I also found this. It might help mounting NFS shares in Mac OS X.
[http://docs.info.apple.com/article.html?artnum=25344]("http://docs.info.apple.com/article.html?artnum=25344")

---

### Post by DarchAengel on 2008-07-21
Thanks for the Mac link.  I'm about to read it.  But I'm having a little trouble understanding what to do on the linux box.  I installed the NFS kernel.  It said it was already up-to-date.  I'm not sure how to implement what you are talking about with the shared folder line.  I keep getting a bad bash script.

---

### Post by ktrnka on 2008-07-21
You need to add the shared folder.

```
sudo gedit /etc/exports
```

Put this on a new line in the exports file:

/home/username/sharedfolder 192.168.1.0/24(rw,sync)

The first part is the full path of the folder you wish to share. The second part is to share the folder to the entire 192.168.1 network. Replace that with whatever subnet your network is running. If you want to share it only to the mac, you can input its exact ipaddress. eg. 192.168.1.103(rw,sync)
The part in () tell allow the users to read and write to the folder.

---

### Post by DarchAengel on 2008-07-21
Okay I got added the line that you gave me.  I replaced username with the user name on the linuxbox and sharedfolder with the name of the folder that I want to share with the mac.  Everything seems to be okay on that end but still no dice on the Mac end.  I was even able to make my printer visible on my Mac but still no conversation between the two.

---

### Post by ktrnka on 2008-07-21
Ok, first, what is the ipaddress of your mac? Second did you restart the nfs-kernel-server after you added the line into /etc/exports?

```
sudo /etc/init.d/nfs-kernel-server restart
```







"Please ignore my first post if you are trying to go the NFS route."

---

### Post by DarchAengel on 2008-07-21
Shoot, I forgot to restart.  Okay just did that and my internal address of my mac is 192.168.2.4

Still nothing on my mac end.

---

### Post by DarchAengel on 2008-07-21
I gave up on the samba route since I can't make passwords for the users I was defining.

---

### Post by ktrnka on 2008-07-21
Ok then in your /etc/exports file you changed the 192.168.1.0/24 to 192.168.2.0/24 right?

please copy the output from the command below

```
cat /etc/exports
```

---

### Post by DarchAengel on 2008-07-27
Sorry I've been gone for so long.  Internet crashed...  I did what you told me to do and this is what I got.

```

# /etc/exports: the access control list for filesystems which may be exported
#        to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync) hostname2(ro,sync)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt)
# /srv/nfs4/homes  gss/krb5i(rw,sync)
#/home/deedlit/DarchAengel 192.168.1.0/24(rw,sync)
deedlit@Eeyore:~$ 

```
Did I do it all okay?  Did I miss anything?

---

### Post by ktrnka on 2008-07-27
The reason your shares are not working is that the # sign in front makes it a comment. You need to remove the # infront of your share. Then restart nfs-kernel-server.

---

