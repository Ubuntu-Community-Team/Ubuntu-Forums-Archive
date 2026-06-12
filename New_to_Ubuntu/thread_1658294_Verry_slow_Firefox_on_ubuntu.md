---
title: "Verry slow Firefox on ubuntu"
date: 2011-01-02
forum: New to Ubuntu
---

### Post by WrathofTux on 2011-01-02
Hi my firefox on ubuntu is extreamly slow compared to how fast it is when im on w7 (have both) on my w7 installation i can have >35 tabs up on the same time without any lagg, but on ubuntu firefox i can't see 1 stream because its so slow, any help here please? 

sorry for noob question :lolflag:

---

### Post by blazemore on 2011-01-02
I'm going to troll and say: Try installing Chromium from the Software Centre. It absolutely flies on Ubuntu, and is generally a better browser full stop.

FYI Chromium is Google Chrome, but without the Google branding and sending your data to Google.

---

### Post by perspectoff on 2011-01-02
Does Chromium have all the Gecko plugins? I can't live without the Gecko plugins that are available for Firefox and Rekonq (formerly Konqueror).

Is AdBlock Plus and NoScript available for Chromium, for example?

I agree about not wanting to use Chrome if you don't want all your private data sent to Google.

---

### Post by HermanAB on 2011-01-02
Slower performance than on Windows, is usually due to a lame domain name server.  Test the name servers in /etc/resolv.conf using dig:
$ cat /etc/resolv.conf
nameserver w.x.y.z

$ dig @w.x.y.z [www.google.com](www.google.com)
and look at the response times.

Put the best name server at the top of the list in resolv.conf.

BTW, for comparison, the Google name servers are 8.8.8.8 and 8.8.4.4

---

### Post by blazemore on 2011-01-02
> **perspectoff said:**
> Does Chromium have all the Gecko plugins? I can't live without the Gecko plugins that are available for Firefox and Rekonq (formerly Konqueror).

Is AdBlock Plus and NoScript available for Chromium, for example?

I agree about not wanting to use Chrome if you don't want all your private data sent to Google.

It has adblock, noscript and lastpass.
Used to be that adblock merely stopped the ads from displaying in Chrome, but now it blocks them from downloading at all.

---

### Post by ajgreeny on 2011-01-02
Whilst I agree that chromium is a bit faster than FF, it is not so different on my system that it makes me use it.  I don't like the look of it either, but that is actually of very little consequence, as far as I'm concerned.

However what annoys me most is the generally slow scrolling in long pages, eg forum pages here, which are always jerky, the terrible favourites handling in comparison to FF, the horrible way it deals with tabs with no consistency, the lack of a good RSS feed handler compared with the bookmarks toolbar, and the current lack of several other FF add-ons that I just can't live without.

So my question back to you is - what is making FF so slow for you, and what exactly do you mean by slow?
Is it slow to start, slow to load pages, slow to render pictures, or is everything slow?
Have you disabled ipv6 in the **about:config** page of FF.  If not type **about:config** in the addressbar, ignore the warning, search for ipv6 in the filter, and make sure it ends true ```
network.dns.disableIPv6      user set   boolean         true
``` if it says false at the end, double click it to toggle to true, and you may find FF is much faster.

If that does not help it may be that your profile is corrupt in some way, so rename your home folder ~/.mozilla and restart FF.  Maybe it will now run as it should.  You can then get your bookmarks back from the old profile folder.

---

### Post by WrathofTux on 2011-01-02
Thanks for the help! ipv6 was false so i fixed it and now its fast, im fixing so i can dual monitor and when i use both it laggs really bad, not just FF but FF was lagging worst.

edit: It is still loading slow :/

---

### Post by Crusty Old Fart on 2011-01-02
> **WrathofTux said:**
> ...edit: It is still loading slow :/
Here are some changes that made Firefox run faster for me, maybe they'll make it run faster for you as well:

**In about:config:**

[LIST]
[*]Set network.http.pipelining to true
[*]Set network.http.proxy.pipelining to true
[*]Set network.http.pipelining.maxrequests to some number like 30. This means it will make 30 requests at once. Normally the browser will make one request to a web page at a time. When you enable pipelining it will make several at once, which really speeds up page loading. (Note: Setting this higher than 30 may cause some sites to think you are hammering them and ban you.)
[*]Create a new entry by right-clicking anywhere and select New Integer. Name it nglayout.initialpaint.delay and set its value to 0. This value is the amount of time the browser waits before it acts on information it receives. (to check that the creation was successful, filter for: nglayout)
[/LIST]
In addition to the changes made above in about.config, running Adblock Plus and blocking scripts seemed to speed things up a little more.

Good Luck.

Crusty

---

### Post by sandyd on 2011-01-02
check out the link in my sig if you have too much time on your hands and want to speed up firefox.

---

### Post by WrathofTux on 2011-01-03
Thanks!

---

### Post by WrathofTux on 2011-01-03
ATI/AMD proprietary FGLRX graphics driver

---

### Post by darthspringbok on 2011-01-03
I had a problem with flash and the internet running slow and I am using firefox.
 
I took off flash and reinstalled it. 
 
Don't know if this is the solution but it worked for me as it only happened on 1 of the 3 PCs that I use Ubuntu on.

---

### Post by deadpieface on 2011-01-03
Hello all, I tried all of the above and i am still having ridiculous web browsing speeds.  I have system monitor on the top tool bar and when i click a link or search or whatever, it has an initial spike in activity and then drops to nothing.  Eventually but slowly maybe the website will load.  It is very annoying.  Is there any other suggestions maybe?  Like why would this even be happening?  I am a n00b at this too but I just can't figure it out with the knowledge i do have.  I can download and upload files fine....

---

### Post by ubaidillah on 2011-01-04
> **WrathofTux said:**
> Hi my firefox on ubuntu is extreamly slow compared to how fast it is when im on w7 (have both) on my w7 installation i can have >35 tabs up on the same time without any lagg, but on ubuntu firefox i can't see 1 stream because its so slow, any help here please? 
 
sorry for noob question :lolflag:
 Try to clean install the firefox.
 
Cheers

---

### Post by Crusty Old Fart on 2011-01-04
> **ubaidillah said:**
> Try to clean install the firefox...
That's the right answer. It would be a lot easier and faster than having the rest of us try to figure out what's wrong with it.

---

### Post by WrathofTux on 2011-01-04
Ill reinstall FF and report back, think it is a problem with 2 monitors tho, everything laggs even terminal laggs. >,<

---

### Post by WrathofTux on 2011-01-04
Thanks! installed firefox 3.6 and the loading speed is great! i still have the lagg with all windows :< but thats another story

---

