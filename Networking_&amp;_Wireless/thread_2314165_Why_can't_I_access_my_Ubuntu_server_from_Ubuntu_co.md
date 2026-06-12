---
title: "Why can't I access my Ubuntu server from Ubuntu computer? &quot;Unable to access location&quot;"
date: 2016-02-18
forum: Networking &amp; Wireless
---

### Post by Excuse_Me on 2016-02-18
A long time ago I set up an Ubuntu machine to use as a server for my windows and mac os computer which has worked fine with both, in windows I can just browse it from icons and on mac os I type in the IP for the server in the "go" menu.

Getting an ubuntu laptop I thought it would be really easy to access the ubuntu server but everytime I try I get the following message:
"Unable to access location
Failed to mount Windows share: Permission denied"

When going on the "connect to Server" window instead typing the IP of my server doesn't gain my access either.

So what should I do to access the server??

Many thanks

---

### Post by bab1 on 2016-02-19
> **Excuse_Me said:**
> A long time ago I set up an Ubuntu machine to use as a server for my windows and mac os computer which has worked fine with both, in windows I can just browse it from icons and on mac os I type in the IP for the server in the "go" menu.

Getting an ubuntu laptop I thought it would be really easy to access the ubuntu server but everytime I try I get the following message:
"Unable to access location
Failed to mount Windows share: Permission denied"

When going on the "connect to Server" window instead typing the IP of my server doesn't gain my access either.

So what should I do to access the server??

Many thanks
Start with a little debug.  Post the output of this terminal command from your laptop:
```
smbtree -d3
```

Please post the output between [noparse]```
text here
```[/noparse] blocks.  The easiest way to do that is to click on the [SIZE=5]**#**[/SIZE] icon at the top of the advanced editor that you use to respond with and paste the text between the code blocks.

---

