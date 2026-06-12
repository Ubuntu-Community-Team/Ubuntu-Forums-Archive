---
title: "Websites become unavailable after a few hits on feisty and gutsy"
date: 2007-10-25
forum: Networking &amp; Wireless
---

### Post by webceo on 2007-10-25
Hello all,

Ok here is my problem which I was having with feisty and persists after upgrading to gutsy..
My network and internet work just fine, I can login to pidgin, I can run networking commands (tracerout, host, ping...), everything seems to work just fine. BUT

After hitting the same website a few times (I don't know how many actually), the website become unaccessible for a few minutes (up to 10 mins sometimes). I can ping it's domain name, I can traceroute it, everything indicates that the website is 100% working.

At first I thought it was specific to some websites, but later I discovered it was this way with every single one. I even disabled my wireless card and used wired connection, still nothing.

I've been looking all around for a fix to this, but I don't seem to find one...

Please help

Thank you

---

### Post by Abandon on 2007-10-25
It could be related to IPV6 or resolving. 

What happens if you use the website's ipnumber instead of the domainname?

---

### Post by webceo on 2007-10-25
I have disabled IPv6 a while ago, it doesn't seem to be the problem.
Also it can't be a resolving problem since when I can't access a website from a web browser and I ping it's domain name it can resolve it successfully.

Any other thoughts ?

---

### Post by webceo on 2007-11-09
Any thought guys ? this really is a big issue for me. Can anyone help please ?

---

### Post by NilsE on 2007-11-09
There is only one possibility that comes to mind and it is related to a known Flash problem that many people are having.  However, you said it is all sites so that can't be it.

I just recommend that you verify that it is all sites and not just those with flash (which is most sites now a days). If it is those with flash make sure you have flash installed.

---

### Post by webceo on 2007-11-10
This happens with all sites, even google.com
And I already have flash installed.

Thanks

---

### Post by webceo on 2007-11-15
Well, I've been googling about this and I found this post on a linux forum
[http://www.linuxquestions.org/questions/linux-networking-3/internet-connection-timeout-on-fedora-core-5-using-usb-connection-466951/](http://www.linuxquestions.org/questions/linux-networking-3/internet-connection-timeout-on-fedora-core-5-using-usb-connection-466951/)

My problem is very similar except that I don't use a USB modem, but a Lan connection. I have to note that this problems doesn't happen on other computers running windows, and they have the exact same specs as mine.

Thank you

---

### Post by webceo on 2007-11-21
I can't believe that no one in one of the most active linux forums have any clue of what the problem might be.

Am I the only one this is happening to ? or am I asking this in the wrong place ?

---

### Post by webceo on 2007-11-25
Ok, I did a fresh install of Gutsy on another partition. And guess what ? the same problem persists. Except that it takes less time for the websites to be accessible again.

HELP

---

### Post by webceo on 2007-12-01
Ok, I installed opensuse on a different partition, and everything seems to work perfectly on it. So I'm pretty sure this is a bug in Ubuntu.

I'm really disappointed no one has any idea of what the problem might be....

---

### Post by webceo on 2008-05-04
Just thought I'd let you know, the problem is persisting in Hardy

---

