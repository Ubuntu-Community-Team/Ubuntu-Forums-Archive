---
title: "Tor and SSH Tunneling"
date: 2008-09-19
forum: Networking &amp; Wireless
---

### Post by sinclair86 on 2008-09-19
I've seen it done where ssh to remote machine [which has tor installed] to tor to web. I was wondering if there was any way to go from tor to ssh to remote machine to web. I understand that regardless of what I do the remote server will still be able to see my traffic un-encrypted I just dont want websites to know who I am.

---

### Post by Crafty Kisses on 2008-09-19
Not sure what you're asking but you can create a Tunnel like this:
```
ssh -D 9999 -C me@ipaddress.com
```

---

### Post by sinclair86 on 2008-09-19
Sorry posted that late last night after trying to figure it out. Im on wireless so I use ssh tunneling to computer 2 for browsing. Now I also have tor installed as well. How can I get tor to go through the tunnel. does it have to be on the other end (computer 2) for it to work so that not only is my traffic is encrypted but im anonymous as well..

---

