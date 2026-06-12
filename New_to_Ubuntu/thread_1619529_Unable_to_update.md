---
title: "Unable to update"
date: 2010-11-11
forum: New to Ubuntu
---

### Post by mangurt on 2010-11-11
Greetings all, I'm currently running ubuntu 10.10 which I upgraded when it came out.  I'm currently having a problem when I attempt to update my system:  I receive this error message

```
Err http://ppa.launchpad.net maverick/main Sources
  404  Not Found
Err http://ppa.launchpad.net maverick/main i386 Packages
  404  Not Found
Fetched 6,272B in 1s (3,866B/s)
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 61E091672E206FF0
W: Failed to fetch http://ppa.launchpad.net/user/ppa/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/user/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

I get this error via apt-get or synaptic.

Any ideas on how I can fix this?
Thanks

---

### Post by godspeedmav on 2010-11-12
Please open a Terminal from the menu **Applications > Accessories > Terminal** and type or better copy and paste a row at a time then press enter:

```
gpg --keyserver keyserver.ubuntu.com --recv 61E091672E206FF0

gpg --export --armor 61E091672E206FF0 | sudo apt-key add -

sudo apt-get update

```

give your password when requested, you will not see anything when you type it, so try to key in the password correcctly, then press enter.

Hope this helps

---

### Post by sikander3786 on 2010-11-12
Or you can try disabling those additional ppas from Software Center > Edit > Software Sources > Other Software Tab and update again.

---

### Post by mangurt on 2010-11-12
Well, I ran the commands, and got a little further;

```
W: Failed to fetch http://ppa.launchpad.net/user/ppa/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/user/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

I have no idea what packages are missing, so I don't know what to shut off....:(

---

### Post by sikander3786 on 2010-11-13
You still have 2 PPAs enabled. Once again go to Software Center > Edit > Software Sources, go to Other Software Tab and uncheck all the entries containing Launchpad in their name.

---

### Post by godspeedmav on 2010-11-13
Yes, as said above you have 2 PPAs enabled that is causing it. It's either because the server has no updates or it does not have that PPA on that particular server.

So, go and disable those 2 PPAs, from the guessing it would probably be called [_http://launchpad.net/user/ppa_](_http://launchpad.net/user/ppa_) - something like that or if that doesn't work try changing servers. Both are done from **System > Administrations > Software Sources > Other Software Tab**. IIRC, Maverick doesn't show Software Sources by default in the menus, if it doesn't show, you could go to **System > Administrations > Update Manager > Settings** (near bottom-left) > (It will show Software Sources) **Other Software Tab**.

---

### Post by toekneewood on 2010-11-13
Give this a go.  open up a terminal and run these three lines of code.  Line "1" takes a backup copy of the file just in case.  Line "2" searches for the problem line and places a "#" in front.  Line "3" runs the update again
```

sudo cp /etc/apt/{sources.list,sources.list.bak}
sed -i 's/^deb.http:..ppa.launchpad.net.user.ppa.ubuntu/# &/g' /etc/apt/sources.list
sudo apt-get update

```If you want to put the file back then tun this
```

cp /etc/apt/sources.list.bak /etc/apt/sources.list
or
cat /etc/apt/sources.list.bak > /etc/apt/sources.list

```

---

### Post by tajiknomi on 2010-11-13
[SIZE=2]?!
[/SIZE][]("http://ppa.launchpad.net/user/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz")

---

### Post by tajiknomi on 2010-11-13
[SIZE=2]404 errors indicates that these severs are not responding right now...therefore it shows u that error-message..

Go to system>Administrater>software sources>Repository...

And Uncheck these both...and try again[/SIZE]
[http://ppa.launchpad.net/user/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/user/ppa/ubuntu/dists/maverick/main/source/Sources.gz)

[http://ppa.launchpad.net/user/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/user/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz)

---

### Post by mangurt on 2010-11-13
Ok, I removed two files that had those, and now I don't have the error.  Thanks

---

