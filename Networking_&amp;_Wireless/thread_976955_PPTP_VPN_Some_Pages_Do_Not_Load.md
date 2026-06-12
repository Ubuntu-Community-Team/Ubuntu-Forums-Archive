---
title: "PPTP VPN Some Pages Do Not Load"
date: 2008-11-09
forum: Networking &amp; Wireless
---

### Post by simusid on 2008-11-09
I'm running Ubuntu on a new Dell Mini.  I believe that is Hardy.

I'm trying to connect to an MS VPN server.  I've configured the PPTP client and I can connect and authenticate OK.  I can websurf to some websites (google loads fine).   Others take a *very* long time to load (drudge takes many minutes) and some do not load at all.   It does not appear to be DNS related as all hosts will resolve via nslookup.  It's odd to me that [www.wikipedia.org](www.wikipedia.org) will load fine but en.wikipedia.org will not.

One of my first guesses was routing but that does not appear to be the problem.   I've given up troubleshooting with firefox and I'm now using curl from the command line to try and figure things out.

One odd behavior is "curl www.mec.edu" (a local college) will dump about 1/2 the HTML and then hang.  it hangs at the exact same point every time.   

So if anyone has any PPTP/PPP insights I would love to hear them!

Regards,

Simusid

---

### Post by eleqtriq on 2008-11-20
I am having the same problem ..suddenly.  My server was working fine now I can't even access one of our own websites while the others work fine.

I could use some help, too.

---

### Post by skej on 2011-11-08
I'm have a similar issue but haven't any luck finding someone that may know whats causing this.

[http://ubuntuforums.org/showthread.php?p=11435139]("http://ubuntuforums.org/showthread.php?p=11435139")

---

