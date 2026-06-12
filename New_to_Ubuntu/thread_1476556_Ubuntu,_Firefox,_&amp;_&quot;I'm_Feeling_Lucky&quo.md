---
title: "Ubuntu, Firefox, &amp; &quot;I'm Feeling Lucky&quot;"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by WandersFar on 2010-05-07
Hello,

I'm a new Ubuntu user (just switched over from Windows) and I noticed that the behavior of Firefox's Location Bar in Ubuntu is somewhat different than from what I'm used to.

Specifically, if I hit Ctrl+L and type any one word query, (e.g., "ubuntu") instead of being taken to Google's top hit or "I'm Feeling Lucky" page, I get routed to a "Domain Not Found" search page from my ISP.

Under Windows, if I were to hit Ctrl+L in Firefox and type "ubuntu", I'd get sent to the main Ubuntu page.

How can I get this behavior in Ubuntu?

---

### Post by cariboo on 2010-05-08
You don't need to press Ctrl-L, just type ubuntu in the url bar, and you'll be taken to Ubuntu's home page

---

### Post by WandersFar on 2010-05-08
Thanks for responding, but I think you may have misunderstood me.

Ctrl+L is the Firefox shortcut to give focus to the Location bar.

But regardless of whether I use the keyboard shortcut or click on the bar, anytime I enter a one word query, I get sent to a domain not found page.

---

### Post by detroit/zero on 2010-05-08
Try ALT+D. Same shortcut, only different. 

Also, if a search is what you want, CTRL+K takes you to the search bar, then CTRL+&#8593; or CTRL+&#8595; to get the search you want.

EDIT: Oh, I just saw your searches are screwed up from the URL bar.

Try this: Open a tab and type **about:config** in the bar. Enter "search" as a search string in the bar provided.

Look for the following keys and make sure they have the following values:
> browser.search.defaultenginename;Google
keyword.URL;[http://www.google.com/search?ie=UTF-8&oe=UTF-8&sourceid=navclient&gfns=1&q=](http://www.google.com/search?ie=UTF-8&oe=UTF-8&sourceid=navclient&gfns=1&q=)

---

### Post by flyfishingphil on 2010-05-08
I'm using Lucid and Firefox for my browser. Tried your method and quit when it hadn't opened anything yet after about 10 sec. Went to my search bar and typed in Ubuntu and had it there in about .5. Then went back, opened a blank page, did the Ctrl L and typed in the name of my website(ffpc-rods.com). Was there in about .5.

I've never used your method in looking up sites, just always gone to the Google search bar. Fast and easy every time. May be a problem in Firefox in doing the search using the URL bar with just a word.

---

### Post by detroit/zero on 2010-05-08
Well, hold on a second. You're interchanging terms.

CTRL+L is a shortcut to the URL bar (so is ALT+D)
CTRL+K is a shortcut to the search bar

Are you saying that if you use either the address bar, or Google in the search bar, your searches are not coming up? Or, does one work and the other doesn't?

---

### Post by WandersFar on 2010-05-08
(By the way, I appreciate all of you taking the time to help me figure  this out. :))

Okay, here's another example:

In XP, if I go to the Location/Awesome/URL bar (by either Ctrl+L, Alt+D, or clicking) and type "lifehacker" this is where I'm sent:
[http://lifehacker.com/](http://lifehacker.com/)

In Ubuntu, if I do the exact same thing, this is where I'm sent:
[http://search.domainnotfound.optimum.net/cablevassistsearch_keyword/ws/results/Dns/lifehacker/1/0/0/Relevance/iq=true/zoom=off/_iceUrlFlag=7?_IceUrl=true](http://search.domainnotfound.optimum.net/cablevassistsearch_keyword/ws/results/Dns/lifehacker/1/0/0/Relevance/iq=true/zoom=off/_iceUrlFlag=7?_IceUrl=true)

But if the term I'm entering in the bar is more than one word, for example, "recipe puppy", than everything is hunky-dory. Under both XP and Ubuntu, I am sent here:
[http://www.recipepuppy.com/](http://www.recipepuppy.com/)

Why do multiple word searches trigger "I'm Feeling Lucky" behavior in the URL bar, and singular word searches don't?


(I am aware that I can perform a google search by either going to google.com or using the search bar, but I find this slower and less elegant than using the Location bar for everything. I actually never use the search bar -- I program all my custom searches with one-letter keywords and then drag it off the navigation bar completely. Then I only have to hit, e.g., "Ctrl+L, g bananas foster," and I get a google search, "Ctrl+L, f bananas foster," and I get a recipe search, "Ctrl+L, w bananas foster," and I get a wiki search, etc. Using the search bar, I'd have to hit Ctrl+K, hit Ctrl+Up/Down several times until the search engine I want is selected, and then after I'm done, reset it to google. Too many keystrokes. Also, in this case I *don't* want a google search; I want an "I'm Feeling Lucky" search, which takes you directly to Google's first hit, not Google's search page. This is the default behavior for Firefox in XP, but apparently not so in Ubuntu, at least when it comes to one-word queries.)

Detroit, my about:config strings are the same as yours. Do you have any other suggestions?

[[IMG]http://img718.imageshack.us/img718/623/screenshotaboutconfigmo.th.png[/IMG]]("http://img718.imageshack.us/i/screenshotaboutconfigmo.png/")

---

### Post by detroit/zero on 2010-05-08
> **WandersFar said:**
> (By the way, I appreciate all of you taking the time to help me figure  this out. :))

Okay, here's another example:

In XP, if I go to the Location/Awesome/URL bar (by either Ctrl+L, Alt+D, or clicking) and type "lifehacker" this is where I'm sent:
[http://lifehacker.com/](http://lifehacker.com/)

In Ubuntu, if I do the exact same thing, this is where I'm sent:
[http://search.domainnotfound.optimum.net/cablevassistsearch_keyword/ws/results/Dns/lifehacker/1/0/0/Relevance/iq=true/zoom=off/_iceUrlFlag=7?_IceUrl=true](http://search.domainnotfound.optimum.net/cablevassistsearch_keyword/ws/results/Dns/lifehacker/1/0/0/Relevance/iq=true/zoom=off/_iceUrlFlag=7?_IceUrl=true)

But if the term I'm entering in the bar is more than one word, for example, "recipe puppy", than everything is hunky-dory. Under both XP and Ubuntu, I am sent here:
[http://www.recipepuppy.com/](http://www.recipepuppy.com/)

Why do multiple word searches trigger "I'm Feeling Lucky" behavior in the URL bar, and singular word searches don't?


(I am aware that I can perform a google search by either going to google.com or using the search bar, but I find this slower and less elegant than using the Location bar for everything. I actually never use the search bar -- I program all my custom searches with one-letter keywords and then drag it off the navigation bar completely. Then I only have to hit, e.g., "Ctrl+L, g bananas foster," and I get a google search, "Ctrl+L, f bananas foster," and I get a recipe search, "Ctrl+L, w bananas foster," and I get a wiki search, etc. Using the search bar, I'd have to hit Ctrl+K, hit Ctrl+Up/Down several times until the search engine I want is selected, and then after I'm done, reset it to google. Too many keystrokes. Also, in this case I *don't* want a google search; I want an "I'm Feeling Lucky" search, which takes you directly to Google's first hit, not Google's search page. This is the default behavior for Firefox in XP, but apparently not so in Ubuntu, at least when it comes to one-word queries.)

Detroit, my about:config strings are the same as yours. Do you have any other suggestions?

[[IMG]http://img718.imageshack.us/img718/623/screenshotaboutconfigmo.th.png[/IMG]]("http://img718.imageshack.us/i/screenshotaboutconfigmo.png/")
I'm using FF 3.6.3 in Win 7 right now, and for me, the default behavior when entering (single- or double-word search terms) is to take me to a list of Google search results. I haven't used XP in about four years, so I can't say for sure what the default behavior there is.

A quick Google search (Ha!) of the terms "change firefox default search to i'm feeling lucky" yields this webpage: [http://www.proposedsolution.com/solutions/change-firefox-address-bar-default-search-behaviour/](http://www.proposedsolution.com/solutions/change-firefox-address-bar-default-search-behaviour/) which contains instructions for changing the default behavior back to the *I'm Feeling Lucky* behavior.

Post back if it works.

---

### Post by Sir Jasper on 2010-05-08
Hi,

Here are a few random thoughts, but only one question:

Are you using the same version of Firefox in both Windows and Linux?

A recent version of Firefox (possibly 3.6.3) considerably extended its search flexibility and versatility.

Clicking the Home icon used to take me to ¨I feel lucky¨, but not when I just tried it.

Using Wine (1.0.1 in my case) all versions of Firefox (currently 3.6.3) work well. The freeware program SlickRun works with wine and has an ¨I feel lucky¨ option (with dropdown list) which can be used with Firefox Windows versions.

My regards

---

### Post by WandersFar on 2010-05-08
Detroit, I changed the keyword.URL value to **[http://www.google.com/search?btnI=I%27m+Feeling+Lucky&q=](http://www.google.com/search?btnI=I%27m+Feeling+Lucky&q=)** as suggested by proposedsolution.com, but with no success.

I also tried changing that value in my about:config and restarting Firefox to see if that would have some effect, but it didn't. I still get a domainnotfound for one-word queries.

Jasper, yes, I am using the same version of Firefox (3.6.3) in both Ubuntu and XP.

---

### Post by Sir Jasper on 2010-05-08
Hi,

Here is the instruction I set up in my SlickRun magic word which I can run in conjunction with Wine to use ¨I feel lucky¨.

http://www.google.com/search?hl=en&btnI=I%27m+Feeling+Lucky&q=$W$

I have no idea if can be easily adapted to your need.

There are many clever and helpful forum members (including at least one with a deep understanding of Firefox) so I suspect it will not be too long before you find your answer.

My regards

---

### Post by WandersFar on 2010-05-08
Jasper, thank you very much for your suggestion, but SlickRun and Wine are a bit over my head. (This is my third day using Ubuntu, heh.)

Hopefully someone knows of a setting I can tweak in Firefox somewhere, but if not I will learn to adapt to Ubuntu's way of handling things.

Thanks again for your help.

---

### Post by ugm6hr on 2010-05-08
This is odd.  It appears that FF in Ubuntu uses optimum.net (presumably your ISP) Search Engine for single words in Navigation Toolbar, but not double words (which go to Google).

This must be something to do with your DNS setting.  As for why Windows behaves differently, I don't understand networking well enough to explain.

This is my supposition....

When you type any entry without spaces, FF (in Ubuntu) assumes you are typing a true url - and passes the "address" (e.g. lifehacker) to your DNS (which appears to be provided by ISP optimum).  The DNS realises there is no such url, and then defaults to its search page "Domain not found"

When you type a space (i.e. 2 words), presumably FF realises it can't be a url and passes it to Google directly.

I can tell you my (current) DNS sends me to lifehacker.com even when I enter "lifehacker" as 1 word.

You could try using OpenDNS: [http://www.opendns.com/](http://www.opendns.com/) as an alternative, which might do what you expect.

---

### Post by WandersFar on 2010-05-08
Well, I set up OpenDNS, and now both single word and multiple word queries get directed to OpenDNS' search page.

lifehacker:
[http://guide.opendns.com/?url=lifehacker](http://guide.opendns.com/?url=lifehacker)

ubuntu:
[http://guide.opendns.com/?url=ubuntu](http://guide.opendns.com/?url=ubuntu)

recipe puppy:
[http://guide.opendns.com/?url=recipe+puppy&client=ff](http://guide.opendns.com/?url=recipe+puppy&client=ff)

OpenDNS does have a "shortcut" feature that I can use to manually program each of these terms to the appropriate sites, but this doesn't solve the larger issue of any single word queries not automatically resolving to an "I'm Feeling Lucky" site.

Plus, the time spent in setting up shortcuts would probably be better spent setting up bookmarks that could sync with Weave, so, meh.

Thanks for the suggestion, though, ugm6hr.

EDIT:
Okay, now I'm having trouble reverting back to my ISP's DNS. I changed Static DNS 1 and 2 on my router back to what I had before, but I'm still getting the OpenDNS search pages for the above queries. Any thoughts?

EDIT AGAIN:
Alright, a reboot cleared everything up. Now I'm back to where I started: multi-word queries trigger "I'm Feeling Lucky" while single words trigger my ISP's "Domain Not Found" search page.

---

### Post by WandersFar on 2010-05-08
> **ugm6hr said:**
> When you type a space (i.e. 2 words), presumably FF realises it can't be a url and passes it to Google directly.

This gave me an idea for a workaround: Insert a random space somewhere within a one word query, and Firefox will route it to the "I'm Feeling Lucky" page.

Normal way: "digg"
[http://search.domainnotfound.optimum.net/cablevassistsearch_keyword/ws/results/Dns/digg/1/0/0/Relevance/iq=true/zoom=off/_iceUrlFlag=7?_IceUrl=true](http://search.domainnotfound.optimum.net/cablevassistsearch_keyword/ws/results/Dns/digg/1/0/0/Relevance/iq=true/zoom=off/_iceUrlFlag=7?_IceUrl=true)

Misspelled way: "dig g"
[http://digg.com/](http://digg.com/)

"engadget"
[http://search.domainnotfound.optimum.net/cablevassistsearch_keyword/ws/results/Dns/engadget/1/0/0/Relevance/iq=true/zoom=off/_iceUrlFlag=7?_IceUrl=true](http://search.domainnotfound.optimum.net/cablevassistsearch_keyword/ws/results/Dns/engadget/1/0/0/Relevance/iq=true/zoom=off/_iceUrlFlag=7?_IceUrl=true)

"en gadget"
[http://www.engadget.com/](http://www.engadget.com/)

Okay, so this seems to be working. Hopefully someone will come up with a better solution, but if not, this could be an effective workaround for anyone else in the same situation as me.

---

### Post by Sir Jasper on 2010-05-08
Hi again,

Congratulations on your ingenious yet simple solution.

My  regards

---

### Post by WandersFar on 2010-05-08
Thanks, Jasper. :)

It's not perfect, as if you have keyword search engines set up like I do, it can interfere with them. (For example, on my system, I have "d" = definr, so if I put in "d igg" I'll get an immunoglobulin definition instead of a news site. :p) But it'll do until someone comes up with a true solution.

---

### Post by TheNerdAL on 2010-05-08
Please mark this thread as solved if your problem is solved. :)

---

### Post by ugm6hr on 2010-05-09
Does inserting a space before digg - i.e. " digg" work?

Given OpenDNS sends to a search page for either space or no space entries, this presumably means that the entire behaviour of FF url bar is determined by your DNS.

Found this: [http://kb.mozillazine.org/Location_Bar_search](http://kb.mozillazine.org/Location_Bar_search)

My about:config keywrod.URL in 10.04 is : [http://www.google.com/search?ie=UTF-8&oe=UTF-8&sourceid=navclient&gfns=1&q=](http://www.google.com/search?ie=UTF-8&oe=UTF-8&sourceid=navclient&gfns=1&q=) 

I think changing it back to:
[http://www.google.com/search?btnI=I%27m+Feeling+Lucky&ie=UTF-8&oe=UTF-8&q=](http://www.google.com/search?btnI=I%27m+Feeling+Lucky&ie=UTF-8&oe=UTF-8&q=) 

Should achieve what you want - although I notice you have a tried a similar variation before.

PS: An OpenDNS solution: [https://addons.mozilla.org/en-US/firefox/addon/7993](https://addons.mozilla.org/en-US/firefox/addon/7993)

---

### Post by WandersFar on 2010-05-09
> **ugm6hr said:**
> Does inserting a space before digg - i.e. " digg" work?
Unfortunately, no. That was the first variation I tried, but it gets sent to the usual Domain Not Found page. The space can't be at the end of the word, either. It has to be within the text itself.

> I think changing it back to:
[http://www.google.com/search?btnI=I%27m+Feeling+Lucky&ie=UTF-8&oe=UTF-8&q=](http://www.google.com/search?btnI=I%27m+Feeling+Lucky&ie=UTF-8&oe=UTF-8&q=)

Should achieve what you want - although I notice you have a tried a similar variation before.Well, I tried modifying the keyword.URL value with this link, but there was no change, even after a browser restart. I also tried the second link in the mozillazine article, but with no success.

> PS: An OpenDNS solution: [https://addons.mozilla.org/en-US/firefox/addon/7993](https://addons.mozilla.org/en-US/firefox/addon/7993)I'd rather not install an addon for this, but thanks for providing the link for anyone else in the same situation.

---

### Post by darthmob on 2010-05-09
> **WandersFar said:**
> I'd rather not install an addon for this, but thanks for providing the link for anyone else in the same situation.Does the addon work for you? I tried it without using OpenDNS and as expected it didn't change anything.

It's a pretty weird problem. I was at my parents place over the weekend and I had the same issue there. Entering a single word on Linux FF forwarded me to a search / error page from the provider (Telekom). It didn't happen under XP. I'm back in my flat now and now both Linux and Windows work as supposed to. Using a different provider here as well, though.

---

### Post by butters stotch on 2011-03-02
> **WandersFar said:**
> Hello,

I'm a new Ubuntu user (just switched over from Windows) and I noticed that the behavior of Firefox's Location Bar in Ubuntu is somewhat different than from what I'm used to.

Specifically, if I hit Ctrl+L and type any one word query, (e.g., "ubuntu") instead of being taken to Google's top hit or "I'm Feeling Lucky" page, I get routed to a "Domain Not Found" search page from my ISP.

Under Windows, if I were to hit Ctrl+L in Firefox and type "ubuntu", I'd get sent to the main Ubuntu page.

How can I get this behavior in Ubuntu?


I had the exactly same problem and it was so annoying.
I found a solution for me, I hope it works for you:

Preference->Advanced->Connection, Settings
After I changed it from "Use system proxy settings" to "No proxy", problem solved!!

---

### Post by teegs on 2011-05-01
I'm having the same problem and unfortunately none of the helpful suggestions mentioned have worked for me. I would like to see a better solution than adding spaces in single word queries since this is more of an inconvenient hack than an actual solution.

Any help would be greatly appreciated.

---

### Post by teegs on 2011-05-03
This problem went away when I tested FF with a different ISP. Why would this be the case? Shouldn't anything that isn't a URL be caught by FF prior to sending the request out to the ISP?

---

### Post by teegs on 2011-05-03
I tried changing the keyword:URL field in FF about:config page to something obscure like duckduckgo to see if it was just the ISP realizing the URL didn't exist and forwarding the text to google but the one word search queries went to duckduckgo meaning that FF caught the one word request and treated it as a a search rather than a URL.

Why would this behavior be ISP specific? Requests act normally with FF in Wn7 for me on all ISPs.

---

### Post by teegs on 2011-05-08
bump

---

