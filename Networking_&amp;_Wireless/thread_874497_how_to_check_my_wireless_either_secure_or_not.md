---
title: "how to check my wireless either secure or not?"
date: 2008-07-30
forum: Networking &amp; Wireless
---

### Post by ding dong bell on 2008-07-30
hi
i want to ask how can we test our own network whether it's secure or not so that we can detect our wireless network weakness.

everyone,if u have any idea..please tell me.thanks a lot:)

---

### Post by lisati on 2008-07-30
_Disclaimer:_ I am not an expert on Ubuntu or security.


[LIST=1]
[*]You might want to check out [http://ubuntuforums.org/showthread.php?t=765421](http://ubuntuforums.org/showthread.php?t=765421) which has a couple of suggestions for checking for security vulnerabilities
[*]MAC filtering or WEP encryotion on their own are probably not a good idea.... If you *must *use one of them, use it in combination with something else.
[/LIST]

---

### Post by jimv on 2008-07-30
Enable WPA or preferably WPA2, put in a decent passPHRASE (the longer the better...something like "ilovemymombecauseshebakedme12cookies" would be great), and rest well knowing that your wifi is pretty darned secure.

If you wanted to go all out, you could do some kind of certificate based authentication.

---

### Post by trigsenior on 2008-07-30
> how can we test our own network whether it's secure or not

[http://ubuntuforums.org/showthread.php?t=528276](http://ubuntuforums.org/showthread.php?t=528276)

good guide to cracking into a network if you really do want to test ..

---

### Post by ilrudie on 2008-07-30
If security is important I would say your best bet is to treat your wireless network as if it is not secure and make sure you have good application security.  Assume it is insecure and force people to use things like ssh instead of telnet and scp instead of ftp.  Perhaps even firewall off the wireless vlan of your network only allowing the few select protocols that are secure and necessary.  Just my thought on it.

---

