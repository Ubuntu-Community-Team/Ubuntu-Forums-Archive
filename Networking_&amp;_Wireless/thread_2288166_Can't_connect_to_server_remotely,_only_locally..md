---
title: "Can't connect to server remotely, only locally."
date: 2015-07-24
forum: Networking &amp; Wireless
---

### Post by privatedonut2 on 2015-07-24
Hello,

I've used Ubuntu as my main OS for a lot of things over the years, but only on dedicated servers. But recently I've been working on setting up a local server to save some money, and everything is going great until this point. I'm trying to enable it so I can connect to my ubuntu server remotely from another IP address, in case I'm out of town at the time. I have port forward the port correctly, and it can be seen from [http://www.canyouseeme.org](http://www.canyouseeme.org). But I can't seem to connect to it by the IP, I keep getting "Timed Out" errors after awhile. Any help will be awesome. Thanks. :)

---

### Post by papibe on 2015-07-24
Hi privatedonut2. Welcome to the forum ):P

Take a look at this response to a similar problem: [http://ubuntuforums.org/showthread.php?t=2257106&p=13188842#post13188842](http://ubuntuforums.org/showthread.php?t=2257106&p=13188842#post13188842)

My first guess is that you're trying to access your public IP from your local network. If that is the case, you should need to test remote access using a different method.

Hope that points you in the right direction. Let us know how that goes, and if you have more questions.
Regards.

---

### Post by privatedonut2 on 2015-07-24
Hello papibe! Thank you for the welcome! ):P

I actually had everything setup correctly as it seems, because I downloaded a SSH client on my phone and turned off the wifi. And it connected just fine, I'm going to have a friend test it also! :) It's weird that it didn't work on my local computer, but works on my phone. :O But thank you! :)

---

### Post by papibe on 2015-07-24
You're very welcome :D

Usually you can't access the public IP of a LAN network from inside the LAN. Most consumer routers don't allow it. The feature is call NAT loopback, and it is available in more 'pricey' routers, or in open source firmware.

When you have the chance, please mark the thread as solved ([here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")'s how to do it).

Come here often, and have fun.
Regards.

---

### Post by privatedonut2 on 2015-07-24
> **papibe said:**
> You're very welcome :D

When you have the chance, please mark the thread as solved ([here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")'s how to do it).

Come here often, and have fun.
Regards.

I've marked it as solved! :) I'll visit the forums often, might be able to help a few members out here and there who knows. :D Have a good day!

---

