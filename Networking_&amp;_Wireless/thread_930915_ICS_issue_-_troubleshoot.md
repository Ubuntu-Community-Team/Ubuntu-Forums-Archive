---
title: "ICS issue - troubleshoot"
date: 2008-09-26
forum: Networking &amp; Wireless
---

### Post by wdypdx1 on 2008-09-26
Hi,

I set up ICS yesterday between 2 'buntu boxes using this doc,

[https://help.ubuntu.com/community/Internet/ConnectionSharing#Advanced%20Gatway%20Configuration](https://help.ubuntu.com/community/Internet/ConnectionSharing#Advanced%20Gatway%20Configuration)

It worked like a charm once I figured out there was a typo on my part.

Problem is that I get up today and the ICS set-up seems to have disappeared. The ICS was working last night; and today after powering up both machines, it's not. 

Any tips on how to troubleshoot this? I'll probably redo the Gateway and client ICS set-up, but I want it to stick around when I turn my computers on and off.

The hardware setup is:

<<Internet>><Wireless-router><Ubuntu 8.04><Wired-to-HUB-wired-to><Xubuntu 8.04>

The wireless part is fine. Just the gateway and client part isn't working any more.

Thanks

---

### Post by cariboo on 2008-09-26
Check to see if dnsmasq was started when you restarted the computer:

```
ps ax | grep dnmasq
```

should give you an output something like this:

```
19955 ?        Ss     0:00 dnsmasq
19957 pts/0    R+     0:00 grep dnsmasq
```

If it hasn't started automatically, you can use update-rc.d to start dnsmaq at start up eg:

```
sudo update-rc.d dnsmasq start 30 2 3 4 5 . stop 70 0 1 6 .
```

For more on update-rc.d see:

```
man update-rc.d
```

Jim

---

### Post by wdypdx1 on 2008-09-27
Thanks, but I hadn't gotten to the Advanced Gateway Configuration part of that tutorial yet. I was going to do that today and then discovered that what I had done yesterday didn't save after powering off the computers. 

wdy

---

