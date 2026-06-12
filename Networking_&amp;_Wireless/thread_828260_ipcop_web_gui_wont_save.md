---
title: "ipcop web gui wont save"
date: 2008-06-13
forum: Networking &amp; Wireless
---

### Post by essexboyracer on 2008-06-13
Hi All, not really ubuntu related (although i access this via firefox in xubuntu)

I have set up a spare machine with IPCOP 1.4.18. GREEN + RED interface. 

ADLS ROUTER-->IPCOP-->SWITCH-->xubuntu

it works as i am writing this via it, and IPCOP is logging bandwidth etc. Where it all falls down is using the ultra slick IPCOP web interface to change settings. No matter which page I go on and change a setting, then click save, it just returns the page with changes lost. V.Annoying as I cant switch SSH on (or anything else) Its almost like the web interface is read only.

Has anyone had this?

---

### Post by ModelM on 2008-06-13
This almost sounds to be HTML related. The first thing I'd try is accessing it from a different browser. I'm sure those folks put those HTML setup pages together with great care - and tested them throughly - in Internet Explorer....

---

### Post by essexboyracer on 2008-06-14
I solved it, all by myself!, see the ipcop forum below;

[http://www.ipcops.com/phpbb3/viewtopic.php?f=16&t=11523](http://www.ipcops.com/phpbb3/viewtopic.php?f=16&t=11523)

Basically it had to do with HTTP referrer switched off in FF. switch it on and it works.

---

