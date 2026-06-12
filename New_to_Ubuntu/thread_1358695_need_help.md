---
title: "need help"
date: 2009-12-18
forum: New to Ubuntu
---

### Post by Chloekpb on 2009-12-18
yea im trying to install libnet on my cpu  (iMAC OSx 10.6) and this is the error that i get at the end 



make[3]: Nothing to be done for `install-exec-am'.
/bin/sh ../../mkinstalldirs /usr/include/libnet
mkdir /usr/include/libnet
mkdir: /usr/include/libnet: Permission denied
make[3]: *** [install-libnetincludeHEADERS] Error 1
make[2]: *** [install-am] Error 2
make[1]: *** [install-recursive] Error 1
make: *** [install-recursive] Error 1


any ideas

---

### Post by Some Penguin on 2009-12-18
Ask yourself whether the account you're using to execute whatever command you just run actually has the privileges to create the directory mentioned in the error message.  If not, ask yourself which account actually does.

---

### Post by Chloekpb on 2009-12-22
IM in my admin acount im the only user on this cpu nad i dont know what other permissons i would need

---

