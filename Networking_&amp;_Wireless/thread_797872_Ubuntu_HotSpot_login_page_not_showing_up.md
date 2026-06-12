---
title: "Ubuntu HotSpot login page not showing up"
date: 2008-05-17
forum: Networking &amp; Wireless
---

### Post by cnich23 on 2008-05-17
I am having the most difficult time connecting to the internet in my barracks.  We have wifi that is set up like a hotspot w/a webpage user/pass login.

I am able to connect to the network and I am assigned an address but when I got to open firefox it does not navigate to the login page.  I am on a dual boot system, and in XP when I open firefox it navigates to the login page.

I have two wireless cards both of which connect to the network but do not navigate to the login page.

Any help to get this up and running would be great to get me started on this new version of ubuntu.  Thanks!

---

### Post by netztier on 2008-05-17
> **cnich23 said:**
> Any help to get this up and running would be great to get me started on this new version of ubuntu.  Thanks!

Any plugins or functions in Firefox that would need to be disabled? These portal pages sometimes do unexpected things in HTML/HTTP, to which some browsers with rather conservative security settings (Popup blockers, redirection prevention) do not like at all.

Other idea: one hotspot product I know redirects a page request for "http://www.example.com/" to "http://hotspot/loginpage" (note: with a unqualified hostname). Some DNS resolvers on some OSs do not seem to like this occasionally. I have no clue why and where this happens, and I've seen it across all Windows versions and also on OS X. In all cases, adding a line to **/etc/hosts** like this one *did* solve the problem.

```
192.168.200.1   hotspot 
```

Of course, you'll have to put your hotspot's IP address and hostname in there, you should be able to spot it in the URL your browser is redirected to.

regards

Marc

---

### Post by cnich23 on 2008-05-17
I should note that this is a fresh out of the box install. I played around a bit more and I am not to get a reply from the dhcp serve, even after I have been assigned an ip.  I can ping my assigned ip but not the host, but it says that I am connected!  I'm so confused.

---

### Post by cnich23 on 2008-05-18
I played with it all evening w/no luck kinda not fun on ubuntu w/out the internet to figure out what I'm exactly doing.  Can anyone tell me another approach I can take?

---

### Post by cnich23 on 2008-06-22
I'm still having tons of trouble trying to access the internet and Im really ready to start using ubuntu but Im stuck w/out the interenet.

My driver is zydas/ar5212 and I am able to connect and be assigned a ip but cannot navigate or ping the host

---

### Post by cnich23 on 2008-06-22
If this helps any this is my wifi
[http://cgi.ebay.com/USB-WIRELESS-Extender-Booster-Cantenna-802-11b-802-11g_W0QQitemZ160251626243QQihZ006QQcategoryZ294QQssPageNameZWDVWQQrdZ1QQcmdZViewItem](http://cgi.ebay.com/USB-WIRELESS-Extender-Booster-Cantenna-802-11b-802-11g_W0QQitemZ160251626243QQihZ006QQcategoryZ294QQssPageNameZWDVWQQrdZ1QQcmdZViewItem)

---

### Post by cnich23 on 2008-06-24
Can anyone tell me what info Ineed to provide to start finding a solution to  this problem?

---

### Post by ramakrishna_cse on 2010-12-12
I had similar problem,now it is solved.
please check if you can see the default gateway ?

type this command in terminal

ifconfig

and  
route

if you can see an entry for default gateway, then it is ok,else you set it manually

command is
#route add default gw  ur-default-gateway-address

hope this helps

---

