---
title: "wlan stopped working, don't know why"
date: 2008-08-18
forum: Networking &amp; Wireless
---

### Post by christinak on 2008-08-18
Hello!

Sorry for this really lost question, but I have a big problem and i am quite puzzled with it:

All last week, I was using knetworkmanager to log into the network at faculty, and it was working just fine. Over the weekend, I had one strange login at my residence (the screen was bizarre... the login could be seen multiplied various times) and then i don't remember if i could log in once more or not... in any case, neither on sunday at the residence (where the connection is somewhat bad) nor today at work will my computer find any of the wireless networks. It works just fine with a wired connection, however, without the cable, there is an X over knetworkmanager saying not connected and that is it.

The question is now, is it my software (and what can i do to change that) or is it my hardware (and how can i find out)? 

As I have said, I am using knetworkmanager (though i was using something else before using the internet here at faculty, i don' know what... i also did some changes to proxy and the like but as it worked before i figured it can't be that), the most recent version of kubuntu, my laptop is Asus F6Sseries, the wireless 802.11a/b/g + BT... and I guess I am still something of a newbie, so I am very lost.
Ah, if I type ifconfig into the console, my PC finds eth0 and lo, and thats it.

Any help would be very, very much appreciated. 

Cheers,
Christina

---

### Post by christinak on 2008-08-18
oh, and what I forgot... why I think it might be a hardware problem is that the wlan sign on my pc is on (i.e. lit up) and I cant turn it off...

---

### Post by christinak on 2008-08-26
Hey!

So, problem solved...

After I had used the command dmesg (I think that was more or less what I had been looking for talking about hardware or software problem) and sent all that to a friend, he figured the problem must be something a lot simpler. Like maybe a switch on the side of the laptop I had incidentally moved and I didn't know about. 

*feeling silly*

Anyway, that was the solution.

---

