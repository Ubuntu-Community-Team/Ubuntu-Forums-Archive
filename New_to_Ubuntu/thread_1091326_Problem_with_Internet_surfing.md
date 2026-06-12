---
title: "Problem with Internet surfing??"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by karan virdi on 2009-03-09
i hav recently installed ubuntu on my desktop as a 2nd OS next to windows.............now i am facing a problem .... i am using a BSNL internet connection.......now i have entered the username and password settings in the DSL connections.....now when i switch on my modem it detects it and after sometimes it shows "connected to etho" but i delete this connection and it asks for the default password i enter it and then it shows"connected to the mentioned user name" which means now my internet connections is activated....but when i click on the firefox icon it just opens up ans shows address not found.....i hav also untick the work offline option but it still doesn't work??............the mian thing is that i am not able to surf the net while my internet connection is working......

---

### Post by Mark Phelps on 2009-03-09
When you get the "connected to" popup, don't delete it -- that is your network connection.  The specification of eth0 merely indicates the first "wired" network, as opposed to wlan0 which would indicate the first wireless network.

---

### Post by karan virdi on 2009-03-11
ok ,,i hav done this way also but it doesn't yield any result........i am still getting the "adress not found error".....i am completely lossed now

---

### Post by Mark Phelps on 2009-03-13
Sorry ... don't have a solution.  Suggest you visit the Networking subforum.  They have some pinned posts dealing with networking problems.

---

### Post by Peter09 on 2009-03-13
can you post the output of the terminal commands

```
ifconfig
```
and
```
lshw -C network
```

Note that you can make the output into a file by doing for example

```
ifconfig > ifconfig.txt
```

this will put the output into a file called ifconfig.txt in your home directory.

---

