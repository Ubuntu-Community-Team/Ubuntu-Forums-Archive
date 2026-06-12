---
title: "how to share files between linux windows in home securely?"
date: 2022-07-03
forum: Networking &amp; Wireless
---

### Post by ronjjjg8885 on 2022-07-03
hi
i've two desktop computers and i want the to have a local network.
is there a good video or guide for how to do it securely?
tnx

---

### Post by TheFu on 2022-07-03
If you make Linux the "server", then you can load "ssh" on it and use winscp from Windows to transfer files. It may be possible to setup ssh-keys for authentication inside WinSCP. IDK.  

PuTTY has support for ssh-keys, but they use an odd format. PuTTY includes an scp tool ... pscp.exe I think. If putty has ssh-keys, then the pscp.exe and psftp.exe tool should be able to use those from the CLI. Yuck.

Or you can use the Win10 built-in ssh/scp/sftp clients in a CLI window, but the terminal that Windows provides sorta sucks.  They did include ssh-keygen which works just like the Unix version (with Windows file locations instead of Unix), but they didn't provide ssh-copy-id, so pushing the public key to the Linux ssh-server will be a hassle - like it was in the 1990s.

I've never seen a secure samba or CIFS connection.  I attempted to turn on encryption, but it didn't work.  [https://docs.microsoft.com/en-us/windows-server/storage/file-server/smb-security](https://docs.microsoft.com/en-us/windows-server/storage/file-server/smb-security) implies it is a Win11 or Windows Server 2022 only feature. 

Going the other way, to a Windows network share from Linux, I don't think it is possible for this to be secure, but that would depend on the CIFS libraries supporting the encryption that MSFT implemented.

Hopefully, someone who knows more will post how wrong I am and provide clear steps that work for all supported versions of Windows.

---

### Post by Morbius1 on 2022-07-03
What do you mean by "securely" ?

Do you mean requiring the passing of credentials to gain access to the share or are you talking about encrypted transport ( traffic encryption )?

And what version of Windows are you talking about.

---

### Post by ronjjjg8885 on 2022-07-05
i just mean a simple connection between them.
if anyone has a video i would like to know about it.
it's windwos 11

---

### Post by schwim-dandy on 2022-07-05
SAMBA would fit your needs perfectly.

[https://www.youtube.com/watch?v=675p5fuEQa4](https://www.youtube.com/watch?v=675p5fuEQa4)

---

### Post by TheFu on 2022-07-05
> **ronjjjg8885 said:**
> i just mean a simple connection between them.

That changes everything, by dropping "secure" from the list.  Linux can be the samba server and Windows the client.  Do it like 50 posts in these forums say for Win10. Morbius1 usually has the correct settings to the /etc/samba/smb.conf file in those posts.  

Going the other way (Win11 as the server), you'll want to use a CIFS mount in the fstab. Just this week, Morbius1 posts both a mount and an fstab line to make that happen.

If you want security, I think using something ssh-based is the easiest to implement solution.

---

### Post by Morbius1 on 2022-07-05
Samba seems the most appropriate here:

To connect to a Linux Samba share from Win11 configure samba on the Linux:

[1] Install samba:
```
sudo apt install samba
```
[2] Install WS-Discovery so your Win11 box can "discover" it from Explorer:
```
sudo apt install wsdd
```
[3] Make sure avahi is running - just in case:
```
sudo service avahi-daemon restart
```
[4] Edit /etc/samba/smb.conf and create a share definition of something simple first - like I did of my Public folder:

At the bottom of the smb.conf add a share definition:
```
[Public]
path = /home/morbius/Public
guest ok = no
read only = no
force user = morbius
```

Save smb.conf and restart samba:
```
sudo service smbd restart
```

[5] Add your user to the samba password database:
```
sudo smbpasswd -a morbius
```


Because of step [2] Win11 should be able to see it under Network in Explorer. When it asks for credentials add your Linux user name and samba password.

You can also state the network path explicitly in explorer:
```
\\linux-host-name.local\Public
```
*[COLOR="#0000FF"]Don't forget the ".local" at the end of the linux host name.[/COLOR]*

It's easy enough to enable encrypted transport to this setup but it will slow things down a bit since there is an encryption / decryption process that takes place. You may consider it unnecessary in a home network.

The other way around: connecting to a Win11 share from Linux is more problematic for a variety of reasons.

I recommend using "Connect to Server" in Nautilus to get to the Win11 share explicitly:

```
smb://win11-host-name.local/share-name
```

You can also force encrypted transport from the Linux client but it's best done with a cifs mount in my opinion. Actually, I prefer a CIFS mount period. I can show you how to do that if you want.

---

### Post by mIk3_08 on 2022-07-06
> **ronjjjg8885 said:**
> hi
i've two desktop computers and i want the to have a local network.
is there a good video or guide for how to do it securely?
tnx
If you are to transfer a small data/files. I prefer to use via internet and share. But If you have a bulk of data to transfer I prefer to use smb. Or use local sharing method using local handmade Linux server. This is fast too... I have try this one, without using this smb I only use local host to share data/files. My configuration involves databases. If you know about this, then it is very easy to you then. This can transfer a bulk of  data/file locally. Regards and cheers.

---

