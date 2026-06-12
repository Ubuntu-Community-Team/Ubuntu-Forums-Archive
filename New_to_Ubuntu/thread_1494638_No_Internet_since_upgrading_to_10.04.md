---
title: "No Internet since upgrading to 10.04"
date: 2010-05-27
forum: New to Ubuntu
---

### Post by greensbohemian on 2010-05-27
I've been using Ubuntu since Hardy. and this is the first time I have a problem I just can't find the answer to.  When I first upgraded, I had the common problem of the disappearing network icon on the header bar.  I tried all the suggestions I found, but none worked.  This didn't bother me, though, because the Internet was still functional.  A couple days later, though I can't remember making any changes to the computer, the Net just refused to work.  If I try to open a page in Firefox it gets past the "Looking up..."  but halts on the "Connecting to..."  I dual boot, and can access everything with Windows no problem.  Same with my netbook, which is still running 9.10.  Any ideas?

P.S.  I apologize if my problem is already covered in the forums.  I always do a search first, but if there's info there that can help I overlooked it.  Thanks!

---

### Post by cariboo on 2010-05-27
It sounds like you may have a DNS problem. You can set DNS manually by right-clicking the network manager icon and selecting Edit Connections. Highlight your network device, then click the edit button, next click the IPv4 tab and select in the method drop-down Automatic (DHCP) addresses only, enter the DNS addresses provided by your ISP, then click apply, enter your password, and restart networking, either by rebooting, or opening a terminal and typing:

```
sudo service networking restart
```

---

