---
title: "Can't forward Port 25 via ssh"
date: 2006-07-23
forum: Networking &amp; Wireless
---

### Post by cmfarley19 on 2006-07-23
Hi all.

I wrote a script to forward ports via ssh
```
#!/bin/bash sudo ssh -p 443 -L 5906:192.168.0.101:5900 -L 26:pop.mailserver.com:25 -L 112:smpt.mailserver.com:110 uname@192.168.0.163
```


When I try to send mail from thunderbird on port 26 I get the following message:
```
channel 7: open failed: administratively prohibited: open failed
```


This worked fine in breezy.

Any thoughs?

---

### Post by cylon359 on 2006-07-24
Are you sure it worked in breezy?

Port 25 is a restricted port (< 1024), so only root can bind to it.

---

### Post by cmfarley19 on 2006-07-24
I'm positive it worked in breezy.

Note that the ssh command has a sudo in front of it and I am prompted for a password for sudo as well as for ssh.

---

### Post by harisund on 2006-07-24
Try doing

```
sudo sh -c "ssh -p 443 -L 5906:192.168.0.101:5900 -L 26:pop.mailserver.com:25 -L 112:smpt.mailserver.com:110 uname@192.168.0.163"
```

Basically added a sh -c and enclosed everything following that within quotes. 

Can you see if this works?

---

### Post by cmfarley19 on 2006-07-24
I'll give that a shot later tonight and report back.

Thanks,

Chris

---

### Post by cmfarley19 on 2006-07-24
OK... Ijust gave that a shot.  It had the same results.

Any other ideas?

Could it be some kind of default firewall settings thing?

Chris

---

