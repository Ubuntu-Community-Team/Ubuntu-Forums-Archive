---
title: "Please help trying to understand ssh tunneling"
date: 2007-11-26
forum: Networking &amp; Wireless
---

### Post by neil.the.blue on 2007-11-26
Hello,

I am trying to understand some behaviour I have seen with ssh tunneling a few times now, when ssh tunneling doesn't seem to connect. Here is an example using vmware.

1) On the local machine I map port 902

ssh [email]me@home.org[/email] -L 9002:vmwarehost:902

2) On the local machine I try to connect to the new local port 9002:

vmware -h localhost -P 9002 

But on the remove machine I get the error:
channel 3: open failed: connect failed: Connection refused

I have also seen the same error for a few other applications in the past (I don't recall which ones they were now), but I don't understand what this message means when it appears on the remove machine.I thought the problem would have occured on the local machine? Can anyone explain what is happening here please. Searching a similar thing also seems to happen with mysql. I have seen a few work arounds, but I am more interested in knowing what is happening.

Thanks
Neil

---

