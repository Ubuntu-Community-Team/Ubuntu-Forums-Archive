---
title: "Update problem after a tiny mistake"
date: 2011-01-13
forum: New to Ubuntu
---

### Post by Jundy on 2011-01-13
Hi,

I was trying to install this :
sudo apt-get install ubuntu-restricted-extras

Then I reached to agreement page where you need to press OK. By mistake I press a keyboard shortcut and I closed down the terminal.

Now I am stuck with this error every time I run sudo apt-get update

```
Hit http://gb.archive.ubuntu.com maverick-updates/main i386 Packages
Hit http://gb.archive.ubuntu.com maverick-updates/restricted i386 Packages
Hit http://gb.archive.ubuntu.com maverick-updates/universe i386 Packages
Hit http://gb.archive.ubuntu.com maverick-updates/multiverse i386 Packages
Fetched 317B in 1s (213B/s)
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0
```I have tried many solution posted here and across the inter-webs, nothing has worked for me.

I even run a script I found here in the forums, 
```
masters@masters-ubunto1010:~/Downloads$ sudo ./launchpad-update intrepid
Release: intrepid
Please Wait...
cat: keyss: No such file or directory
rm: cannot remove `keyss': No such file or directory

```Please advise. 
J

---

### Post by mikewhatever on 2011-01-13
It's unlikely that what you've described had anything to do with the error. Try removing that launchpad repository if you don't need it, or remove and re-add it later.

---

### Post by Jundy on 2011-01-13
> **mikewhatever said:**
> It's unlikely that what you've described had anything to do with the error. Try removing that launchpad repository if you don't need it, or remove and re-add it later.

:D it worked 

I removed it via the software source,

but you know its nice if you could let me know how to do it via command terminal!

---

### Post by mikewhatever on 2011-01-13
Glad it worked.:KS

To remove the ppa from Terminal, I don't know of any other way, other then editing the software sources list.

```
sudo nano /etc/apt/sources.list
```

---

### Post by jmszr on 2011-01-13
Jundy,

You might be interested in PPA Purge: [http://www.webupd8.org/2010/08/ppa-purge-added-to-official-ubuntu-1010.html](http://www.webupd8.org/2010/08/ppa-purge-added-to-official-ubuntu-1010.html) .

It has worked well for me.

---

### Post by hansolo4949 on 2011-01-13
You should try sudo apt-get autoremove


That might resolve the issues.

You should also try installing the software package again.


hansolo4949

---

