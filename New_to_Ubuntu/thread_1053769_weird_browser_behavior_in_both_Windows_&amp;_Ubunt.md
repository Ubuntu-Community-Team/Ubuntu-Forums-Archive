---
title: "weird browser behavior in both Windows &amp; Ubuntu"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by rockerphil on 2009-01-29
ok, i know this isn't really the forum to post this problem to, but hopefully i can get some help on it. a friend has been fighting with a problem on his Windows conmputers i havn't encountered until now and i'm baffled. here's the deal. when he does a search through any search engine (Google, Yahoo, doesn't matter) it will complete the search just fine, but when the desired link is clicked it redirects both IE and Firefox (doesn't matter what browser you use) to a random site. now comes the interesting part. i've scanned both Windows machines and they're clean, so i dual booted one with Kubuntu, and it does the same thing in both Konquerer and Firefox, well, the home is running a router to connect both computers to the net, so i disconnected the router and just connected the DSL modem to the primary machine and lo and behold the problem is gone, so i'm sitting here trying to figure out WHY this is happening. any suggestions guys? much thanx in advance,

Phil

edit: but what's really weird is when the URL at the bottom of the desired link is typed in to the address bar of the browser it goes directly to the site.

---

### Post by kansasnoob on 2009-01-29
I read about such a "virus" a few weeks ago but I've not seen it in Firefox!

I've never used Konqueror or Evolution or Thunderbird.

---

### Post by AlucardArg on 2009-01-29
Just some guesses, and nothing sure about this, as I've never heard of anything like it:
1) Restart the router. If you know the settings, or if they are automatic, try to reset it to factory default.
2) I doubt it, but it may be some kind of strange problem with your DNS server. Try using OpenDNS server, or any other.

---

### Post by kansasnoob on 2009-01-29
Is this happening on Firefox 3.05?

I've not seen it and I do some risky surfing!

---

### Post by Temposs on 2009-01-29
So, suppose you delete your firefox profile(easy way is to delete the ~/.firefox directory) and try the action that causes the problem again. Does that change the result?

---

### Post by rockerphil on 2009-01-29
yes, it's happening in FF3, as well as every other browser i try in both Windows & Kubuntu, but as i said earlier, when the router is taken out of the picture the problem is gone. yes, i've tried rebooting the router, several times, and the router doesn't have a reset button that i knows of, yes, i know, weird.

---

### Post by The Joe on 2009-01-29
> **kansasnoob said:**
> Is this happening on Firefox 3.05?

I've not seen it and I do some risky surfing!

Risky or risque?

Anyway, what country are you in? Is it possible that you've somehow started to have your internet service censored? If this happens on more than one OS and different browsers it's certainly not a Virus.

Try restarting the router as mentioned before and contact your ISP to see if you've been capped, filtered or censored some how.

---

### Post by rockerphil on 2009-01-29
i live in the US, so i seriously doubt i'm being censored, and yea, i figured i'd need to onctact my ISP, i was just trying to avoid "allo, velcome to <companyname> teck sooport"

---

### Post by The Joe on 2009-01-29
Ah, bloody call centres... We keep getting bothered by some Indian call centre because... Well actually I have no idea!

But try restarting the router before calling them, if they're anything like my ISP they won't be too happy if you're using a router.

---

### Post by rockerphil on 2009-01-29
well seeing as the problem is non-existant when the router is taken out of the equation i think I'm gonna be making a call to Lynksys, much thanks for the suggestions guys,

Phil

---

### Post by kansasnoob on 2009-01-29
> Risky or risque?

Both! But regardless I've not seen that behavior!

---

### Post by 73ckn797 on 2009-01-29
Access the router and reset everything to default. Then see what happens.

Enter: ```
http://192.168.1.1/
``` in the address bar to access router.

---

