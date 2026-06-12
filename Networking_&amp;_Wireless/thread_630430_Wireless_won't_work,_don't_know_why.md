---
title: "Wireless won't work, don't know why"
date: 2007-12-03
forum: Networking &amp; Wireless
---

### Post by Busby on 2007-12-03
I'm a total newbie, i did that lspci command once on advice from some1, it finds the wireless card but it says "DISABLED" next to it.

also, when i put my connection settings in, it appears to connect to the network, but just says "0%" all the time and won't do anything

any suggestions?

---

### Post by glasswalkerny on 2007-12-03
What system do you have and/or what wireless card is in it?

---

### Post by buntunub on 2007-12-03
Please post the results of lspci -v | grep wireless, and ifconfig. Nobody can possibly help you out without knowing 1) what type of hardware you have, and 2) is it working or not, and just not connecting, or not working/configured at all. However, in general, 99.999999999% of your issues can be very quickly resolved by using the search function on these forums, "bcm43xx help", for example, turns up a plethora of "how to's", and guides for getting bcm cards working. This is also true of Google. Also, the Ubuntu documentation project (both official and community) are a priceless treasure trove of information.

PS. for wireless, you also need to know what type of encryption your needing - WPA, WEP, etc. There are guides/how-to's for that as well. Its a shame that your wireless did not work out of the box, and most of us share your pain there, me included. I simply followed the "bcm 4306 in 5 minutes or less" guide on these forums and guess what?.. In less time than it took you to post this thread, I was up and running on WPA encrypted wireless with blazing fast speed!

---

