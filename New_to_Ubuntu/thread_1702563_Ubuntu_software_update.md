---
title: "Ubuntu software update?"
date: 2011-03-08
forum: New to Ubuntu
---

### Post by Learning Linux 2011 on 2011-03-08
When I first installed Ubuntu, the Software Update program said there were something like 10,000 programs available, but then the next time I opened it there were like 34,000 programs available.

At one point I went to a terminal and typed "sudo apt-get update" for something else.

Is that why there were suddenly more programs? Is that how you "refresh" Ubuntu Software Update?  Or was that just a coincidence?

I guess my basic question is:  How do i get the most up-to-date programs to appear in Ubuntu Software Update

---

### Post by mmsmc on 2011-03-08
terminal > sudo apt-get update
sudo apt-get upgrade

update manager > refresh > install

---

### Post by Learning Linux 2011 on 2011-03-08
What is the difference between "upgrade" and "update"?  Or is there a difference?

Do you have to type both or just one?

---

### Post by garvinrick4 on 2011-03-08
Look in:
```
gedit /etc/apt/sources.list
```
Every line without comment sign (#) is in play.
The more repositories you have open the more packages available.

---

### Post by garvinrick4 on 2011-03-08
update does just that updates your sources.list
upgrade does just that upgrades your packages to newest available.
```
sudo apt-get update && sudo apt-get upgrade
``````

```

---

### Post by mmsmc on 2011-03-08
thank you, that && was escaping me!! :)

---

