---
title: "firefox ssh ubuntu server"
date: 2009-11-30
forum: New to Ubuntu
---

### Post by jpr13 on 2009-11-30
I have ubuntu-server running in a VM on my home computer and Xubuntu running on a laptop. I am able to ssh in with Putty and sftp in with filezilla from remote locations, but I can't seem to get Firefox to work with foxyproxy/putty to send my web traffic to my home box.

It was working before, but now it won't. The ssh tunnel works, firefox just won't see the web.

HELP! 

Thanks,
Jason

---

### Post by bsharp on 2009-11-30
Connect to your ssh box with the -D option to specify dynamic forwarding, e.g:

```
ssh -D *port* *yourserver*
```

I don't know how to set up foxyproxy or putty for this but it should be configured to use SOCKSv5 protocol on the port you specified (usually 1080).

edit:[This]("https://help.ubuntu.com/community/SSH/OpenSSH/PortForwarding#Introduction") will help you.

---

