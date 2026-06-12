---
title: "Weird connection problem (MTU change doesn't help)"
date: 2008-03-21
forum: Networking &amp; Wireless
---

### Post by trifold on 2008-03-21
I have HP Pavilion tx1120us laptop and KUbuntu Gutsy amd 64 on it. I have problem when browsing, some web site won't open. For example ubuntuforms.org won't open, but when I start windows from vmware and open Internet explorer I can open that site. (that is how I am writing this post). I have ethernet conncetion with my wireless router, I tryed to change MTU (on ruter value was 1452 bytes and on linux 1500) but still nothing. Interesting is that I can open web sites with lynx (works for ubuntuforums.org) but can't open from Mozilla or Konqueror. And sometimes I can open some site I sometimes I can't. Weird!

Any ideas?

regards...

---

### Post by HermanAB on 2008-03-21
Check your DNS settings in /etc/resolv.conf.  Use 'dig' and ensure that all listed DNS are alive and responsive.  Put the best one at the top of the list.

---

### Post by trifold on 2008-03-21
> **HermanAB said:**
> Check your DNS settings in /etc/resolv.conf.  Use 'dig' and ensure that all listed DNS are alive and responsive.  Put the best one at the top of the list.
I access internet trought router so in resove.conf is ip address of my router. Why do you think that dns is problem? (how to you explain that I can visit some sites, and that I can visit every site using lynx or windows from vmware - witch uses linux conection)

regards

PS. I am using lynx to write this post, sorry if formating is not good

---

### Post by stream303 on 2008-03-27
In a situation like this, you might try putting your ISP's primary and backup dns router addresses in the router setup page itself.  If you don't know your isp's dns addresses, you may want to look at the bottom right page of

[http://www.opendns.com](http://www.opendns.com)

No matter what you choose, the trick for me for the least amount of pain was to install the dns server addresses inside the router itself.

---

### Post by trifold on 2008-03-27
I tried that but still the same... Any ideas why? Weird thing is that it loads half of the page (for example if page has frames it loads left and top frame) and never load the whole page.

regards...

---

