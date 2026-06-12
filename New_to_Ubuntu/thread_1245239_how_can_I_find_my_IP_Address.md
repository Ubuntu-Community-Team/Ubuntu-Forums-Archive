---
title: "how can I find my IP Address?"
date: 2009-08-20
forum: New to Ubuntu
---

### Post by concerto on 2009-08-20
[SOLVED]

Is their something I can type into the terminal to find what my IP Address is?

I am hooked up to a router and I'm not looking for the routers address, If that makes any sense at all.

Thank you so much for your time.
Let me know if your need more information from me to solve this.
Thanks again

---

### Post by Keith Hedger on 2009-08-20
```
ifconfig
```

---

### Post by fooman on 2009-08-20
in a terminal:

```
ifconfig
```

but that may only yield the address assigned from the router....so from firefox,  go to this address:

[http://www.whatismyip.com/](http://www.whatismyip.com/)

hope that helps.

---

### Post by credobyte on 2009-08-20
```
curl www.whatismyip.org

```

Take a look at aliases ( bash ) - might be easier :)

---

### Post by philinux on 2009-08-20
curl needs installing first. ;)

---

### Post by concerto on 2009-08-20
OK.  I did it!  Thanks to everyone here everything is working fine!
You guys are awesome!
Now where is the mark thread as solved button?????

---

### Post by philinux on 2009-08-20
> **concerto said:**
> OK.  I did it!  Thanks to everyone here everything is working fine!
You guys are awesome!
Now where is the mark thread as solved button?????

Not available any more. Was causing database problems.

---

### Post by Paddy Landau on 2009-08-20
> **concerto said:**
> Now where is the mark thread as solved button?
It broke (seriously).

[LIST]
[*]Go to your first post.
[*]Select Edit.
[*]Select Go Advanced.
[*]Add [Solved] in front of the title.
[*]Save.
[/LIST]

---

### Post by bubbles1991 on 2013-02-13
Thanks [fooman]("http://ubuntuforums.org/member.php?u=229348"),
I don't have experience about that site.
Personally i use [ip-details.com]("http://www.ip-details.com/")  Here i found external ip.

---

### Post by matt_symes on 2013-02-13
Old thread. Closed

---

