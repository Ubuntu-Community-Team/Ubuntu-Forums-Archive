---
title: "[SOLVED] Define new DNS servers"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by pshootr on 2008-12-11
I have used "vi /etc/resolv.conf " And I get "/etc/resolv.config" [New File]" So the field is empty exept for the mentioned message. So how do I enter my dns info? I get a beep when I press any key.

---

### Post by kpkeerthi on 2008-12-11
Use 'nano' or 'gedit' to edit the file
```
sudo nano /etc/resolv.conf
```
or
```
gksudo gedit /etc/resolv.conf
```

---

### Post by hyper_ch on 2008-12-11
and the entry would be
```

nameserver  xxx.xxx.xxx.xxx

```
where xxx.xxx.xxx.xxx would be the ip address.

---

