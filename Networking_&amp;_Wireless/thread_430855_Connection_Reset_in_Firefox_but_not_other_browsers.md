---
title: "Connection Reset in Firefox but not other browsers"
date: 2007-05-02
forum: Networking &amp; Wireless
---

### Post by holomorph on 2007-05-02
I've tried this on two different computers, one at home, one at work, both running Fiesty.  When I try to visit [http://www.mdsplus.org/](http://www.mdsplus.org/) in firefox I get a connection reset error page :
> 
The connection was reset

The connection to the server was reset while the page was loading.
 
    *   The site could be temporarily unavailable or too busy. Try again in a few
          moments.

    *   If you are unable to load any pages, check your computer's network
          connection.

    *   If your computer or network is protected by a firewall or proxy, make sure
          that Firefox is permitted to access the Web.


But, using other computers here at work, which run windows or gentoo and firefox, they have no problem accessing the site.  Also, if I use a different browser (eg dillo) I also have no problem reaching the site from my Ubuntu box.  So it's something specific to the way firefox in Fiesty is configured, but I don't know what the problem could be. Any ideas?

- Bjørn

---

### Post by holomorph on 2007-05-08
further testing indicates it's not specific to firefox.  So far Firefox, Epiphany, and Galeon get the connection reset, while Dillo, w3m, and lyx do not.

obviously, this has me stumped.

---

### Post by NeTo on 2007-05-11
--

---

### Post by NeTo on 2007-05-11
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/89160/](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/89160/) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I had the exact same problem with several other sites, and found a solution at [thread=385094]this thread[/thread].

Basically, you can try writing in a root terminal:```

echo "4096 16384 131072" > /proc/sys/net/ipv4/tcp_wmem
echo "4096 87380 174760" > /proc/sys/net/ipv4/tcp_rmem
```

If that solves the problem, you can make the changes permanent, adding the following to /etc/sysctl.conf :```
net.ipv4.tcp_wmem = 4096 16384 131072
net.ipv4.tcp_rmem = 4096 87380 174760
```

You can find about what's behind this issue in [http://lwn.net/Articles/92727/](http://lwn.net/Articles/92727/) and [http://inodes.org/blog/2006/09/06/tcp-window-scaling-and-kernel-2617/](http://inodes.org/blog/2006/09/06/tcp-window-scaling-and-kernel-2617/)

---

### Post by holomorph on 2007-05-11
thanks for the links, I learned a little bit, but unfortunately it did not fix my problem :(

I guess now that I think about it I'm not too surprised, since Dillo, w3m, lyx, and wget all seem to have no issue connecting to that server, but firefox, epiphany and Galeon do have issues.  I wish I knew what the difference was.

---

### Post by NeTo on 2007-05-11
> **holomorph said:**
> thanks for the links, I learned a little bit, but unfortunately it did not fix my problem :(

I guess now that I think about it I'm not too surprised, since Dillo, w3m, lyx, and wget all seem to have no issue connecting to that server, but firefox, epiphany and Galeon do have issues.  I wish I knew what the difference was.

Sorry, I depicted it as the "same issue" because i wasn't able to load those exact pages (although other loaded just fine). I guess there are more changes in Feisty than the TCP Window Scaling.

Have you tried [thread=265897]disabling IPv6 support in Firefox?[/thread]

---

### Post by holomorph on 2007-05-11
yea, I tried disabling ipv6 too, but it didn't make a difference.

---

### Post by obenauer on 2007-05-11
I'm having the same problem as holomorph.  Just installed Feisty Fawn today, and Firefox doesn't see any web pages, but Konqueror does (which is how I'm writing this).  I too am surprised others haven't had this problem.

---

### Post by holomorph on 2007-05-11
I think your problem is different from mine: I can see almost any web page in firefox, it's just the mdsplus.org site that's giving me trouble.

---

### Post by obenauer on 2007-05-11
I found a bizarre but effective solution at this link:

[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/95241](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/95241)

Type about:config in the address bar to get to Firefox's settings, right-click on general.useragent.extra.firefoxComment, and change its value from "(Ubuntu-feisty)" to just "(Ubuntu)".  Then close and restart the browser.  After that, I was able to go to any web page in Firefox.

I can't imagine why this would work, but it did.

Note:  I just saw your reply that we may not have the same problem, so I don't know if this will help.

---

### Post by holomorph on 2007-05-11
wow, that works like a charm. . .wtf?

lol,  apparently having the string 'ist' in the user agent parameter causes whatever firewall they are running to think my computer is infected with ISTbar, which is adware, and drops the connection :P

[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/99759](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/99759)

*sigh*
very wierd.
thanks for the tip :)

---

### Post by JCakeC on 2007-05-17
> **holomorph said:**
> further testing indicates it's not specific to firefox.  So far Firefox, Epiphany, and Galeon get the connection reset, while Dillo, w3m, and lyx do not.

obviously, this has me stumped.

Be advised... Galeon and Epiphany uses Mozilla Engine to run, so you had the same problem on those as it was using the same engine as FF.

Thanks for the solution, I had the same problem. worked like a charm.

---

### Post by holomorph on 2007-05-17
in this case it had nothing to do with using the same engine, only that the user agent string contained "ist".

---

### Post by JCakeC on 2007-05-18
Actually it had. The 3 browsers had the same problem because they share the engine and has the problem with the ist on the configuration. I was trying to compelte the post with the advise, so if ppl is having problems with any of the browsers mentioned, they will know that it's a common error on the engine.

:)

---

### Post by holomorph on 2007-05-18
yes but it's not in the engine, it's in the configuration for each browser; I've fixed firefox (can now go to mdsplus.org) by changing the string in about:config, but epiphany still gets the connection reset because I haven't bothered fixiing it there.

---

### Post by trevorj on 2007-06-30
I too would get the connection reset error when attempting to connect to [www.agri.idaho.gov]("http://www.agri.idaho.gov").  I use Fiesty 7.04 and Firefox 2.0.0.4.  

Yet, I could access it fine from my windows machine (using Firefox).  My windows machine is behind the same router and in the same network as my Linux machine.  Additionally, I hadn't noticed problems with accessing other web sites using my Linux machine.

I then followed the recommendation of changing the [COLOR="DarkGreen"]**general.useragent.extra.firefoxComment**[/COLOR] from '[COLOR="Sienna"]**(Ubuntu-fiesty)**[/COLOR]' to just '[COLOR="Blue"]**(Ubuntu)**[/COLOR]' in the **about:config** --- and now my browser seems to work fine!  Interesting.

---

