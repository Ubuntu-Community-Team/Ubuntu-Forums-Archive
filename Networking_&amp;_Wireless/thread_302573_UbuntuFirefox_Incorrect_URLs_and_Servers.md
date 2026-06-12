---
title: "Ubuntu/Firefox Incorrect URLs and Servers"
date: 2006-11-18
forum: Networking &amp; Wireless
---

### Post by ColinWilliams on 2006-11-18
I have a strange problem regarding Ubuntu and Firefox.  I am currently using Edgy, but the problem occurred in Dapper as well.  

At seemingly random time when I am browsing the internet with Firefox, something in my system seems to get confused as to which server it is supposed to contact, and it ends up requesting pages that exist on one server from a completely different server.  I.e. I will be browsing one site, say, ubuntu.com, and it suddenly wacks out and starts trying to get everything from a completely different site, like google.com.  Since the page I want doesn't exist on the server that it tries to get it from, I get the 404 page of the second server in my browser.  The location bar still shows the correct url, but it's trying to get the page from a different server.  There are also times when it'll get stuck requesting everything from one server, regardless of the site.  Earlier today it would only try to get things from a server which required HTTP authentication, and since I didn't have that password, I couldn't see anything at all.

Now, ordinarily I would think this is a Firefox problem, but when I completely shut down Firefox and restart it, the same this occurs with the same server.  In addition, I installed Mozilla earlier today and the same thing is happening with it.

Also this morning, the problem seems to have gotten worse.  Now it not only connects to the wrong server, it completely redirects to that server, location bar included.  

I think I have eliminated my router, connection, and ISP from the problem, since this only occurs to me, on this computer, using Ubuntu.  Windoze 2K works fine.  ](*,) 

Thanks for any help that can be given.

---

### Post by stream303 on 2006-11-23
Yikes!  Maybe check that your **/etc/resolv.conf** file truly has your *real* isp's dns server addresses in it.  If they aren't there, you might want to take a look at this summary I posted:

[http://www.ubuntuforums.org/showthread.php?t=305275](http://www.ubuntuforums.org/showthread.php?t=305275)

---

### Post by ColinWilliams on 2006-11-24
Following the instructions in your guide seems to have fixed the problem, as it hasn't happened again since I did that.  

Thanks very much!

---

