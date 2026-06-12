---
title: "Installing Gwibber on 8.04"
date: 2009-04-04
forum: New to Ubuntu
---

### Post by chackoge on 2009-04-04
Hi I'm trying to install gwibber on 8.04. 

$sudo apt-get install gwibber

gets me a " Couldn't find package gwibber" message.

The links to [http://wiki.ubuntu.com/gwibber](http://wiki.ubuntu.com/gwibber) seem to be down as well.

Thanks for any help. GC

---

### Post by unutbu on 2009-04-04
gwibber is not part of the official repository on Hardy.
According to [https://launchpad.net/~gwibber-team/+archive/ppa](https://launchpad.net/~gwibber-team/+archive/ppa)

Open a terminal (Applications>Accessories>Terminal) and type
```

gksu gedit /etc/apt/sources.list
```
Add 
```
deb http://ppa.launchpad.net/gwibber-team/ppa/ubuntu hardy main
```

to the end of the file. Save and exit gedit.

Next, add the gwibber public key to your system's GPG keyring:
```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 5AFADBD4AA1C92B0
```

Then, to install gwibber, type
```
sudo apt-get update
sudo apt-get install gwibber
```

PS. My information comes from 
[https://launchpad.net/~gwibber-team/+archive/ppa](https://launchpad.net/~gwibber-team/+archive/ppa)
[https://help.launchpad.net/Packaging/PPA#Adding](https://help.launchpad.net/Packaging/PPA#Adding) a PPA to your Ubuntu repositories

---

### Post by chackoge on 2009-04-04
Thanks. I get the following error now. Excuse my limited knowledge please.

sudo apt-get install gwibber
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gwibber: Depends: libwebkit-1.0-1 but it is not installable
           Depends: python-webkitgtk but it is not going to be installed
E: Broken packages

---

### Post by unutbu on 2009-04-04
Let's try this: According to [https://wiki.edubuntu.org/Gwibber](https://wiki.edubuntu.org/Gwibber)

In a terminal type
```

gksu gedit /etc/apt/sources.list
```

Add 
```

deb http://ppa.launchpad.net/webkit-team/ubuntu hardy main

```
Save and exit gedit. 

Then type
```

sudo apt-get update
sudo apt-get install gwibber
```

---

### Post by chackoge on 2009-04-04
Thanks. I also had to to import the public key f991E6CF92D9A3C5Bc. I followed your instructions and ended up with the same result.

The following packages have unmet dependencies:
  gwibber: Depends: libwebkit-1.0-1 but it is not installable
           Depends: python-webkitgtk but it is not going to be installed

---

### Post by unutbu on 2009-04-04
Okay, sorry. My last post was a mistake. 
The webkit-team ppa repo provides libwebkit-1.0-2 but no longer provides libwebkit-1.0-1. The gwibber-team ppa repo provides a gwibber package which demands libwebkit-1.0-1 and will not accept libwebkit-1.0-2.

So I did a google search for "libwebkit-1.0-1 hardy" and came up with this ppa repo: 
```

deb http://ppa.launchpad.net/andrewsomething/ppa/ubuntu hardy main
```

(See [https://launchpad.net/~andrewsomething/+archive/ppa](https://launchpad.net/~andrewsomething/+archive/ppa)).

If you'd like to try installing libwebkit-1.0-1 from this PPA, you can add the above deb source line to /etc/apt/sources.list, and (optionally) remove the "webkit-team" line.

You will need to add Andrew Starr-Bochicchio's Launchpad PPA public key (CA1F91146F087E5A)

Then try installing gwibber yet again.

---

### Post by chackoge on 2009-04-04
I tried something else in the meantime. I upgraded to 8.1 and followed the instructions on 

[https://wiki.edubuntu.org/Gwibber](https://wiki.edubuntu.org/Gwibber)

which worked without problems. Thanks very much for your advice which pointed me in the right direction, gc

---

### Post by komboykomboy on 2009-12-31
thank you very much unutbu..
it really works.
i'm sticking with hardy, waiting for the next lts

---

