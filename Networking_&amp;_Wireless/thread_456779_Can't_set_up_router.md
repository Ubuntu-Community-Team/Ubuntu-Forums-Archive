---
title: "Can't set up router"
date: 2007-05-28
forum: Networking &amp; Wireless
---

### Post by God Of Atheism on 2007-05-28
I set up a static ip address, and am now trying to connect to my router. I do have internet, if I ping the router's address I do get an answer, but if I try to set up the router by typing in the ip address in a browser, I do get nowhere. The router in question is an ECI B-focus 270PR, the manual can be found [here](http://ioannis.mpsounds.net/blog/?dl=Router270Eng.pdf). More precise, I've tried reaching the address (192.168.1.1) in both Firefox and Opera to no avail, but ping -R -c 20 192.168.1.1 gives the following output.
```

PING 192.168.1.1 (192.168.1.1) 56(124) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=255 time=2.60 ms
RR:     192.168.1.10
        192.168.1.1
        192.168.1.10

64 bytes from 192.168.1.1: icmp_seq=2 ttl=255 time=1.67 ms      (same route)
64 bytes from 192.168.1.1: icmp_seq=3 ttl=255 time=1.59 ms      (same route)
64 bytes from 192.168.1.1: icmp_seq=6 ttl=255 time=1.60 ms      (same route)
64 bytes from 192.168.1.1: icmp_seq=7 ttl=255 time=1.52 ms      (same route)
64 bytes from 192.168.1.1: icmp_seq=8 ttl=255 time=1.69 ms      (same route)
64 bytes from 192.168.1.1: icmp_seq=9 ttl=255 time=1.61 ms      (same route)
64 bytes from 192.168.1.1: icmp_seq=10 ttl=255 time=1.78 ms     (same route)
64 bytes from 192.168.1.1: icmp_seq=11 ttl=255 time=1.67 ms     (same route)
64 bytes from 192.168.1.1: icmp_seq=12 ttl=255 time=1.62 ms     (same route)
64 bytes from 192.168.1.1: icmp_seq=13 ttl=255 time=1.79 ms     (same route)
64 bytes from 192.168.1.1: icmp_seq=14 ttl=255 time=1.71 ms     (same route)
64 bytes from 192.168.1.1: icmp_seq=15 ttl=255 time=1.62 ms     (same route)
64 bytes from 192.168.1.1: icmp_seq=17 ttl=255 time=1.47 ms     (same route)
64 bytes from 192.168.1.1: icmp_seq=18 ttl=255 time=1.64 ms     (same route)
64 bytes from 192.168.1.1: icmp_seq=20 ttl=255 time=1.48 ms     (same route)

--- 192.168.1.1 ping statistics ---
20 packets transmitted, 16 received, 20% packet loss, time 19060ms
rtt min/avg/max/mdev = 1.473/1.696/2.609/0.254 ms

```

Any ideas? I already tried turning off and resetting the router.

---

### Post by Ek0nomik on 2007-05-28
Were you able to connect to the router at any point in time?

---

### Post by God Of Atheism on 2007-05-28
I think so, the screens (in the manual, I can't access the gui now) look familiar. I also realise I did not read through the troubleshooting instructions in the manual. So now I'm following the upgrade instructions, after finding an upgraded firmware version, only to get an error message:
```

ftp> put application_20040123_270pr.bin app2
local: application_20040123_270pr.bin remote: app2
200 PORT command successful.
553 app2: Unknown destination file or in ASCII mode

```
Now since the instructions are for terminals anyway, I think the ASCII mode above is a bit redundant. Anyway, I don't get a transfer complete message, and after restarting the router, the version is still the same old one.

---

### Post by Ek0nomik on 2007-05-28
I feel like there could be a lot of different reasons as to why you can't get into your router.

Can you reset all of the routers settings so you can get back into it like you were at an earlier point in time?  If you were able to access it earlier, than whatever you changed borked it.  ;)

---

### Post by God Of Atheism on 2007-05-28
I don't think I changed anything (apart from attempting to upgrade the firmware today), the last time I was in was a year or so ago, and that was because I had problems connecting to the internet. I was running windows 2000 at the time, and it was in fact a technician from the telephone company who got in then.
But there might be something: in the end, one of my network cards (the one not connected to anything, but present on the motherboard) was disabled to get it working, I do remember not running into trouble when turning it back on (next windows and linux reinstall), but it might just be causing trouble when trying to get into the router set up. I'll try to disable it and see what happens.

---

### Post by Ek0nomik on 2007-05-28
> **God Of Atheism said:**
> I don't think I changed anything (apart from attempting to upgrade the firmware today), the last time I was in was a year or so ago, and that was because I had problems connecting to the internet. I was running windows 2000 at the time, and it was in fact a technician from the telephone company who got in then.
But there might be something: in the end, one of my network cards (the one not connected to anything, but present on the motherboard) was disabled to get it working, I do remember not running into trouble when turning it back on (next windows and linux reinstall), but it might just be causing trouble when trying to get into the router set up. I'll try to disable it and see what happens.

Any luck?

If you have a brand new router that isn't setup to block anyone, you should easily be able to connect to it using 192.168.1.1

You could also try using https:// if that's how it's setup (to use SSL).  I know I have my router only work on http**s**://

---

### Post by God Of Atheism on 2007-05-28
> **Ek0nomik said:**
> Any luck?

If you have a brand new router that isn't setup to block anyone, you should easily be able to connect to it using 192.168.1.1

You could also try using https:// if that's how it's setup (to use SSL).  I know I have my router only work on http**s**://

Nope, no luck whatsoever. Tried disabling the other network card, and also now just tried your https suggestion. The latter does give a "problem loading page" much faster than the regular http (less than 20 seconds versus many minutes), which leads me to guess the normal http is what should be used for my router.

I did think about one thing, the manual lists that I should get 2048 bytes/hash mark, but I get only half of that when I do ha on an ftp connection to the router, which might be problematic for updating the firmware, but then I know too little about the actual meaning of that hash setting to be sure. After googling for ftp commands, to understand what I was actually doing when trying to upgrade the firmware, I tried some more, in particular I tried to discover the directory structure on the router (the error message indicated that I might be trying to write to a wrong directory). Unfortunately I then got a message `list not implemented', so I couldn't discover too much, although I do need to try whether that app2 directory actually exists by just changing the directory. I could also try to set ascii instead of binary, but I very much doubt the file is an ascii file, first of all since it has a bin extension, and that is the case for all the different but ultimately equivalent firmware updates I downloaded. (I downloaded a few from sources I did not know, until I eventually found the well-hidden one on my telephone company's website, which turned out to be the same file)

By the way, the router is not brand new, it's quite a few years old (roughly three to five is my guess), but I can't give an exact age unless I go digging in my bureaucratic archive, which I prefer not to do.

Anyway, I'll try all of that tomorrow since I'm way too tired now.

Goodnight and thanks for the help (even if it doesn't yet solve the problem)

---

### Post by likwid on 2007-05-28
Might be a stupid suggestion but maybe the router's web interface doesn't support your browser. I know i had similar problems in the past and only Internet Explorer worked, what with it's shoddy standards and all.

---

### Post by Ek0nomik on 2007-05-28
**God of Atheism**

Do you have a Windows box available?  I would try getting into your router with that.

---

### Post by God Of Atheism on 2007-05-29
I do not have a windows box available.

And a technical question on the suggestion that the interface only supports Exploiter: if http is used as protocol, shouldn't I get at least something instead of nothing?

The manual indeed does state internet explorer 5.5 or above, but states for operating system requirements various windows version, UNIX or MacOS. As far as I know, internet explorer never reached version 5.5 on MacOS and was never released for UNIX at all.

Should it be possible to not use the gui, and instead configure the router in some other way, for example by using telnet?

And needing internet explorer only applies to accessing the gui, it is not needed to update the firmware, which I haven't managed to do yet either.

---

### Post by niceguy123 on 2008-06-08
Hi,

I know that this is a year old thread, but, if anyone can help I'm having some hardship whith the same today.

The Router was working fine on a network with 2 ubuntu and 1 xp boxes. I upgraded the Ubuntus' to 8.04 and found that I couldn't reach gmail. So I started fidling around till I accessed the modems interface via the xp ie. And I made some changes in the configuration. At first I lost my internet connection all together than somehow I was able to backtrack but now I can't access the internet on ether of the Ubuntu boxes at all.

If I knew what I was doing with the configuration I wouldn't have got where I am. Does some here know how I should have the modem configuered?

---

