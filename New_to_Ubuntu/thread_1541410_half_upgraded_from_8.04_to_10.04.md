---
title: "half upgraded from 8.04 to 10.04"
date: 2010-07-29
forum: New to Ubuntu
---

### Post by byenary on 2010-07-29
Hello,

I have upgrade a 8.04 server to a 10.04 halfway the process it went wrong, had to reinstall python etc...
Eventually i managed him to continue, restarted do-release-upgrade --proposed again without errors.

Now I end up with a system wich is pretty much okay execpt.
-On the server itself im no longer prompted a promt, the last entry shown while booting is starting apache2 (I checked apache and its running.
I can log in to the machine using ssh so I can still use it but a local prompt could come in handy at some point.
-When i check /etc/issue it's still mentioning 8.04

Any suggestions how should fix this ?

---

### Post by SpockVulcan on 2010-08-02
I never really liked the way ubuntu does their releases and allows in OS rolling updates. A lot can go wrong with this method as you can see firsthand. I think the best thing for you to do is to backup everything and then reinstall

Here is a great backup tool to use. Just backup your home folder and software selection to removable media, install the backup tool on your next install of ubuntu and restore

[http://j.mp/cALCEa]("http://j.mp/cALCEa")

---

### Post by Frogs Hair on 2010-08-02
There are a few notes about 8.04 to 10.04 sever upgrades here.  [http://www.ubuntu.com/desktop/get-ubuntu/upgrade](http://www.ubuntu.com/desktop/get-ubuntu/upgrade)

---

