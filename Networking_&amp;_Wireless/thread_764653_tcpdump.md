---
title: "tcpdump"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by vanderkerkoff on 2008-04-24
Can someone tell me how to view the http headers using tcpdump?

sudo tcpdump -vvv -n port 80

I can see the packets going back and for, but I want to inspect the http headers.

thanks for any help

---

### Post by vanderkerkoff on 2008-04-24
[http://livehttpheaders.mozdev.org/](http://livehttpheaders.mozdev.org/)

This is one way I've found, it's still a bit clunky as it caches all headers, I wonder if I can configure it.

Still would like to hear about how to make tcpdump do that if anyone knows.

---

### Post by SpaceTeddy on 2008-04-24
in tcpdump, this gets real ugly. I have found a way to display the stuff, but it is near unreadable still... 

however, why use tcpdump ? i'd suggest wireshark. That has a nice gui, and displays the pakets properly... but then, i never really cared about the payload of anything...

what do you need to see the http for anyway, and why do you need to get it out of the paket ?

hope it helps :)

---

### Post by vanderkerkoff on 2008-04-24
Hi Space Teddy

There's enough configuration options in livehhtheaders for this task.

I'm developing a web application that is going to be accessing multiple google API's, seeing the live http headers is good for debugging.

And there'll be lots of that

:-)

Thanks for you tips mate.

---

### Post by Monicker on 2008-04-24
> **vanderkerkoff said:**
> Hi Space Teddy

There's enough configuration options in livehhtheaders for this task.

I'm developing a web application that is going to be accessing multiple google API's, seeing the live http headers is good for debugging.

And there'll be lots of that

:-)

Thanks for you tips mate.


ngrep may work for you.

ngrep port 80 && [www.google.com](www.google.com)

ngrep searchterm "port 80 && www.google.com"


There is even an option to have it show empty packets.

---

### Post by vanderkerkoff on 2008-04-24
ngrep is goooood

thanks

---

