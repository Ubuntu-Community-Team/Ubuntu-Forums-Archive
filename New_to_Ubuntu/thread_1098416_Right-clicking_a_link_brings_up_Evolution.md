---
title: "Right-clicking a link brings up Evolution?"
date: 2009-03-17
forum: New to Ubuntu
---

### Post by apolaustic on 2009-03-17
I'm using Ibex/8.10 and I've got an intermittent odd problem in Firefox. About a third of the time when I right-click a link, instead of bringing up the right-click menu, it starts Evolution. All of the links this happened with were standard links, not mailto links, and left-clicking them brought up the page without any problems. Moreover, sometimes I just needed to right-click the link a few times (closing Evolution in between each click) and it would go back to normal functioning.

In a similar issue, sometimes when I right-click links it brings up the bookmark menu. Again, left-clicking works fine, sometimes it resolves itself after a few right-click attempts, everything about the problem is the same except that what's brought up is the bookmark menu instead of Evolution.

I thought at first that maybe I was just being sloppy with the mouse or accidentally resting my other hand on the keyboard, so I've been very conscientious, but it keeps happening.

Any thoughts? It's not that big of a deal, but I'd like to be rid of the annoyance anyway. Thanks in advance.

---

### Post by binbash on 2009-03-17
It is a known firefox bug.No fixes for months

---

### Post by apolaustic on 2009-03-17
Thanks! At least now I know it's not unique to my system.

---

### Post by Yashiro on 2009-03-17
> It is a known firefox bug.No fixes for months
So what causes it? I've never experienced this on any Ubuntu or Debian box, ever.

---

### Post by kanikilu on 2009-03-17
A lot of people are experiencing this problem. It's very strange and sporadic, hard to reproduce. I noticed it was doing it to every link on one website, but after restarting FF, it didn't happen on that site. Sometimes it opens a new window, sometimes a new tab. No particular pattern that I can see, other than it didn't happen on 8.04, but does on 8.10.

For the time being, the only work around I've found is to simply hold down the button when you right-click rather than clicking and letting go. This gets the proper context menu every time but it has been a little annoying having to retrain myself to hold the button down ;)

---

### Post by azebuski on 2009-03-17
I thought it was just me this happened to. I'm running 8.10 with FF 3.0.7.  For me it happens when I right click a picture to Save Image As. Sometimes the Bookmark This Page box opens up and sometimes a blank new tab is opened.

---

### Post by mvalviar on 2009-03-17
Hey I thought I am the only one experiencing that. I thought its my just my mouse. Whenever I right clicking on something automatically brings up one of the options on the context menu i.e. evolution, set desktop background and save as. In addition, whenever I left click the Bookmarks menu firefox automatically proceeds on bookmarking the page I'm currently at. I hope someone has a fix on this.

---

### Post by Yashiro on 2009-03-17
So which distirbutions/versions does this still appear on?

I've NOT seen it on default installs of (x86_64): 
Ubuntu 8.04,9.04a (Firefox 3 to 3.07)
Xubuntu 9.04 (Firefox 3.07)
Debian 5.0 (Firefox 3 to 3.07)

Is it a case of some spurious cursor jumping/selecting by Xorg?

---

### Post by binbash on 2009-03-17
I have seen this on Fedora 10, debian and ubuntu.There is a bug report for this on firefox site

---

