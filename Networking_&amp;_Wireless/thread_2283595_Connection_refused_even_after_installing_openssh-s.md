---
title: "Connection refused even after installing openssh-server"
date: 2015-06-23
forum: Networking &amp; Wireless
---

### Post by James_Ko on 2015-06-23
I have been spending the last 4 hours trying to get my VNC connection to work. Eventually, I realized it was because my Ubuntu remote host was unable to host SSH connections- **even though I had already installed openssh-server**.

I then tried some basic tests to verify that sshd was working on my machine, and found that "ssh localhost" gives a "Connection refused on port 22" error. Also, "sudo service ssh start" and "sudo start ssh" both give a "start: Unknown job: ssh" error. I tried purging and reinstalling "openssh-server", but no luck. Why can't I receive clients?

**EDIT:** When I try to connect via the local machines (the VNC viewers) they give me a "Connection timed out" error.

---

### Post by Lars Noodén on 2015-06-23
Welcome.  

What version of openssh-server do you have installed?

```

apt-cache policy openssh-server

```

And is the configuration file ok?

```

/usr/sbin/sshd -T
```

---

