---
title: "Send a test mail using Telnet"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by karthick87 on 2010-10-24
I was trying to send a test mail using telnet function,but i was not able to do it..I get the following error...

```
karthick@Ubuntu-desktop:~$ telnet localhost smtp
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
Connection closed by foreign host.

```

---

### Post by lisati on 2010-10-24
Try this and let us know how you get on:
```
telnet localhost 25
```

---

### Post by karthick87 on 2010-10-24
> **lisati said:**
> Try this and let us know how you get on:
```
telnet localhost 25
```

```
karthick@Ubuntu-desktop:~$ telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
Connection closed by foreign host.

```

---

### Post by stmiller on 2010-10-24
Do this:

```
sudo dpkg-reconfigure postfix
```

And choose internet site.

[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

---

### Post by karthick87 on 2010-10-24
> **stmiller said:**
> Do this:

```
sudo dpkg-reconfigure postfix
```And choose internet site.

[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)


I have choosen internet site still i get the same error..

---

