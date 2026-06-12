---
title: "File sharing with OS X"
date: 2007-05-06
forum: Networking &amp; Wireless
---

### Post by victory2007 on 2007-05-06
I am having trouble connecting to my mac mini.  I can see it on my network servers and open it but it never asked me for my user name and password.  It just opens a blank window.  I installed samba and netatalk and configured my mac for file sharing but it still doesnt work.  Please help.

---

### Post by aysiu on 2007-05-06
What are you using? Ubuntu, Kubuntu, or Xubuntu?

---

### Post by victory2007 on 2007-05-06
I am using regular ubuntu 6.10

---

### Post by aysiu on 2007-05-06
Well, you shouldn't have to install extra software.

First, in Mac OS X, go to Applications and find Terminal.app. It may be under Applications > Utilities. In that, type ```
ifconfig
``` to find out the IP address of that computer. Let's just say, for the sake of this example, that it's 192.168.0.105

Then, in Ubuntu, go to Places > Home, press Control-L, and in the location bar, type ```
smb://192.168.0.105/sharename
``` and hit *Enter*. You should get a spinning mouse cursor for about a half-minute and then be prompted for a username, group, and password. The group should be WORKGROUP. The username and password would be the username and password of the Mac user who's sharing.

---

