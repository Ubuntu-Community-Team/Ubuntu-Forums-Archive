---
title: "SSH: Does local port-forwarding with SSH have a timeout?"
date: 2014-08-24
forum: Networking &amp; Wireless
---

### Post by godzig2 on 2014-08-24
I've got a port forwarded for some remote mysql work via:
```
ssh -L 3307:127.0.0.1:3306 me@someplace.com -N 
```

I've also got some nightly python scripts that depend on this port being open to perform their magic, but somehow the port is not always forwarding. In the absence of better information about exactly why it's failing, I've scoured the docs for mention of a timeout on a local port forward -- not seeing anything.

Is there a timeout on these forwards -- or some other relevant setting I'm missing?
Perhaps there is some other chaos monkey that you'd suggest investigating? 

Thanks.

---

### Post by gordintoronto on 2014-08-24
Port forwarding is usually a router thing. Perhaps that is where you need to look?

---

### Post by papibe on 2014-08-24
Hi godzig2.

There are ssh timeouts, and tcp timeouts. If you are trying to keep the connection alive, thus the forwarded port open, I recommend both taking a look at the ssh options, and also thinking in a script that can take care of a lost connection.

This [thread]("http://ubuntuforums.org/showthread.php?t=1861143&highlight=rsync+internet+dhcp") has a similar concern, and it may point you in the right direction (note that rsync runs over ssh in this example).

Hope it helps. Let us know if that helps.
Regards.

---

### Post by Lars Noodén on 2014-08-25
> **godzig2 said:**
> Is there a timeout on these forwards -- or some other relevant setting I'm missing?


There is a timeout on SSH if there is no activity.  As pabibe suggests, look at the options for ssh_config, specifically the [ServerAliveInterval and ServerAliveCountMax](http://manpages.ubuntu.com/manpages/trusty/en/man5/ssh_config.5.html) options.  You can test them by adding them to the runtime arguments:

```
ssh -L 3307:127.0.0.1:3306 **-o ServerAliveInterval=60** me@someplace.com -N 
```

Then if that does what you want, you can make it default for your user's client configuration by editing ~me/.ssh/config

```

Host someplace.com
  ServerAliveInterval 60

```

---

