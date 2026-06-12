---
title: "network problem"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by y_garti on 2009-04-26
hello everyone
i have a small problem (i guess that it not really a problem its just something that i dont know how to do)
i have a LAN network

ubuntu call ub with ip 192.168.1.10
and vista call vi 192.168.1.11

when i do ping to ub from vista i don't get replay
when i do ping for ubuntu to vi i don't get replay
but when i do ping to 192.168.1.10 from vista i got replays
and when i do ping from ubuntu to 192.168.1.11 i got replays

i just did a clean install to my ubuntu (i install 9.04 with ext4) 
and before the format it works fine

thanks for your help

---

### Post by Bodsda on 2009-04-26
Hi, I think the problem is that the computers dont have an entry of the hostnames to resolve to ip addresses. Assuming the ip addresses wont change, adding the following lines to

/etc/hosts

should fix the problem

```

192.168.1.10    ub
192.168.1.11    vi

```

You need to add the lines under the loopback addresses, it should look something like this.

```

bod@bod:~/C++/code/ch08$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	bod
192.168.1.10    ub
192.168.1.11    vi

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

To edit the file, run this command from a terminal

```
gksudo gedit /etc/hosts
```

Hope this helps,

Bodsda

---

### Post by y_garti on 2009-04-26
thanks for host answer but i want to figure why before i reinstall my ubuntu it work without the host (on the vista side or the ubuntu side)

---

### Post by Bodsda on 2009-04-26
Im not sure, It may be a problem with the dns on the router not logging the hostname properly or the hostname may have changed.

Sorry I dont know a definite answer

---

### Post by y_garti on 2009-04-26
well thanks anyway i will use the host files in ubuntu and vista



p.s
i love your signature:lolflag:

---

### Post by Bodsda on 2009-04-26
Cheers :)

oh, i forgot, you only need to add the vista entry to ubuntu and the ubuntu entry to vista, I think the host file on windows lives in

C:\Windows\System32\drivers\etc

Hope this helps,

Bodsda

---

