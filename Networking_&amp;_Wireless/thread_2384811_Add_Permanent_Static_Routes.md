---
title: "Add Permanent Static Routes"
date: 2018-02-12
forum: Networking &amp; Wireless
---

### Post by rockygunner on 2018-02-12
I am very new in ubuntu. 

I tried to add static routes but everytime VM restarts it is gone.

I have two LAN cards. 

I want to route traffic as 

all traffic from 192.168.5.0 will go through gateway 192.168.230.233 
and all other traffic through gateway 192.168.200.1

i edited /etc/network/interfaces as the pic but internet does not work. 

[ATTACH=CONFIG]278499[/ATTACH]

any help will be appreciated. Thanks

---

### Post by TheFu on 2018-02-12
Which release of Ubuntu?  Server or Desktop?  Networking has changed a few times since 12.04, so how it is done changes.

For 16.04, 14.04 the manpage for the interfaces file has all the options spelled out. Just restart networking after any change to see the updates.  SystemD doesn't always handle network restarts correctly for non-trivial stuff, IME.  Sadly. 17.10 change networking config again - I haven't any clue about it since I only run LTS versions.

Images aren't efficient. Use sftp/scp/putty/ssh ... anything into the VM to copy/paste text easily.  Text is vastly preferred here to be nice to people who pay by the byte.

---

