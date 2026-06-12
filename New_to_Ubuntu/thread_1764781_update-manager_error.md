---
title: "update-manager error"
date: 2011-05-22
forum: New to Ubuntu
---

### Post by jakuloy on 2011-05-22
i have this problem when i updated my ubuntu using this command "sudo apt-get update"

E: Unable to parse package file /var/lib/apt/lists/ph.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages (1)
E: Problem opening /var/lib/apt/lists/ph.archive.ubuntu.com_ubuntu_dists_natty_restricted_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.


in /var/lib/apt/lists, i have a lots of .bz2 and i try to extract using bzip2recover, and it's failed, it won't work


indeed, i neither update nor install softwares from ubuntu software center

please help me!!!

thanks in advance...

---

### Post by Rubi1200 on 2011-05-22
Hi and welcome to the forums :-)

Do the following please as a first step in trying to fix this:

Try changing to the Main Server in Synaptic -> Settings -> Repositories -> Download from

Let us know if this helps.

---

### Post by Frogs Hair on 2011-05-22
Try running these commands _one at a time_ if changing the sever fails.
```
sudo dpkg --configure -a
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get update

```

---

### Post by jakuloy on 2011-05-23
yeah...it works...thanks guys!!!!:KS

---

### Post by Rubi1200 on 2011-05-23
> **jakuloy said:**
> yeah...it works...thanks guys!!!!:KS

Excellent! Glad you got it sorted out :-)

Enjoy :-)

---

### Post by jakuloy on 2011-05-24
but sir what's this....

W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_natty_main_source_Sources  Hash Sum mismatch
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_natty_multiverse_source_Sources  Hash Sum mismatch
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_natty_universe_source_Sources  Hash Sum mismatch
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages  Hash Sum mismatch
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_natty_universe_binary-i386_Packages  Hash Sum mismatch
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_natty_multiverse_binary-i386_Packages  Hash Sum mismatch
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_natty-updates_main_source_Sources  Hash Sum mismatch
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_natty-updates_main_binary-i386_Packages  Hash Sum mismatch
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_natty-updates_universe_binary-i386_Packages  Hash Sum mismatch
, E:Some index files failed to download. They have been ignored, or old ones used instead.


i can't install some apps from ubuntu software center...

---

### Post by Rubi1200 on 2011-05-24
Do you still have Main Server set in Software Sources? If not, please set it to the Main Server and follow the advice below.

Try these commands and see if it fixes the issue:

```
sudo apt-get update -o Acquire::http::No-Cache=True
sudo apt-get update && sudo apt-get upgrade
```If this doesn't work, do this:
```
sudo apt-get update -o Acquire::BrokenProxy=true
sudo apt-get update && sudo apt-get upgrade

```

---

### Post by jakuloy on 2011-05-25
Do you still have Main Server set in Software Sources? If not, please set it to the Main Server and follow the advice below.

Try these commands and see if it fixes the issue:

Code:
sudo apt-get update -o Acquire::http::No-Cache=True
sudo apt-get update && sudo apt-get upgrade
If this doesn't work, do this:
Code:
sudo apt-get update -o Acquire::BrokenProxy=true
sudo apt-get update && sudo apt-get upgrade



nope...won't work either

---

### Post by Rubi1200 on 2011-05-25
Try running this:

```
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get update
```

From the information I have found so far about these errors it is mostly just a question of waiting till the mirrors are synced and then trying to update again.

---

### Post by jakuloy on 2011-05-30
won't work also sir

i guess, because of this errors...

W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

---

### Post by Rubi1200 on 2011-05-30
Wow, this is really an ongoing story here ;)

Try these commands:

```
sudo apt-get clean 
cd /var/lib/apt 
mv lists lists.old 
mkdir -p lists/partial 
sudo apt-get clean 
sudo apt-get update
```

---

### Post by thaDM on 2011-06-03
> **Rubi1200 said:**
> Wow, this is really an ongoing story here ;)

Try these commands:

```
sudo apt-get clean 
cd /var/lib/apt 
mv lists lists.old 
mkdir -p lists/partial 
sudo apt-get clean 
sudo apt-get update
```

I just had this problem with Xubuntu and the above commands fixed it, cheers Rubi!

---

### Post by Rubi1200 on 2011-06-03
> **thaDM said:**
> I just had this problem with Xubuntu and the above commands fixed it, cheers Rubi!
No problem, you are more than welcome :-)

---

### Post by neha123 on 2012-02-15
I had the same problem. Changing download from Main server solved my problem.. thanks a lot....:)

---

