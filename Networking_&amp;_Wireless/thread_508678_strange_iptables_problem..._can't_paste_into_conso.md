---
title: "strange iptables problem... can't paste into console?"
date: 2007-07-24
forum: Networking &amp; Wireless
---

### Post by Underpants on 2007-07-24
OK. I'm new to iptables, so stick with me.

I'm wanting to input two lines:
```

iptables –I INPUT –p tcp –-dport 22 –j DROP
iptables –I INPUT –s xxx.xxx.xxx.xxx –p tcp -–dport 22 –j ACCEPT

```

I have them saved in a document so I can reference them... If i hand type each line, iptables accepts them without err. If I copy and paste them into the console OR run them in a .sh script... I get the following output. 

```

root@chips:/home/aaron# iptables –I INPUT –p tcp –-dport 22 –j DROP
Bad argument `–I'
Try `iptables -h' or 'iptables --help' for more information.

```

What in the world is going on?

---

### Post by Koybe on 2007-07-24
I'm not sure, I haven't used it for a long time but I think -I, is for Insert and so you need to tell where you are inserting the rule.

If you simply want to add a new rule at the end, you should use -A.

For what I remember briefly ;)

---

