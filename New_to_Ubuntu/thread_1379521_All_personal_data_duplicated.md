---
title: "All personal data duplicated?"
date: 2010-01-12
forum: New to Ubuntu
---

### Post by ScottinSoCal on 2010-01-12
It's taken me a while to notice this (my hard drive is much bigger than I use) but it appears that all the data in my /home folder is being duplicated in the .encryptfs folder. Did I select an option during install for this? If so, how do I turn it off? It hasn't been a problem, my HDD is less than 20% full, but HDD reads and writes should be faster if I'm not writing everything twice, shouldn't it?

Or have I completely misunderstood what's happening here?

---

### Post by warfacegod on 2010-01-12
Check the properties of that folder to see how big it is.

---

### Post by ScottinSoCal on 2010-01-13
> **warfacegod said:**
> Check the properties of that folder to see how big it is.

The exact same size as my home folder. That's how I stumbled across this - running a disk use analysis with one of the utilities.

---

### Post by warfacegod on 2010-01-13
What happens when you do this?:

```
sudo aptitude ecryptfs-utils
```

---

### Post by warfacegod on 2010-01-13
I think that should read apt-get not aptitude.

---

### Post by ScottinSoCal on 2010-01-13
> **warfacegod said:**
> I think that should read apt-get not aptitude.

Hmmm. I've done apt-get several times for this or that, but I'm getting an error message that doesn't seem to make sense.

Invalid operation encryptfs-utils

Isn't my operation apt-get, and the parameter is encryptfs-utils?

---

### Post by da burger on 2010-01-13
When you run apt-get it should be followed by, for example, install or uninstall (There are other things as well).

eg.
```
sudo apt-get install package
```

There has to be an operation between apt-get and the package name.

---

### Post by warfacegod on 2010-01-13
I was thinking on a hunch that obviously didn't pan out. Have you tried backing up your home folder and deleting the .encryptfs one? I'm not necessarily suggesting you do that, just wondering if you have.

---

### Post by ScottinSoCal on 2010-01-13
Yeah, I caught that after I'd played a couple more minutes.

Now I'm getting "ecryptfs-utils is already the newest version", so apparently there's some file encryption going on.

However, after doing a little bit of simple math, I'm wondering if the data is really duplicated?

I have a 500 GB HDD. The reported size for my home directory is 70.5 GB, as is the encrypted folder. If they both actually exist, I'd have - at a minimum - 141 GB used on my hard drive, leaving me with something less than 359 GB (less, because my swap takes up some amount of space that isn't included in the main filesystem size). But I don't, I have over 400 GB free. Something is clearly not adding up.

If I selected to encrypt my home folder, would it then unencrypt on login to a bogus mount point? And be reported twice? Because that's what appears to be happening. I'm not familiar with hard drive encryption, I've never seen a need for it, so I haven't looked into it much.

---

### Post by The Cog on 2010-01-13
My guess is that the un-encrypted files don't really exist on the disk. They look as though they are there because ecryptfs has made them look as though they are there - the physically existing encrypted system is mounted to the empty folder creating the appearance of a set of unencrypted files.

---

### Post by OpenSourceOfAwesomeness on 2010-02-22
Did anyone sort this out? The same thing appears to be happening to me. I'm using Karmic Koala and my numbers are like this:

Ubuntu partition total: 52GB
Free Space: 13.5GB
usr,lib,var,boot,etc: 5GB

which implies that I should have about 33.5GB of total files on my Ubuntu partition. Disk usage analyzer is reporting something like 25GB of files in my home directory and 27GB of files in the .ecryptfs directory, which clearly adds up to more that 33.5.

So do those files actually exist? Or is this some sort of bogus mount that's fooling the disk usage analyzer program? Either way, if I don't need any disk encryption, how do I turn it off?

---

### Post by ScottinSoCal on 2010-02-25
> **OpenSourceOfAwesomeness said:**
> So do those files actually exist? Or is this some sort of bogus mount that's fooling the disk usage analyzer program? Either way, if I don't need any disk encryption, how do I turn it off?

The only one that actually exists is the encrypted folder. When I log in, the files are unencrypted and presented as partitions. <shrug> It's secured, that's all I was worried about.

---

