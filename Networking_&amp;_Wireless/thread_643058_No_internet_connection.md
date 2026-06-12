---
title: "No internet connection"
date: 2007-12-17
forum: Networking &amp; Wireless
---

### Post by Yorgos Kourtakis on 2007-12-17
I've just installed Ubuntu 6.10 on the first HD of my HP Proliant and Ubuntu 7.10 on the second HD.

The NIC is a Broadcom NeXtreme BCM5721 Gigabit, connected to a modem/router.

When I start with Ubuntu 6.10, I  have no problem.

When I start Ubuntu 7.10, I can't navigate nor download anything, like Ubuntu update, etc.

There is a few exceptions: Mozilla site and some Mozilla links.

Ping works, but nothing else.

I've changed DHCP, IP, etc., but with no result.

Thanks for your help!

---

### Post by blingo on 2007-12-17
ME TOO!

Exactly the same problem, can only access Mozila sites.
I have a Realtek Gigabit wired connection vie router. 
Tried disabling IPv6 and also tried several other distributions - no change.
I don't think it's DNS - I can get ip numbers from address, FireFox seems to find the sites and then it's stuck on "waiting for...".

---

### Post by wherethebibawi on 2007-12-17
Try disableing IPv6 in firefox.

In the address bar type **about:config** and the configuration of firefox should appear.

In the filter bar (search) type IPv6.

The line should read somthing like **IPv6 disable false**
Click on it, it goes **BOLD** then IPv6 should be disabled in firefox now.

See if that solves your problem.

---

### Post by ubutufan on 2007-12-17
Guys contrary to what you say it smells DNS to me.
Do not give DNS of your ISP. Instead in DNS write the IP of your router. It should be the same with gateway.

---

### Post by Yorgos Kourtakis on 2007-12-18
> **wherethebibawi said:**
> Try disableing IPv6 in firefox.



Yet done, but connection doesn't work.

---

### Post by Yorgos Kourtakis on 2007-12-18
> **ubutufan said:**
> Guys contrary to what you say it smells DNS to me.
Do not give DNS of your ISP. Instead in DNS write the IP of your router. It should be the same with gateway.

Yet done, but nothing goes.

---

### Post by blingo on 2007-12-18
Regarding the DNS - If ping [www.something](www.something)... is done, I can see the ip numbers. also tried entering ip numbers directly to the address bar for no effect.

---

### Post by blingo on 2007-12-20
Anyone? 
Please.

---

### Post by ubutufan on 2007-12-21
Very confusing.
Does your email clent work? If yes then the concern is firefox tuning
For the sake of a good exercise, I suggest you do the following.
In Firefox go to Tools>Clear private data.
this will clear up your cache memory. Retry with the mozilla site (that was working). what happens now? does it work?
Also post here the configuration options of network.http... To do that at the address bar of firefox type
about:config
then at the filter bar type
network.http
take a screenshot of the page and post it if that is possible. I understand that you don't have internet access, at least using firefox but you may save the screenshot on a usb and do it from another machine. It is a .png file

---

### Post by blingo on 2007-12-24
[IMG]http://www.uploadpak3.com/freeupload/download2.php?a=32a3aca50f282eb3f290e91bb5ca65ad&b=eb5ab528666ee18fbd8a54f1f402f6b6[/IMG]

Much thanks for the help,
I've cleared privte, I can still access Mozila sites and only them.
Much thanks again.

Note: I've ereased the user name in the screen-shot.

---

### Post by bigken on 2007-12-24
could be the mtu in the router most uk providers are set to 1500 were as aol is 1400 check your service providers mtu

---

### Post by blingo on 2007-12-24
Hello,
Thank you for the help.

Regarding the MTU, The computer is working fine on it's other operating system, also the router works well with other computers. I don't know how to change the MTU on Linux if I should on 7.10.

Strangely when I had an error on an address I've ended up with
something from www,layer0.x3u.com I don't know what it is, and I don't seem to manage to get into it vie the other operating system.

Many Thanks.

---

### Post by blingo on 2007-12-31
Someone?

---

### Post by Yorgos Kourtakis on 2008-01-09
> **blingo said:**
> Someone?

RESOLVED.

I installed kernel 2.6.17-10 and Internet connexion now works.

---

### Post by SuperBo on 2008-01-09
Can you show me how to update kernel without internet.

---

### Post by Yorgos Kourtakis on 2008-01-09
> **SuperBo said:**
> Can you show me how to update kernel without internet.

I installed first Ubuntu 6.10 and so the connection was working.

After I updated to Ubuntu 7.04 saving old kernel.

So from Ubuntu 7.04 to 7.10.

And now I've Ubuntu 7.10 with the kernel of Ubuntu 6.10.

Pay attention to GRUB to choose the correct order of booting kernels.

---

### Post by dstath on 2008-01-09
I think my problem is related. I have internet connection for a few seonds and then it stops. See [here ]("http://ubuntuforums.org/showpost.php?p=4093248&postcount=32")for a description.

---

