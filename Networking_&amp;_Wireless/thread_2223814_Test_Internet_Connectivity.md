---
title: "Test Internet Connectivity"
date: 2014-05-13
forum: Networking &amp; Wireless
---

### Post by parkour86 on 2014-05-13
What is the best known method for testing for internet connectivity after joining a network with a bash script?

Here's what i've tried:
```

wget -q --tries=20 --timeout=10 http://www.google.com -O google.idx &> /dev/null
if [ ! -s google.idx ]; then
	echo -e "No Internet\n"
else
	echo -e "Has Internet\n"
fi


rm google.idx

```

```

if  ping -w 5 google.com >/dev/null 2>&1
then
	echo -e 'Network is up"
else
	echo -e 'Network is down!"
fi

```

---

### Post by spynappels on 2014-05-13
What is the problem with the methods above? the second one definitely works.
Are you just looking for other methods to try?

---

### Post by parkour86 on 2014-05-13
Whenever I try to run it, it always says "Network is down" when there is internet activity. You seem 100% sure that it works so I think it might be an issue with my OS. I will have to play with it more. Thanks for the help.

---

### Post by spynappels on 2014-05-13
The second one definitely works for me!

```
stefan@stefan-laptop:~$ if ping -w 5 google.com >/dev/null 2>&1; then echo -e 'Network is Up'; else echo -e 'Network is Down'; fi
Network is Up
stefan@stefan-laptop:~$
```

---

