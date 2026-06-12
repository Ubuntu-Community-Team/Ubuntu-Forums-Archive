---
title: "How do I mount Windows work group"
date: 2008-02-14
forum: Networking &amp; Wireless
---

### Post by toomuchcomputertime on 2008-02-14
I am trying to mount a windows computer to a folder in my home folder (under both user names), and I can't figure out how. Could anyone help me. I have been searching  Google for quite a while, but have not found anything clear enough that worked. Thanks. I will be happy to add specifics.

---

### Post by dca on 2008-02-14
Is this a one way deal where the Windows workstation will be accessing certain information on the Ubuntu box?
 
If this is the case, then Samba needs to be installed on your Ubuntu box.  Currently, if you look in Synaptic Package Manager and search for 'Samba', you'll find that only samba-common and smbclient are installed by default.  This is what allows you (if you wanted) to access a share on a Windows system.  In order for Windows to access your stuff, you need to install the package called 'samba'.  This installs the Samba server for access.  Once installed, the config file is located in /etc/samba/smb.conf
 
You could perform a search for 'samba' on the forums here or click here:
 
[https://help.ubuntu.com/7.10/server/C/windows-networking.html](https://help.ubuntu.com/7.10/server/C/windows-networking.html)
 
for a more definitive explanation.

---

### Post by toomuchcomputertime on 2008-02-14
I am trying to access windows files on the ubuntu. The windows has my files, I just need to use them through the ubuntu. I have linneighborhood, samba, samba-common, smbclient, smbfs, and libsmbclient installed. I can access the network (I am posting from the ubuntu), but I want to mount the windows file system. Thanks

---

### Post by toomuchcomputertime on 2008-02-14
This also helped.
[http://grumpymole.blogspot.com/2006/11/xubuntu-browsing-samba-shares-with.html](http://grumpymole.blogspot.com/2006/11/xubuntu-browsing-samba-shares-with.html)

---

### Post by toomuchcomputertime on 2008-02-15
I have not yet figured out how to make samba mount the network to my folder on reboot. Here is a picture  of some of the errors I am getting, I have worked some out, but these keep reoccurring.

---

### Post by Iowan on 2008-02-15
See if the "automount" link in my signature helps.

---

### Post by toomuchcomputertime on 2008-02-15
Thanks for the link. I read it, and tried to understand it. I have only used Linux for 2 weeks, and not everything makes sense. I have tried to follow the instructions, but I am still having to go through pyNeighborhood to mount the system. If I can clarify, please let me know.

---

### Post by gjhicks on 2008-02-15
Hi,

Had the same problem with use of pyneighborhood.

I think you have a 'permissions' problem.

Solved it by:

1) Create a folder in your home folder, that is where you have full rights.  For example, if your home folder is /home/ubuntu make a folder called /home/folder/lan

2) In pyneighborhood, under the 'preferences - general', enter '/home/folder/lan' in the 'Mount folder:' dialog.

3) Also in pyneigborhood, under the 'preferences - network', enter the name of your windows workgroup.

4) Also in pyneigborhood, under the 'preferences - file managers', add your default file manager.  The pyneighborhood default is MC, which is not included in Xubuntu (which I use).

Then it will hopefully work.

Bye,

Geoff,

---

### Post by toomuchcomputertime on 2008-02-16
Thanks for the reply,
it now it says it can't mount, and in addition, I am trying to make it mount at boot. 

Here are some links I have looked at:
[http://www.swerdna.net.au/linhowtosambacifs.html](http://www.swerdna.net.au/linhowtosambacifs.html)
[http://learn.clemsonlinux.org/wiki/Samba_client](http://learn.clemsonlinux.org/wiki/Samba_client)

Thank you everyone who has tried to help.

---

### Post by toomuchcomputertime on 2008-02-16
During boot, the computer has been telling me to look at /var/log/fsck/checkfs. 

"Log of fsck -C -R -A -a 
Sat Feb 16 13:41:06 2008

fsck 1.40.2 (12-Jul-2007)
fsck.ext3: Unable to resolve 'LABEL=/boot'

fsck.ext3: Unable to resolve 'LABEL=/home'

fsck died with exit status 8

Sat Feb 16 13:41:06 2008"

Would this be relating to my mounting at boot? I can't make sense of this file. Thanks

---

### Post by toomuchcomputertime on 2008-02-16
I have shared folders that say 'smb' on the desktop now, but I can't figure out how to mount them to "home/mnt". I mounted them through places 'Connect to Server',

---

### Post by Iowan on 2008-02-19
I use (or have in the past) that technique to put shared folders on the desktop - it seems to be pretty stable (although it seems to require password the first time/session I access the share.

---

