---
title: "Clear all iptables information"
date: 2020-10-30
forum: Networking &amp; Wireless
---

### Post by mspichty on 2020-10-30
Hi, all,

I am using iptables under Ubuntu 18.04. For some reason I have some entries in my iptables that I cannot get rid off.
I tried:

1) iptables-restore < iptables.backup

(where  iptables.backup does not contain these entries)

2) apt-get remove iptables
   apt-get install iptables

(magically the unwanted entries are still there....)

Could someone point me out where iptables stores this metadata under Ubuntu 18.04?
Help would be really appreciated!!

Best,
Martin

---

### Post by mspichty on 2020-10-30
OK, I found the solution:

[COLOR=#000000]apt-get remove iptables
reboot[/COLOR] 
[COLOR=#000000]apt-get install iptables[/COLOR]
[COLOR=#000000] iptables-restore < iptables.backup[/COLOR]

---

### Post by SeijiSensei on 2020-10-30
I thought you just wanted to remove the rules in memory. For future reference you can use

```
sudo iptables -F
```

to remove all the rules. See "[man iptables]("https://linux.die.net/man/8/iptables")" for details.

---

### Post by SeijiSensei on 2020-10-30
I thought you just wanted to remove the rules in memory. For future reference you can use

```
sudo iptables -F
```

to remove all the rules. See "[man iptables]("https://linux.die.net/man/8/iptables")" for details.

If you use other tables like nat, you may have to flush them separately.

```
sudo iptables -t nat -F
```

---

