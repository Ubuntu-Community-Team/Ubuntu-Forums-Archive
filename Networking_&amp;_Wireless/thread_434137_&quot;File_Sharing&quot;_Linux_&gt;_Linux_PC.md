---
title: "&quot;File Sharing&quot; Linux &gt; Linux PC"
date: 2007-05-05
forum: Networking &amp; Wireless
---

### Post by GuiGuy on 2007-05-05
There are five PCs on my home network, three are Linux and two are Windows XPs.

I have no difficulties sharing WinXP <> Linux 

However, I can't get my head around what I need to do to share files, printers etc between Linux <> Linux.

Is there are simple step by step guide somewhere?

Thanks

---

### Post by chriscando on 2007-05-05
I think the easiest way is through ssh
you can install openssh by:
apt-get install openssh-server

Once thats installed you can use the command line to copy files back and forth by:
scp file-on-local-machine user@remoteip:/home/path...
or visa versa:
scp user@remoteip:/home/path file-on-local-machine

You can use a gui too if you dont like command line, konqueror is really good, you can connect to the remote machine by entering 'sftp://user@machine' in the address bar

Many options with ssh

---

### Post by jeffreyldavidson on 2007-05-05
I have been wrestling with the same issue. I have to Fiesty laptops I want to share files with. It seems to be easier to connect with a Windoze box than another Linux box. That does not make sense.

---

### Post by toorima on 2007-05-05
samba if there are windows machines on the network, nfs if the network is linux only, but personally I just use ssh like chriscando said, ssh://username@machine works fine in nautilus as well, or you can install sshfs and then you can mount over ssh.

---

### Post by GuiGuy on 2007-05-06
> **chriscando said:**
> I think the easiest way is through ssh
you can install openssh by:
apt-get install openssh-server<SNIP>

Many options with ssh

Great- Easy as. Many thanks

---

### Post by GuiGuy on 2007-05-06
> **toorima said:**
> samba if there are windows machines on the network, nfs if the network is linux only, but personally I just use ssh like chriscando said, ssh://username@machine works fine in nautilus as well, or you can install sshfs and then you can mount over ssh.

Thanks. ssh did the trick. 

regards

---

### Post by shane2peru on 2007-05-08
What kind of security risk does this present if any?  Does it leave your computer open, or are you required to enter passwords etc before actually writing to the other computer?  Thanks.

Shane

---

### Post by emp1953 on 2007-11-26
> **chriscando said:**
> I think the easiest way is through ssh
you can install openssh by:
apt-get install openssh-server

Once thats installed you can use the command line to copy files back and forth by:
scp file-on-local-machine user@remoteip:/home/path...
or visa versa:
scp user@remoteip:/home/path file-on-local-machine

You can use a gui too if you dont like command line, konqueror is really good, you can connect to the remote machine by entering 'sftp://user@machine' in the address bar

Many options with ssh


I have a unix box running red hat linux.  It will be running a Java application that was developed on a windows machine.
That Java application "communicates" with a proprietary VB script application on a windows based pc.
The VB script application does not support sockets.
While the Java was running on the windows machine, The two computers shared a drive, the Java application watched for a new file to appear, written by the VB script app on the other pc.  It used the exchange of files, on a shared drive, to accomplish data communications.

My only option for interplatform communications here is a shared directory.  Can this be done?
If the solution is ssh, can the command line functions be written into a program so that all is handled automatically with no user intervention?

Thanks

emp1953

---

