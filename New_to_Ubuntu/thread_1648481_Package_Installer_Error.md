---
title: "Package Installer Error"
date: 2010-12-18
forum: New to Ubuntu
---

### Post by Ellume on 2010-12-18
I'm trying to install a .deb file but when it runs the package installer it gives me the error: ```
Error: Dependency is not satisfiable: libmodplug1
```I went to look up libmodplug1 and I installed "libmodplug-dev" and I already have "libmodplug0c2" installed but can't see any "libmodplug1". I still get the same error so I'm kinda clueless as what to do next.

---

### Post by oldos2er on 2010-12-18
Which version of Ubuntu are you using? Have you run ```
sudo apt-get update
``` lately?

---

### Post by Ellume on 2010-12-18
I'm running Ubuntu 10.10. I ran "sudo apt-get update" and then "apt-cache search libmodplug" but it still lists only the two I have and then something called "cmus" which it says is just some lightweight audio player. 

The program I'm trying to install is called LÖVE, and there is a older version in the Ubuntu Software Center, but I'm trying to install the new version. Someone at the LÖVE forum said they had the same problem and said they added the PPA to their sources list. I'm looking up stuff on PPA now, but I still haven't figured out what that all means.

---

### Post by Ellume on 2010-12-18
Alright I found info on installing PPA at [https://launchpad.net/+help/soyuz/ppa-sources-list.html](https://launchpad.net/+help/soyuz/ppa-sources-list.html)

So I added the PPA, then did another "sudo apt-get update" then "apt-get install love" and it looks like I have the most recent version! So I think this problem is now solved :D

Thanks for your help! ^_^

---

### Post by oldos2er on 2010-12-18
I'm running 10.10, and I see libmodplug1 in the main repository. Not sure why it's not showing for you.

You can find it here: [http://packages.ubuntu.com/maverick/libmodplug1](http://packages.ubuntu.com/maverick/libmodplug1)

---

