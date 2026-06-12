---
title: "Ubuntu 18 headless server Samba share with windows 10 enterprise"
date: 2021-02-25
forum: Networking &amp; Wireless
---

### Post by steve248 on 2021-02-25
This is driving me crazy i have exisiting samba shares on this server that worked fine under windows 7 
but under win10 i can see them after turning on smb1 but i cannot access them and they do not 
give me a popup window to put in the login information.

How the hell do i access a samba share on ubuntu WITH A USER ID AND PASSWORD that is not 
the same as the windows 10 login. How do i get it to ASK ME FOR CREDENTIALS when i click
the share under network instead of just failing saying it cannot access or find the share location
without making the share public in ubuntu I want it to be password protected.

I don't want to create a user in samba that matches the windows box i want the user i already
have to stay the same and want windows 10 to ASK ME FOR THOSE credentials the first time
i access them just like it did under windows 7.

as it stands now i can only access win10 shares between windows10 computers that have the 
same login and password i can see all ubuntu and raspberry pi shares in the network section
but i cannot access any of them

---

### Post by guiverc on 2021-02-25
Ubuntu 18?

Are you talking about a Ubuntu Core 18 headless server? or Ubuntu 18.04 LTS Server?

Ubuntu has used *year* format for their smaller IoT appliance/device/cloud products (*which are snap only*) since 2016. They are designed for headless server use, but aren't as powerful (*being light has its advantages*) as the main server product (which is 18.04).

---

### Post by grahammechanical on 2021-02-25
As uneducated as I am (in most things but not all) it seems to me that you are describing a Windows 10 problem. This may help. See the third possible answer.

[https://askubuntu.com/questions/661611/make-samba-share-visible-in-windows-network](https://askubuntu.com/questions/661611/make-samba-share-visible-in-windows-network)

Another alternative

[https://devanswers.co/discover-ubuntu-machines-samba-shares-windows-10-network/](https://devanswers.co/discover-ubuntu-machines-samba-shares-windows-10-network/)

Regards

---

### Post by steve248 on 2021-02-25
Its Ubuntu 18.04 LTS Server no keyboard, mouse or monitor. I use SSH for most work on it.

---

### Post by steve248 on 2021-02-25
> **grahammechanical said:**
> As uneducated as I am (in most things but not all) it seems to me that you are describing a Windows 10 problem. This may help. See the third possible answer.

[https://askubuntu.com/questions/661611/make-samba-share-visible-in-windows-network](https://askubuntu.com/questions/661611/make-samba-share-visible-in-windows-network)

Another alternative

[https://devanswers.co/discover-ubuntu-machines-samba-shares-windows-10-network/](https://devanswers.co/discover-ubuntu-machines-samba-shares-windows-10-network/)

Regards

I saw and read hundreds of these links I initially could not see the shares at all and did turn smb1 on to see them, but that is not my issue
at this point. I can see the shares, i cannot connect to them. It seems windows sends the windows10 username and password to ubuntu
when connecting the the shares without asking me to enter anything, which fails of course because the username and password for the
shares in ubuntu is not the same as windows, and i don't want it to be the same.

so if windows is has a login of USERNAME:PASSWORD and ubuntu samba has a login of OTHERUSER:OTHERPASSWORD under win7 it would
pop a box up where i could put in the user name and password setup with samba and all was fine, windows10 seem to only send its own
username and password as credentials and does not asking me to enter anything which fails.

It seems to me all these fixes make it work on smb1 which is not secure, and would force me to make the ubuntu box have the same login
credentials as the windows box which i don't think is secure either. I don't know how to get windows to pop up the box that win7 did and
ask me for the login id and password for the share setup in samba which was in no way related to the login id of the windows computer.

---

### Post by Morbius1 on 2021-02-26
So far I haven't been able to reproduce this error but I will keep trying. I'm doing this without setting the Win10 client to SMB1 but I'm not sure if it would make any difference.

This may come across as insulting since you have probably checked all this but:

Are you sure you didn't add this user to the samba password database:
```
sudo pdbedit -L
```
And did you by any chance use a username map in your servers smb.conf:
```
testparm -s | grep 'username map'
```

---

### Post by TheFu on 2021-02-26
> **steve248 said:**
> Its Ubuntu 18.04 LTS Server no keyboard, mouse or monitor. I use SSH for most work on it.

WinSCP isn't an option?  That would use scp or sftp for transfers.

---

### Post by steve248 on 2021-02-26
I have found a fix for accessing the shares but this does mean turning on smbv1 in windows to see them which i believe is a security threat to get access to them i had to add the user id and password setup in samba on all the different machines to the windows credential manage in windows10 once i did this i could access the shares, but i still would like to get this to work without needing to turn on smbv1 in windows ie get it to work under smb3 i believe

---

### Post by Morbius1 on 2021-02-28
It is "discovering" the Samba server via NetBIOS under SMB1. It has no choice since it is the only way it can do it without implementing WS-Discovery on the Server.

But it is not connecting to the Samba server with SMB1. It is connecting to it with SMB3:

Connect to the samba share from Win10. Then on the Ubuntu server run:
```
sudo smbstatus
```
You should see the Win10 machine accessing your share using SMB3_11.

This is the way Samba / SMB works. There is an initial contact followed by a "protocol negotiation" where the two systems agree upon the highest level of the smb dialect they can both use.

And you don't have to "discover" the server ( so you don't have to enable SMB1 on the Win10 client ) if you don't want to do so. You just have to connect to the server from Win10 explicitly:

If you are really lucky by ubuntu's host name:
```
\\ubuntu-host-name
```
Better would be by its mDNS host name:
```
\\ubuntu-host-name.local
```
[COLOR=#ff0000]*Ubuntu server does not install avahi ( the mDNS part ) by default so you would have to install it:*[/COLOR]
```
sudo apt install avahi-daemon
```
But the best way is by ip address:
```
\\192.168.0.100
```

---

### Post by rsteinmetz70112 on 2021-02-28
Is SAMBA an NT style domain or an AD ?
There is a registry hack to allow a Windows 10 to join an NT domain.
What version of SAMBA?

---

