---
title: "[How-To] TOR Middlebox: route all the traffic from a VM to TOR"
date: 2016-06-22
forum: Networking &amp; Wireless
---

### Post by alainb06 on 2016-06-22
Hello,

I have been using the TOR Middlebox setup posted on How-To Forge: [https://www.howtoforge.com/how-to-set-up-a-tor-middlebox-routing-all-virtualbox-virtual-machine-traffic-over-the-tor-network#](https://www.howtoforge.com/how-to-set-up-a-tor-middlebox-routing-all-virtualbox-virtual-machine-traffic-over-the-tor-network#)

But [COLOR=#ff0000]**since 16.04, it is broken**[/COLOR], the worst part being that is _silently leaks DNS requests_ (which is already mentioned by the last poster on the How To comments).
As a side effect, with the parameters given in the tutorial for dnsmasq, it fails in systemd (which fortunately does not prevent your host machine to work).

Having looked upon more closely, it was also working out of luck with 14.04!

So I have developed a fix, with a lot of explanations about WHY (and not only giving the commands!)
The filtering is also much stricter now.

For those who need it, I have hosted it on my GitHub here: 

[https://github.com/Bylon/TOR_Middlebox](https://github.com/Bylon/TOR_Middlebox)

Look at the wiki you have the instructions, and for those curious, the explanations (WHY paragraphs).

Feel free to use it, comment, propose enhancements (especially if you think there can still be leaks in spite of the must stricter filtering), ask for improvements, etc..

You can either post here or post bugs or pull requests (if you submit code or even typo corrections) directly on GitHub.

Be safe!

*P.S.: I decided to host it on my github because apparently the community How-To pages are quite restricted here, or I was too dumb to find how to post there! Also it makes more sense for the script itself to host it on a platform dedicated to code hosting.*

---

