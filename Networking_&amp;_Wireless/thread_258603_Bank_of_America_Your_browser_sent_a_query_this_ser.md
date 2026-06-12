---
title: "Bank of America: Your browser sent a query this server could not understand."
date: 2006-09-16
forum: Networking &amp; Wireless
---

### Post by totfit on 2006-09-16
I have inquired about this problem in other forums and it was once mentioned for me to post here. When I try to log in to online banking I get this message: Your browser sent a query this server could not understand. I do not get this message with any other bank. I do not get this message using another ID or by browsing as sudo. I only get this message with my default ID, Bank of America and any browser that I try Opera, Firefox, Konq. etc. I have tried permissions, Java, etc and can't seem to find the solution. Typically, I have lately just been using sudo Opera to log into my bank. Not a major problem as I just have the bank set up as my home page. This is however a perplexing issue. I have inquired in several forums and have yet to receive an answer. I have compared permissions with my default ID and other ID's and can't find a difference. I am using Dapper by the way with the latest updates. Thanks for any help in advance.

Gregg

---

### Post by ubernoob on 2006-09-16
It is strange if the information is diffrent between when you use the browser as sudo and not. You can check out if you are using anoter version.
try:  which firefox
and: sudo - which firefox

---

### Post by spd106 on 2006-09-16
You could use Wireshark (Ethereal) to capture the packets and compare.

---

### Post by totfit on 2006-09-16
> **ubernoob said:**
> It is strange if the information is diffrent between when you use the browser as sudo and not. You can check out if you are using anoter version.
try:  which firefox
and: sudo - which firefox

Versions are the same. This behavior occurs no matter which browser I use.

---

### Post by totfit on 2006-09-16
> **spd106 said:**
> You could use Wireshark (Ethereal) to capture the packets and compare.

Not familiar with Wireshark. Is it in the repositories?

Gregg

---

### Post by spd106 on 2006-09-16
Yeah ethereal is in the universe repo. The original developers forked it and created wireshark early this summer. Going by the changelog there isn't much difference yet, except a few security fixes [http://www.wireshark.org/](http://www.wireshark.org/). 

It will enable you to compare the http headers, ssl encrypted traffic is difficult to make much sense of though.

---

### Post by totfit on 2006-09-16
> **spd106 said:**
> Yeah ethereal is in the universe repo. The original developers forked it and created wireshark early this summer. Going by the changelog there isn't much difference yet, except a few security fixes [http://www.wireshark.org/](http://www.wireshark.org/). 

It will enable you to compare the http headers, ssl encrypted traffic is difficult to make much sense of though.

Well, I downloaded installed an ran comparisons and yes, I can't make sense of it. I could find it useful in the future however.

Thanks,
Gregg

---

### Post by davidomundo on 2007-06-18
I've been able to verify that the problem is caused by Flash.
It seems that the newest version of Flash for Linux does not send a correct query.
Uninstall Flash or use a flashblocker and try logging in.

---

### Post by totfit on 2007-06-18
When I had the problem I was thinking it might be a permissions, java or flash problem, but it only happened with one identity and as far as I could tell everything was the same between identities. 

Gregg

---

### Post by jnesis on 2008-05-18
I had the same issue. Clear the cookies and try again. It worked for me.

---

### Post by totfit on 2008-05-18
Thanks, but it was not cookies. First thing I tried. I never got rid of that problem under that identity. It wasn't just one browser either, but all. I most likely will never know why.

---

### Post by TheBouleOfFools on 2008-06-16
I have this exact same problem. On my desktop (running Gentoo), and only on my desktop, I get this error at Bank of America with Konqueror, Opera, and Firefox. I can however, access the page just fine on my laptop, which is on the same network, with any browser.

I have tried clearing cookies, history, cache... anything. I haven't tried is reinstalling or deleting everything in my home directory. This problem hasn't always existed, however I'm not sure what started it. My best guess would be after a Firefox upgrade, however like I stated earlier, no browser works.

---

### Post by totfit on 2008-06-17
The only thing I know that works is to create a new identity and use that. I never found another resolution not matter what I tried.

---

### Post by phixx2000 on 2008-06-22
I just filled a bug report. Please feel free to add your comments for quick resolution.

[https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/242037](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/242037)

---

### Post by securityJ on 2008-07-17
Hello,

The reason is due to a corrupt flash "cookie".  The flash cookies are global to a user profile...OS profile that is.  Which means, multiple browsers under the same OS account will not solve the problem.  You have 3 options.  1. You can create a new user account, 2. run under sudo to call up an root level browser profile, or 3. simply launch Adobe Flash manager <http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager07.html> and clear your BofA website (or for good measure clear all Flash cookie websites).  Restart your browser and you should be all set.

Hope this helps!  I will copy this post to the Ubuntu thread as well.

---

### Post by deandog on 2008-07-21
> **securityJ said:**
> Hello,

The reason is due to a corrupt flash "cookie".  The flash cookies are global to a user profile...OS profile that is.  Which means, multiple browsers under the same OS account will not solve the problem.  You have 3 options.  1. You can create a new user account, 2. run under sudo to call up an root level browser profile, or 3. simply launch Adobe Flash manager <http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager07.html> and clear your BofA website (or for good measure clear all Flash cookie websites).  Restart your browser and you should be all set.

Hope this helps!  I will copy this post to the Ubuntu thread as well.
I, too, have the same "Bank of America: Your browser sent a query this server could not understand" problem whereupon I went to Adobe Flash manager ... 

[http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager07.html](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager07.html)

... and cleared my BofA website, and still had the same problem.

I then went back and cleared ALL of my Flash cookie websites, and still had the same problem.

I then shut my computer down, restarted, and went back to ,,,

[http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager07.html](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager07.html)

... and saw that all my Flash cookie websites were, as expected,  still deleted / gone.

I then tried to access the BofA website and still received the "Your browser sent a query this server could not understand" message.

---

### Post by totfit on 2008-07-22
> **jnesis said:**
> I had the same issue. Clear the cookies and try again. It worked for me.

Good luck. Didn't work for me along with many other measures. I couldn't get any browser at all to work. Only a new identity would. That is old history however. No problems today.

---

