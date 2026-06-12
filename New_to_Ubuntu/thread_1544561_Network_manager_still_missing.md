---
title: "Network manager still missing"
date: 2010-08-02
forum: New to Ubuntu
---

### Post by tweety_r78 on 2010-08-02
I run the Ubuntu 10.04 Lucid, and I have managed to unistall (and obviously removed) the network manager. I have now found both the network manager 0.8 and the gnome network manager (through another computer) and installed them. But the network-manager is still not working. I would be extremely happy if someone could help me fix this:).

---

### Post by ubudog on 2010-08-02
Type this into a terminal.
```
ps ax | grep NetworkManager
```

Post the output here.

---

### Post by tweety_r78 on 2010-08-02
> **ubudog said:**
> Type this into a terminal.
```
ps ax | grep NetworkManager
```
 
Post the output here.
 
Hi.
 
When I run this I get:
 
696 ?          Ss   0:00 NetWorkManager
1237 pts/0  S+   0:00 grep --color=auto NetWorkManager

---

### Post by jtarin on 2010-08-02
Try ```
sudo NetworkManager
```

---

### Post by tweety_r78 on 2010-08-02
> **jtarin said:**
> Try ```
sudo NetworkManager
```
 
When I type this I get that the Network Manager is allready running

---

### Post by ubudog on 2010-08-02
But it doesn't show up on your panel?  Try this:
```
killall gnome-panel
```

---

### Post by tweety_r78 on 2010-08-02
> **ubudog said:**
> But it doesn't show up on your panel? Try this:
```
killall gnome-panel
```
 
nope, sorry... that didn't work either. the panel stayed the same...

---

