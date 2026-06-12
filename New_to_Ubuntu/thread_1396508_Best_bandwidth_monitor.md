---
title: "Best bandwidth monitor?"
date: 2010-02-02
forum: New to Ubuntu
---

### Post by keymoo on 2010-02-02
Hi there,

I have a headless Ubuntu Server used as a firewall/router and I'm looking to monitor one of the interface's bandwidth usage. I'd ideally like a web front end so I can look at it through a browser from my desktop. Would like it to store up to a year's history. Any suggestions for something simple?

Thanks,
keymoo

---

### Post by NickJones on 2010-02-02
System->Adminstration->System Monitor-> Network
Shows all uploaded and downloaded in current session, as for you WebIF,
TightVNC has a web interface :-)
Nick

---

### Post by keymoo on 2010-02-02
Nick, thanks but I'm using a headless Ubuntu Server.

---

### Post by amauk on 2010-02-02
have a look at munin (it's in the repos)

System info graphing tool (web based)
comes with lots of plugins by default (and the ability to write your own)

google image search for "munin" to get an idea of what info you'll get

---

### Post by lotharmat on 2010-02-02
vnstat is quite good - can be tricky if you are moving between wireless networks though as I have found out. but in a pretty static situation it works well.

Not too sure about a web-frontend though..

maybe you could build one

---

### Post by ayenack on 2010-02-02
webmin is good for this. It's not only for this, it's really more of an admin tool but can be used for this. I use it on my servers. There're more apps in the repo's just type in admin in synaptic.

Here's a tutorial on setting up webmin.

[http://www.ubuntugeek.com/webmin-installation-and-configuration-in-ubuntu-linux.html](http://www.ubuntugeek.com/webmin-installation-and-configuration-in-ubuntu-linux.html)

BTW:- If you have ssh setup on the server then you could just install bmon

```
 sudo apt-get install bmon
```

Brilliant little app for monitoring bandwidth but not sure it keeps logs. It's run in terminal just type bmon.

Here's a list of bandwidth monitors for Ubuntu.

[http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-ubuntu-users.html](http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-ubuntu-users.html)

[http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html](http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html)

---

### Post by superprash2003 on 2010-02-02
phpsysinfo too gives you the information of interface usage , the best part is that it displays all this info in one single page making it easier to read and access [http://www.prash-babu.com/2010/02/phpsysinfo-get-important-information.html](http://www.prash-babu.com/2010/02/phpsysinfo-get-important-information.html)

---

