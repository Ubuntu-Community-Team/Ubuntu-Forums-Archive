---
title: "Help connecting to the internet"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by Schoales on 2009-03-23
I have Ubuntu installed and I open FIrefox but I am not connecting to my comcast router. How do I get to the internet?

---

### Post by bodhi.zazen on 2009-03-23
I moved this to a support forum.

What hardware are we talking here ? wireless ? wired ?

---

### Post by Schoales on 2009-03-23
I have wireless

---

### Post by sandyd on 2009-03-23
> **Schoales said:**
> I have wireless
```

sudo lspci

```

type that in the terminal
post the result here

---

### Post by Schoales on 2009-03-23
> **carlee said:**
> ```

sudo lspci

```

type that in the terminal
post the result here
Where is the terminal?

---

### Post by nothingspecial on 2009-03-23
In your menu - accessories > terminal

Also, you don`t have to sudo it, ```
lspci
``` will do

---

### Post by Schoales on 2009-03-23
> **nothingspecial said:**
> In your menu - accessories > terminal

Also, you don`t have to sudo it, ```
lspci
``` will do
I did that and found my network was listed as disabled. I looked for network manager under system>admin>network, but I have network tools, not network, in the dropdown menu.

---

### Post by Schoales on 2009-03-23
> **Schoales said:**
> I did that and found my network was listed as disabled. I looked for network manager under system>admin>network, but I have network tools, not network, in the dropdown menu.
I typed in lspci and got a long list of bridge, bus, modem, controller, etc info

---

### Post by Schoales on 2009-03-23
> **Schoales said:**
> I typed in lspci and got a long list of bridge, bus, modem, controller, etc info
I also tried iwconfig and got an ESSID=""  and tried the help link, which said WPA Support is integrated with Network Manager, which I can't find.

---

### Post by sandyd on 2009-03-23
> **Schoales said:**
> I typed in lspci and got a long list of bridge, bus, modem, controller, etc info
were actually looking for your network controler hardware info

post it.

---

### Post by nothingspecial on 2009-03-24
Type ```
lspci
``` again and copy and paste the output in a new post here.

---

