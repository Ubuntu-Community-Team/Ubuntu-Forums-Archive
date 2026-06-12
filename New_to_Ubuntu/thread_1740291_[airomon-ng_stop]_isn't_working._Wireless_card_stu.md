---
title: "[airomon-ng stop] isn't working. Wireless card stuck in monitor mode"
date: 2011-04-26
forum: New to Ubuntu
---

### Post by slavelaborer on 2011-04-26
^^^^
I was working with airomon-ng and the other airo tools and now my wireless card is stuck in monitor mode and will not connect to my wifi. 

airomon-ng stop eth1 is not working. 

Help please!

---

### Post by Ghost|BTFH on 2011-04-27
WARNING! Assumptions incoming!

Type:
```

ifconfig
```

If your wireless card is ATH0, try:

```
sudo ifconfig ath0 down
sudo ifconfig ath0 up
```

These commands tell the wireless card to turn off, then back on - which will usually stop any monitoring and set it back to normal.

Another option is, if it's a program that has hold of the card, you could always use:

```
ps aux
```

Find the program, user and the process id.

If it's a normal user, just use

```
kill -9 (processid)
```

If it's root, you have to give the **sudo** command with the above command.

Cheers,
Ghost|BTFH

---

### Post by 5149.5 on 2011-04-27
Are you sure eth1 is the correct interface name? What does iwconfig show.

---

### Post by slavelaborer on 2011-04-27
thanks!
My card is definitely "eth1"
I used those commands you listed earlier and it still wasnt working. Somehow I turned it back on today and it was back in "Managed" mode.

---

