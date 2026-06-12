---
title: "Firefox address bar searches"
date: 2009-12-26
forum: New to Ubuntu
---

### Post by cmcanulty on 2009-12-26
I have set my firefox to search with google from the address bar at about:config, yet it still goes to yahoo. I even changed it to yahoo and then back to google and it shows google but goes to Yahoo which I hate. I hope someone can help solve this

---

### Post by 0cton on 2009-12-26
get used to yahoo search you will love it in time.
you love google just cause you got used to it. human nature.

---

### Post by cartisdm on 2009-12-26
> **0cton said:**
> get used to yahoo search you will love it in time.
you love google just cause you got used to it. human nature.

maybe, maybe not.  personally, I hate yahoo searches.

Another thing you can try is installing the add-on Omnibar.  I love it and its one of my first add-ons I install every time.  It works just like the search bar in Google Chrome browser

---

### Post by peakshysteria on 2009-12-26
> **cmcanulty said:**
> I have set my firefox to search with google from the address bar at about:config, yet it still goes to yahoo. I even changed it to yahoo and then back to google and it shows google but goes to Yahoo which I hate. I hope someone can help solve this

Mozillazine might be your friend: [[COLOR="Red"]Search Bar[/COLOR]]("http://kb.mozillazine.org/Search_Bar#Managing_search_engines")

---

### Post by Sir Jasper on 2009-12-26
Hi,

It might help if  you advise which version you are using and where it happens - meaning:

is it when you have the opening Firefox screen search box usually seen when Firefox first opens and also when you click on the House icon?
Or is it, instead or as well, if you press Ctrl + K or directly use the other search box?
Also do you have a down arrow next to the G in the Ctrl + K box and can you select from a number of search engines and use them?

My regards

I understand this is irritating, but does it mean that your hyper serious problems from some weeks back are now resolved.

---

### Post by cmcanulty on 2009-12-26
I am talking about typing it a term in the address bar which firefox is supposed to send to the preferred serach engine but it uses yahoo instead of google. I think they also call it the awesome or location bar. I could use the google search box but the address bar zeroes in on places you've been before, even quite a long time ago.

---

### Post by Sir Jasper on 2009-12-26
Hi again,

If you perform a new search (not a replication of a previous one) is Google used?

If the answer is yes, then you could try clearing the Search History - unless there is a better suggestion.

---

### Post by peakshysteria on 2009-12-27
> **cmcanulty said:**
> I am talking about typing it a term in the address bar which firefox is supposed to send to the preferred serach engine but it uses yahoo instead of google. I think they also call it the awesome or location bar. I could use the google search box but the address bar zeroes in on places you've been before, even quite a long time ago.

You're not clarifying your problem. If you want to remove (the idiotic) Awesomebar there are several threads about this. I'm not sure this really is your problem. View the link from my above post for a more indept explanation of locationbar, searchbar and history among other things. Anyways, to remove the so called the Awesomebar:

> How to Completely disable the AWESOME BAR!

1. In the URL Address bar, type about:config and press Enter.

o The about:config "This might void your warranty!" warning page may appear. Click I'll be careful, I promise!, to continue to the about:config page.

2. Search for the preference browser.urlbar.maxRichResults.

3. Double-click the browser.urlbar.maxRichResults preference and enter a value of -1.

4. Whilst there also double-click browser.urlbar.matchOnlyTyped to change it to True ...... it is directly above browser.urlbar.maxRichResults

5. From the menu at the top of the Firefox windowbar, select File and then select Exit.

6. Start Firefox again.

Tell us if this really is part of your problem and if it helped.

---

### Post by cmcanulty on 2009-12-27
I don't see where to clear search history, there used to be an option under preferences for clear private data, but it is not there in firefox 3.5 or else it is somewhere I didn't see. I am specifically talking about searching from the awesome bar. It is supposed to use the search engine you specify in about:config in the line keyword.url mine however goes to a yahoo search no matter what I enter under keyword.url for the preferred search provider, thanks.

---

### Post by sliketymo on 2009-12-27
you have to set it to" Use custom settings for History".

---

### Post by cmcanulty on 2009-12-27
I have it set to custom settings for history. I downloaded the ommnibar and it goes to google as I set it so I will ignore the other problem and use the omnibar, thanks all.

---

### Post by cartisdm on 2009-12-28
> **cmcanulty said:**
> I have it set to custom settings for history. I downloaded the ommnibar and it goes to google as I set it so I will ignore the other problem and use the omnibar, thanks all.

Cool, glad to see the omnibar helped.  I love it but I have found it to be slightly buggy when you have AUTOCOMPLETE turned on for firefox (so that you don't have to type full addresses).

Also, it doesn't seem to integrate well with the FasterFox (smarterfox) add-on.

---

