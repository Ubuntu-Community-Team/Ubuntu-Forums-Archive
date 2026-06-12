---
title: "unable to add computers to my /etc/hosts"
date: 2008-02-13
forum: Networking &amp; Wireless
---

### Post by jeeves on 2008-02-13
I'm trying to save myself time typing IP addresses by adding the IP address and the names  of computer on my network to my ** /etc/hosts** file. All the computers on my network have static IPs, so I added the following to my hosts file:
```

xx.xxx.xx.xx  computer1
yy.yyy.yy.yy  computer2
```
*of course I used real IP address instead of xx.xxx.xx.xx & yy.yyy.yy.yy in the actual host file.*

The problem is that is does not work. Even  with these additions I  can't ping or ssh into these computers.

So running** ping computer1** will produce nothing. Same goes for running** ssh    me@computer1**

Any idea what could be going wrong? I did reboot the computer after editing the hosts file.

---

### Post by jetsam on 2008-02-13
Two possibilities:

1.) Check that your hosts hasn't been overwritten.  **cat /etc/hosts** is probably the quickest way to check.  

2.) What's the output of 
```
cat /etc/nsswitch.conf | grep hosts
```

"files" should be the first item on the list after "hosts:" to ensure that the host file is checked before other types of name service lookups.  

Mine reads:
```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4

```
Yours may be slightly different depending on your set-up.

---

