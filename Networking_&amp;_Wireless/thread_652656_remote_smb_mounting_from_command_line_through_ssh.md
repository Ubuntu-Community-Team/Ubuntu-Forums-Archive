---
title: "remote smb mounting from command line through ssh"
date: 2007-12-29
forum: Networking &amp; Wireless
---

### Post by macmichael01 on 2007-12-29
hello, 
I have 2 boxes at my house one with vista and the other with ubuntu. I have logged into my ubuntu machine via ssh and was wondering if there is a command to mount a share to my ubuntu machine from my vista machine.  I need to grab a file from my vista machine and this was the best solution that I have come up with to do so ( at a distant location at the moment). Also this maybe pose as a pain in the butt, but one of my mounts on my vista machine is named Chris's Shares. Is there a special way that I need to type this out when I mount as well?

Thanks in advance.

---

### Post by kevdog on 2007-12-29
If you can use ssh, why dont you just use scp?

---

### Post by macmichael01 on 2007-12-29
because as I mentioned my file is on my vista machine and I am trying to mount a share from my vista to my ubuntu machine. Once I have my share mounted then I can do the scp from my ubuntu machine or better yet sftp. But I need to know the command to mount via the command line.

---

### Post by macmichael01 on 2007-12-29
Does anyone have a solution to what I am asking?????

---

### Post by kevdog on 2007-12-29
Im not really trying to be a jerk, but I guess I still dont really know what you are asking for

Vista <------>  Ubuntu

Ok that is your configuration on two computers.

You can either use samba to mount shares, or simply run ssh daemons (cygwin on Vista since this bring unix functionality) on both machines and use scp (which uses ssh) to complete the file transfers.

I dont see why you would need to mount the share (like samba) and then use scp (ssh) to complete the transfer.  I suppose you could do this, however with scp you would still need an ssh daemon installed on the server machine.

---

### Post by macmichael01 on 2008-01-02
Ok so I am NOT at my 2 computers and so I am trying to do this remotely.  cygwin would not be an option for vista at this time since I am not at my computer to install that. If it were installed then I could log directly into my vista box and grab my file.  My vista box DOES NOT have any remote services enable nor are there any types of servers running on it except for a shared folder that can only be accessed ONLY by a local network. Since I have no way of accessing my vista box remotely, I need to log into my ubuntu box which DOES have remote services installed (which in my case SSH). so I login to my ubuntu box via ssh and once I do that I need to mount my drive from the command. Once I have done that, then I can CP the file to a location onto my ubuntu box and from there SCP to my laptop. Just to re-iterate there is NO option to work remotely with my vista box but I CAN work remotely with my ubuntu box which can communicate with my vista a box via local network shares.

So basically I need the mount command to mount a vista share to a ubuntu box via the command line.

---

