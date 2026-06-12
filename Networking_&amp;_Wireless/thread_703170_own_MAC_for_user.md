---
title: "own MAC for user"
date: 2008-02-21
forum: Networking &amp; Wireless
---

### Post by vvitt on 2008-02-21
Hi folks,

I've a problem and NO idea how to handle it. I'm building an small internet-cafe with 3 stations for the members of a club. All should run on Ubuntu 6.06. One Station is a new computer. The others are thin clients (LTSP). For the accounting we use an external service via a WRT54GL router and chilipod. And there starts the problem:
The accounting is done via the mac-address. After a logon the mac of a client computer is give access to the internet. But, with my thin client solution, each of the three stations is using the same mac = the mac of the server. The result is net access to all three sation as soon as one of them is using a correct account.
Has anybody of you an idea how to handle this? Maybe an own tap device (with it's own mac) for each user is a possibility.
I would be happy about any help, link or howto.

thx, vvitt

---

### Post by nixscripter on 2008-02-21
Let me make sure I have this right:

```

  _______
 /       \
 |Internet|
 \_______/
    |
    |
    |
    V
+---------+
| Router  |
+---------+
    |
    |                   +-------------+
    |               +-->| Thin Client |
    V               |   +-------------+
+------------+      |
| Fat Client |      |   +-------------+
| Has Acct   |<-------->| Thin Client |
+------------+      |   +-------------+
                    |
                    |   +-------------+
                    +-->| Thin Client |
                        +-------------+

```

If that's all, then you should just set up the fat client as an NAT router That will have it retransmit all of the thin client's packets as itself, using its MAC address. There are tutorials on how to do that that are too long for me to post. Try this:

[http://ubuntuforums.org/archive/index.php/t-91370.html](http://ubuntuforums.org/archive/index.php/t-91370.html)

Hope that helps.

---

### Post by matey3 on 2008-02-21
wow pretty darn cool :)



> **nixscripter said:**
> Let me make sure I have this right:

```

  _______
 /       \
 |Internet|
 \_______/
    |
    |
    |
    V
+---------+
| Router  |
+---------+
    |
    |                   +-------------+
    |               +-->| Thin Client |
    V               |   +-------------+
+------------+      |
| Fat Client |      |   +-------------+
| Has Acct   |<-------->| Thin Client |
+------------+      |   +-------------+
                    |
                    |   +-------------+
                    +-->| Thin Client |
                        +-------------+

```

If that's all, then you should just set up the fat client as an NAT router That will have it retransmit all of the thin client's packets as itself, using its MAC address. There are tutorials on how to do that that are too long for me to post. Try this:

[http://ubuntuforums.org/archive/index.php/t-91370.html](http://ubuntuforums.org/archive/index.php/t-91370.html)

Hope that helps.

---

### Post by vvitt on 2008-02-23
@nixscripter
That's exactly what I'm trying to do. The thin clients are planned as stupid terminals. They just show the picture from the fat client. This means the browser is running on the fat client. Hopefully, my English is good enough to make my problem clear. But I will check that tutorial and will write about the success.

---

