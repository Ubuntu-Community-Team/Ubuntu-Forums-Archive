---
title: "NFS - Mount Ok on Client but No files...."
date: 2008-12-03
forum: New to Ubuntu
---

### Post by gyrene2083 on 2008-12-03
Here's my setup and problem;

HTPC (Hardy 8.04 Command Install) 

    (Fstab) /dev/sdb1       /mnt/sdb1       ext3    defaults   0   0
           /mnt/sdb1       /export/Videos   none    bind  0  0

NFS Server (installed)

Mounts ok on the server and I can see the files. But when I try to view the files from my Laptop running Intrepid 8.10, I am able to mount the drive but I can't see any of the files. I'm read somewhere that it's a permissions issue, but I couldn't understand what they were talking about. 

Can someone give me a hand? Also, with what I have on the Fstab would that automatically mount when I boot up the HTPC?

---

### Post by gyrene2083 on 2008-12-04
Any ideas?

---

### Post by Paqman on 2008-12-04
Sorry, i'm a little confused about what you're trying to do. Are you trying to mount a folder from your server on your HTPC using NFS?

All you really need to do is add an entry to /etc/exports in the server, then a single line in /etc/fstab in the host.

---

### Post by gyrene2083 on 2008-12-04
> **Paqman said:**
> Sorry, i'm a little confused about what you're trying to do. Are you trying to mount a folder from your server on your HTPC using NFS?

All you really need to do is add an entry to /etc/exports in the server, then a single line in /etc/fstab in the host.

Yes but let me explain a little better. My HTPC has NFS Server installed and I setup a file called /export/Videos on my HTPC. I want to be able to share that Videos file on my laptop and be able to RW to that directory. Now when I mount that file on to my laptop from the HTPC I can't see any of the directories or files. Also, when I reboot the laptop I lose the mount, and have to manually do it. I'm sure it's a matter of fine tuning the fstab, I appreciate any help you or anyone has to offer.

---

### Post by gyrene2083 on 2008-12-04
Ok, so I have it working now I am able to browse all the directories but transferring files is horrific almost to a point where it freezes up the pc. The files aren't large either. Any ideas?

---

### Post by Paqman on 2008-12-04
> **gyrene2083 said:**
> I'm sure it's a matter of fine tuning the fstab, I appreciate any help you or anyone has to offer.

Sure, what have you got in fstab entry on the laptop?

---

### Post by gyrene2083 on 2008-12-04
This is what I have in the fstab -

```
192.168.1.145:/export/Videos ~/Intermedia nfs rsize=8192,wsize=8192,timeo=14,intr,bg
```

I'm hoping to be able to have it remount and speed up transfers between the client and server. I read somewhere on here that increasing the rsize and wsize could help with that, but being a n00b I don't want to try something that will render my system useless. Thanks for the help.

---

### Post by Jose Catre-Vandis on 2008-12-04
Are you trying to do this wirelessly? If so at what speed? (NFS not always great wirelessly due to type of traffic) What happens when you try to play a video from your HTPC?

---

### Post by gyrene2083 on 2008-12-04
I am doing everything wirelessly. But my HTPC is not streaming video. I am actually just copying video to the HTPC. I have the HTPC with a Geoforce 9400Gt that has an HDMI out, so it's hooked up to my tv. I usually do video transcoding on my laptop and then transfer it to the box via, usb thumb drive. Before I installed Ubuntu I had it working in windows but changed from using the explorer shell, to using xbmc as my shell. I had shares and everything working great, but I didn't want to have to worry about security updates, and antivirus software.

With the Linux command line install I can get it to boot up in about 20 seconds 30 seconds tops.. With windows even replacing the explorer shell, and disabling antivirus, it took way longer to load. 

That being said, I want to learn linux. ;) So, any help would be greatly appreciated.

---

### Post by Jose Catre-Vandis on 2008-12-06
Suggest you start by running through the nfs setup on your htpc first, and checking your nfs setup on your laptop. Be careful with your paths when exporting on the server and listing in fstab, I always write out full paths as opposed to using redirects like "~/" or "$HOME". Make sure your HTPC has a static IP. I use the same line as you have in my fstab, but on a wired network.:

from malco2001's tut:
```
Install NFS Server Support
at the terminal type
sudo apt-get install nfs-kernel-server nfs-common portmap
When configuring portmap do =not= bind loopback. If you do you can either edit /etc/default/portmap by
hand or run:
sudo dpkg-reconfigure portmap
sudo /etc/init.d/portmap restart
Editing /etc/exports
the /etc/exports file is used for creating a share on the NFS server
invoke your favorite text editor or
sudo vi /etc/exports
Here are some quick examples of what you could add to your /etc/exports
For Full Read Write Permissions allowing any computer from 192.168.1.1 through 192.168.1.255
       /files 192.168.1.1/24(rw,no_root_squash,async)
Or for Read Only from a single machine
       /files 192.168.1.2 (ro,async)
save this file and then in a terminal type
/etc/init.d/nfs-kernel-server restart
Also aftter making changes to /etc/exports in a terminal you must type
sudo exportfs -a
Install NFS client support
sudo apt-get install portmap nfs-common
Mounting manually
Example to mount server.mydomain.com:/files to /files. In this example server.mydomain.com is the name
of the server containing the nfs share, and files is the name of the share on the nfs server
The mount point /files must first exist on the client machine.
cd /
sudo mkdir files
to mount the share from a terminal type
sudo mount server.mydomain.com:/files /files
Note you may need to restart above services:
sudo /etc/init.d/portmap restart
sudo /etc/init.d/nfs-common restart
Mounting at boot using /etc/fstab
Invoke the text editor using your favorite editor, or
gksudo gedit /etc/fstab
In this example my /etc/fstab was like this:
        server.mydomain.com:/files /files nfs rsize=8192,wsize=8192,timeo=14,intr
You could copy and paste my line, and change &#8220;servername.mydomain.com:/files&#8221;, and &#8220;/files&#8221; to match
your server name:share name, and the name of the mount point you created.
It is a good idea to test this before a reboot in case a mistake was made.
type
mount /files
in a terminal, and the mount point /files will be mounted from the server.
```

---

