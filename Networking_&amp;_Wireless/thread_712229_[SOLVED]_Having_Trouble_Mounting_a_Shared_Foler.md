---
title: "[SOLVED] Having Trouble Mounting a Shared Foler"
date: 2008-03-01
forum: Networking &amp; Wireless
---

### Post by Daniel591992 on 2008-03-01
Hi, I want to mount an external hard drive that is attached locally on my other computer. I am able to access it via:
```
smb://carolina-desktop/My%20Book/
```
And I want to mount it to:
```
/mnt/My Book
```
So I tried this:
```
sudo smbmount //carolina-desktop/My%20Book/ /mnt/"My Book"
```
And got this:
```
Could not resolve mount point /mnt/My Book
```
What is wrong?

I do not have a static IP address (I think) and I'm not sure if there is a username or password I need to enter.


Thanks :KS

---

### Post by kesomir on 2008-03-01
1. does /mnt/My Book exist?

2. try My\ Book (spaces can cause trouble - I see you have quotes, but need they be round the whole mount point?)

- also try that instead of the %20 for the space in the smb section

---

### Post by Daniel591992 on 2008-03-01
> **kesomir said:**
> 1. does /mnt/My Book exist?

2. try My\ Book (spaces can cause trouble - I see you have quotes, but need they be round the whole mount point?)

- also try that instead of the %20 for the space in the smb section

Hi, /mnt/My Book does not exist. Also, I'm pretty sure that I'm using the quotes the right way. I'm gonna try creating the dir and seeing what happens.

---

### Post by kesomir on 2008-03-01
aye - you need the dir to exist to mount to it
```

sudo mkdir /mnt/My\ Book
```

---

### Post by Daniel591992 on 2008-03-01
> **Daniel591992 said:**
> Hi, /mnt/My Book does not exist. Also, I'm pretty sure that I'm using the quotes the right way. I'm gonna try creating the dir and seeing what happens.

Alright, I just made the dir and tried this:
```
daniel@daniel-laptop:~$ sudo smbmount //carolina-desktop/"My Book" /mnt/"My Book"
```

Then it asks for password, and I put in my Ubuntu account pass.

Then I get this:
```
14769: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed
```

---

### Post by kesomir on 2008-03-01
progress - now it's rejecting your credentials.

Is there a password you use on the samba share from the other pc?

also try using the variant of //carolina-desktop/My%20Book/ that you can get to work by directly accessing it.

---

### Post by Daniel591992 on 2008-03-01
> **kesomir said:**
> progress - now it's rejecting your credentials.

Is there a password you use on the samba share from the other pc?

also try using the variant of //carolina-desktop/My%20Book/ that you can get to work by directly accessing it.

Alright, when it is asking for my password, I left it blank (don't remembering ever setting up one) and got:

```
Anonymous login successful
15824: tree connect failed: ERRDOS - ERRnosuchshare (You specified an invalid share name)
SMB connection failed
```

---

### Post by kesomir on 2008-03-01
You need to leave the password field blank then, and it's telling you that the 

```
//carolina-desktop/My%20Book/ 
```

part is wrong. I guess it's to do with the space. You could try renaming the share on the windows pc to remove it, or try different syntax on the ubuntu side.

You might need to ```
sudo apt-get install smbfs
``` or ```
sudo apt-get install cifs
```

you may also find this thread helpful:

[http://ubuntuforums.org/showthread.php?t=280473](http://ubuntuforums.org/showthread.php?t=280473)

---

### Post by dstew on 2008-03-01
Really, try to get rid of unusual characters in the file and directory names when using Samba, I was connecting using Samba over VPN and had a terrible time getting a directory listing until I removed a trademark symbol from a file name in the directory. Then everything went OK. But trying to quote and escape out funny characters will give you a headache.

---

### Post by Daniel591992 on 2008-03-01
> **kesomir said:**
> You need to leave the password field blank then, and it's telling you that the 

```
//carolina-desktop/My%20Book/ 
```

part is wrong. I guess it's to do with the space. You could try renaming the share on the windows pc to remove it, or try different syntax on the ubuntu side.

You might need to ```
sudo apt-get install smbfs
``` or ```
sudo apt-get install cifs
```

you may also find this thread helpful:

[http://ubuntuforums.org/showthread.php?t=280473](http://ubuntuforums.org/showthread.php?t=280473)

Got it! Thanks a lot. It was the damn spaces :P

Now how can I get rid of the first one. When i go to:
```
smb://carolina-desktop
```
I see "My Book" (the first) and MyBook.
It won't let me remove the first one. Is there a way of forcing it or maybe clearing the cache?

---

### Post by dstew on 2008-03-01
You should be able to delete the "My Book" shared folder in the Shared Folders window on your carolina-desktop server (System --> Administration --> Shared Folders). The other way would be to delete that share from the /etc/samba/smb.conf file on the server. Then restart samba (sudo /etc/init.d/samba restart) and it should be gone when you browse the server.

---

