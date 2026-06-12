---
title: "None of my programs are opening"
date: 2010-01-23
forum: New to Ubuntu
---

### Post by lolzwut on 2010-01-23
I decided to change my terminal prompt name, so as root I did nano /etc/hostname, changed my name and then switched back to my other account, closed the terminal then I tried to open it to see if it worked and it just says "Starting terminal" in the task bar but then it fails to open. The same thing happens for every other thing I try to open that wasn't already opened. Can someone please tell me how to fix this? I assume it has to do with me editing /etc/hostname right? Thanks.

---

### Post by bogdan.veringioiu on 2010-01-23
If you change the hostname, make sure that you change also /etc/hosts, to match your new host name.
You should have some entries in /etc/hosts similar to this:
> 127.0.0.1	localhost
127.0.1.1	<your_host_name>
Modify the second entry to match /etc/hostname entry.
Then restart the computer.
Let me know if it works for you.

---

### Post by lolzwut on 2010-01-23
What do I use to modify that? I can't open any text editors or my terminal, so how would I go about doing that?

---

### Post by d3v1150m471c on 2010-01-23
load into safe mode and see if you can fix this.

---

### Post by lolzwut on 2010-01-23
It worked, all I had to do was restart, I didn't wanna do it at first though because my computer also has windows on it, and they often time don't mix when you shut linux down improperly causing one of them to not boot up. Anyway thanks.

---

