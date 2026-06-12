---
title: "Picture loading in Firefox"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by bhaskar1729 on 2009-01-23
Hi, this is my first post. :)
I'm using firefox 3.05 and constantly face the problem of pics not loading when I open any webpage. Could someone suggest a remedy?
Thanks

---

### Post by Muffinabus on 2009-01-23
Edit > Preferences, On the Content tab, is 'Load images automatically' checked?

---

### Post by RomeReactor on 2009-01-23
Hi. You could also try clearing the cache and see if it loads them now.

What kind of internet connection do you have? Do you get frequent timeouts?

---

### Post by bhaskar1729 on 2009-01-28
I cleared the cache and increased it upto 100 mb (previously it was 50).
That didn't help.
The automatic picture reloading option was activated.

As for connection, I am using a proxy server here and No, I don't get frequent timeouts.

Others out here switched back to Firefox 2.20 because the same problem doesn't exist in it. It's only with Firefox 3.x (and Chrome).

Help??

Thanks.

---

### Post by Rabindranath on 2009-01-28
I guess it is due to the proxy server. Try to connect to the internet directly and other proxy servers and see if it works. Then we'll be able to find out whether it a firefox problem or a problem in the proxy.

---

### Post by bhaskar1729 on 2009-01-28
> **Rabindranath said:**
> I guess it is due to the proxy server. Try to connect to the internet directly and other proxy servers and see if it works. Then we'll be able to find out whether it a firefox problem or a problem in the proxy.
I don't have an option of a direct connection (certain restraints).
I tried different proxies (and at different times of the day, when traffic levels are really low) and that really didn't help.

So, what do you infer?

---

### Post by crimesaucer on 2009-01-28
Sometimes the adblock Add-Ons can cause problems with certain websites.

---

### Post by bhaskar1729 on 2009-01-28
> **crimesaucer said:**
> Sometimes the adblock Add-Ons can cause problems with certain websites.
Thanks but that's not the case. I checked my add-ons.
Does anyone else face a similar problem? On a lower bandwidth, say?

---

### Post by RomeReactor on 2009-01-28
Try disabling ipv6 in Firefox; in the address bar, enter
```
about:config
```
then enter **ipv6** in the filter bar.

---

### Post by bhaskar1729 on 2009-01-28
> **RomeReactor said:**
> Try disabling ipv6 in Firefox; in the address bar, enter
```
about:config
```
then enter **ipv6** in the filter bar.


Well, apart from making me promise to be careful, the config menu only showed that by default the value was set as false.
Now I don't know much but I guess that its indicative of a disabled ipv6, but does it mean its filtered?

---

### Post by RomeReactor on 2009-01-28
You have to set it to "true" by double-clicking on the option, or right-clicking on it and selecting "Toggle", then restart Firefox.

---

### Post by bhaskar1729 on 2009-01-28
> **RomeReactor said:**
> You have to set it to "true" by double-clicking on the option, or right-clicking on it and selecting "Toggle", then restart Firefox.
All right, something did happen, but it wasn't the reloading of pics. Instead some of the unloaded pics were displayed as stricken off urls (google.com) and the whole display of some webpages (i tried megatokyo.com) changed.

???

---

### Post by RomeReactor on 2009-01-28
In the previous page you mentioned that the problem only happens with Firefox 3 and Chrome; have you tried other browsers to see if the problem happens there as well? Has the problem always happened, or just recently? Do you have connectivity problems with other applications?

---

### Post by bhaskar1729 on 2009-01-29
> **RomeReactor said:**
> In the previous page you mentioned that the problem only happens with Firefox 3 and Chrome; have you tried other browsers to see if the problem happens there as well? Has the problem always happened, or just recently? Do you have connectivity problems with other applications?
Well, when I used Windows Xp (which was till quite reently, and I still frequent it sometimes), the same problem happened with Firefox 3 AND chrome. So, ya, it is, I guess, a browser specific problem, here at least. Firefox 2 didn't give any such problems. Nor did IE 7.
What does connectivity imply here? I usually get to open all sorts of stuff on the net, if that's what you mean. 
Is it a bandwidth related problem? 
Help?

Ya, also of some mention might be the fact that sometimes pages open in simple html formats (the ones where all the background colors and graphics go missing and the formatting goes all haywire so that the complete text is left indented).

:|

---

### Post by RomeReactor on 2009-01-29
> **bhaskar1729 said:**
> Well, when I used Windows Xp (which was till quite reently, and I still frequent it sometimes), the same problem happened with Firefox 3 AND chrome. So, ya, it is, I guess, a browser specific problem, here at least. Firefox 2 didn't give any such problems. Nor did IE 7.
So the problem doesn't appear to be OS specific (it happens in XP and Ubuntu), but rather application specific. According to [this page]("http://kb.mozillazine.org/Images_or_animations_don%27t_load"), certain [problematic extensions]("http://kb.mozillazine.org/Problematic_extensions") cause Firefox to not load images; the solution is to disable them. Also make sure javascript is enabled, and that there are no exceptions in the "Load images automatically" option in Firefox's preferences. 

If the images still don't load, try closing Firefox (export your bookmarks to a file first, so you can add them back later), backing up your Firefox profile (by moving it somewhere else, for example your desktop):
```
mv ~/.mozilla/firefox ~/Desktop
```
and starting Firefox again to see if the images start loading now.


> What does connectivity imply here? I usually get to open all sorts of stuff on the net, if that's what you mean.
Is it a bandwidth related problem?
I meant connectivity regarding other types of internet applications or protocols, like BitTorrent, or streaming music with RhythmBox. If the problem is not solved by disabling your extensions or starting with a fresh Firefox profile, then the problem is likely related either to the proxy configuration or your ISP.

> Ya, also of some mention might be the fact that sometimes pages open in simple html formats (the ones where all the background colors and graphics go missing and the formatting goes all haywire so that the complete text is left indented).

:|

I think some of those problems are covered in one of the previous links.

---

