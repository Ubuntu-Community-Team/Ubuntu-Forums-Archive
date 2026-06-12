---
title: "ubuntu client cannot see windows home server after recent update"
date: 2010-11-21
forum: New to Ubuntu
---

### Post by yakinikku on 2010-11-21
running 10.04.1, after a recent update via update manager I am no longer able to see/connect to my windows home server.  no changes have been made to the server.  any suggestions?

---

### Post by cariboo on 2010-11-22
Check the workgroup.

---

### Post by yakinikku on 2010-11-22
> **cariboo907 said:**
> Check the workgroup.

thats what im saying, its not there.  if i go to the network, all i see is "windows network."  before the recent update i would get "windows network" and the home server name.  double clicking on "windows network" does not bring me to another window that shows the server either.  perhaps i am doing something wrong but it seems unlikely to me that i would be considering how simple this is.  what i had done was bookmarked the location of a folder on the server and after the recent update i found that i am no longer able to access the folder, this led me to investigate and find that the server is no longer listed in the network.

any other suggestions?

edit: here is a link that has screenshots that show how things should be

[http://www.howtogeek.com/howto/19389/access-windows-home-server-from-an-ubuntu-computer-on-your-network/](http://www.howtogeek.com/howto/19389/access-windows-home-server-from-an-ubuntu-computer-on-your-network/)

my server is no longer showing, IE im not able to see/access "geekserver"

double clicking on windows network i get a samba error saying it cannot mount the location with the subtext of it was unable to get the share list from the server.

does that make it any more clear?

---

### Post by yankysunny on 2010-11-22
open terminal and type "nautilus smb://IP address of windows home server/"
I am also facing same problem but with Windows XP.

[http://ubuntuforums.org/showthread.php?t=1626065](http://ubuntuforums.org/showthread.php?t=1626065)

---

### Post by theozzlives on 2010-11-22
at the bottom of your /etc/hosts file put the following:
```
192.168.x.xxx <hostname>
```
do that for every box you have.

---

### Post by yakinikku on 2010-11-22
> **theozzlives said:**
> at the bottom of your /etc/hosts file put the following:
```
192.168.x.xxx <hostname>
```
do that for every box you have.

i did that, i dont know if it made any difference as once i connected to the location and authenticated via the location bar in nautilus i was once again able to view the workgroup location by double clicking on windows network.  just rebooted the computer to test and see if it connects automatically and it did.  i dont know if this means its solved though, why the sudden change?

---

### Post by yakinikku on 2010-11-22
> **yankysunny said:**
> open terminal and type "nautilus smb://IP address of windows home server/"
I am also facing same problem but with Windows XP.

[http://ubuntuforums.org/showthread.php?t=1626065](http://ubuntuforums.org/showthread.php?t=1626065)

actually i was just looking at a thread and it got me thinking so i tried something, in the location bar in nautilus i entered smb://serveripaddress and i was able to connect and bookmark the location.

---

### Post by theozzlives on 2010-11-22
> **yakinikku said:**
> i did that, i dont know if it made any difference as once i connected to the location and authenticated via the location bar in nautilus i was once again able to view the workgroup location by double clicking on windows network.  just rebooted the computer to test and see if it connects automatically and it did.  i dont know if this means its solved though, why the sudden change?

For some reason, the hosts file needs edited since 10.04.

---

### Post by yakinikku on 2010-11-22
> **theozzlives said:**
> For some reason, the hosts file needs edited since 10.04.

this doesnt make sense because it was working fine on 10.04 until a recent security/weekly update.  after the most recent update is when things got wonky.

---

