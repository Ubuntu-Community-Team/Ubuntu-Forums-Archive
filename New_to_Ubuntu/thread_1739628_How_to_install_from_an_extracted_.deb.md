---
title: "How to install from an extracted .deb"
date: 2011-04-26
forum: New to Ubuntu
---

### Post by john77eipe on 2011-04-26
Hi,

I know to install a downloaded .deb package using the utility dpkg.

But I have an extracted package. How do I install this? Do I need to create a .deb package from these files to install them??

The list of files in the extracted folder "bmon"
```

$ ls -l
total 32
-rw-r--r--  conffiles
-rw-r--r--  control
-rw-r--r--  debian-binary
drwxr-xr-x  etc
-rw-r--r--  md5sums
-rwxr-xr-x  postinst
-rwxr-xr-x  postrm
drwxr-xr-x  usr

```

---

### Post by matt_symes on 2011-04-26
Hi

Where did you download it from ? Do you have a link ?

Kind regards

---

### Post by john77eipe on 2011-04-26
yes. 
[http://packages.debian.org/squeeze/i386/bmon/download](http://packages.debian.org/squeeze/i386/bmon/download)

---

### Post by jtarin on 2011-04-26
> If you are running Debian, it is strongly suggested to use a package manager like aptitude or synaptic to download and install packages, instead of doing so manually via this website.

The same package is available in the Maverick repositories......use apt or Synaptic to download and install.

---

### Post by Lateralis on 2011-04-26
I was just able to download the .deb file from a few of the European mirror sites. All appear to be OK.  Could it be that your download location or the download itself is/was borked?

... And what jtarin said!

---

### Post by john77eipe on 2011-04-26
No no. I just wanted to learn to install from extracted files. :)

---

### Post by matt_symes on 2011-04-26
Hi

I'm a bit confused. I just downloaded it from the link ftp.uk.debian.org/debian on the page you just referenced and installed it as a normal deb using gDebi.

Am i missing something ?

You can also install it using apt-get (version Installed: 2.0.1-3)

```
sudo apt-get install bmon
```

BTW: You can also get the source for it and install it that way (newer version)

[http://linux.softpedia.com/dyn-postdownload.php?p=15883&t=0&i=1](http://linux.softpedia.com/dyn-postdownload.php?p=15883&t=0&i=1)

I would love to help but i'm really not sure what the problem is :(

**EDIT:** How long was i installing that software ? :)

> No no. I just wanted to learn to install from extracted files. 

Then try installing from source.

Kind regards

---

### Post by jtarin on 2011-04-26
> **john77eipe said:**
> No no. I just wanted to learn to install from extracted files. :)
Then read the extracted files that tell you where to place everything,how to make symlinks,how to solve dependencies and register installation with apt. You want to take the wheels off the wagon and run that way.....I won't stop you. Get another distro ....like Linux From Scratch and learn everything the hard way.The problem is you can't keep track of your packages that way. If you ever want to uninstall.

---

### Post by john77eipe on 2011-04-26
> **matt_symes said:**
> **EDIT:** How long was i installing that software ? :)
Then try installing from source.


You mean source code?
I like to install it from the extracted/uncompressed-untared binary files. Not from the source code.

---

### Post by matt_symes on 2011-04-26
Hi

> **john77eipe said:**
> You mean source code?
I like to install it from the extracted/uncompressed-untared binary files. Not from the source code.

> Then read the extracted files that tell you where to place everything,how to make symlinks,how to solve dependencies and register installation with apt. 

This ;)

Kind regards

---

### Post by Paqman on 2011-04-26
> **john77eipe said:**
> No no. I just wanted to learn to install from extracted files. :)

You want to unpackage the software and install it from there? Can I ask why? Just curiosity? If so, you can actually compile software directly from source, which is arguably a bit more useful thing to learn than pulling .debs apart.

If you're insterested in learning how to package, take a look at the [Packaging Guide](https://wiki.ubuntu.com/PackagingGuide/Complete). They're always looking for more volunteers to help with packaging.

---

