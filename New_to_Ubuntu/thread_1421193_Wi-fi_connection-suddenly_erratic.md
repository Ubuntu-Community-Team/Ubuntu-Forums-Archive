---
title: "Wi-fi connection-suddenly erratic?"
date: 2010-03-03
forum: New to Ubuntu
---

### Post by D1Knight on 2010-03-03
Hello.:) My wi-fi connection is suddenly and randomly becoming erratic? Does this indicate some kind of attack? Thanks for the help.:)

---

### Post by undecim on 2010-03-04
What do you mean?

Are you having stability problems? (i.e. connection keeps dropping)

If you think it's an attack, check your router's logs. Also, make sure you have WPA (NOT WEP!) encryption with AES (NOT TKIP!)

---

### Post by D1Knight on 2010-03-04
> **undecim said:**
> What do you mean?

Are you having stability problems? (i.e. connection keeps dropping)

If you think it's an attack, check your router's logs. Also, make sure you have WPA (NOT WEP!) encryption with AES (NOT TKIP!)

Hi undecim.:)Thanks for your response. My puter at home, wireless connection is WEP. The location of computer, I tend to average 70-75% strength (could be stronger, but don't want to move the location-for now). 

About every hour or two, wireless connection gets erractic (bouncing around-like it is about to drop) 37%-50% and lasts about 10-15 minutes. Noob question: How/where do I check the router logs?

---

### Post by undecim on 2010-03-04
> **D1Knight said:**
> How/where do I check the router logs?

It depends on the router. My router is a Linksys, and I can get to mine via Administration -> Log, but your mileage may vary.

Also, you may need to turn logging on manually. If so, turn it on, wait for your router to go erratic again, then check the logs.

Relatedly, what kind of wireless card do you have? Typing "lspci | grep Wireless" into a terminal should give you the details on that.

---

### Post by D1Knight on 2010-03-06
> **undecim said:**
> It depends on the router. My router is a Linksys, and I can get to mine via Administration -> Log, but your mileage may vary.

Also, you may need to turn logging on manually. If so, turn it on, wait for your router to go erratic again, then check the logs.

Relatedly, what kind of wireless card do you have? Typing "lspci | grep Wireless" into a terminal should give you the details on that.

Hi undecim.:)Thank you very much for the advice.

In answer to your question, it came up as Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05).
Have a good one.:)

---

