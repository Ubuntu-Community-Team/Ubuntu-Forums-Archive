---
title: "Ubuntu 14.04 SSH server issue"
date: 2015-11-30
forum: Networking &amp; Wireless
---

### Post by chris382 on 2015-11-30
I'm running Ubuntu 14.04 LTS on a chromebook using crouton and while trying to get my ssh server up and running i come across this error during the installation.. after entering this command ```
sudo apt-get install openssh-server
```
"runlevel:/var/run/utmp: No such file or directory
invoke-rc.d: policy-rc.d denied execution of stop.
start: Unknown job: ssh" 
Anything i can do to solve this and maybe an explanation? Thank you.

---

### Post by mitch_feaster on 2015-12-14
I have the same problem with crouton on a chromebook.  Apparently [the utmp error messages are normal]("https://github.com/dnschneid/crouton/issues/1438").  As far as I can tell job management doesn't work at all in crouton, but you can start sshd with:

```

sudo mkdir -pv /var/run/sshd
sudo /usr/sbin/sshd

```

---

