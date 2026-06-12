---
title: "LAN network with 1 Ubuntu PC and 1 windows PC?"
date: 2007-01-06
forum: Networking &amp; Wireless
---

### Post by ZankerH on 2007-01-06
Hi

At home, I have a PC running Ubuntu 6.10, and another one running windows XP. They're both running on an ADSL connection, through an external modem and a router. Is there anyway I could connect them in a network, to share files and the printer?

---

### Post by xiaoxin on 2007-01-06
yes just install samba on ubuntu, i assume they are already on the same network

---

### Post by ZankerH on 2007-01-07
I don't know if they're on the same network, they're just sharing the connection.

---

### Post by willskills on 2007-01-07
Sudo apt-get install samba

There are a few howto's on how to set Samba up on the forums, just have a quick search.

Just remember to make sure - any windows PC you want to connect to your ubuntu box, must have a User Accnt on Ubuntu, which is the same as the Samba accnt/pwd you create.

I still can't convince my flatmate to run Ubuntu - he has WinxP, and our fileshare works great, as does the printer. 

We are on some random unencrypted wifi network, for our net connection. He is serving me a connection through that.... pretty ropey, but it works :)

---

### Post by ZankerH on 2007-01-07
> **willskills said:**
> Sudo apt-get install samba

There are a few howto's on how to set Samba up on the forums, just have a quick search.

Just remember to make sure - any windows PC you want to connect to your ubuntu box, must have a User Accnt on Ubuntu, which is the same as the Samba accnt/pwd you create.

I still can't convince my flatmate to run Ubuntu - he has WinxP, and our fileshare works great, as does the printer. 

We are on some random unencrypted wifi network, for our net connection. He is serving me a connection through that.... pretty ropey, but it works :)


Yeah, my situation is somewhat similar, but could you please explain more in detail? I'm really new to networking in ubuntu in general, until recently I only had one PC with an ADSL connection that just worked, all I had to do was enter my username and password in pppconfig.

---

### Post by shareMenaPeace on 2007-01-07
Ok we need to install samba server and than we need to create an account under windows

i.e.:

Win xp account:
shareAccount // matrixLoginPassword2theLimiT

and same for

Ubuntu account:
shareAccount // matrixLoginPassword2theLimiT

So does this mena i only can share data between both computers when both logged in with the share account?

---

### Post by rbhigday on 2007-01-07
Creat a network in windows with a name. Give your pc a name as well
The create a network in Ubuntu with the same network name. Give this pc a name different than the windows pc.

Install samba, there are a few guide out there not sure which one is better, will try to find the one I used and post the link later.

---

### Post by rbhigday on 2007-01-07
[Samba Guide]("https://help.ubuntu.com/community/SettingUpSamba")

---

### Post by ZankerH on 2007-01-07
I think there was a misunderstanding, so I'd just like to make myself clear:

I need to make a FAT32 and a NTFS partitions on my ubuntu PC readable and writeable on my windows PC.
The two PCs are not in a network of any kind, just sharing a connection.
I can't create a network in windows either, because it won't detect the ubuntu PC.

---

### Post by ZankerH on 2007-01-07
I followed that tutorial, and when I reloaded /etc/fstab, I get this error:

```
13222: Connection to OKV failed
SMB connection failed
```

(OKV being the name of the windows PC I'm trying to establish a network with)

---

### Post by kombucha on 2007-01-07
(EDIT - resolved, I'm leaving this here for others' reference)

I'm attempting the same thing, and got essentially the same error, but with a different number:

> [mntent]: warning: no final newline at the end of /etc/fstab
5438: Connection to HOME failed
SMB connection failed


Now, here is what I added to my fstab:
//HOME/OLDCOMPUTER /media/downstairs smbfs credentials=/home/eli/.smbpassword,uid=eli 0 0

Where "HOME" is the name of the workgroup my XP computer is on, "OLDCOMPUTER" is the name of my XP computer, "/media/downstairs" is an empty folder on my Ubuntu computer, and "eli" is my account.

Another question, for when this does work - I had to create a new account on my XP computer because the main (and previously only) account has no password; I hate dealing with a login screen. Is it possible to do all of this with a password-less XP user account?

Thanks!

EDIT: I think I got the fstab wrong. I think I don't need the workgroup, and instead need //(name)/(dir) . So I changed it to:
//OLDCOMPUTER/downc /media/downstairs smbfs credentials=/home/eli/.smbpassword,uid=eli 0 0

Where "downc" is the name of "C:" as a shared folder.

Now I get the error:
> [mntent]: warning: no final newline at the end of /etc/fstab
5649: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed


Seems better, because it's at least a bit specific... but I made all of the settings I found in the security settings on the XP machine as lenient as possibe - disabled all of the digital signing and whatnot.

Any ideas now?

Also:

> eli@ELIS-COMPUTER:~$ smbclient -L OLDCOMPUTER
Password:  (I left this blank, when I put in the password I got "session setup failed: NT_STATUS_LOGON_TYPE_NOT_GRANTED")
Anonymous login successful
Domain=[HOME] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Sharename       Type      Comment
        ---------       ----      -------
Error returning browse list: NT_STATUS_ACCESS_DENIED
Anonymous login successful
Domain=[HOME] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Server               Comment
        ---------            -------
        OLDCOMPUTER          Downstairs computer

        Workgroup            Master
        ---------            -------
        HOME                 OLDCOMPUTER


So maybe that folder isn't shared properly? (Actually I guess not, because if I try a different folder I get: "ERRnosuchshare (You specified an invalid share name)")

I guess maybe I don't understand what password it asks for when I try something like:
sudo mount -t smbfs -o user=eli,pass=XXXXXX ,ip=192.168.10.XXX //OLDCOMPUTER/downc /media/downstairs
password: ??



EDIT: OK, fixed that error - in fact it was the same problem I'd been having with two XP computers. For some reason, within the Local Security Policy on the XP computer, the "allow to access from network" key keeps wiping itself - I added myself as a user, and now I can connect without error. Party!!! Hopefully that key will stop erasing itself - if not, a Ubuntu forum clearly isn't the place for a dumb XP question :P (This is why I left XP, because of crap like that)

---

