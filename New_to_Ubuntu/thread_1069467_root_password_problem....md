---
title: "root password problem..."
date: 2009-02-14
forum: New to Ubuntu
---

### Post by Leo Dragonheart on 2009-02-14
I tried to log into my root terminal w/su and it asks for the password, I type in the only one that I know I have but it tells me Authentication Failed. Any suggestions?

---

### Post by aloshbennett on 2009-02-14
I hope you have administrator previlages (System -> Admin -> users and groups -> your user -> properties -> previlages)

---

### Post by Leo Dragonheart on 2009-02-14
Yea I am the only one that uses this computer and it did have the Administrate the System box checked....;(

---

### Post by stumbleUpon on 2009-02-14
> **Leo Dragonheart said:**
> I tried to log into my root terminal w/su and it asks for the password, I type in the only one that I know I have but it tells me Authentication Failed. Any suggestions?

Its not 'su' to go to the root terminal, but 'sudo su' and then your passwd.

---

### Post by Leo Dragonheart on 2009-02-14
Thank you it worked just fine. I was following these instructions. I wonder why they did not include the sudo part...huh.

```
 To install the Linux (self-extracting) file

Follow these instructions:

   1. At the terminal: Type:
      su
   2. Enter the root password.

```

---

### Post by stumbleUpon on 2009-02-14
this might clarify

[http://fosswire.com/2008/02/03/sudo-vs-su/](http://fosswire.com/2008/02/03/sudo-vs-su/)

---

### Post by Leo Dragonheart on 2009-02-14
Ahhhh thank you now I understand....

---

