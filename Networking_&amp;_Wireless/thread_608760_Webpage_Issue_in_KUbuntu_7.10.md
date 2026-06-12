---
title: "Webpage Issue in K/Ubuntu 7.10"
date: 2007-11-10
forum: Networking &amp; Wireless
---

### Post by chazco on 2007-11-10
Hi,

I'm having a problem with a single webpage following installing 7.10. The web page starts to load, then goes very slowly and stalls, but no errors are displayed and it still claims to be loading. The web page is in a password protected area of a site, but other pages inside the passworded area work fine (i cant wget the page either due to the login). The web page changes almost daily, and I need to check it often.

The following has been established so far:
[LIST]
[*]The same happens in Opera / dillo / Ephinay
[*]It also happens in Kubuntu 7.10
[*]It also occurs when using the 7.10 LiveCD (Kubuntu or Ubuntu)
[*]It occurs on any computer that runs 7.10 that i have tried
[*]The page works on the same version of Firefox + Ubuntu 7.04
[*]The page works on Firefox + Vista
[*]All other internet activity is fine
[*]Disabling ipv6 (both in Firefox and globally) doesn't help
[*]There is only basic JavaScript on the page (and HTML)... no flash etc
[/LIST]

I'm assuming something changed between 7.04 and 7.10 at the network level, but dont know where to go from there. Any help appreciated :)

---

### Post by danbh on 2007-12-07
Try installing the firebug extension.  Use that extension to check under the NET tab.  See if anything is taking a long time to connect:
[https://addons.mozilla.org/en-US/firefox/addon/1843](https://addons.mozilla.org/en-US/firefox/addon/1843)

---

### Post by chazco on 2007-12-07
Nothing shows up apart from the actual page itself (which still never finishes loading).  I've also discovered that the same affects guest operating systems running in Virtualbox on 7.10 when using NAT.

---

### Post by OldManRiver on 2007-12-07
What is being used?  HTML, DHTML, XML, PHP, Python, Perl, Java?

Look in the code or post here so we can determine what is up.  

Reloading Ubuntu sometime does not load PHP, Python, etc. so you have to maually load the apps and module with the:
> apt-get install app-name
I had to reload all my PHP etc after running internet upgrade from 7.04 to 7.10 as it lost some of the app links by overwriting my existing conf files.

OMR

---

### Post by chazco on 2007-12-07
The page has just HTML and i think some basic JavaScript.

> Reloading Ubuntu sometime does not load PHP, Python, etc. so you have to maually load the apps and module with the:
I think thats only really needed when serving a page... i'm trying to view one.

---

### Post by danbh on 2007-12-07
Have you tried saving the page after it finally loads?  And then just viewing it as a static page.

---

### Post by chazco on 2007-12-08
It changes every time (its an entrance form to a timetable). If i save it on a non 7.10 computer (on 7.10 it doesn't finish loading and eventually times out) and then copy it over it'll open, which seems to say its not the page itself thats the problem.

---

### Post by chazco on 2007-12-19
Thanks to **erUSUL** on #ubuntu this is now working. =D> :D

Edit /proc/sys/net/ipv4/tcp_window_scaling so that it is set to 0, close down the browser and then try. If anyone can give an explanation of why this actually fixes it please do :)

---

