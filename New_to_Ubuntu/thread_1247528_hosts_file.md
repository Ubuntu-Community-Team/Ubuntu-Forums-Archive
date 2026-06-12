---
title: "hosts file"
date: 2009-08-23
forum: New to Ubuntu
---

### Post by loosescrew on 2009-08-23
I would like to update my host files. I have been reading thru the security section and came across this.[http://hostsfile.mine.nu/downloads/updatehosts.sh.txt](http://hostsfile.mine.nu/downloads/updatehosts.sh.txt) Do i just copy and paste this code into terminal ? Thanks Joe

---

### Post by k3lt01 on 2009-08-23
I uses [this]("http://www.mvps.org/winhelp2002/hosts.txt") copying it from the webpage and then pasting it into my hosts file. There is a procedure to do this and you need to be sure you follow it or you could cause other problems.

1. Cut and paste this into your terminal

```
 gksudo gedit /etc/hosts
```

2. There are a few lines already in the hosts file.

```
127.0.0.1	localhost
127.0.1.1	michael-laptop

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

These lines MUST be left there and anything else must be placed after these lines.

3. Now copy and paste the contents on the page in the link above AFTER the lines already in the hosts file. 

4. Now save the file and you should be done.

---

### Post by loosescrew on 2009-08-23
Thanks k3lt01.

---

