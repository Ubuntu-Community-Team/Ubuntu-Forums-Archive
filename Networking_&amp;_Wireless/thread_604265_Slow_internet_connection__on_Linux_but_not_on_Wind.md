---
title: "Slow internet connection  on Linux but not on Windows"
date: 2007-11-05
forum: Networking &amp; Wireless
---

### Post by greenpea on 2007-11-05
The problem started to occur after i installed 7.10. Before, when i was using 7.04 or other linux's distributations, the internet was fine. Now the internet is very slow. If i disconnect and connect the internet, there will be sudden burst of speed. But after few seconds, the speed will die out. And I need to disconnect and connect again, in order to surf the web. I tried all my old linux's distributations. The results are still the same, slow as a snail.

Any idea?

During these past hours, I tried disable IPV6, changed the firefox about:config and changed the DHClient into 208.67.222.222. None of these, seems to be working for me. 

Hope someone will help me  out.

---

### Post by minq on 2007-11-16
I had a similar problem. I fixed it by looking in the Network Interface under the DNS tab and i saw that it was including my rounter as the primary dns. I deleted it from the table and restarted my computer and everything worked fine. Sorry i cant give anymore detail im at school and not able to look at my Ubuntu desktop :(

---

### Post by moe_syzlak on 2007-11-29
this prolem has been solved here ---> [http://ubuntuforums.org/showthread.php?t=616744](http://ubuntuforums.org/showthread.php?t=616744)

please search the forums for a solution BEFORE asking for help. many problems advanced and some of the noob problems (such as "how do i get root on my computer," or "how to install xxxxx package" that is in the repository) have been fixed. and you can get the answers to your problem by searching

---

### Post by snowguy on 2008-07-19
I found this thread searching and minq's advice helped me solve my problem.  In my case the issue was that browsing the internet was VERY slow but oddly when I did a speed test it took forever for the test to load but the results weren't so terrible. I since learned that it was taking forever to figure out how to make the initial connection but once the connection was made, the download speed was reasonable. This was the result of a bad entry in my resolve.conf file causing the DNS lookup to take forever. 

Here are more details in terms of solving. (Note I'm no expert so it would be nice if someone else can confirm/correct my instructions but this did work for me. )

from the terminal

sudo nano /etc/resolv.conf

(or your preferred text editor in place of nano, e.g. gedit)

remove the first line of the form: 

nameserver xx.xx.xx.xx 

AND (and this is the important part) the xx.xx.xx.xx is a local ip address on your own homenetwork AND you haven't set this up as a nameserver. (And I think if you don't know what a nameserver is (as I don't really) then you can guess you didn't set one up. In my case the ip started with 172, e.g. 172.xx.xx.xx. Also, I believe the fact that there were 3 entries there was a clue that something was up. 

In my case some package I installed or something I had been messing around on must have added this ip because I certainly hadn't edited the file myself.

---

### Post by snowguy on 2008-07-23
For completeness I needed to come back here and say I figured out what was causing this line to be added. I had mistakenly added in my router configuration a DNS entry which wasn't correct. Somehow ubuntu was pulling from my router this line--so that I would delete it and pretty soon it would add it back in. this kept going on until I went to the router and took the bad dns entry out there. I hope this helps anyone who stunbles along this post.

---

