---
title: "Terminal-am I the root?"
date: 2010-03-08
forum: New to Ubuntu
---

### Post by MisFitt on 2010-03-08
Hi,
I'm trying to install cinepaint and,well,this is what the terminal says:

computer@computer-desktop:~$ aptitude install CinePaint
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
computer@computer-desktop:~$ 

Now I've had a look in users groups and am needing assistance so I don't stuff anything up.Solid knowledge needed here!
Thanks

---

### Post by inobe on 2010-03-08
```
sudo apt-get install whatever
```

or

```
sudo aptitude install whatever
```

be sure synaptic is closed when using terminal.

---

### Post by waspbr on 2010-03-08
the "sudo"code in front of a command is going to enable root rights

---

### Post by Don1500 on 2010-03-08
> **MisFitt said:**
> Hi,

E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?


No, you're a user.
instead of this: ```
computer@computer-desktop:~$ aptitude install CinePaint
```

type this:
```
computer@computer-desktop:~$ sudo aptitude install CinePaint
``` 

The "sudo" makes you temporarily root. I could tell you how to become root, but then I'd have to kill you.

---

### Post by Leoq on 2010-03-08
I got a similar problem going on... with being locked out of a different file. 

as for root thing this will help.

sudo -i

---

### Post by derekeverett on 2010-03-08
Sudo stands for "Super User Do".. it's a little safer than actually logging on as root.

Plus it allows for a lot of bad jokes in the forums!

---

### Post by thecliff on 2010-03-08
You can always enter "whoami" in terminal to display the user

---

### Post by Don1500 on 2010-03-08
"Easy questions get fast answers" - Old Chinese Proverb.

---

### Post by MisFitt on 2010-03-08
Oh thanks Don,
I needed a laugh,kill away!

---

### Post by MisFitt on 2010-03-08
thanks but I'm confused enough as it is.
What a classic,great thread for me-and it's free!

---

### Post by MisFitt on 2010-03-08
Couldn't find any package matching "CinePaint".  However, the following
packages contain "CinePaint" in their description:
  create-resources icc-profiles 
Couldn't find any package matching "CinePaint".  However, the following
packages contain "CinePaint" in their description:
  create-resources icc-profiles 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
=oh well,at least I learned something

---

### Post by rnerwein on 2010-03-08
hi
about your problem with: /var/lib/dpkg/lock  --> permission denied.
in this case - you work with sudo that means your command is running with root permissions.
on the other side "permission denied" comes from that there is another processes wich holds this
lock at the moment. in fact you want's to install a package there is another process running wich want to do the same stuff ( uptdate manager ).
you can figure out wich process that is with following command sequence.
cd /var/lib/dpkg/
sudo fuser -u ./lock
this will give you the process-id of the process wich holds the lock.
ciao

---

### Post by MisFitt on 2010-03-08
thanks,got it,cool!
Much better

---

### Post by 3rdalbum on 2010-03-08
> **MisFitt said:**
> Couldn't find any package matching "CinePaint".  However, the following
packages contain "CinePaint" in their description:
  create-resources icc-profiles 
Couldn't find any package matching "CinePaint".  However, the following
packages contain "CinePaint" in their description:
  create-resources icc-profiles 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
=oh well,at least I learned something

1. Cinepaint isn't in the main Ubuntu repositories. You need to add another repository. For instance, I've noticed that Cinepaint is in the Getdeb.net repository, or you could do a search on Google for "cinepaint ppa".

2. No uppercase letters in package names. Linux is case-sensitive.

3. You can always look in Synaptic Package Manager to find out what packages are currently available.

---

