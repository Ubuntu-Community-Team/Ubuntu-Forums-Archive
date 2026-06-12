---
title: "Reason for &quot;ifstat: warning: rollover for interface...&quot; FOUND!"
date: 2014-04-09
forum: Networking &amp; Wireless
---

### Post by GNU-Cody on 2014-04-09
*(This is strictly an informational/response post related to my original thread located [here]("http://ubuntuforums.org/showthread.php?t=2054513"). I would have posted this on that thread, but it was closed and I was unable to reopen it.) *

**PROBLEM:**
The following error is generated while using ifstat to monitor a highly utilized network interface...

[FONT=courier new]ifstat: warning: rollover for interface [interfaceName] reinitialising[/FONT]


**SOLUTION:**
*The short answer... *
There is no solution, but it's okay because it isn't hurting anything or signifying any problems in your system!

*The long answer...*
It took a while to find (over a year, in fact, if you noticed the date on [my original post]("http://ubuntuforums.org/showthread.php?t=2054513")), but I finally tracked down what I believe is the answer... counter rollover!
What is that, you ask? It goes like this... Linux uses counters to keep track of all sorts of things on the system. These counters are, of course, limited to a maximum number of bytes they can hold by the data-structure they are defined with. In example, an 8bit data-structure can only hold 256Bytes (2^8 bytes). Once a counter is pushed over it's maximum it resets (aka rolls over, hence the term *counter rollover*). 

Depending on your machine's architecture, or the counter you are referencing, the data-structure can vary. Linux's network counters are implemented with a 32bit data-structure. This means they can only hold a max of 4GB (2^32 = 4294967296 bytes) before they are reset. The program ifstat, I believe, uses these network counters as input to calculate it's output of KBytes per second. Hence when the network counter is reset, ifstat produces the above error.

I've timed it out on a few machines with multiple NICs and configurations and found that every time it reaches approximately 4GB of data transferred it pops up the above warning message. So it's not an error and it's not an unexpected behaviour but ifstat wants to warn you about it, for some reason.


**CREDITS:**
This possible explanation was revealed to me while reading [this paper on dstat from the 2007 LinuxConf Europe written by Dag Wieers]("https://github.com/dagwieers/dstat/blob/master/docs/dstat-paper.txt"). Here's an excerpt...

> [I]Unfortunately Dstat is susceptible for counters that "rollover." This means that a counter gets bigger than its maximum value the data-structure is capable of storing. As a result the counter is reset.

For some architectures and some counters, Linux implements 32bit values, this means that such counter can go up to 2^32 (= 4294967296B = 4G) values.

For example the network counters are calculated in absolute bytes. Every 4GB that is being transferred over the network will cause a counter reset. For example on a bonded 2x10Gbps interfaces that is using its theoretical transfer limit, this would happen every 1.6 seconds.[/I]

---

