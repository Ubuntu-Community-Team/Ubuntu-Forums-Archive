---
title: "Internet Strangeness"
date: 2005-06-09
forum: Networking &amp; Wireless
---

### Post by Teren on 2005-06-09
Hello. :D

Recently, because I had to use a machine with WinXP on it, I noticed that browsing on it seems much snappier than on Linux.

I have a 2mb cable connection, same on the Windows machine. Both use Opera. The thing that bugs me, is not the rendering time, but the time it takes to start downloading a page.

On Windows, the page is loaded immediatly, after you click a link. But on Linux, it takes 4-7 seconds to start loading a page... I know it's not a rendering or downloading problem, because on Linux Opera spends time on "Sending request to blabla.com". Once a few seconds pass, it changes to "Receiving from blabla.com", and the page is rendered super-fast.

I'm starting to think it has something to do how Linux handles DNS. But that doesn't seem to be the case - if I ping something, itdoesn't take ant longer than on Win to get the IP of the host.

Also, I have no problems downloading, I get steady 200-300kib/s

So, now I have no idea what's the problem.

Any one has any ideas?
Thanks in advance.

---

### Post by BimberiDreamer on 2005-06-09
Hi Teren,

Give this a try:

[http://www.ubuntuguide.org/#loadwebsitefasterfirefox](http://www.ubuntuguide.org/#loadwebsitefasterfirefox)

Cheers, Dave.

---

### Post by Teren on 2005-06-09
[QUOTE=BimberiDreamer]Hi Teren,

Give this a try:

[http://www.ubuntuguide.org/#loadwebsitefasterfirefox](http://www.ubuntuguide.org/#loadwebsitefasterfirefox)

Cheers, Dave.[/QUOTE]
 I think you missed one thing - I use Opera ;)

---

### Post by Teren on 2005-06-09
[QUOTE=Teren]I think you missed one thing - I use Opera ;)[/QUOTE]
 I just turned off ipv6 off completely, nothing changed.
So, it's something else... :(

I'm again getting the feeling it's a DNS problem...

"telnet google.com 80" takes abit longer than "telnet 216.239.37.99 80" to get a "Connected to google.com".

---

### Post by BimberiDreamer on 2005-06-09
[QUOTE=Teren]I think you missed one thing - I use Opera ;)[/QUOTE]Oops.  So I did?  My apologies.   :?

Dave.

---

### Post by Joeb on 2005-06-10
[QUOTE=Teren]I think you missed one thing - I use Opera ;)[/QUOTE]

You might still want to load firefox and make the changes suggested in the link previously posted, just to test whether it is a linux problem or an opera problem.

---

### Post by Adlerauge on 2005-06-11
Hi!

I have the same problem and I tried konqueror and mozilla.

---

### Post by az on 2005-06-11
Firefox is a little more sluggish than IE, but I usually still get better performance from Linux...

---

### Post by Joeb on 2005-06-11
It sounds like a configuration problem.  The computer I use dual-boots both windows and linux and Firefox runs the same speed.  Do other internet things run the same speed (ie ftp, nntp)?

You might check that you have the same the same dns server in the configuration for both windows and linux.

---

### Post by skoal on 2005-06-11
[QUOTE=azz]Firefox is a little more sluggish than IE, but I usually still get better performance from Linux...[/QUOTE]
On a recent visit to my parents house, I secretly installed firefox, removed the IE desktop icons, and changed the firefox icon to IEs.  They actually thought I had "fixed" their computer and it ran faster all of a sudden.  That was just firefox on 2 win boxes.  I still think pound for pound, firefox Linux is the fastest most resilient heavyweight "fighta" to ever step foot in the browser ring.  Maybe I wear rose colored glasses, but I'm stickin to that story...

\\//_

---

