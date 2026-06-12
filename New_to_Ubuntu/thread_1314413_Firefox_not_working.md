---
title: "Firefox not working"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by donaldshelton on 2009-11-04
I upgraded the Ubuntu Christian Edition from 9.04 to 9.10.

Now I am afraid that Firefox doesn't connect to the internet.

I am connected, as Pidgin works, and I am able to use synoptic to get new packages.

I made sure that the box next to offline (file-work offline) is unchecked.

When I try to load a page, it says connecting to (page), but it never loads.

I had conkeror installed, but removed it. 

What else should I do to troubleshoot?

Don

---

### Post by Little Girl on 2009-11-04
What are your settings if you click the Settings button after opening Edit --> Preferences --> Advanced -->> Network in Firefox?

---

### Post by donaldshelton on 2009-11-04
The setting for network is "no proxy".

Should I change this?

Thanks

Don

---

### Post by philinux on 2009-11-04
Try running firefox in safe mode.

Open a terminal. Apps>access>terminal

```
firefox -safe-mode
```

---

### Post by donaldshelton on 2009-11-04
I tried that--no luck!!

---

### Post by Jcdlvsrbld on 2009-11-04
uninstall and use swiftfox. if you dont want to do that, try reinstalling firefox (upgrade to 3.5) and check your proxy settings

---

### Post by Little Girl on 2009-11-04
Mine is **Use system proxy settings** and I haven't made any changes in those settings. I doubt it would help to change it, because I think the system default **is** no proxy, but I suppose it's worth a try.

Another thing you could try is to run Firefox from the command line by opening a terminal and typing **firefox** to see if the terminal shows any errors during the session.

This may be deeper than just a Firefox issue. Can you successfully do all the network tests Koybe recommends in [this thread]("http://ubuntuforums.org/showthread.php?t=144771")?

---

### Post by -=hazard=- on 2009-11-04
> **donaldshelton said:**
> I upgraded the Ubuntu Christian Edition from 9.04 to 9.10.

Now I am afraid that Firefox doesn't connect to the internet.

I am connected, as Pidgin works, and I am able to use synoptic to get new packages.

I made sure that the box next to offline (file-work offline) is unchecked.

When I try to load a page, it says connecting to (page), but it never loads.

I had conkeror installed, but removed it. 

What else should I do to troubleshoot?

Don

[Forget firefox. Totally remove it and try Opera for 10 minutes ;)]("http://www.opera.com/browser/")

---

### Post by wojox on 2009-11-04
See here [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567"). Scroll down to **Solution [FOT005]:**

---

### Post by Crunchy the Headcrab on 2009-11-04
You might have the DNS error that a lot of Karmic users have been experiencing.  Click system > preferences > network connections and on the IPV4 tab select dhcp (addresses only).  Then input your isp's recommended dns servers manually in the box titled dns.  Restart your pc.

---

### Post by donaldshelton on 2009-11-04
Thanks to all who have replied.

I tried everyone's suggestions, only to find none have solved the problem.

We happen to have another identical computer running Ubuntu 4.10, and I have copied all of the settings, etc. from it onto the one we are having difficulty with.  No help.

I guess what I should do then is to reinstall the OS.  I only have it in the 4.04 version, which I may just leave as is.  I didn't have any trouble until i "upgraded" to 4.10.

I'll check back in a few moments in case someone has posted another idea.

BTW  How do I get Opera?  It's not listed in Synaptic or Ubuntu Software Center

---

### Post by stoogiebuncho on 2009-11-04
Though I don't know how to fix it, I think I might know what your problem is.

Ubuntu Christian Edition uses dansgaurdian to block unwanted content on the internet.  So I'm pretty sure that firefox SHOULD be connecting to the internet through a proxy.  

The problem is that I don't know what your proxy settings should be.  But if you spend a little time on Google and see if you can find what proxy settings you should use if you are using dansgaurdian, that may solve your problem.

If you can't find anything, post back.  I may have some time to help you look later on.

Edit:  You can download Opera from their website.  It's not in synaptic.  Download the .deb file and double-click it to install.

---

### Post by dearingj on 2009-11-04
> **donaldshelton said:**
> Thanks to all who have replied.

I tried everyone's suggestions, only to find none have solved the problem.

We happen to have another identical computer running Ubuntu 4.10, and I have copied all of the settings, etc. from it onto the one we are having difficulty with.  No help.

I guess what I should do then is to reinstall the OS.  I only have it in the 4.04 version, which I may just leave as is.  I didn't have any trouble until i "upgraded" to 4.10.

I'll check back in a few moments in case someone has posted another idea.

BTW  How do I get Opera?  It's not listed in Synaptic or Ubuntu Software Center

There is no Ubuntu 4.04. Perhaps you meant 9.04? :)

You can download opera from this page:
[http://www.opera.com/browser/download/](http://www.opera.com/browser/download/)

---

### Post by donaldshelton on 2009-11-04
OK  folks

I reinstalled Ubuntu CE 9.04 and things are now working.

I notice on this version that Dansguardian GUI is listed in the system-administration list.  Was this there in version 9.10?  I have disabled it on this version.

So much for upgrading!!!

Thanks again to all who offered their help!!

Don

---

### Post by -=hazard=- on 2009-11-05
> **donaldshelton said:**
> OK  folks

I reinstalled Ubuntu CE 9.04 and things are now working.

I notice on this version that Dansguardian GUI is listed in the system-administration list.  Was this there in version 9.10?  I have disabled it on this version.

So much for upgrading!!!

Thanks again to all who offered their help!!

Don

What? You reinstalled Ubuntu because of firefox...? Anyway [COLOR="Red"][click here]("http://www.opera.com/download/get.pl?distro=ubuntu&id=32521%2C32527%2C32526&pack=&location=237&sub=++++")[/COLOR] to download a .deb package of latest opera version for karmic and try it.

---

