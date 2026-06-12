---
title: "ping: icmp open socket: Permission denied"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by olegtim on 2007-10-19
After upgrading to 7.10 I started getting this error on ping:

ping: icmp open socket: Permission denied

I tried running ping as root and still get same error message.
Any ideas? Thanks, Oleg

---

### Post by olegtim on 2007-10-19
friendly bump

---

### Post by jonobr on 2007-10-19
Hello


What happens if you just type in ping.

Assume you get some additional help info.

Are your seeing the same with other ICMP commants?
traceroute cnn.com or so on............

---

### Post by jonobr on 2007-10-19
also, what do you see for ls -l /bin/ping

SHould be something like

-rwsr-xr-x 1 root root 30724

---

### Post by olegtim on 2007-10-19
> **jonobr said:**
> Hello


What happens if you just type in ping.

Assume you get some additional help info.

Are your seeing the same with other ICMP commants?
traceroute cnn.com or so on............

Just typing ping does return ping usage help. Tried doing a traceroute and it work fine

---

### Post by olegtim on 2007-10-19
> **jonobr said:**
> also, what do you see for ls -l /bin/ping

SHould be something like

-rwsr-xr-x 1 root root 30724

Yep, thats what I get:

-rwsr-xr-x 1 root root 30856 2007-07-06 00:40 /bin/ping

---

### Post by jonobr on 2007-10-19
mmm..... And you say you did sudo ping?

---

### Post by olegtim on 2007-10-19
> **jonobr said:**
> mmm..... And you say you did sudo ping?


Yep :( sudo ping returns same error. Weird, never seen it before. Traceroute works fine, no problems with nextworking card or connection. At this point not sure what to look for. :confused:

---

### Post by olegtim on 2007-10-22
Sorry for bumping it up but still cannot resolve this problem, ping returns:

ping: icmp open socket: Permission denied

---

### Post by mikeize on 2007-10-22
I have a similar problem, but "sudo ping <ipaddress>" works in my case.

-mike

---

### Post by olegtim on 2007-10-23
> **mikeize said:**
> I have a similar problem, but "sudo ping <ipaddress>" works in my case.

-mike

Nope, I wish :)

---

### Post by jonobr on 2007-10-23
To mikeize point, I am assuming your using sudo ping name or ip address.

and further .....For example does  ping google.com fail but ping 64.233.167.99 works, is that true?

---

### Post by olegtim on 2007-10-23
> **jonobr said:**
> To mikeize point, I am assuming your using sudo ping name or ip address.

and further .....For example does  ping google.com fail but ping 64.233.167.99 works, is that true?

Nope, both:

sudo ping google.com
and
sudo ping 64.233.167.99

return ping: icmp open socket: Permission denied

Still cannot figure out what the problem is. Thanks, Oleg

---

### Post by mikeize on 2007-10-23
Someone had me do this command:

```
which ping
```

and that gave me:

```
/home/mike/bin/ping
```

if I typed out:

```
/bin/ping whateverIPaddress
```

then it worked without sudo.  Maybe you have multiple ping files on your machine, and you could try a different one.

-mike

---

### Post by gubemton on 2007-10-24
it's not works as root too

root@Kitana:~# uname -a
Linux Kitana 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux
root@Kitana:~# which ping
/bin/ping
root@Kitana:~# ping google.com
ping: icmp open socket: Permission denied
root@Kitana:~#

---

### Post by olegtim on 2007-10-24
I see somebody else having this problem, well at lest I am not alone :)

I tried which ping, it identified correctly /bin/ping. Doing sudo /bin/ping xxx.xxx.xxx.xxx returns same error:

ping: icmp open socket: Permission denied

---

