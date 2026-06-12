---
title: "Can't remote access when target PC not logged in"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by snuffy on 2009-07-10
When I have logged into the target PC (9.04) I can access it via Remote Desktop Viewer from my laptop, no problems. However, what I want to be able to do is wake-on-lan (which is working fine) and then log into the PC (which i am using as a server, with a view to running it 'headless') from my laptop (9.04). 

As it stands, I have to go to the PC and log in before going back to the laptop to access the PC shared files.

I have tried the 'auto login' feature of ubuntu, but for some reason it messes up the samba shares on my disks, when they mount. Plus there's the security issue.

How can I login in to the PC remotely?

Can't find an answer anywhere! Any help would be much appreciated.

Cheers, 
Tim.

---

### Post by scorp123 on 2009-07-10
There are several ways to achieve what you want.

One way would be to load VNC (that's the protocol that is used to access the shared desktop, in case you didn't know that ...) automatically as network service, so you'd be able to access the login screen remotely:

[http://ubuntuforums.org/showpost.php?p=4963842&postcount=1](http://ubuntuforums.org/showpost.php?p=4963842&postcount=1)


Another less elaborate method would be to remotely login to your other computer and to start things manually -- As I said: it's less elaborate but also less complicated:

[http://ubuntuforums.org/showpost.php?p=4527622&postcount=2](http://ubuntuforums.org/showpost.php?p=4527622&postcount=2)


Last but not least: If you only want to use one specific application remotely and don't really need the full desktop, you might just as well use SSH and just launch the application remotely so it gets displayed onto your screen:

```
 ssh -X youruseraccount@remote-PC /usr/bin/firefox 
```

... this would log you in and instantly launch Firefox from the remote PC. BUT: if for some odd reasons a disconnect happens (e.g. bad WiFi signal?) then whatever application you launched this way will instantly die and crash. It ultimately depends on what you want. Firefox for example takes such crashes rather well and will offer to restart wherever you left off when it crashed; other applications (OpenOffice comes to my mind ...) are more complicated and it's better to have them run via VNC rather than via "ssh -X" ...


And just so I don't forget to mention this:  for SSH to work you need the "openssh-server" package or else remote logins won't work.

---

