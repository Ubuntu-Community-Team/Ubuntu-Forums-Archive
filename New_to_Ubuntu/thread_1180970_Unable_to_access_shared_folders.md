---
title: "Unable to access shared folders"
date: 2009-06-07
forum: New to Ubuntu
---

### Post by rrroninnn on 2009-06-07
I have samba installed on my main Ubuntu desktop with the sharing option enabled for the folders I want to share.

My Vista laptop cannot access the shared files.  It shows the Ubuntu desktop on the network device window, but when I try to double click on the icon,I get a message that says Windows cannot access the Ubuntu desktop.  The details arrow shows that the network path was not found.

This has me totally confused since all I want to do is access certain /home folders using my laptop.  Please advise.

---

### Post by cmnorton on 2009-06-09
> **rrroninnn said:**
> I have samba installed on my main Ubuntu desktop with the sharing option enabled for the folders I want to share.
.
.
.


I am confused as to what the "sharing option" is.

---

### Post by Celauran on 2009-06-09
> **cmnorton said:**
> I am confused as to what the "sharing option" is.

In Nautilus. Right-click -> Sharing Options. Always seems to cause problems and I'll never understand why people use this over proper shares defined in smb.conf.

---

### Post by superprash2003 on 2009-06-10
in your ubuntu terminal type **smbtree** and post output.. in windows go to windows explorer and type \\x.x.x.x where x.x.x.x is the ip of the ubuntu machine.. that should hopefully give you list of shares..

---

### Post by eckie on 2010-07-04
Sorry for necro-ing this thread but I thought I'd share the solution I found to this elsewhere in the forum (where I don't seem to have sufficient privileges to post).

With the same problem as the OP I came upon this thread (links to the page containing the solution): [http://ubuntuforums.org/showthread.php?t=737664&page=3](http://ubuntuforums.org/showthread.php?t=737664&page=3). This got me trying various permission configurations for "other" users (since adjusting group permissions would be useless without changing the group of a share, which one might not always want to do).

The generic (but complex) resolution to this problem is that the user trying to access a share must also have sufficient privileges to traverse the parent directories (though not necessarily read the files in those directories).

In the specific case of guest access to a share in a user's home directory: The "execute" permission for "other" users needs to be set on the home directory.

```
chmod o+x /home/user
```

Even the 10.04 "Lucid" Nautilus filesharing GUI doesn't seem to ensure this automagically when you enable sharing for the first time.

I'll write a blogpost about how to do this with just the GNOME GUI and link to it from here later.

---

