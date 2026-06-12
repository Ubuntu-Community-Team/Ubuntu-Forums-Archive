---
title: "update information out dated"
date: 2009-09-19
forum: New to Ubuntu
---

### Post by djyoung4 on 2009-09-19
i have 9.04 and i get a caution symbol in my alerts panel that says my system is outdated.  when i go to update i get an error that says it cannot connect to the GPL.  im sorry i dont have the error.  i cant copy and paste it for some reason.

---

### Post by bodyharvester on 2009-09-19
any chance of a screenshot of the error?

thanks

---

### Post by djyoung4 on 2009-09-22
GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DCF9F87B6DFBCBAEGPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991GPG error: [http://deb.opera.com](http://deb.opera.com) lenny Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F9A2F76A9D1A0061GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7889D725DA6DEEAAGPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9BF3BB4E5E17B5GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 632D16BB0C713DA6GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 28A8205077558DD0GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2ED6BB6042C24D89GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FC6D7D9D009ED615GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 66D5C734F6EFB904GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6E871C4A881574DEGPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4FEC45DD06899068GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6298AD34413576CBGPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7FB8BEE0A1F196A8GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D79F61BE8D31A30GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D739676F7613768DFailed to fetch [http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages](http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages)  404 Not Found [IP: 204.9.165.83 80]
Failed to fetch [ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/binary/Packages](ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/binary/Packages)  Unable to fetch file, server said 'Failed to open file.  '
Failed to fetch [ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/source/Sources](ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/source/Sources)  Unable to fetch file, server said 'Failed to open file.  '
Some index files failed to download, they have been ignored, or old ones used instead.

that is the error
i included a screenshot.  if you look it says it hasn't been updated in 29 days but i updated today.  im kinda confused

---

### Post by MelDJ on 2009-09-22
no pub key means you must add the gpg key. watch this video: [http://blog.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu](http://blog.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu)

---

### Post by Zoot7 on 2009-09-22
Try out the script that's posted here:
**[http://ubuntuforums.org/showthread.php?t=1056099]("http://ubuntuforums.org/showthread.php?t=1056099")**
It'll automatically update outdated keys and repos.

---

### Post by ajithsen on 2009-10-30
Read [https://answers.launchpad.net/ubuntu/+question/73171](https://answers.launchpad.net/ubuntu/+question/73171).
This explains how to add a public key.
Very useful, worked for me in Jaunty.

---

