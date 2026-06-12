---
title: "Secure Ubuntu from Remote Access thru SSH"
date: 2007-07-17
forum: Networking &amp; Wireless
---

### Post by textguru on 2007-07-17
I have setup an ubuntu server that has two network card, one connected to a lan and one connected to the internet. I have activated ssh server so I may access it thru my lan. My question is, is it possible for me to block ssh access thru my internet lan?

---

### Post by Peter76 on 2007-07-17
You can set ssh to only listen on your lan; edit your sshd.conf and look for #ListenAddress. Now after this line add:

ListenAddress  your.lan.ip.address

and then restart the ssh server; it now only listens on the ip specified by you

---

### Post by textguru on 2007-07-17
> **Peter76 said:**
> You can set ssh to only listen on your lan; edit your sshd.conf and look for #ListenAddress. Now after this line add:

ListenAddress  your.lan.ip.address

and then restart the ssh server; it now only listens on the ip specified by you
thanks for the reply. where can I find the sshd.conf?

---

### Post by meierfra on 2007-07-17
> /etc/ssh/sshd_config


The fastest way to find files is to use  "slocate". For example 

```

:~$ slocate sshd

/etc/ssh/sshd_config
/usr/lib/codecs/vsshdsd.dll
/usr/lib/win32/vsshdsd.dll
/usr/sbin/sshd
/usr/share/man/man5/sshd_config.5.gz
/usr/share/man/man8/sshd.8.gz
/usr/share/vim/vim70/syntax/sshdconfig.vim

```

only takes about a second.

---

### Post by textguru on 2007-07-17
> **meierfra said:**
> The fastest way to find files is to use  "slocate". For example 

```

:~$ slocate sshd

/etc/ssh/sshd_config
/usr/lib/codecs/vsshdsd.dll
/usr/lib/win32/vsshdsd.dll
/usr/sbin/sshd
/usr/share/man/man5/sshd_config.5.gz
/usr/share/man/man8/sshd.8.gz
/usr/share/vim/vim70/syntax/sshdconfig.vim

```only takes about a second.
thanks :KS

---

