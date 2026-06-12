---
title: "Question regarding sharing secondary drive as a share with Samba on Ubuntu Server"
date: 2014-02-20
forum: Networking &amp; Wireless
---

### Post by jeremygotcher on 2014-02-20
First off please forgive me if I use the wrong terminology or sound like a noob. I've fiddled with Ubuntu for a number of years but just recently decided to setup a file server at my house using Ubuntu Server 10.04 (Its on a older machine), I've always wanted to take the leap and start using Linux but could never commit to it, and setting this up is kind of forcing me to do it so.. 

My issue is I've have Ubuntu Server installed and running I even have the latest Samba installed, Last night I started looking at the config files and found where it talks about setting up the folder that you want to share.

(This isn't mine, i'm just using it as an example)
[global]
    workgroup = METRAN
    encrypt passwords = yes
    wins support = yes
    log level = 1 
    max log size = 1000
    read only = no
[homes] 
    browsable = no
    map archive = yes
[printers] 
    path = /var/tmp
    printable = yes
    min print space = 2000
[test]
    browsable = yes
    read only = yes
    [COLOR=#b22222]path = /usr/local/samba/tmp

[/COLOR][FONT=Verdana]Do I need to just replace the folder path with the path of the drive or is this something a little more in depth?
Any suggestions would be appreciated, 

Thanks
J
[/FONT]

---

