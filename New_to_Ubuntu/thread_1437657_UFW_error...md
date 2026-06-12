---
title: "UFW error.."
date: 2010-03-24
forum: New to Ubuntu
---

### Post by karthick87 on 2010-03-24
I have enabled UFW in my machine,it shows the following error...What it mean and how can i resolve it?

```

karthick@Learners-desktop:~$ sudo ufw enable
ERROR: Couldn't stat '/etc/ufw/after6.rules'
```

---

### Post by karthick87 on 2010-03-26
Bump..

---

### Post by philinux on 2010-03-26
```
sudo ufw status
```

---

### Post by karthick87 on 2010-03-27
```
karthick@Learners-desktop:~$ sudo ufw status
ERROR: Couldn't stat '/etc/ufw/after6.rules'

```

---

### Post by gmargo on 2010-03-27
Is the **/etc/ufw/ **directory empty, or is just the one file missing?

The **ufw** package includes default versions of rules files in the **/usr/share/ufw/** directory.  So try:
```

sudo cp -p /usr/share/ufw/after6.rules /etc/ufw/

```and now see if "sudo ufw status" works.

---

### Post by karthick87 on 2010-03-27
```
karthick@Learners-desktop:~$ sudo cp -p /usr/share/ufw/after6.rules /etc/ufw/
karthick@Learners-desktop:~$ sudo ufw status
ERROR: Couldn't stat '/etc/ufw/before6.rules'

```

---

### Post by gmargo on 2010-03-27
And.....?  What happens when you take the next obvious step?

---

### Post by karthick87 on 2010-03-27
I got the same error., No change :(

---

### Post by gmargo on 2010-03-27
> **getyourkarthick said:**
> I got the same error., No change :(
That can't be right.  Show what you did, and what the error was.

---

