---
title: "Mount Network Drive"
date: 2009-10-11
forum: New to Ubuntu
---

### Post by Jason Cook on 2009-10-11
I have been searching for about 30-45 minutes trying to find out how to do this. I want to mount smb://okwaho/dvddrive/ so I can can use it in wine. If their is a way to do this without restarting because I am installing the item I need the CD for. I am using a netbook (no CD Drive) so I need to use the drive over the network.
    
    What I have done:
    ```
sudo mkdir /media/DVD
```Add ```
//OKWAHO/DVDDrive  /media/DVD  cifs  guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0
```to /etc/fstab.
  ```
sudo mount -a
```
and recieve this error:
```
mount error: could not resolve address for Okwaho: No address associated with hostname
No ip address specified and hostname not found
```Any ideas?

---

### Post by falconindy on 2009-10-11
use OKWAHO.local, the IP (if static).

---

### Post by Jason Cook on 2009-10-11
> **falconindy said:**
> use OKWAHO.local, the IP (if static).
So should I change ```
sudo mkdir /media/DVD
```Add ```
//OKWAHO/DVDDrive  /media/DVD  cifs  guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0
```
to
```
sudo mkdir /media/DVD
```Add ```
//OKWAHO.local/DVDDrive  /media/DVD  cifs  guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0
```

---

### Post by falconindy on 2009-10-11
You've got it right. There should be an 'or' somewhere in my last post. Samba uses a derivative of Bonjour, which is used to keep track of LAN clients by name. Unlike Windows, which uses NetBIOS, you need the .local suffix on the computer name to identify it.

OKWAHO.local should be valid for pinging, tracing, whatever... if you're concerned about testing it before you go mindlessly throwing it into your /etc/fstab, you can use ```
smbclient -L OKWAHO.local
``` to test connectivity. If it works, you'll be prompted with a password, which you can leave blank to connect anonymously.

---

### Post by Jason Cook on 2009-10-11
> ```
smbclient -L OKWAHO.local
``` to test connectivity. If it works, you'll be prompted with a password, which you can leave blank to connect anonymously.
When I do what via the terminal I get this error:
```
Connection to OKWAHO.local failed (Error NT_STATUS_BAD_NETWORK_NAME)
```but I can access it via nautilus

---

### Post by falconindy on 2009-10-11
What's the output of `mount` after you connect to it via Nautilus? Might give us some insight into how to "properly" refer to it...

---

### Post by Jason Cook on 2009-10-11
> **falconindy said:**
> What's the output of `mount` after you connect to it via Nautilus? Might give us some insight into how to "properly" refer to it...

I think that this is what you are referring to.
```
smb://okwaho/dvddrive/
```

---

### Post by falconindy on 2009-10-11
Nah. I was thinking that once FUSE mounts the drive, you could pop up a terminal and post the output from the `mount` command. The fact that you're able to resolve the DNS name "okwaho" in Nautilus but not elsewhere is a tad bit perplexing.

---

### Post by Jason Cook on 2009-10-12
> **falconindy said:**
> Nah. I was thinking that once FUSE mounts the drive, you could pop up a terminal and post the output from the `mount` command. The fact that you're able to resolve the DNS name "okwaho" in Nautilus but not elsewhere is a tad bit perplexing.
I don't think I understand. In the terminal am I supposed to type:
```
mount smb://okwaho/dvddrive/
```When I do get this error:
```
mount: can't find smb://okwaho/dvddrive/ in /etc/fstab or /etc/mtab
```

---

### Post by Jason Cook on 2009-10-15
bump

---

