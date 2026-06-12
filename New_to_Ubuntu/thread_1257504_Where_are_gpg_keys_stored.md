---
title: "Where are gpg keys stored?"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by cat2005 on 2009-09-03
Where are gpg keys stored?

I can see 3 listed in synaptic that I have.  

I am using a program called "reconstructor" to make a live CD and am being asked to "import" gpg keys.  I have no idea where they are located, let alone what they are.

Any help would be appreciated.

Thanks.

---

### Post by mprince on 2009-09-03
-

---

### Post by cat2005 on 2009-09-03
I had a thought.  Since I don't even know what is a "gpg" key, perhaps I don't have it.  Perhaps I mistook something else for it.

Here is a screen-shot.  

[http://img35.imageshack.us/img35/2273/arethesegpgkeys.png](http://img35.imageshack.us/img35/2273/arethesegpgkeys.png)

Are those gpg keys?  Or are they something else?  Those are the only "keys" that I know of.

Thanks.

---

### Post by niteshifter on 2009-09-04
> **cat2005 said:**
> I had a thought.  Since I don't even know what is a "gpg" key, perhaps I don't have it.  Perhaps I mistook something else for it.

Here is a screen-shot.  

[http://img35.imageshack.us/img35/2273/arethesegpgkeys.png](http://img35.imageshack.us/img35/2273/arethesegpgkeys.png)

Are those gpg keys?  Or are they something else?  Those are the only "keys" that I know of.

Thanks.

Yes, those are gpg keys. They are stored in /etc/apt/trusted.gpg. As you have seen, you can use Synaptic to display them or from a command line:

```
sudo apt-key list
```

For more info:
```
man apt-key
```
Perhaps the application can deal with /etc/apt/trusted/gpg, but if it can't you'll probably want to use:
```
sudo apt-key exportall > repokeys.txt
```
or to get a specific repository key:
```
sudo apt-key export *keyid*
```

Whats *keyid*? Sample output of apt-key list below, the *keyid* is in boldface:
```
sudo apt-key list
/etc/apt/trusted.gpg
--------------------
pub   1024D/**437D05B5** 2004-09-12
uid                  Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
sub   2048g/79164387 2004-09-12
```

---

### Post by cat2005 on 2009-09-04
niteshifter, et al:
 
Thanks!

---

