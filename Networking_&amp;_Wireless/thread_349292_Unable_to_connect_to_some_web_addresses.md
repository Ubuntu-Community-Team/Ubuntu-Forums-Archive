---
title: "Unable to connect to some web addresses"
date: 2007-01-30
forum: Networking &amp; Wireless
---

### Post by sdlewis on 2007-01-30
I've recently installed 6.06 and I've run into strange internet connection problems. I'm unable to connect to some sites; specifically google. 
Rundown of my setup:
I'm connected to a DSL router that is servicing other computers. Other computers (all WinXP) have no connection problems. The internet connection is working generally. I'm able download security updates and new packages. I'm able browse the web for the most part, but anytime I run into a that tries to direct to a google site (example: slashdot has links to googlesyndication.com) the page load will not complete; eventually I'll get a connection timeout.

I'll start FireFox and try to go to google.com. No luck - connection timeout. Other web sites will load OK. I open a terminal and do a "nslookup google.com". I get back 
    name: [www.l.google.com](www.l.google.com)
  address: 66.102.7.147

If I switch back to firefox and enter "www.l.google.com", I'll now be able to load the google page. Open a new tab, enter "google.com", now the connection works.

Any ideas? I can't figure out why the internet connection is working generally, but requests to google sites time out, until I do the nslookup command. I'm stumped.

Steve

---

### Post by linuxpimp on 2007-01-30
HI

In firefox type:
about:config

Filter and look for IPV6, set the disable to true and Bob's yer uncle. Most sites work with IPV4...

Either that or change your DNS servers...

Good luck.

LP

---

### Post by sdlewis on 2007-01-30
Bob's more than my uncle!
Not only can I connect everywhere, but performance loading web pages is much faster.

Were all of my DNS requests using ipv6 by default? 

Thanks for the quick answer.

Steve

---

### Post by linuxpimp on 2007-01-30
> **sdlewis said:**
> Bob's more than my uncle!
Not only can I connect everywhere, but performance loading web pages is much faster.

Were all of my DNS requests using ipv6 by default? 

Thanks for the quick answer.

Steve

Yup, they were.

Glad it helped, do a Google for "firefox" "hack" "pipelining" and you will speed it up even more

lp

---

### Post by bteck on 2007-01-30
I must say a BIG Thank you to linuxpimp.  Your solution about disabling ipv6 in Firefox has helped me to connect to the Internet successfully!  I was struggling for 2 days with lots of frustrations.  Many newbees may be facing the same problem too.  I reported my case in more detail in the forum thread: "how do you setup up adsl internet connection"

Thank you again linuxpimp.

---

### Post by Yob on 2007-01-30
Thank you!
Had the same problem all of a sudden after a reboot today.

Maybe to do with the update that came earlier today?

---

### Post by linuxpimp on 2007-01-30
You're welcome, i had that when i first installed Dapper last year.

LP

---

### Post by paydaydaddy on 2007-01-31
:guitar: Bob is my uncle too! I have been struggling with this issure for a couple of days. Been searching the forums and asking questions, then stumbled across this. Problem fixed. Thank you! Thank you!

---

### Post by bteck on 2007-02-15
> **linuxpimp said:**
> HI

In firefox type:
about:config

Filter and look for IPV6, set the disable to true and Bob's yer uncle. Most sites work with IPV4...

Either that or change your DNS servers...

Good luck.

LP

linuxpimp,

I am just curious.  Disabling IPv6 in Firefox works.  But what happen if a site requires IPv6?  Will Firefox fail here?
:-?

---

