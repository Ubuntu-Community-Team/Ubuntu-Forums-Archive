---
title: "Trying to install FTP server stuck on first step!"
date: 2009-09-19
forum: New to Ubuntu
---

### Post by arpalermo on 2009-09-19
Hi all,

I'm trying to setup an FTP server with ubuntu. I was trying to use VSFTPD but i cannot install it. 

When i type "sudo apt-get install vsftpd" in console it tells me "E: Couldn't find package vsftpd"

How can i install vsftpd? I tried downloading it from there site, but i don't know what to do with the folder i got :(

---

Also, if i setup an FTP server on a linux machine, will windows machines be able to access files from it?

---

### Post by dearingj on 2009-09-19
Try this:
```
sudo apt-get update
sudo apt-cache search vsftpd
```

The first of those commands is to ensure that your computer has the latest package information available, and the second will search through said information for packages related to vsftpd. I suggest you install any packages you find.

---

### Post by seshomaru samma on 2009-09-19
> Also, if i setup an FTP server on a linux machine, will windows machines be able to access files from it? 
yes

---

### Post by arpalermo on 2009-09-19
Updated and now it works. Thanks!

---

### Post by talsemgeest on 2009-09-19
> **arpalermo said:**
> Also, if i setup an FTP server on a linux machine, will windows machines be able to access files from it?
Yes, as long as the windows machine is able to connect to the server. For example, you can connect on the LAN, but not from the net (unless you set up port forwarding.)

---

### Post by dearingj on 2009-09-19
Good to hear it's working :)

---

