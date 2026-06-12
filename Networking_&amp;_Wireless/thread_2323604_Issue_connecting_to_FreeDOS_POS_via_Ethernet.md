---
title: "Issue connecting to FreeDOS POS via Ethernet"
date: 2016-05-06
forum: Networking &amp; Wireless
---

### Post by Lizzy_Coles on 2016-05-06
In my store our POS (tills) run FreeDOS, there are specialized POS machines from IBM. The ones with no screen, just the 50-key keyboard with the 2 line LCD on it.

There running a custom made POS software, that's about 20 years old, but it works and is solid. 

We've updating our PCs from Windows XP to Lubuntu, and I just updated my Office PC (a Dell Optiplex 390) and I try to connect to our main till ([http://192.168.1.17:5045](http://192.168.1.17:5045)) and it doesn't connect, but if I just go out and try it on a different machine, It works fine. 

I can get online to the internet, hence writing this but it doesn't want to connect to this internal site. I can't figure out why?

Do you have any ideas as to why this isn't working?

---

### Post by SeijiSensei on 2016-05-06
Are your client machines also on the 192.168.1.0/24 network?  If not, can we see the results of the command "route -n" (in [noparse]```

```[/noparse] tags) on the non-working machine?

Can you ping the POS machine ("ping 192.168.1.17")?

---

### Post by Lizzy_Coles on 2016-05-09
> **SeijiSensei said:**
> Are your client machines also on the 192.168.1.0/24 network?  If not, can we see the results of the command "route -n" (in [noparse]```

```[/noparse] tags) on the non-working machine?

Can you ping the POS machine ("ping 192.168.1.17")?


Hi SeijiSensei,

Thanks for your reply. 

All of the machines are connected to the same router through either a HP 48 port switch or a TPLink 8 port Gigabit switch in the office, both switches' go into the Network router which is from our ISP, made by Cisco.

I run the command from both my office PC and from another office PC (running Windows XP) and they both went through fine.

I also, tried connecting to a different POS machine and it didn't load either (address 192.168.1.31:5045)

---

### Post by Lizzy_Coles on 2016-05-09
Screenshot of the error message

---

### Post by SeijiSensei on 2016-05-09
That's pretty uninformative.  Can you ping the machine?

---

