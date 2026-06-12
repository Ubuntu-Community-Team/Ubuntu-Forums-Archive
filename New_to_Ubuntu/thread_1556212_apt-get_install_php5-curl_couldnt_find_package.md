---
title: "apt-get install php5-curl couldnt find package"
date: 2010-08-19
forum: New to Ubuntu
---

### Post by Michaelc-2010 on 2010-08-19
Hi,

when i try : apt-get install php5-curl 
I get 
Reading package list done
building dependency tree
reading state information tree done
E: could not find package php5-curl

now the network is working I have ubuntu server 32bit running on a lan and it can communicate with the outside world as i tried a ping to a google ip address
can you help

Regards
Michael

---

### Post by themusicalduck on 2010-08-19
All I can think of is to try running ```
sudo apt-get update
``` first.

If that hasn't been run yet since the OS was installed then it won't be able to find anything.

---

### Post by Rushyang on 2010-08-19
May be you need to add it's repository. ( I don't know whether this package is available by default or not)

---

