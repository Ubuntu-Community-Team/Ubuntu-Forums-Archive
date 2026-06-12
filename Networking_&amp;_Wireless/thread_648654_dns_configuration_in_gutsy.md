---
title: "dns configuration in gutsy"
date: 2007-12-23
forum: Networking &amp; Wireless
---

### Post by bc040401056 on 2007-12-23
hi
what is the method for configuring dns in gutsy??????????????????????????

---

### Post by scxtt on 2007-12-23
put your dns server(s) in /etc/resolv.conf

search <searchdomain.com>
nameserver x.x.x.x

---

### Post by bc040401056 on 2007-12-23
if it was easy than y i ask for help please tell me all the steps like u teach a young kid

---

### Post by scxtt on 2007-12-23
sudo vi /etc/resolv.conf
(this will allow you to edit resolv.conf)

type **i** to go into insert mode

-- make your changes --

hit escape

type :wq
(this will write the changes and quit vi)

---

### Post by grainbarcelona on 2007-12-24
even easier: simply go to system --> administration --> network. Select your connection; click on the dns tab, and there you are....

---

### Post by burbankmarc on 2007-12-24
easiest way:

```

sudo -s
echo "nameserver *your.dns.ip.here*" >> /etc/resolv.conf

```

---

### Post by bc040401056 on 2007-12-24
Hi
Sorry i went for sleep and i have solved this problem and i heartily thanks to all ppl who help me and warm wishes to them well can someone tell me after scanning ports what to do with that information

---

