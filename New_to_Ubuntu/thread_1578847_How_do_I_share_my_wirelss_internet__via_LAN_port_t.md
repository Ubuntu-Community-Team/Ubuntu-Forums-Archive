---
title: "How do I share my wirelss internet  via LAN port to other PC"
date: 2010-09-21
forum: New to Ubuntu
---

### Post by Ducatiboy Stu on 2010-09-21
Running Ubuntu 10.04, I want to share my wireless conection via the LAN port to another PC that does not have wireless conection

Eth0 is my LAN port

Eth1 is my inbuilt wireless port


Yes I do have a cross over LAN cat 5 cable...

---

### Post by sikander3786 on 2010-09-21
I have used [Firestarter]("https://help.ubuntu.com/community/Firestarter") to serve the purpose in past. I think its development is stopped for now but it is still available in the repos and still in a good working condition.

Also see post # 9 in the following thread. The OP got it working with a few clicks without any additional software. I haven't tested but it should work.

[http://ubuntuforums.org/showthread.php?p=9788453](http://ubuntuforums.org/showthread.php?p=9788453)

---

### Post by 3rdalbum on 2010-09-21
Connect to your wireless. Set up a new connection in Network Manager that uses your Ethernet port, and in the IPv4 tab of the Properties, choose "Shared to other computers". Choose "Connect Automatically". Delete all other Ethernet connections and plug in the cable and that's it.

---

