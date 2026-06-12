---
title: "You need permission to perform that action, Samba"
date: 2008-09-03
forum: Networking &amp; Wireless
---

### Post by trashjunkid on 2008-09-03
Hello all-

I was torn between posting this in the absolute beginners forum and the networking & wireless forum.

I am using heron 8.04 and the latest samba. I have two external usb hard drives mounted in a shared /home/samba/.

One drive works perfectly, with read and write permissions (and liberty and justice) for all. The other drive, no matter how I configure it, will only allow read access. Under a windows connection, I get a "you need permissions to perform that action" error and a similar complaint using a linux connection.

I've tried sudo chmod 0777 /home/samba/troublesome_mounted_drive with it mounted, unmounted, samba started and stopped. That does not work. If the drive is mounted it shows no change and if it is not the permissions revert as soon as it is mounted.

I've skimmed the samba documents and a bunch of forum postings and most all of it is above my head. It seems the problems have something to do with certain dos attributes or dosattribs set on some of the files on the drive that linux treats in a special and difficult to override manner.

This is the command being offered up as a possible solution:
sudo chown -R username /media/disk

which would be used on the /home/samba/troublesome_mounted_drive directory in my case.

I don't understand what that will do and if it will work with the various user connections I've setup. 

My samba is setup in accordance with the instructions set out here:
[HOWTO: Setup Samba peer-to-peer with Windows]("http://ubuntuforums.org/showthread.php?t=202605")

So what is a basic explanation of how that command might or might not help with and if anyone has better insight into the permissions issue I am having, I would welcome it. And sorry for the dumb questions.

Thanks in advance,

Trashjunkid

---

### Post by trashjunkid on 2008-09-03
Arrgh.

Well I tried the chown command and got a lot of "operation not permitted" errors.

The drive that's not working is fat32, so after a while I tried "sudo mount -o umask 0777 /dev/sdc1/ /home/samba/troublsome_mouted_drive/"

That removed almost all permissions. Then I tried ""sudo mount -o umask 0000 /dev/sdc1/ /home/samba/troublsome_mouted_drive/" and that gave all the permissions I was looking for.

I restarted the computer and now.... that samba share has disappeared when logging on from the windows machine. I haven't tested the linux machine yet.

I umounted and mounted again without the umask option, stopped and restarted samba-- no joy.

arrgh. Any ideas?

-Trashjunkid

---

### Post by trashjunkid on 2008-09-03
I tried the previously working linux machine connection and it is busted too. I am now considering reinstalling samba and starting over.

-Trashjunkid

---

### Post by Iowan on 2008-09-03
IIRC, **umount** works almost backwards to what you'd expect - for full permissions, you'd want a 000 mask. ( Oops - guess you tried that.)
BTW, check [this]("http://www.ubuntuforums.org/showthread.php?t=288534") thread for CIFS mounting information.

---

### Post by trashjunkid on 2008-09-04
Iowan-

I did have some difficulty with the umask all permissions being 0000, but I got it in the end.

I attempted to reinstall the samba package through the synaptic package manager, and also tried mark for complete removal, restart the computer, install again.

I came across a thread suggesting that I delete the /etc/samba folder and it's contents ```
sudo rm -fr etc/samba
``` and then reinstall. When reinstall I get an error message (fails, returns 1).  I tried to uninstall re-install a few times, with the same result. I then remade the deleted directory: ```
sudo mkdir /etc/samba
``` and tried to reinstall. Same error.

Again, in the end, I am unable to connect or see the server.

I dread saying so, but I believe I am going to reinstall ubuntu and start over. That's drastic, but it seems to be the only sure fix. I keep trying new fixes and breaking things more.

Before I do that, any last words of experimentation?

-Trashjunkid

---

### Post by trashjunkid on 2008-09-04
It's working!

Can someone who has a working/ relatively unmodified samba install on ubuntu tell me the contents of the folder /etc/samba ?

I know smb.conf is there, but what else did I delete and will I miss it?

I probably should have copied or renamed the folder rather than delete it....

-Trashjunkid

---

### Post by Iowan on 2008-09-04
My /etc/samba folder has :dhcp.conf  gdbcommands  smb.conf 
I'm not sure that dhcp.conf belongs there.

---

### Post by trashjunkid on 2008-09-06
Iowan-

Thanks. Now I have to figure out what the dhcp.conf and gdbcommands files did and how to get them back if needed. If anyone knows those answers I'd be grateful to hear from them.

-Trashjunkid

---

### Post by Iowan on 2008-09-08
This is a Gutsy Ubuntu box, my Hardy Xubuntu box has the same files. **dhcp.conf**has filesize 0, **gdbcommands** has filesize 8.  Difference in ownership: both files owned by root,root on Gutsy box, **dhcp.conf** owned by root,dhcp on Hardy Xubuntu. **gdbcommands** also root,root on Xubuntu.

I could post whichever you'd like - you'd need to change suffix (and maybe permissions - all are [-rw-r--r--])

---

