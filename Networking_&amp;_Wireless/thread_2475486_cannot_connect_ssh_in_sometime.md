---
title: "cannot connect ssh in sometime"
date: 2022-05-29
forum: Networking &amp; Wireless
---

### Post by chat-4432 on 2022-05-29
it shows this message sometimes I try to connect to ssh
```
connect failed ECONNREFUSED (Connection refused)
```
what should I do??

---

### Post by TheFu on 2022-05-29
Check the remote system for firewall rules, network connectivity issues.
Depending on what is between the client and the server, any point in that chain can be failing.  Could be a bad cable anywhere in between, but that's unlikely if only ssh is impacted.

From the client, you can ask for more information.
```
$ ssh -vvvv userid@server
```
will show lots more verbose output that can help determine what the issue actually is.

---

