---
title: "Windows share in Ubuntu 8.10"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by melrokz on 2009-03-01
Hi. I've been trying to connect to a windows share via 'connect to server' option in the places menu, in Ubuntu 8.10. It only gives an error 'no application is registered for handling this kind of file'. Ubuntu 7.10 had no such problem. File sharing is over an ethernet connection and it is connected. In Windows, there seems to be no problem. What could be the problem here?

---

### Post by blueridgedog on 2009-03-02
Can you post the details that you use to enter into the "connect to server" box?  You can substitute fake data for any personal information.

Also, can you post the output of the command:
```

smbtree
```

As above, you can edit out any personal information or private information.

---

### Post by melrokz on 2009-03-04
I select 'windows share' and enter 192.168.0.2 in the 'server' box and press 'connect'. smbtree asks for my password and does not give any further output.

---

### Post by blueridgedog on 2009-03-05
From the output of smbtree, it is almost as if you the remote box is off.

---

