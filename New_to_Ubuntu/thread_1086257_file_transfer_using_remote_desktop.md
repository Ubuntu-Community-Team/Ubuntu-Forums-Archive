---
title: "file transfer using remote desktop"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by championboxes on 2009-03-03
Currently I have an older desktop computer running xubuntu with no monitor/keyboard/mouse hooked to it and the way I access it is with my much faster ubuntu laptop thats in the other room using vino... is there a simple way to take files from the desktop and put them on my laptop and vice-versa without setting up a FTP?  Something like a right click and on the drop box say sendto->remote desktop?

---

### Post by ddixonr on 2009-03-03
Read this SSH How to: [https://help.ubuntu.com/community/SSHHowto]("https://help.ubuntu.com/community/SSHHowto")

---

### Post by asmoore82 on 2009-03-03
> **ddixonr said:**
> Read this SSH How to: [https://help.ubuntu.com/community/SSHHowto]("https://help.ubuntu.com/community/SSHHowto")

+1 ...

in a nutshell, install the `openssh-server` package and
then under GNOME "Places -> Connect to Server -> Service Type: SSH" will "Just Work!"

and bonus - it's all secure and encrypted

---

### Post by championboxes on 2009-03-03
> **ddixonr said:**
> Read this SSH How to: [https://help.ubuntu.com/community/SSHHowto]("https://help.ubuntu.com/community/SSHHowto")

Thanks this should help and with using SSH I should be able to connect from anywhere as long as I know the IP?

---

### Post by bodhi.zazen on 2009-03-03
> **championboxes said:**
> Thanks this should help and with using SSH I should be able to connect from anywhere as long as I know the IP?

As long as the ssh port is forwarded from your router.

If you are going to connect over the internet be sure to secure your ssh server.

[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

If you are connecting from a windows box, take a look at winscp (a gui front end)

---

### Post by ddixonr on 2009-03-03
Adding to asmoore82, you can do this from any file browser window under 'file' as well. You can choose to save your password when logging on, and then bookmark it, so it just becomes another folder in your 'places'. This will save some time entering ip addresses and such.

---

