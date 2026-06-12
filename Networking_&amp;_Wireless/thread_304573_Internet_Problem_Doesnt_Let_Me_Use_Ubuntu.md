---
title: "Internet Problem Doesnt Let Me Use Ubuntu"
date: 2006-11-22
forum: Networking &amp; Wireless
---

### Post by tansu on 2006-11-22
Well,
I've been trying to use Ubuntu for about two years, and I also tried suse, fedora, mandiriva before ubuntu.
The same problem occurs with every distro, but now I wanted to stick to Ubuntu.
Here's my problem:
Everytime I install Ubuntu, it goes perfect for about a week. Then suddenly, when I type a common web page visited by me to any browser, for example ubuntu.com, it redirects to bbc.co.uk, cnn.com or last.fm. As I mentioned it happens with all distros.
I never could fix this because my connection sucks with these three web sites.
Finally, I set Edgy and it really goes well again for a week, then I realized that something worked without my permission or demand and as well as I could see it, it was something like "cache cleaner". Right after that, my web pages started to redirect again.
Strange thing is, just after it occurs, when I switched to Windows, for the first time it always happens again with any browser.
So any ideas to make me a long term Ubuntu user?

---

### Post by dmizer on 2006-11-22
well, i'm having a difficult time trying to figure out how to reply to this, because this is unheard of in linux.

tell you what.  try this:
instead of clicking on the icon to open firefox, open a terminal window.  type: firefox and hit enter.  firefox will appear.  now browse.  when you get redirected, take a look at the terminal window.  if there's anything written in it, copy that and paste it here.

edit:
are you using a laptop with a touchpad for a mouse?

---

### Post by tansu on 2006-11-22
Ok, I will do that..

---

### Post by tansu on 2006-11-22
> **dmizer said:**
> 

edit:
are you using a laptop with a touchpad for a mouse?
No I dont,
I use AMD desktop, 64 bit processor, it happens with both 64-bit and 32-bit distros..

---

### Post by tansu on 2006-11-22
&#304;t did not happen yet, but I know it will. And then I will post the terminal contents.
You can see in the screeny, the web page is my own web site, but the favicon is bbc, because it was redirected at the previous logon.

[[IMG]http://img292.imageshack.us/img292/327/ekrangrntscr1.th.gif[/IMG]](http://img292.imageshack.us/my.php?image=ekrangrntscr1.gif)

---

### Post by dmizer on 2006-11-22
there sure is a lot of active x on that site.

please forgive my ignorance, but what language are you operating under?  maybe it's a problem specific to your locale.

---

### Post by Peepsalot on 2006-11-22
Maybe it is some bizarre DNS issue?  Could it be your DNS is resolving urls to the wrong IP addresses?  Do you know how your DNS is configured?

Next time it happens, you could try pinging the url and seeing what ip it goes to.
```

ping ubuntu.com

```

---

### Post by tansu on 2006-11-22
> **dmizer said:**
> there sure is a lot of active x on that site.

please forgive my ignorance, but what language are you operating under?  maybe it's a problem specific to your locale.
Thats my web site, [www.doctus.net](www.doctus.net) and as much as I know it s only vbulletin :) I am operating under Turkish but it is absolutely not a language issue. I tried tones of languages and other distros.
Normally I use English but edgy has an issue with my Turkish keyboard..

> **Peepsalot said:**
> Maybe it is some bizarre DNS issue?  Could it be your DNS is resolving urls to the wrong IP addresses?  Do you know how your DNS is configured?

Next time it happens, you could try pinging the url and seeing what ip it goes to.
```

ping ubuntu.com

```
I have no idea about the DNS's. If you tell me exactly how to configure it I will surely do.
And as I mentioned before, just after this thning, when I switched to Windows, it makes the same thing too, So maybe it is an hardware problem.
And I forgot to tell you, I use static IP

Edit: it is not only happening to my web site, it happens to my much visited web sites like google, wilderssecurity, and some others... But the common point is, I use them a lot.

---

### Post by stream303 on 2006-11-23
Huh, wonder if you've got a rogue dns server in your **/etc/resolv.conf** file?  I'd doublecheck to make sure that the primary and backup nameservers are those from your isp....

---

### Post by tansu on 2006-11-23
> **dmizer said:**
> well, i'm having a difficult time trying to figure out how to reply to this, because this is unheard of in linux.

tell you what.  try this:
instead of clicking on the icon to open firefox, open a terminal window.  type: firefox and hit enter.  firefox will appear.  now browse.  when you get redirected, take a look at the terminal window.  if there's anything written in it, copy that and paste it here.

edit:
are you using a laptop with a touchpad for a mouse?
Here is what it shows in Terminal, Which I typed [www.hotmail.com](www.hotmail.com) and it goes to 360.xbox.de.
```
** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

```

> **stream303 said:**
> Huh, wonder if you've got a rogue dns server in your **/etc/resolv.conf** file?  I'd doublecheck to make sure that the primary and backup nameservers are those from your isp....
That is written there: 192.168.1.1

---

### Post by dmizer on 2006-11-23
what plugins do you have installed?  how about extensions?

---

### Post by tansu on 2006-11-23
> **dmizer said:**
> what plugins do you have installed?  how about extensions?
The only change I made in Edgy, installing Amarok. There are absolutely no changes in any package. And ofcourse mozilla firefox is also did not changed, no extensions or plugins...

---

### Post by dmizer on 2006-11-23
here's a shot in the dark.

try this:
in the address bar, type about:config
search for **keyword.url**
right click on the google url and select "modify".
replace the entire string with: [http://www.google.com.my/search?q=](http://www.google.com.my/search?q=)
click ok, restart firefox and run with that for a while.

---

### Post by stream303 on 2006-11-24
> **tansu said:**
>  192.168.1.1

aha.  I'd definitely edit /etc/resolv.conf and put your isp dns nameservers at the top of the list.  This private ip address listed may not be sufficient.

Since you are running static, there should be no worry of this file getting overwritten.

I don't run windows anymore, but you should be able to find them out from the commandline - perhaps a quick search or windows-savvy user could chime in.

---

### Post by monkieie on 2006-11-24
I would certainly contact the ISP and ask them for their DNS addresses and use them directly instead. The fact that the problem is also occuring via Windows certainly tells us that the OS is not at fault. I would most probably suggest that there isn't a HW issue here but try using the DNS IPs directly and see what happens.

---

### Post by tansu on 2006-11-27
I believe, puting my ISP DNS IP's to resolv.conf solved the problem.
Thanks to everybody.
If anything goes wrong I will surely let you know here..:D

---

### Post by tansu on 2006-11-28
Eh, it was a nice journey :) 
I installed Beryl and resolv.conf revert back to original.

---

### Post by tansu on 2006-11-30
resov.conf is kiddin me..
after a crash (of any application) it resets itself to original.
Guys I tried so hard to use linux for a year but..

---

### Post by stream303 on 2006-12-01
No problem now that we know the isp's dns addresses.

Easiest option : place your isp's dns primary and backup nameserver addresses into your *router* setup page.

If you don't have access to the router you can edit /etc/dhcp3/dhclient.conf and look for the PREPEND line. Just edit that one line, reboot and you should be good to go.

I wrote a quick howto for it here - don't give up just yet! :)

[http://www.ubuntuforums.org/showthread.php?t=307758](http://www.ubuntuforums.org/showthread.php?t=307758)

---

### Post by tansu on 2006-12-02
> **stream303 said:**
> No problem now that we know the isp's dns addresses.

Easiest option : place your isp's dns primary and backup nameserver addresses into your *router* setup page.

If you don't have access to the router you can edit /etc/dhcp3/dhclient.conf and look for the PREPEND line. Just edit that one line, reboot and you should be good to go.

I wrote a quick howto for it here - don't give up just yet! :)

[http://www.ubuntuforums.org/showthread.php?t=307758](http://www.ubuntuforums.org/showthread.php?t=307758)
all right..
Thanks to everyone..
I replaced dns addresses in my router, and used "opendns". It runs fast and clean now..
I can now enjoy.
Thanks to everyone again..

---

