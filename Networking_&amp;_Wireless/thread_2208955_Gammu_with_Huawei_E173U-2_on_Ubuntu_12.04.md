---
title: "Gammu with Huawei E173U-2 on Ubuntu 12.04"
date: 2014-03-03
forum: Networking &amp; Wireless
---

### Post by jugurtha.hadjar on 2014-03-03
Hello everyone, this is not a question.

As the title hints, I'm using a Huawei E173U-2 3G modem on Ubuntu 12.04. I'm toying with Gammu. I was able to read messages and send them, etc. But had some difficulty with USSD. After trying many things, reading threads and looking at a lot of closed threads on this forum with no answers, I was able *finally* of successfully sending a USSD "command" and receiving a reply.

I used to get ```
Press Ctrl+C to break...
``` and nothing would happen.


First things

I created a ```
.gammurc
``` configuration file with the following content:

> 
[gammu]
device = /dev/ttyUSB0
connection = at115200
model = E173


For USSDk, I didn't get anything until I tried ```
device = /dev/ttyUSB2
```

I was able to see that unplugging and plugging the dongle and running ```
dmesg
```.

So you change .gammurc line to /dev/ttyUSB2 and you should be able to send execute ```
gammu getussd *222#
``` (for my operator, to check the balance)

Here's the output:

```

Press Ctrl+C to break...
USSD received
Status               : No action needed
Service reply        : "[Reply of the operator, in clear text, not UCS-2 or something]"

```


This is an ongoing thing. If it's irrelevant, please feel free to delete it (although by the amount of unanswered closed threads, I think it's relevant).

---

