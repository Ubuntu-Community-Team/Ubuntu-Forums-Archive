---
title: "internet disconnects"
date: 2007-08-19
forum: Networking &amp; Wireless
---

### Post by enduser on 2007-08-19
many many linux users just post code and think  people what to do with that. Buggy expensive windows is better than cocky poorly explained spit fix gibberish in lieu of an explanation and actual fix. my internet when directly plugged in to the router cannot maintain connection. This is the same problem everyone else has so its a problem in the coding not my hardware (which works using any other OS)

If this is Ipv6 then dont just tell me to blacklist it:    ------> "file not found" when i try to save the blacklist file. the instructions were incomplete.

if you are going to make instructions do it right. tell me how. pretend im a mac user and cant handle the idea of another button. Dont make instructions a sermon. A sermon says "fisrt you need to open a terminal and type"  Instructions say "in terminal type"    save my eyes the squinting. it can be 200 steps if you like as long as you leave nothing out and keep them simple. Linux doesn't support its own community well yet and that IS THE DIFFERENCE BETWEEN EASY AND OVERLOOKED. You'll never turn windows users away from a product they know if they don't get BETTER support than they are used to.

again ill state the problem: internet disconnects SUPER frequently. Wired or wireless doesnt matter. Anything built into the OS works fine with internet and never disconnects (ex: add programs, and updates). I use firefox (downloaded from updates). It may be Ipv6 is my problem but many of the fixes make no sense. the few i could decipher didnt work.

I also dislike the idea of just "disabling something to make something else work" i want to know WHY this problem is happening and if the fix is a correct one.

sorry to get all ranty but you get that way after hours of refreshing your internet connection to read a single forum thread at a time while looking for a fix. ***which some of you silly users can do by double clicking the network connection (no need to reboot router or computer or anything)

---

### Post by aoakley on 2007-08-20
Hi, I appreciate your patience with this. Please remember that unless you are paying Canonical for support, all the replies you will see are from unpaid amateur volunteers, most of whom don't care whether you stick with Linux or go back to paying for Microsoft Windows.

I need to clarify what your problem is. When you say "the internet disconnects" do you mean:

1. You cannot access the Internet for any service such as email, web, usenet, telnet, bittorrent, or

2. Firefox web browser is not working for you

(My point being that The Internet is a lot more than just web pages)

You also seem to suspect that IPV6 is causing a problem in Firefox. If you want to turn off IPV6 in Firefox (which is unlikely to make anything worse, and may help if your ISP doesn't support IPV6), you can do this by:

1. Start Firefox

2. Type **about:config** in the address bar and press Enter/Return

3. Scroll down until you find **network.dns.disableIPv6**

4. Double-click **network.dns.disableIPv6** so that the Value column says True

5. Close and re-start Firefox

If this works, you should also consider turning off IPV6 entirely for your entire system, but that is complicated and you sound stressed enough already.

---

