---
title: "Regex help"
date: 2010-04-22
forum: New to Ubuntu
---

### Post by TurnOfTide on 2010-04-22
I have a log file with various statements in it. Each statement is either:

DEBUG
INFO
WARN
ERROR


I want to obtain all lines that do not contain DEBUG. (note: not every line has a level statement, for example: )

java.net.NoRouteToHostException: No route to host
    at java.net.PlainSocketImpl.socketConnect(Native Method)
    at java.net.PlainSocketImpl.doConnect(PlainSocketImpl.java:333)
    at java.net.PlainSocketImpl.connectToAddress(PlainSocketImpl.java:195)
    at java.net.PlainSocketImpl.connect(PlainSocketImpl.java:182)
    at java.net.SocksSocketImpl.connect(SocksSocketImpl.java:366)
    at java.net.Socket.connect(Socket.java:525)


Which is why I really need a match on NOT DEBUG.

---

### Post by kvsm on 2010-04-22
grep -v DEBUG logfile

---

### Post by TurnOfTide on 2010-04-22
:popcorn:

---

