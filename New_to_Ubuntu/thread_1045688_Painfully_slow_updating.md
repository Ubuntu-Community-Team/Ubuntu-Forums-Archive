---
title: "Painfully slow updating"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by Orangefromwin on 2009-01-20
Hey guys, I just got Ubuntu, and I have a full slate of downloads to get (200+ updates in the update manager) but my problem is the updates take extremely long to download. Whenever it decides to show my dl rate it is in the bytes! I downloaded some stuff from firefox and I don't have the same issue. This could take me several days to get everything downloaded as I run different OSes most of the day. Am I alone here? Is there a way to speed up these updates?

---

### Post by taurus on 2009-01-20
Are you using the Canadian server?

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```
Go into System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and switch to another server.  Use the US or even the Main Server.  Don't forget to click the Reload.

---

### Post by Orangefromwin on 2009-01-20
I went into System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and did as you said, and saw that my server was United States. So I decided to switch to the main server, but when I did reload the download package was going in the bytes, so I cancelled and went back to the US server and even thought the reload went fast my updates are still going at an extremely slow rate, if going at all.

---

### Post by Orangefromwin on 2009-01-21
Ok I went into more detail and picked out a better US server. I downloaded 150+ updates in about 5 minutes. Thanks!

---

