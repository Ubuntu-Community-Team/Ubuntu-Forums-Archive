---
title: "rsync intermittent failures"
date: 2019-12-17
forum: Networking &amp; Wireless
---

### Post by spjackson on 2019-12-17
As per [this thread]("https://ubuntuforums.org/showthread.php?t=2406083") I am backing up a website using rsynch thus:
```
rsync -avz --copy-links user@some-ftp.site.com: . 
```
Intermittently it fails with:
```

receiving file list ... Write failed: Broken pipe

rsync: connection unexpectedly closed (0 bytes received so far) [Receiver]
rsync error: unexplained error (code 255) at io.c(226) [Receiver=3.1.1]

```
When it succeeds, it takes roughly 40 minutes. When it fails, it takes 2 hours 11 mins (always) and the error message is as above (always). The pattern over the last 10 nights has been:
Success, Success, Fail, Success, Success, Success, Fail, Success, Fail, Fail.

Sometimes it might work 7 nights in a row, or fail for 3 or 4 in a row. Are there any suggestions that might help me reduce the failure rate? I have no control over the remote system's configuration.

---

### Post by TheFu on 2019-12-17
Is the connection working through an ssh connection?  ssh has been the default mode for network-ed rsync for a long time.
Check the stability of the local network --> internet  and likewise the remote server network --> internet.
Some firewalls will close connections after 60 minutes.  I've come across this in a corporate setup when they added a firewall rule to disconnect connections after 24 hrs without asking anyone.  Some of our servers were in different network zones based on risk mitigation efforts.  In the software, we had to setup a keep-alive setting from the client to the server.  ssh has this as an option, controllable by the client.

---

### Post by spjackson on 2019-12-19
@TheFu Thanks for your reply. Yes it is ssh. Your suggestions are worth looking into - I will do this.

---

