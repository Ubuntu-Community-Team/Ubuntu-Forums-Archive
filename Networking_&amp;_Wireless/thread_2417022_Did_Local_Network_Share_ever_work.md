---
title: "Did Local Network Share ever work?"
date: 2019-04-19
forum: Networking &amp; Wireless
---

### Post by palteater on 2019-04-19
Hi. Just upgraded my HTPC to 19.04.

Does (or did) Local Network Share actually (ever) work? 

I mean when you right-click on a folder and choose "Local Network Share" and tick the "Share this folder". I think I have tried it on every iteration since 14.04 or such, and it never worked and it still doesn't.

Because when I go to my other computer (still on 18.10) and look in "+ Other Locations" I do see the 19.04 computer under Networks, and when I double-click it I do see the "shared" folder, plus print$, and when I double-click it I do get the "Password required" where I tick Registered User, enter Username, guess that the Domain is right, enter password - but it never accepts and just flips the same dialog back up, this time greyed out.

It has always been like this, and my go-to method has been to arduously set up a Samba share manually instead - but I have a nagging suspicion that there should be a simpler way. Why else would the Local Network Share thing even exist, if it has been broken for 5+ years?

So please: can someone shed some light on what I am doing wrong? What magic tick box did I forget to click?

I don't much fancy the idea of stabbing and guessing in smb.conf again. Last time I spent two days troubleshooting before I realized that the documentation did not mention that I needed to add myself to the Samba group and set the password. 
This time, it turns out that the 19.04 version of system-config-samba does not even exist. There is always something like that.

---

### Post by Morbius1 on 2019-04-19
Yes indeed it still works. I just installed Ubuntu 19.04, shared a folder, and accessed it over the lan. The whole process took me two minutes. Seriously ... two minutes.

It would have taken a bit longer I suppose had I required a username and password be passed before access was granted. Then I would have to create a local user on Ubuntu ( or used my own login user name ) then added that user to the samba password database:
```
sudo smbpasswd -a morbius
```
So ... I don't know ... add another minute to the total time?

---

### Post by palteater on 2019-04-19
Huh. You are right. Many thanks!

It turned out I only added myself to the Samba group which of course is not the same thing. I wonder how many times I have ground to a dead stop here and only much later gotten to the password thing during the process of setting up smb.conf. 

It does strike me as odd that there is this convenient menu thing where we just click "share" and everything required is installed automagically - except for that it doesn't work unless you also pull up the terminal and type in admin commands, which it neither informs you of or offer to help you with. And the resources on the net I find does not mention this either but are curiously content with telling us to enable "Guest access", which is not quite a security best practice.

---

