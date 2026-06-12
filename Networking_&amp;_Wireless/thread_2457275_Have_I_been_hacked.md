---
title: "Have I been hacked?"
date: 2021-01-29
forum: Networking &amp; Wireless
---

### Post by garyed on 2021-01-29
For a couple days I experimented with hosting my own site by routing a domain name to my computer. I didn't really want any outside traffic but i found i was getting a few visitors & i didn't have confidence in my password security. So i decided to unlink the domain name so at least someone would have to get my ip address to get to my site . I found that I was still getting a few visitors each day so I decided to use a password through .htaccess. Everything seemed to be working & as far as I could tell no more visitors were getting in to my site. Now I find that two of my directories will not work through either browser, Chrome or Firefox. When I go to localhost to work on my site & to those two directories I just get"
> This site can’t be reached
localhost refused to connect.
Try:
Checking the connection
Checking the proxy and the firewall
ERR_CONNECTION_REFUSED
     

I've checked permissions & can't find anything different than my other directories that do work. All my files are still there so I'm a little confused. I have plenty of other directories on my site still working. 
I have messed with some configuration files to get .htaccess password to work but I can't even remember what I did. I tried removing the .htaccess file but that didn't help either.
Any ides?

---

### Post by garyed on 2021-01-29
A little more info,
If I move the files to another directory with the same permissions, everything seems to work fine.
I assume there is a way in the Apache config files where those specific directories could be blocked but I don't know where to look.
Can anyone think of any other way that specific directories could be block?

---

