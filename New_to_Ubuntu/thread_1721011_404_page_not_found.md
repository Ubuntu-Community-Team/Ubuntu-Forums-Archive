---
title: "404 page not found"
date: 2011-04-03
forum: New to Ubuntu
---

### Post by ssdt on 2011-04-03
I was having a 404 page not found error in specific websites that i visit to. this forum was one of those which i could not go to with a 404 error coming from Google. i searched from yahoo and still the site redirected to google's 404 error page. then i downloaded klamav and right after that the problem was gone.

has anyone seen this kind of an error? if so, does that have anything to do with virus?

---

### Post by ~Plue on 2011-04-04
try clearing your browser's cache, maybe the 404 redirect was still in it when you searched yahoo

---

### Post by ssdt on 2011-04-07
I have cleared the cache. What I see now is that when I go to facebook.com, the page redirects to google. This is also persistent for other websites. Has anyone else seen this problem?
I have installed KlamAV and on the first scan, it was clean and I used Ubuntu nicely. Now again after a few days, I have that back.

---

### Post by conradin on 2011-04-07
I have had issues like that, but clearing the cache as Plue has suggested allways worked before. Is this a wubi install?
try clearing both the /tmp files, as well as $ '/home/username/.mozilla/firefox/RandonStuff.default/Cache/' 

that flash writes to.

---

### Post by Paqman on 2011-04-07
> **ssdt said:**
> I have cleared the cache. What I see now is that when I go to facebook.com, the page redirects to google. This is also persistent for other websites. Has anyone else seen this problem?


This sounds like a DNS problem. Are you using anything except completely default DNS settings on your machine or router? If you are, you might want to contact your ISP. You may need a Windows machine on hand to do any fault finding they require.

---

### Post by ssdt on 2011-04-11
Nope, I don't use any dns. I checked my auto eth0 connection settings and everything looks fine there.

---

### Post by ssdt on 2011-04-11
Has anyone seen this kind of an error? [http://img522.imageshack.us/img522/216/screenshoterrorthereque.png](http://img522.imageshack.us/img522/216/screenshoterrorthereque.png)

This is also what I am getting.

---

### Post by 5149.5 on 2011-04-11
Are you using any script or ad blocking plugins?

---

### Post by crispy_420 on 2011-04-11
At the times you are unable to go to a site (blocked?) are you able to ping said site? This may resolve the issue of DNS or some other setting that has to do with http. If you can ping successfully, it is not a DNS issue more likely a http issue.

Also I didn't see anyone throw the idea of trying another browser as a tool of diagnostics. If it works it must be a Firefox setting. 

Speaking of which, did you look at Firefox's settings for anything unusual?

---

### Post by Miljet on 2011-04-11
A good while back I had a similiar problem in that I could access some sites but not others. After fighting it for a full day, I finally tried pulling the power plug on the router for a few minutes. After plugging it back in everything was fine. I have no idea why this worked, but it did.

---

### Post by 5149.5 on 2011-04-12
> **Miljet said:**
> A good while back I had a similiar problem in that I could access some sites but not others. After fighting it for a full day, I finally tried pulling the power plug on the router for a few minutes. After plugging it back in everything was fine. I have no idea why this worked, but it did.

This can happen when your router gets the ISPs DNS server addresses as part of its initialization. The router then passes the DNS address to your PCs when they initialize. If the ISP has a DNS server issue and sends out the address to  the new DNS server, your PCs will continue to use the address to the broken DNS server until you power cycle the router and your PCs.  Don't ask how I know this.

---

