---
title: "For the Love of God!!!!!!!!! (Proxies)"
date: 2007-05-18
forum: Networking &amp; Wireless
---

### Post by Seer on 2007-05-18
Call me what you will....

But it is the year 2007. In the century where even Buck Rogers was able to roam the universe! We (the general population) have had this new fangled interwebtubes for over a decade and for 90% of the world's corporate users... this is from behind a proxy that requires authentication.

So tell me, why is it that no linux distro (not even the most popular and widest used distro!) can manage something so simple without all kinds of ridiculous hoops to jump and somersault through?

Why even bother having a menu entry in gnome to enter these details? This setting certainly doesnt seem to be used by any actual programs! In fact I am counting 7 different places I have  had to set up proxy details so far and STILL apt-get doesn't work.

Maybe its simpler for those behind non authenticating proxies, but as noone is stupid enough to go without authentication in any company I have ever worked for, it's besides the point!

This is basic, fundamental, CRITICAL functionality that makes Ubuntu (and the rest) look like an old hackers platform. This is the sort of thing that drives the even system architects like me crazy, and drives the average user to hop straight into the Windows comfy chair again.

For the love of god, please, help me convince my bosses that Linux is the way to go? At the moment I am gonna have to describe all these places to change something so simple..... AND THEN we will have to do it EVERY SINGLE MONTH FOR EVERY USER AGAIN WHEN THEIR PASSWORD CHANGES!

Cost of ownership anyone?

/rant

---

### Post by kidders on 2007-05-19
Hi there,

> **Seer said:**
> So tell me, why is it that no linux distro (not even the most popular and widest used distro!) can manage something so simple without all kinds of ridiculous hoops to jump and somersault through?Linux normally makes it quite easy to use proxies. What it _won't_ do is allow you to force all applications to obey the same proxy policy (which would be undesirable, even if it were possible). In any case, applications normally require no more than a minor configuration tweak or an appropriate environment variable.

> **Seer said:**
> Why even bother having a menu entry in gnome to enter these details? This setting certainly doesnt seem to be used by any actual programs!Except Gnome, perhaps? Most users would find it surprising (to say the least) if asking one application to use a proxy suddenly overwrote the configurations of others.

> **Seer said:**
> At the moment I am gonna have to describe all these places to change something so simple..... AND THEN we will have to do it EVERY SINGLE MONTH FOR EVERY USER AGAIN WHEN THEIR PASSWORD CHANGES!

Cost of ownership anyone?Shell scripts are free!

---

### Post by Seer on 2007-05-19
Hi Kidders

You must be used to some incredibly strange environments... I have never worked for an organistion that has used more than one proxy server address for the whole organisation. We are talking 5000 to 50000 users here and any other system would be insanity.

So one configuration writing to that change to applications is EXACTLY what a corporate wants.

Shellscripts are free, asking all 25000 users (in our case) what their new passwords are once a month is not desirable and certainly not free.

Several critical components need the user's password in clear text in a config file or 3! It's laughable on the security front, and makes scripting such a thing nigh impossible.

I hate to say it but, but windows manages it better, and since about windows 95!

---

### Post by kidders on 2007-05-19
Hey again,

> **Seer said:**
> So one configuration writing to that change to applications is EXACTLY what a corporate wants.That's very unlikely to be true. One obvious example is apt-get. If an organisation is large, forcing software updates through a HTTP proxy intended for use by web browsers would be totally insane!

> **Seer said:**
> asking all 25000 users (in our case) what their new passwords are once a month is not desirable and certainly not free.Again, this is a curious observation. It seems to me that, ideally, users should be asked for their proxy passwords far more frequently than that.

> **Seer said:**
> Several critical components need the user's password in clear text in a config file or 3! It's laughable on the security front, and makes scripting such a thing nigh impossible.In security terms, your focus is in the wrong place, imo...
[LIST]
[*]I'm assuming you trust the permissions management that is protecting your users' files, as an effective means of keeping people out of each others' data.
[*]Proxy passwords are hardly critical pieces of information, so making the files that store them readable only by the user to whom they apply should be more than adequate protection ... especially if they're regularly changed (which seems to be the case).
[*]The *real* point of vulnerability for proxy authentication information is usually the network itself. For compatibility reasons, many applications use basic HTTP authentication (which might as well be plain text), revealing proxy passwords to anyone with a packet sniffer.
[/LIST]

I'm pretty sure that, if you consider it for a while, your proxy configuration won't turn out to be nearly as complicated as you think ... especially since you will obviously want users to enter their passwords at least once per login.

---

### Post by Seer on 2007-05-21
Why should users be asked for their proxy password?

Once they are logged on to a PC and authenticated they are able to work within the environment without having to deal with constant proxy prompts in Windows. I for one would be insanely annoyed to be asked for my proxy password every time I pop open a browser.

That's my point, it should be seemless, I am a unix/linux fan but have to say Windows has it down when it comes to this.

But all this is beside the point, In the last 10 years I have worked at probably 30+ firms (as employee or consultant) and every one of them has had a single proxy (though it may be a cluster of machines) for users. They have all authenticated. They have all used the same proxy for all applications. They have all been seamless using an authenticated NT or AD session. I can guarantee you not one of them has had users entering passwords for proxies.

Ubuntu could at least start with the basics, when entering proxy info into the gnome menu item, it should be aopplied to the core system essentials, apt, the browser, the ftp client, ssh, etc. That alone would make it least seem like a 1990's operating system :/

---

### Post by kidders on 2007-05-21
Since you seem determined to believe that Linux cannot meet your needs, I don't know if I can do very much for you. The simple suggestions I've made already (for instance that, in practice, apt is obviously not normally proxied in a corporate environment) are based on years of experience with Linux ... but you seem intent only on finding fault. For example, I never once implied that any company network I've worked with used more than one proxy server!

If you feel like actually solving your problem, I strongly suggest re-posting your issue at some point.

---

### Post by Seer on 2007-05-22
A nice tardy tone, but non the less I will play ...

You seem very defensive of the whole situation, taking apt one example out of dozens of apps that require proxy settings. I don't believe I have said anywhere I am determined that Linux cannot help me, the OP and resultant posts are suggestions for easing administrative overhead for corporate users, whilst also putting a nice shine on usability for home users. 

In a complex environment such as the AIX clusters we run, with all kinds of complex firewall, routing, and similar network granularity required, this current situation would be acceptable... perhaps even desirable.

But here we want desktops, remember my goal here... to convince Directors (mostly non IT inclined) that we would be better served by using Linux as a desktop with Ubuntu, Debian, FC as some of the obvious candidates. That goal is not served by explaining that something that should be so simple, and that is controlled with a policy and AD authentication in the current Windows environment is going to be (as far as we can see so far) expensive in terms of time and manpower for us to manage in a prospective Linux build. 

I am not on a witch-hunt here, just looking for some light on the horizon, or even that we may have missed something, and gosh-darn-it .... perhaps even suggesting an improvement .... the horror of it all!

---

