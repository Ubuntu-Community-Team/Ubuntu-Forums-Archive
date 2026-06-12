---
title: "How do I disable my nic's?"
date: 2008-02-01
forum: Networking &amp; Wireless
---

### Post by Mr.Johnny on 2008-02-01
Hi! I am running a machine for multimedia purposes, and I would like to disable the nic's, to see if I can stop the pops and clicks in the audio.

How do I do that? Do I have to edit some file and comment it or something?

thanks.

---

### Post by patryk77 on 2008-02-01
```
sudo ifconfig eth0 down
```

or whatever your interfaces are called...

Just running sudo ifconfig with no arguments will give you a list.

---

### Post by Mr.Johnny on 2008-02-01
thanks, it worked, but once I restart the machine they're on again... How to make it permanent?

---

### Post by scxtt on 2008-02-01
sudo vi /etc/network/interfaces

remove the "auto eth#" for the device you don't want up at boot.

---

### Post by Mr.Johnny on 2008-02-02
done ;) thanks a lot.

---

