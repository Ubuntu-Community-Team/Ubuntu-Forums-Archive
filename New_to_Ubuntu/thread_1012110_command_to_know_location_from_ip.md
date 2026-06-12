---
title: "command to know location from ip?"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by uarale on 2008-12-15
hi,

sometimes i want to know where is a person come from? all i know is the ip he uses. of course i can go to sites such as ip2location to get the information i want. but openning a heavy page just to know that is like a pain!

anyone could suggest a command to handle this in terminal?

---

### Post by Achetar on 2008-12-15
There is none that I know of. You might could build a list of regions that use certain google.com and ISP servers and crossreference that with a traceroute, but that is a lot more work than you probably want to do.

I would be interested as well if anyone has a better answer

---

### Post by Viranh on 2008-12-15
The utility "tracert" can give you some information about an ip address. I'm not sure this is quite what you're looking for, but you can give it a try.

```
sudo apt-get install traceroute
sudo tracert <ip address>
```

It's funny, I've used this command on Windows a bit, so I typed it in the terminal to see if Linux had something similar, and it worked (almost, the extra arguments may be different) exactly the same.

---

### Post by Bachstelze on 2008-12-15
The free edition of GeoIP ([font="monospace"]apt-get install geoip-bin[/font]) gives you the country:

```
firas@nobue ~ % geoiplookup 88.191.79.242
GeoIP Country Edition: FR, France
```

---

