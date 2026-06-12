---
title: "Cannot connect from Windows to Ubuntu"
date: 2007-07-20
forum: Networking &amp; Wireless
---

### Post by Tom Brown on 2007-07-20
Hi all,

Have Ubuntu computer running in Windows network.

From Ubuntu computer have perfect acces to windows computer but from Windows computer (XP SP2) cannot acces the Ubuntu computer.

Windows takes a lot of time to connect and finally says that I do not have te necessary rights.

Can anyone help ?

Many thanks
Tom

---

### Post by renzokuken on 2007-07-20
have you installed samba on your ubuntu machine?

you need to install samba (available in repos System -> Admin -> Synaptic Package Manager )

then you can install samba to share files and folders with windows computers

---

### Post by Tom Brown on 2007-07-21
Many thnx for your reply.
Apparantly Samba was already installed (Ubuntu 7.04).
However do not know how to access and configure it.:(
Thanks in advance for your help.

---

### Post by kirios on 2007-07-21
[COLOR="DarkRed"]That's samba-client, right? I think you'll need samba-server if you want to make your ubuntu box visible to windows machines on your network.[/COLOR]

---

### Post by Koybe on 2007-07-21
Here is a simple howto : [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

Anyway if you want more information, you need to be more specific in what you need. (Access what?)

---

### Post by kirios on 2007-07-21
[COLOR="Blue"][https://help.ubuntu.com/7.04/server/C/configuring-samba.html#windows-networking-clients]("https://help.ubuntu.com/7.04/server/C/configuring-samba.html#windows-networking-clients")[/COLOR]

---

### Post by stuart.moss on 2007-07-22
I have exactly the same problem. I have installed Ubuntu 7.04 on a PC that is connected to a network with other pcs running windows XP. I want to use the Ubuntu machine as a central shared storage facility for the two windows pcs. I have set up a shared folder and want to send files to this folder from either windows pc.

I can see the ubuntu PC from windows networking within the correct mshome network group. Double clicking  the unbuntu pc icon gives me a dialogue box asking for user name and password.  I type in my ubuntu user name and password and that's where it stops.

Am I missing something?

BTW - I have installed SAMBA

---

### Post by kirios on 2007-07-22
[https://help.ubuntu.com/7.04/server/...orking-clients](https://help.ubuntu.com/7.04/server/...orking-clients)

---

### Post by stuart.moss on 2007-07-22
Thanks, I can read the documentation for myself - several times in fact.

I am looking for some ideas from those who may have had to work this out themselves and can share their information with everyone else.

 Is there anyone who can please  provide more helpful and coherent advice on this?

---

### Post by mewisemagic on 2007-07-22
hey, i have same problem and i can't open files from ubuntu m/c to xp pro m/c here is a screenshot of my problem. how do irename it to open the files?
[IMG][IMG]http://i56.photobucket.com/albums/g182/mewisemagic_2006/Screenshot.png[/IMG][/IMG]

---

### Post by kirios on 2007-07-23
> Thanks, I can read the documentation for myself .... more helpful and coherent advice on this?

**[COLOR="Sienna"]To access a samba share from a windows system in the same workgroup, you need to add users with the encrypted password.[/COLOR]**

```
# smbpasswd –a stuart.moss
New SMB password: ********
Retype new SMB password:********
```
[B]
[COLOR="Sienna"]If the command fails because the password file does not exist, [/COLOR][/B]

```
# touch /etc/samba/smbpasswd
```

**[COLOR="Sienna"]Hope that is a bit more helpful and coherent.[/COLOR]**

---

### Post by stuart.moss on 2007-07-23
Thanks - Yes it is.

I found this useful also:

[http://youtube.com/watch?v=Ad17kma8rNM](http://youtube.com/watch?v=Ad17kma8rNM)

---

### Post by kirios on 2007-07-23
[COLOR="Sienna"]Glad it was useful. None of the Samba documentation on the Ubuntu wiki seems to address this issue, so I can understand your frustration. :-)
Btw there's a HOW-TO at [http://ubuntuforums.org/showthread.php?t=202605]("http://ubuntuforums.org/showthread.php?t=202605") that may be useful.[/COLOR]

---

