---
title: "[SOLVED] SWF issues or Networking Problem?"
date: 2007-09-26
forum: Networking &amp; Wireless
---

### Post by VSack on 2007-09-26
I have a fresh install Feisty that is having problems.  The problem appears to be in regards to networking connectivity, though I am at a brick wall in regards to what to try next.

So far:

I have been able to browse and use the internet successfully using my Intel Mac and My XP box.  Both can access the soon-to-be-mentioned issues in question.

On fresh install, Firefox would hang.  My first thought was that it was a flash issue, but even going to the adobe.com website was posing a problem.

Local network access is fine.  I can connect to servers, etc.  and use Synergy just fine.

When I place my Ubuntu box on an external DSL used for pen testing, the unit works terrific.  The issue only appears when behind a firewall in which all other OSes are presenting fine...including a web kiosk using Dapper.

When attempting to wget [http://wwwimages.abode.com/www.adobe.com/swf/homepage/fma_shell_FMA.swf](http://wwwimages.abode.com/www.adobe.com/swf/homepage/fma_shell_FMA.swf)  I hang at exactly 5,463 each time.

I have disabled and summarily blacklisted IPV6.

I even tried using Automatix, and that refused to download Opera, or the Flash plugin.

After connecting to the DSL and getting the Flash Plugin AND Epiphany, both Firefox and Epiphany continue to have the same problem.

I'm at a loss here folks...It sounds to me like its clearly an issue with our Linksys RV016 and something in Feisty, but I was unable to find any such information on the web.  Can anyone help to point me in the right direction? 

Thanks!

- John

---

### Post by ddrichardson on 2007-09-26
Hope [this]("http://www.drewb.com/blog/") helps.

---

### Post by VSack on 2007-09-26
You can't get much more specific than that :)

I will definitely try this out first thing tommorrow morning, and report back here for posterity purposes.  It can never hurt to have too much information in this repository!

Thanks for the heads up ddrichardson!

---

### Post by VSack on 2007-09-27
ddrichardson's fix worked!

The issue exists not within Ubuntu, but its Linux underpinnings.  In short, you must make a manual adjustment to disable tcp_window_scaling to work.  This problem is apparently persistent not just with my connection, but this appears to be something alot of people may have to deal with.

Please visit the link ddrichardson posted for more information.  If that link should go down for any reason, sudo edit /etc/sysctl.conf and add:

net.ipv4.tcp_window_scaling = 0

---

### Post by ddrichardson on 2007-09-27
It's always a bonus when things work out. Can you mark the thread solved, to help anyone searching for this problem, there's a link in my signature.

Update: I've contacted the poster of the blog entry and intend to incorporate this information and solution into the Ubuntu Help Wiki.

---

