---
title: "Locating files in fuse filesystem"
date: 2006-11-25
forum: Networking &amp; Wireless
---

### Post by akarun on 2006-11-25
Hi, 
I installed fusesmb to mount the windows shares of my network.
I run it with the command```
fusesmb /home/akarun/network -o allow_root
```

Everthing works fine.. All the shares get mounted to this mountpoint..
I can do an ```
ls -R > filelist
```
all the shares are listed and copied to this file "filelist"...

I wanted to do something better..
I wanted **updatedb** to probe this folder and hash the files in it.. so that I can go for a **locate filename**

When I do ```
sudo updatedb
```
and ```
locate filename
```

it seems the files are not hashed.. just the **WORKGROUPS/HOSTNAME** gets hashed.. :( 

Is there anyway of getting around with this problem??

Can anyone help in this?

Arun

---

