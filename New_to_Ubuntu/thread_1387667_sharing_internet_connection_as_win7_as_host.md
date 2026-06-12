---
title: "sharing internet connection as win7 as host"
date: 2010-01-22
forum: New to Ubuntu
---

### Post by bibas on 2010-01-22
Hi, i have a modem connected to a windows 7 computer and i want to share that connection with ubuntu 9.10 computer which also has win7 installed in it.
I could do that easily between win7 - win7 via a ad hoc connection. but when i try to connect to win7 host via ubuntu it only shows the name of the wireless adhoc but cannot connect.
please help.(noob in linux):(

---

### Post by cariboo on 2010-01-22
Internet connection sharing is pretty easy, just make sure that the shared network, is in a different netblock from the connection to the internet. eg:

If your Win & ip address is 192.168.0.100, the ad hoc network should be in the 192.168.1.0/24 range.

To setup an ad hoc network have a look [here]("https://help.ubuntu.com/community/WifiDocs/Adhoc").

---

