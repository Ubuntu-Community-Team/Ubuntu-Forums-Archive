---
title: "Problems mounting windows shares"
date: 2007-04-11
forum: Networking &amp; Wireless
---

### Post by paullew on 2007-04-11
Hello,

I'm having some trouble mounting a remote SMB drive. The file and folder names are coming back as gibberish.

Now, the funny thing is:
 - browsing using smbclient in interactive mode is fine
 - smb://lanserver/PUBLIC in nautilus is fine
 - connecting with a windows client is fine 

But when I try to mount the drive with:
sudo mount -t smbfs //lanserver/PUBLIC /media/lanserver/

This is what I see in /media/lanserver : 

```

-rwxr-xr-x 1 root root 128199817920000000 1940-10-24 12:26 upc
-rwxr-xr-x 1 root root 127489753540000000 1940-10-24 12:26 ?u??
-rwxr-xr-x 1 root root 138179498140000000 1940-10-24 12:26 ?RX????
-rwxr-xr-x 1 root root 138209295400000000 1940-10-24 12:26 ?????????????????????????????
-rwxr-xr-x 1 root root 127489753540000000 1940-10-24 12:26 ???
-rwxr-xr-x 1 root root 138207782140000000 1940-10-24 12:26 _?}????
```

The file names are normally in plain english ... all my computers are running in english (or should be).

Any tips?

Many thanks,
-Paul

---

### Post by bnuytten on 2007-04-21
Just guessing: try "mount -t cifs" instead?

---

