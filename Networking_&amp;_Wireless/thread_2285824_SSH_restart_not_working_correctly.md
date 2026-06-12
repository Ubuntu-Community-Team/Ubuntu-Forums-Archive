---
title: "SSH restart not working correctly?"
date: 2015-07-08
forum: Networking &amp; Wireless
---

### Post by Growlizing on 2015-07-08
I was doing some configuring remotely at work to a ubuntu computer.

I executed this, and continued working on what I was gonna test:

```

# service ssh restart
ssh stop/waiting
ssh start/running

# 

```

I have used Linux for many, many years, including this type of configuration for ssh.

To my great fear, the connection of course reset (!) and when I tried connecting again: Connection refused.
Oh crap.

I can't login to the server with SSH anymore, so I'm guessing the config somehow was bad.

BUT WHY DID IT NOT TELL ME?!

The output above looks perfectly fine to me even now...

I would expect the restart to FAIL if the config is bad, or am I just really, really stupid?

Please can anyone help? =)

---

