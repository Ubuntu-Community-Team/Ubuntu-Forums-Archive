---
title: "Problem Connecting to Webpage."
date: 2007-06-29
forum: Networking &amp; Wireless
---

### Post by imotlaw on 2007-06-29
Hi all. I'm using Feisty 7.04. I'm unable to load pages from the New York Times when I am logged in at the Times, but am able to view some (they allow a finite number of stories before they require a log in) if I am not logged in. This happens on both of the browsers I have installed, FIrefox 2.0.0.4 and Opera 9.21. Here's what happens: I go to the NYT ([http://www.nytimes.com/](http://www.nytimes.com/)). If I haven't got any NYT cookies (say I've had Firefox clear out all my cookies) then I can click on any old non-Times Select link and the page will load just fine. If I then click on the "Log In" link ([http://www.nytimes.com/auth/login?URI=http://](http://www.nytimes.com/auth/login?URI=http://)) and log in, then the page just hangs until I get a "Problem loading page. The connection to the server was reset while the page was loading." error. I get the same thing if I try to view the page source. Furthermore, I can't even go to NYT anymore at that point (typing it in and hitting enter gets me the "Problem loading page." error again.  Clearing out my cookies gets me back to where I was at the start of this whole procedure.

* UPDATE * 
Just as I was finally writing this up (I've been having this problem since I started using Ubuntu) I noticed an interesting thing: I installed NoScript the other day, and if  (1) I haven't got any cookies left over from a with-javascript-log-in, and (2) NoScript does not allow any javascript for the NYTimes,  then the whole of the NYTimes works just fine; I can log in and view pages to my little heart's content. Turning the javascript back on while logged in causes all of my problems once again, and even after I turn the NoScript blocking on again it won't work until I've cleared out the old cookies. So, I guess I have a fix, but not a solution. Can anyone shed any light on why this is happening, and what might be done *other* than blockign javascript?  (Note: I'm perfectly happy to block javascript; I just wish to know what the actual problem is. Has anyone else come across this kind of problem?)

---

