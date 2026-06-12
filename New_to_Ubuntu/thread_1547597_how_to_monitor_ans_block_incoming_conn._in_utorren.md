---
title: "how to monitor ans block incoming conn. in utorrent"
date: 2010-08-06
forum: New to Ubuntu
---

### Post by fremantle on 2010-08-06
im using utorrent under wine and i need to block utorrent/wine from accepting incoming connections. i know it can be done in windows firewall. how can i do it in ubuntu??

---

### Post by bodhi.zazen on 2010-08-07
To answer your question, open a terminal and enter:

```
sudo ufw enable
sudo ufw default deny
```

Why utorrent ? There are several linux native clients available. If you like small and light weight , try rtorrent .

---

### Post by fremantle on 2010-08-07
> **bodhi.zazen said:**
> To answer your question, open a terminal and enter:

```
sudo ufw enable
sudo ufw default deny
```Why utorrent ? There are several linux native clients available. If you like small and light weight , try rtorrent .

thnx but can u explain what the commands do?

*i need ut for a specific reason. in linux i prefer Deluge better.

---

### Post by Elmer Fudd on 2010-08-07
> **fremantle said:**
> thnx but can u explain what the commands do?

*i need ut for a specific reason. in linux i prefer Deluge better.

First enables the firewall.
Type "man ufw" in a terminal and look at the "default" and "deny" and "rule syntax" for further explanations.

---

