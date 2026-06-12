---
title: "SSH drops connect after X bytes/rows"
date: 2016-01-06
forum: Networking &amp; Wireless
---

### Post by snakyjake on 2016-01-06
Problem:
SSH terminates connection after so many bytes/rows are transferred.

Situation:
Remote into server with SSH using PuTTY.
Transfer <1000 rows from the console, and SSH will terminate the connection (example apt-get update).
Same problem if transfer small byte size file.
Reproduceable.
Problem only occurs with a transfer, not time limit.  Connection stays connected regardless of time, only on data transfer.
Everything was working good for months.  Problem started late 1/5/2016 or early 1/6/2016.
Client reports error:  FlowSocketReader: Error receiving bytes.  Windows error 10054.  An existing connection was forcibly closed by the remote host.  Read error from remote host.
No errors found in router.
Not seeing any SSH errors in /var/log

Suggestions?

Ubuntu 15.10

UPDATE 1:
It appears to have been a problem with my Windows client firewall.  Running the command below seems to have resolved the issue:
```
netsh advfirewall set global statefulftp disable
```

Thanks,
Jake

---

