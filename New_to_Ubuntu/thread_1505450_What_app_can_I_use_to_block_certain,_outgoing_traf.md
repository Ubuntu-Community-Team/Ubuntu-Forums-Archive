---
title: "What app can I use to block certain, outgoing traffic"
date: 2010-06-09
forum: New to Ubuntu
---

### Post by YosefKaro on 2010-06-09
I just discovered that I am part of a botnet and I want to block outgoing traffic on port 6667.  The program that I know (gufw) will block all outgoing traffic but then I will have to make rules for all of my internet apps.  I'd rather just block a few outgoing ports.  Is this possible?

-Yos

---

### Post by qamelian on 2010-06-09
You don't need to set rules for each application. You set the rules for each port. IN the case you describe, it should be as easy as:
```
ufw deny out 6667
```

If you read the man page for ufw in a terminal, you'll see other possible options, as well.
```
man ufw
```

---

