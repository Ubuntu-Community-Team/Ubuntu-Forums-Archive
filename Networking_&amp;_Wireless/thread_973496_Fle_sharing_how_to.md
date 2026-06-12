---
title: "Fle sharing how to"
date: 2008-11-06
forum: Networking &amp; Wireless
---

### Post by TMC on 2008-11-06
I've just purchased an Iomega network drive and would like someone to point me to a good, simple (I've never done anything like this before) how-to to get it connected to my Hardy Heron box.

I guess it's to do with Samba, but every Samba how-to I've found seems to be focussed on getting your Linux box seen by Windows, rather than the other way round.

Many thanks, in advance,

David Shaw

---

### Post by froy02 on 2008-11-07
Here's how I setup my NAS from Hardy heron (it's a D-link but I assume that the following would work just as well with Iomega).  

Assuming you have installed samba.

1. Find out the names of your drives in Ubuntu by navigating Places then Network.  Your NAS server name would appear.  Let's assume the name of your NAS is Iomega-xxxx.  Double-click on it and it would show the names of the drives.  Let's assume the name of the drives are disk_1 and disk_2.
2. Before you can use them, they need to "mounted" to a directory in Ubuntu.
3. Let's assume you want them to be mounted so that they would appear on your desktop in with names NetDrive_1 and and NetDrive_2.
4. Let's create 2 directories. Open a terminal and enter the following code:
	sudo mkdir /media/NetDrive_1
	sudo mkdir /media/NetDrive_2
	
5. Now we mount the drives to this directories.  You need your username and password to as NAS user.
	sudo mount -t smbfs -o username=yourUsername,password=yourPassword //Iomega-xxxx/disk_1 /media/NetDrive_1
	sudo mount -t smbfs -o username=yourUsername,password=yourPassword //Iomega-xxxx/disk_2 /media/NetDrive_2

6. You should get drive icons on your desktop with names NetDrive_1 and Netdrive_2.
7. You may need to unmount them before shutting down Ubuntu or it would lock up during shut down.
8. To unmount them:
	sudo umount /Iomega-xxxx/NetDrive_1
	sudo umount /Iomega-xxxx/NetDrive_2
Now whenever you want to access them follow step 5.
Or you could mount them when Ubuntu start by by putting editing your /etc/fstab file (another story).
Or you could put the lines in step 5 in a bash script and just run the script when you want to mount them as well as the unmount commands.

Also you could probably access the setup of your NAS from firefox by using the address [http://Iomega-xxxx](http://Iomega-xxxx)

---

### Post by dmizer on 2008-11-07
SMBFS is no longer included in Ubuntu (since Hardy). Please see the second link in my signature.

If your Iomega supports FTP, you might be better off using the 5th link instead.

---

### Post by TMC on 2008-11-10
Thanks for the help, guys, but no joy, I'm afraid  :-(

@froy02 - If I navigate to Places > Network as per step 1, the only entries I see are for PUBLIC and Windows Network, the NAS server is not listed

@dmizer - I've followed the instructions given in your first link, with no errors being given and nothing seems to have happened  :-(

Ideas?

David

---

### Post by dmizer on 2008-11-10
> **TMC said:**
> @dmizer - I've followed the instructions given in your first link, with no errors being given and nothing seems to have happened  :-(

What line did you put in your /etc/fstab?

---

### Post by TMC on 2008-11-11
> **dmizer said:**
> What line did you put in your /etc/fstab?

I didn't.  I'm guessing here that udev doesn't pick up network drives, then?

(As you've probably guessed, I know *just* enough about all this to be dangerous.  Hopefully, I'm also just about smart enough to have asked before doing any damage  :-)  )

David

---

### Post by dmizer on 2008-11-11
Actually, perhaps we've errored then.

If you followed the first link, that is a howto for getting Windows computers to see your Ubuntu computer. If you want to connect to Windows shares from Ubuntu, you need to take a look at the 2nd link in my sig regarding CIFS.

There are a lot of problems with browsing Windows shares. There are a variety of solutions. I've found the best to be simply mounting them via /etc/fstab.

---

### Post by TMC on 2008-11-11
> If you followed the first link, that is a howto for getting Windows computers to see your Ubuntu computer. If you want to connect to Windows shares from Ubuntu, you need to take a look at the 2nd link in my sig regarding CIFS.

Ah!  Many thanks - I can now access the drive.  Well, the public share, at least.  Now I just need to work out how to set up a private 'share' and I'm home and dry  :-)

Many, many thanks for your help and patience,

Davi

---

