---
title: "Update Problem"
date: 2009-08-20
forum: New to Ubuntu
---

### Post by sumeshgupta on 2009-08-20
Whenever I run the command "sudo apt-get update" I get that some key does not exist. The snapshot of last few lines is as under:

[php]Hit http://repository.cairo-dock.org hardy Release.gpg       
Ign http://repository.cairo-dock.org hardy/cairo-dock Translation-en_IN
Hit http://repository.cairo-dock.org hardy Release
Hit http://repository.cairo-dock.org hardy/cairo-dock Packages
Fetched 308B in 31s (10B/s)
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7D2C7A23BF810CD5
W: You may want to run apt-get update to correct these problems[/php] Can i get some help as to how can I resolve it? Thanks in advance.

---

### Post by swoody on 2009-08-20
It looks like you didn't add the GPG key for the cairo-dock ppa. Try running:
```
wget -q http://repository.cairo-dock.org/cairo-dock.gpg -O- | sudo apt-key add -
```

---

### Post by Immolatus on 2009-08-20
Looks to me like you added a repo to "/etc/apt/sources.list" am I right??
If you did then you my have copied the repo name wrong in the command line or the key has changed (just a guess) you my want to have a look at your "/etc/apt/sources.list" and edit out the offending line from your list. May be try here -->  [https://help.ubuntu.com/community/CairoDock](https://help.ubuntu.com/community/CairoDock) for cairo-dock??

Hope this helps...

---

### Post by mthalis on 2009-08-20
[http://ubuntuforums.org/showthread.php?t=1236282](http://ubuntuforums.org/showthread.php?t=1236282)

---

### Post by sumeshgupta on 2009-08-20
Cairo_dock was o.k. I had to remove the AWN repositories. Now there are no error messages. Thanks everyone.:guitar:

---

### Post by 3rdalbum on 2009-08-20
That message doesn't actually indicate a problem or a failure; it's just warning you that it won't be able to authenticate the digital signature of that repository. If you were subjected to a man-in-the-middle attack while downloading files from that repository, you wouldn't know about it; whereas if you had the GPG key Apt would know.

I have two repositories where I've forgotten to add the GPG key and I can still install software from them.

---

### Post by jherskow on 2009-08-27
hi im a total newbie, and im getting some problems when i try to update:
```

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://archive.ubuntu.com jaunty-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://archive.ubuntu.com jaunty-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: http://medibuntu.sos-sts.com jaunty Release: The following signatures were invalid: NODATA 1 NODATA 2
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release  

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-security/Release  

W: Failed to fetch http://medibuntu.sos-sts.com/repo/dists/jaunty/free/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Some index files failed to download, they have been ignored, or old ones used instead.
```

any help?

---

