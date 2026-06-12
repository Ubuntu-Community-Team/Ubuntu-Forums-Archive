---
title: "[SOLVED] set up a samba share like an existing windows share"
date: 2008-08-27
forum: Networking &amp; Wireless
---

### Post by DingsBumps on 2008-08-27
Hi,
what I'm looking to do is to set up a samba share that will mimic my shared folders in windows. REPHRASE: I want other computers (all WinXP) on the network to be able to access Example-Folder (my music folder) whether I'm in ubuntu or windows, and I don't want them to be able to tell the difference (or rather, I don't want them to have to deal with changing anything)

My question is, what should my smb.conf file look like?

At the moment, I get an error on the remote machine that asks me for credentials, and no matter what I give, I get an error saying I don't have permission.

This is what I've done: 
my smb.conf is:
```
[global]
    ; General server settings
    netbios name = MyUsername-new
    server string =
    workgroup = MYWORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

;bla bla bla, other stuff is here in my file, i dont think its important. wins support = yes

[MyUsername's Music]
    path = /media/disk/Documents\ and\ Settings/MyUsername/My\ Documents/My\ Music
    browseable = yes
    read only = yes
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = myusername
    force group = myusername

```

Then I used chmod (is 555 right? the document I was following had 777, but I only want to give read+execute, and not read+write+execute because I don't want these users modifying my music):

```
$ sudo chmod 555 /media/disk/Documents\ and\ Settings/MyUsername/My\ Documents/My Music

```

Then I added users to samba:

```
$ sudo smbpasswd -L -a myusername
New SMB password:
Retype new SMB password:
$ sudo smbpasswd -L -e myusername
Enabled user myusername.
$ sudo useradd -s /bin/true remoteusername
$ sudo smbpasswd -L -a remoteusername
New SMB password:
Retype new SMB password:
Added user remoteusername.
$ sudo smbpasswd -L -e remoteusername
Enabled user remoteusername.

```

So, on the remote (WinXP) computer, when I try to open the folder (from my network places), I get a dialog asking for a username and password. I tried remoteusername and the password (which, by the way, is blank), but I got denied. I then tried myusername and the password is use locally, and got denied again. When I try just myusername with no password, the box pops up again with MyUsername-new\myusername in the user field and it asks for a password (so I assume that means that the windows computer is in fact communicating with my ubuntu box?).

I don't have the specific message it gives me at the moment, but it is something along the lines of "you don't have permission to access this something or other (recourse maybe)". 

any ideas? if the specific message is needed (I realize now, after typing all this, that it would probably be easy enough to put my error message into google and find an answer... but on the other hand, I've already typed all this :-| ) I can get it, but if anyone knows the answer after just reading this, great!

---

### Post by DingsBumps on 2008-09-21
Well, my solution to this was just using the 'share' in the properties dialog instead of editing smb.conf. 

Its an easier solution to figuring out what I did wrong in smb.conf, I guess...

---

