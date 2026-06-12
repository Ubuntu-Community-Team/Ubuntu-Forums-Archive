---
title: "DISPLAY for ssh -X"
date: 2013-10-07
forum: Networking &amp; Wireless
---

### Post by mamboknave on 2013-10-07
In my local network I have three computers.

Say that my external IP address is 12.345.678.90

In order to connect ssh from remote to any of them, I've set a different ssh port on each. Something like 2201, 2202, 2203.

Now, I need to connect ssh -X from any of these computer to a remote server in order to see here the graphics of the applications I'm launching there.

How should I set the DISPLAY on that server in order to make sure that I see the graphics on the computer I connect from?

This does not work, as it does not specify which computer, within my IP, the output should be sent to:

export DISPLAY=12.345.678.90:0.0

Thanks!

---

### Post by Lars Noodén on 2013-10-08
ssh should set DISPLAY for you automatically if you want the program to be visible on the computer you are connecting from.   If you want the program to be visible on the computer you are connecting *to* then  you need to set DISPLAY=:****0.0

---

