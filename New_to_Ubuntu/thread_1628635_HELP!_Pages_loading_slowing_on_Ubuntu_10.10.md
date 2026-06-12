---
title: "HELP! Pages loading slowing on Ubuntu 10.10"
date: 2010-11-22
forum: New to Ubuntu
---

### Post by jeremy96 on 2010-11-22
:mad: I am using Ubuntu's default browser, Firefox. I also use it on my Windows 7 laptop with no problems. I noticed today that web pages were starting to load slowly on my Ubuntu 10.10 desktop!! I also tried rebooting and that didn't help! So, what is going on??? :mad:

---

### Post by karlwbloedorn on 2010-11-22
Nevermind, thread is solved already

Anyways, here is what I was gonna say:

There are 2 basic reasons that cause web pages to load slowly
1. Network problem
2. Software error

I can't help with the second problem as I am not familiar with firefox internals, however I have some ideas about the first one.


If you have Flash player installed, run a speed test on your Ubuntu machine:
[http://speedtest.net/](http://speedtest.net/)

If you get approximately the same result on your other computers, bandwidth is fine.

It could also be DNS requests taking more time than usual. Try opening a terminal and typing the command "nslookup microsoft.com".
It should be nearly instant (assuming your internet is not satellite or cellular). If it takes a while, you might have a DNS problem.

It could also be a specific web site that is loading slow. Do all websites load slowly, or only some?

---

### Post by Vanish00 on 2011-01-14
I'm having the same problem some sites load while others just constantly wait for a response from the server.  From that point I keep refreshing till it works.  I did do the speedtest and passed with flying colors.  I know most times youtube videos just stop halfway through and just waits...

So how did you solve your problem?

---

