---
title: "[SOLVED] Help sharing wireless internet via Ethernet"
date: 2007-11-24
forum: Networking &amp; Wireless
---

### Post by dorkdork777 on 2007-11-24
After searching and searching, I could find no answer (with instructions I could follow) for my question, so I decided to post here. Hopefully it hasn't been asked too many times already! :)

So basically, here's what we have - 
Wireless router -> Wireless -> My computer (Ubuntu 7.10)

Everything works fine with that. But here's what I'd like to have - 
Wireless router -> Wireless -> My computer -> Ethernet -> My Xbox 360

I tried Firestarter, but it keeps complaining that ath0 (my wireless card) and eth0 (Ethernet) aren't ready.

Please keep in mind that I am still fairly new to Ubuntu, so, if possible, I'll need instructions to be that bit more detailed than the ones I've found already.

Any suggestions?

---

### Post by dorkdork777 on 2007-11-24
Bump. I completed Halo 3 on single player campaign, and now I need something to do - like play on Xbox Live? Any suggestions at all would be much appreciated!

---

### Post by dorkdork777 on 2007-11-25
Bump. I tried again; still nothing. But once I plug in the Ethernet cable to my PC, Ubuntu expects to get an internet connection from it and switches to a 'wired network connection' from my wireless. Any way to get it to stop doing this?

Any suggestions for my previous question as well?

---

### Post by dorkdork777 on 2007-11-25
Bump (again).

---

### Post by mlacomb on 2007-11-25
You're essentially wanting your computer to act as a bridge.  Google search on "linux ethernet bridge" - here's the first article I came to:

[http://www.linuxjournal.com/article/8172]("http://www.linuxjournal.com/article/8172")

Now this assumes a static configuration on each side, blindly forwarding traffic.  You'll need to adjust the instructions accordingly (i.e. do not modify your wireless card configuration) for your uses.  

Sorry I can't help further - but without knowing your network setup, I can't begin to tell you exactly what to type.

---

### Post by SactoBob on 2007-11-25
would seem to be a painless option (except for the $60 for the bridge).
Run one ethernet cable to your computer, and another to you xbox.
[http://ubuntuforums.org/showthread.php?t=387871](http://ubuntuforums.org/showthread.php?t=387871)

---

### Post by dorkdork777 on 2007-11-26
Thanks a lot for the replies,

I had been using a seperate wireless bridge, before it suddenly broke. All efforts to fix it have failed. So I decided to try and get my computer to act as a wireless bridge (though I didn't know the correct terms), while I searched for a good, cheap, available-in-the-UK replacement.

But what information would be helpful, and how would I get that information? (Like should I run a specific command in the Terminal and post the results, or what?)

Thanks again people, this has to be one of the most helpful communities I've ever been a member of. :)

EDIT: We tested the wireless bridge I have already (the broken one) with a Mac laptop, and it worked perfectly - then after playing with some settings, the Xbox finally caught on, and connected with Xbox Live. Thanks again for all your help, but everything seems fine... for now. :) I'll mark this as Solved.

---

### Post by dragon_788 on 2007-12-29
dorkdork, I use an "old" 3com wireless G AP that allows for bridge and client/AP mode, This allows me to hook up a PC or Xbox behind the AP while it becomes a client to the router. From what I've read on other threads, dnsmasq might be a route to pursue if you plan on using your PC.

---

