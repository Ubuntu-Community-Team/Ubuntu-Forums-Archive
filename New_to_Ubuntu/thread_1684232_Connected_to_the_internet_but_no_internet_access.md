---
title: "Connected to the internet but no internet access?"
date: 2011-02-08
forum: New to Ubuntu
---

### Post by rom3lol on 2011-02-08
I installed guarddog as my firewall about 2 days ago and removed the program that same day. After that I can't access the internet?

I tried ping and wget and this is what I get:

```
ping www.google.com
ping: unknown host www.google.com

```

```
wget www.google.com
wget: unable to resolve host address www.google.com

```

---

### Post by M0use on 2011-02-08
Do you get a connection to your modem?
Check 


```

ifconfig

netstat

```

---

### Post by thefasterblueone on 2011-02-08
Try deleting the configuration files using this command:

```
sudo apt-get remove --purge guarddog
```

---

### Post by jd2012 on 2011-02-08
For some reason I have trouble using the ping command when adding "www." to the front of the address, try:

```

ping google.com

```

---

### Post by rom3lol on 2011-02-09
@M0use yes I do get connection through the modem.

JD2012 ```
ping google.com
``` gives me the exact same output as before but thank you.

> **thefasterblueone said:**
> Try deleting the configuration files using this command:

```
sudo apt-get remove --purge guarddog
```

Thanks alot bro this worked exquisitely :popcorn:
And thank you everyone else :D

---

