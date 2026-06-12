---
title: "Firefox acting weird...."
date: 2011-04-13
forum: New to Ubuntu
---

### Post by ChipRed87 on 2011-04-13
This has been frustrating me all day long,](*,)

Whenever I open Firefox it runs fine for the first few minutes.
But after a little while when I click a link, the browser goes no where.
My bookmarks don't go any where, and I can't even open Google.com.
If I open a link in another page,(middle clicking a bookmark for example) I end up with a "New tab" tab, with the address in the bar and a blank window.
Pressing enter in the bar with the address doesn't make it go either.

In short, it is like this till I close and reopen Firefox, then it works for a bit, then the cycle starts over...

I have Firefox 4 and am on 10.10

Anyone have any suggestions here?:confused:


~~~~~~~Edit~~~~~~~~
On this same machine Opera works fine, so I know it isn't a connectivity/network issue

---

### Post by dearingj on 2011-04-13
Does the problem still occur if you start Firefox in safe mode? To start in safe mode, in a terminal window type:
```
firefox -safe-mode
```

What safe mode does is temporarily disable all your Firefox extensions, so if the problem goes away then you know that one of your extensions must be the cause.

---

### Post by lovinglinux on 2011-04-14
See [http://www.webgapps.org/firefox/general-troubleshooting](http://www.webgapps.org/firefox/general-troubleshooting)

It could be [ipv6]("http://www.webgapps.org/firefox/issues-and-solutions"), but it is weird that the problem occurs after a while.

---

### Post by ChipRed87 on 2011-04-14
Yes this still happens to Firefox in Safemode.:-|

I also have network.dns.disableipv6 in the about:config page selected as true, from a former attempt to resolve the problem.


Still not working right :(

---

### Post by searchfgold6789 on 2011-04-14
I used to have this problem when I was using Tor. Do or did you have that installed?
Tor and torbutton should have been completely disabled from Firefox during the first Firefox run. If they are somehow still running, for example if you have disabled the add-on compatibility check, then restart the tor daemon.
Also double-check all of the other add-ons you may have installed.
 - search

---

### Post by ChipRed87 on 2011-04-14
The above link did not fix the problem (I tryed all the suggestions)

And I do not use Tor, nor have i installed any new software lately (save updates)


This happened out of the blue too, It is not like it died after I messed with something. The only major thing I've done to the system in the last few day is update it.

---

### Post by lovinglinux on 2011-04-14
> **ChipRed87 said:**
> The above link did not fix the problem (I tryed all the suggestions)

And I do not use Tor, nor have i installed any new software lately (save updates)


This happened out of the blue too, It is not like it died after I messed with something. The only major thing I've done to the system in the last few day is update it.

Try a clean Firefox profile.

You can create new profile by running the profile manager:

```
firefox -P
```

---

### Post by ChipRed87 on 2011-04-14
New profile does the same thing to me.](*,)

---

### Post by lovinglinux on 2011-04-14
> **ChipRed87 said:**
> New profile does the same thing to me.](*,)

Have you tried to disable ipv6?

Just to be clear, you don't have problems opening tabs or bookmarks, the problem is that when you open them, the browser keeps loading and the page content is never displayed. Is that right?

---

### Post by ChipRed87 on 2011-04-14
> **lovinglinux said:**
> Have you tried to disable ipv6?

Just to be clear, you don't have problems opening tabs or bookmarks, the problem is that when you open them, the browser keeps loading and the page content is never displayed. Is that right?

I have ipv6 disabled currently.

When this happens (It seems to be more often now, Firefox is all but unusable) it just opens a new tab. The URL is there, It flashes "loading" on the tab for less then a second and just sits on that blank screen.
Successive efforts to load the page (go, reload, enter etc) do nothing at all. In fact I can't even click reload.

---

### Post by lovinglinux on 2011-04-14
> **ChipRed87 said:**
> I have ipv6 disabled currently.

When this happens (It seems to be more often now, Firefox is all but unusable) it just opens a new tab. The URL is there, It flashes "loading" on the tab for less then a second and just sits on that blank screen.
Successive efforts to load the page (go, reload, enter etc) do nothing at all. In fact I can't even click reload.

Try to disable the options to "Block reported attack sites" and "Block reported web forgeries" in the "Security" tab of Firefox Preferences.

---

### Post by ChipRed87 on 2011-04-14
> **lovinglinux said:**
> Try to disable the options to "Block reported attack sites" and "Block reported web forgeries" in the "Security" tab of Firefox Preferences.

Still doing the same thing after these are disabled. :(

---

### Post by lovinglinux on 2011-04-14
> **ChipRed87 said:**
> Still doing the same thing after these are disabled. :(

Are you running something like a torrent client while using Firefox?

If you have a router, try to set the MTU to 1492 in the router setup.

---

### Post by ChipRed87 on 2011-04-14
> **lovinglinux said:**
> Are you running something like a torrent client while using Firefox?

If you have a router, try to set the MTU to 1492 in the router setup.

I have no Torrent client running at all, and no router at all either.

---

### Post by lovinglinux on 2011-04-14
Please do this test:

When the browser starts behaving badly, visit [http://www.canonical.com/](http://www.canonical.com/) and make sure that page is not opening. Then visit [http://91.189.94.12/](http://91.189.94.12/) and check if the page loads.

---

### Post by ChipRed87 on 2011-04-14
I GOT IT!:D

For some odd reason my proxies where messed up.

I manually reset them and now everything SEEMS to be going fine.

Our network Admin said we didn't NEED to go though the proxy, but apparently I do now.


By the way, thank you lovinglinux for all the help and suggestions.

I feel silly now for having this problem and not being able to fix it...

---

### Post by lovinglinux on 2011-04-14
> **ChipRed87 said:**
> I GOT IT!:D

For some odd reason my proxies where messed up.

I manually reset them and now everything SEEMS to be going fine.

Our network Admin said we didn't NEED to go though the proxy, but apparently I do now.


By the way, thank you lovinglinux for all the help and suggestions.

I feel silly now for having this problem and not being able to fix it...

You are welcome. I am glad you figured it out.

---

### Post by dearingj on 2011-04-14
Don't forget to mark this thread as 'solved' now that you've found the solution. :)

---

