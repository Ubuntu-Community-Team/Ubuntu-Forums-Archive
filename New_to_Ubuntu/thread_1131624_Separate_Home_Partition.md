---
title: "Separate Home Partition"
date: 2009-04-21
forum: New to Ubuntu
---

### Post by Sup3r3g0 on 2009-04-21
I followed the psychocats guide [here]("http://www.psychocats.net/ubuntu/separatehome") to create a separate partition for my home folder. So I now have partition for the OS and another for my home folder. I reinstalled 8.10 on the OS partition. What I would like to know is how I can use the separate home partition again. I also want to know if when I copied the home folder according to the guide if the programs were copied too. I only really want my documents and videos, not all the programs I installed.

Sorry if I suck at explaining. Let me know if you need me to elaborate

---

### Post by surfed on 2009-04-21
edit your /etc/fstab to contain a line like this:

UUID=319838morenumbersandletters /home ext3 relatime 0 2

or

/dev/sdxx /home ext3 relatime 0 2


now you can replace UUID with the UUID of your home partition or its /dev/ name, i.e. /dev/sdb1
This will mount your old home partition to /home

make sure the username is the same, so you get /home/username

reboot

---

### Post by pbpersson on 2009-04-21
The Home partition will not contain your application programs, it will contain the preferences relating to each user on your system.

For instance, say you have an email application installed on your system.

When Harry, Sally, Fred, and Jane logon to the system, they all run the email package but each of them only sees their email.  Also, the desktop appears with the colors they chose, with the shortcuts they placed there....

Those are the types of things that go into the home folder, along with the documents, music, movies, etc. for each user.

---

### Post by presence1960 on 2009-04-21
> **Sup3r3g0 said:**
> I followed the psychocats guide [here]("http://www.psychocats.net/ubuntu/separatehome") to create a separate partition for my home folder. So I now have partition for the OS and another for my home folder. I reinstalled 8.10 on the OS partition. What I would like to know is how I can use the separate home partition again. I also want to know if when I copied the home folder according to the guide if the programs were copied too. I only really want my documents and videos, not all the programs I installed.

Sorry if I suck at explaining. Let me know if you need me to elaborate

For future reference when you install again you can mark your home partition mount point as /home in the partitioner. Highlight the /home partition and choose edit. Then set the mount point. Just make sure you don't mark it to be formatted. Then your /home will mount automatically.

---

### Post by 73ckn797 on 2009-04-21
If you are only interested in having your documents standing alone there is an easy way to accomplish this.

Read the last post in this thread: [http://ubuntuforums.org/showthread.php?t=1123750](http://ubuntuforums.org/showthread.php?t=1123750)

You can also designate other directories to have different locations there also.

---

### Post by Gen2ly on 2009-04-21
The guide recommends changing ownership of everything in the new home partition to match the user and group id's of the new user:

```
chown -R username:username /home/username
```

"username:username" is errorneous, and should be "username:usergroup".  Because Ubuntu at this time uses the same name for both use and group this does work.  Unfortunately this command changes ownership of everything and occasionally not all files and folders will have "username:usergroup".  A better way to do this is to find the user and group id's:

```
cd /home/username
ls -la
```

Then change the old user and group id's to the new one:

```
find . -type d -uid 1000 -gid 101 -exec chown username:usergroup {} +
find . -type f -uid 1000 -gid 101 -exec chown username:usergroup {} +
```

The 1000 and 100 id's are the ones on my Arch system.

Once the home partition is setup it can be used when installing other distros or if you have to reinstall Ubuntu.  Some installers allow you to choose a uid and gid (it would be a good idea to choose a higher idea to avoid conflicts) but many don't but this can be done from the command line, but, that, is for another day.

---

### Post by Sup3r3g0 on 2009-04-21
Thanks everyone. It works now. I reinstalled and mounted the partition as my home folder. I still get a DMC error. Do I have to do the chown -R?

---

### Post by presence1960 on 2009-04-22
> **Sup3r3g0 said:**
> Thanks everyone. It works now. I reinstalled and mounted the partition as my home folder. I still get a DMC error. Do I have to do the chown -R?

you can change ownership thru terminal or gksu nautilus in terminal. In your home directory show hidden files, right ckick on .dmrc and choose properties. Reset permissions in the permissions tab.

---

