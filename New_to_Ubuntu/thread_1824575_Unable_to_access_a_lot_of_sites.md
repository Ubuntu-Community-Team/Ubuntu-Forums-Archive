---
title: "Unable to access a lot of sites"
date: 2011-08-14
forum: New to Ubuntu
---

### Post by troublemackr on 2011-08-14
Hello.

I've got a strange problem. I can't access a lot of sites. Most of them shows "403 Error - Forbidden". Some like google and msn doesn't show 403, but it redirects to strange sites.

But some like yahoo, facebook and twitter works.

I've tried firefox and chrome, both have the same behavior.

I'm currently using Ubuntu 11.04 dual booted with windows vista. Vista does not have this issue.

Thanks.

---

### Post by LowSky on 2011-08-14
have you installed any new software or plugins recently?

403 error usually means there is a problem with the information you requested.

what are the sires you are being redirected to?

---

### Post by troublemackr on 2011-08-14
> **LowSky said:**
> have you installed any new software or plugins recently? 

Only chromium to see if it has the same problem.

Xnethack freeciv and xchat about a week ago. Didn't have this problem even after installing.

>  what are the sires you are being redirected to?

When trying google, it is still google.com. But the title becomes "google.com | Google Argentina | Google Video | Ebay | Google Talk" instead of just "google". sometimes the title change again.

This site loads very slowly. The progress bar always shows "sending request" or "waiting for p.chango.com..."

when it really loads it shows a barebone site with a search bar.

Just tried using a proxy server, anonymouse.org, and it does not have this issue.

---

### Post by zeroseven0183 on 2011-08-14
Have you tried Firefox with all the add-ons disabled? 

Can you try these
1. [http://support.mozilla.com/en-US/kb/Searches%20are%20redirected%20to%20another%20site](http://support.mozilla.com/en-US/kb/Searches%20are%20redirected%20to%20another%20site)
2. [http://support.mozilla.com/en-US/kb/Safe%20Mode](http://support.mozilla.com/en-US/kb/Safe%20Mode)
3. [http://kb.mozillazine.org/Standard_diagnostic_-_Firefox](http://kb.mozillazine.org/Standard_diagnostic_-_Firefox)

---

### Post by elgordodude on 2011-08-14
You got jacked!

A strange google page is a hallmark of this problem. Good news, it's probably not an ubuntu problem, bad news, someone is very likely trying to use your computer in ways it wasn't meant to, and you probably don't want it to.

This is likely due to an unintentionally installed app, or even theoretically, just a super malicious line of code on a web site. Hopefully you're not to attached to your current firefox settings and bookmarks, in which case you can uninstall and reinstall firefox with:

```
sudo apt-get remove mozilla-firefox && sudo apt-get install mozilla-firefox
```If you need the bookmarks, settings, preferences, etc, we can try and track down and remove the offending app, but if I were in your boat my preference would be to burn first and ask questions later.

---

### Post by troublemackr on 2011-08-14
> **zeroseven0183 said:**
> Have you tried Firefox with all the add-ons disabled? 

Can you try these
1. [http://support.mozilla.com/en-US/kb/Searches%20are%20redirected%20to%20another%20site](http://support.mozilla.com/en-US/kb/Searches%20are%20redirected%20to%20another%20site)
2. [http://support.mozilla.com/en-US/kb/Safe%20Mode](http://support.mozilla.com/en-US/kb/Safe%20Mode)
3. [http://kb.mozillazine.org/Standard_diagnostic_-_Firefox](http://kb.mozillazine.org/Standard_diagnostic_-_Firefox)

tried them all and didn't work. Issue still persist.

> **elgordodude said:**
> ```
sudo apt-get remove mozilla-firefox && sudo apt-get install mozilla-firefox
```

Just tried it and it didn't work. Here's what is written on the terminal:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Virtual packages like 'mozilla-firefox' can't be removed
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.38-8 libnspr4-0d linux-headers-2.6.38-8-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mozilla-firefox is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'mozilla-firefox' has no installation candidate
```

---

### Post by zeroseven0183 on 2011-08-14
If you're looking in to reinstalling Mozilla Firefox, the correct package name is 'firefox'. But I doubt it would fix the problem since you mentioned disabling the add-ons didn't work.

---

### Post by troublemackr on 2011-08-14
Out of curiosity, I disconnected my adsl internet connection and tethered my phone to the computer and tried accessing the sites with firefox.

And I can access those inaccessible sites!

But there are still some problems. I tried several scenarios with tethering and these are what happened.

scenario 1. With firefox closed, disconnect adsl, connect tethered phone to computer, start firefox and try to open sites. Issue does not happen.

scenario 2. start firefox, open sites with adsl connection, disconnect adsl, connect phone and try to open sites. Issue happens.

scenario 3. After doing scenario 1, disconnect phone and connect adsl, then use the firefox from scenario 1 to open sites. Issue happens.

This means that the modem or at least the configuration is wrong, right?

---

### Post by babakott on 2011-08-14
Could some errant lines in the hosts file cause this problem?

---

### Post by troublemackr on 2011-08-14
Today has been weird, really weird.

I can access all those websites again now! I don't know what happened, they just started working again all of a sudden!

I guess this is solved now. Thanks for your help, everyone.

---

### Post by XubuRoxMySox on 2011-08-14
Sounds like the issue was with the DSL Internet Service Provider, not with your software. Perhaps they will post a little notice up on their default home page or something to explain it.

---

