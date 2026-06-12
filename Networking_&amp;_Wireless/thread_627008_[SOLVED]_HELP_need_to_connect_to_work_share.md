---
title: "[SOLVED] HELP need to connect to work share"
date: 2007-11-29
forum: Networking &amp; Wireless
---

### Post by blurryone on 2007-11-29
EDIT:

I resolved this by using the connect to server app and only using the server name and not filling out any of the other details in it. it then asked me for a username/password/domain.

Bloody awesome. i love Ubuntu.. takes a bit but learning soo much in the process.

Cheers all for all the helpfull hints.

Now to clean this friggin shared drive up... *sigh*

_________________________________________________

Hey guys,

I have to connect to a work share for which i have a network account and know the IP address and domain for.. but..

when i try connecting with 'connect to server' -> windows share etc etc.. it does not give me an area to enter my network password. then when i try an open the icon that it makes on my desktop it says that i cannot connect

also was going to try and use nautilus to browse to the share ala entering the smb:// etc etc but nautilus doesn't have an area to enter an address to browse to..

Any help would be appreciated!!

:confused::confused:

Peace,

Blurry

---

### Post by blurryone on 2007-11-29
Ok so i figured out how to browse using nautilus and the ctrl+L command to browse to a location however it will not let me enter a password/username when i do this

---

### Post by flaggh on 2007-11-29
In the location, try typing:

```
smb://username@xxx.xxx.xxx.xxx
```

It should then prompt you for a password.

---

### Post by blurryone on 2007-11-29
Thanks for the reply flaggh,

No such luck however, when i try to connect to it i get the following error message

'The folder contents could not be displayed'
Sorry, couldn't display all the contents of "Windows Network: xxx.xxx.xxx.xxx".

Any other ideas? i'm reletively new to Linux as a whole let alone networking with it. :(

Cheers

Blurry

---

### Post by jflaker on 2007-11-29
> **blurryone said:**
> Thanks for the reply flaggh,

No such luck however, when i try to connect to it i get the following error message

'The folder contents could not be displayed'
Sorry, couldn't display all the contents of "Windows Network: xxx.xxx.xxx.xxx".

Any other ideas? i'm reletively new to Linux as a whole let alone networking with it. :(

Cheers

Blurry

Are you sure that there is no VPN gateway between the internet and your work's LAN.  I will almost 99.9% guarantee that your work has a firewall in place and you will need to acquire either special VPN software (hopefully they have a Linux version) or VPN credentials from which you can use Linux's VPN to get connected.

What you are seeing is the DMZ side of the firewall, so you can make a connection, but the firewall is saying it doesn't know you and is therefore dropping your connection attempts.

---

### Post by blurryone on 2007-11-29
Yes you are probably right as my DNS etc is in another state and thus when nautilus is trying to connect to 'x' share it will be going there to find out where it is and then back to make the connection... HOWEVER... said share is actually on the same network segment as me (same physical location too) so surely there must be a way to bypass that?

That being said with my vista box (which is not a work build either) i can connect to that share without the use of any vpn apps all i needed was to point my NIC at the DNS servers and it would simply prompt me for UN/PW/domain... so maybe im not so sure if there is VPN or not..

I can do a port scan on the box and everything so i am pretty sure there is no security between me and the share/server

Cheers

Blurry

---

### Post by flaggh on 2007-11-29
jflaker is right.  I doubt any company would share its server to the outside world with simple user authentication through samba, which is what smb:// implies.  How do you normally connect to this network share?  It may be through webDAV or SSH, or SCP, or any number of other ways.

---

### Post by blurryone on 2007-11-29
Its not visible to the outside world this is a closed wan, our ISP supplies us with a backbone between states that is all, and external traffic has to go through our proxy server located in the same segment as the DNS (if Joe Blow wants to go surf the web in his lunch break etc)

---

### Post by blurryone on 2007-11-29
just booted back into vista to try it and all i did was type into the run box \\yourservername\sharename and she went straight in. my account is not locked out so it looks like nautilus isn't even finding the dns server?

---

