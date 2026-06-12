---
title: "Bogus user/pass authentication prompt on nxdomains"
date: 2014-01-27
forum: Networking &amp; Wireless
---

### Post by watchpocket on 2014-01-27
When I want to log into my router's web interface, I enter the following into my browser's address bar and hit return: 
 
***[http://192.168.1.1/Status_Router.asp](http://192.168.1.1/Status_Router.asp)*** 
 
(Actually, I  have that bookmarked.) 
 
My browser (Firefox 26.0) then immediately displays a dialog box with the following text: 
 
***A username and password are being requested by [http://192.168.1.1.](http://192.168.1.1.) The site says: "BuffaloStreet-dd-wrt"*** 
 
(*"BuffaloStreet-dd-wrt"* is what I've named my router.) 
 
Just below that text in the dialog box are two fields prompting for User Name and Password.   
 
Fine, no problem.  This is known as the browser's HTTP Basic Authentication prompt. 
 
 
The problem comes when I enter into my browser's address bar an *nxdomain* (non-existent domain), or *any name that doesn't resolve:*   The exact same dialog box pops up. 
 
This time the message is almost, but not quite, identical: 
 
***A username and password are being requested by [http://](http://)[COLOR=#0000ff]name-that-doesn't-resolve[/COLOR]. The site says: "BuffaloStreet-dd-wrt"*** 
 
In all cases, entering User/Pass takes me to the router's web interface. [I][COLOR=#ff0000]  But this dialog box should not be appearing at all when names entered  in the address bar don't resolve. 
 [/COLOR][/I]
Same thing happens when I run Firefox in safe mode. 
 
This leads me to believe that I've misconfigured something in my router settings, but what? 
 
I'm using Ubuntu 12.04 with Gnome Classic.   The router is a ***Buffalo WZR-HP-AG300H***, with firmware version: ***DD-WRT v24-sp2 (04/13/11) std - build 16785***. 
 
My question is: What's causing this to happen?  Thanks.

---

### Post by coldraven on 2014-01-27
Have you somehow got your router's address in your browser's list of search engines?

---

### Post by watchpocket on 2014-01-27
Thanks for the thought, but no, I checked all my search sites.

---

### Post by CharlesA on 2014-01-27
Check your DNS. It sounds like what my ISP likes to do if I typo a url or address bar search and they redirect me to their landing page of search results instead of google.

I had to remove ALL their DNS servers from my list and set static ones to replace them.

What happens if you try to run dig against a non existent domain?

---

### Post by watchpocket on 2014-01-28
First I need to act on a previous suggestion of yours in another thread where I set OpenNIC nameserver addresses in the static-number setting in my router and, when that didn't seem to resolve non-ICANN names, I put them also in /etc/network/interfaces, after which time, they did.  You said it should have been necessary to put them in the router only.  

I haven't yet tried to remove them from /etc/network/interfaces.  I also need to upgrade my router's firmware, which at this point is very old. 

 But this same dialog box was popping up even before I entered the OpenNIC numbers, when my ISP's numbers were active.  Then, I was getting thrown to Optonline's landing page AND getting the HTTP authentication prompt dialog box.  Now I get the dialog box and only a white window behind it while the favicon endlessly spins.

---

### Post by CharlesA on 2014-01-28
Maybe the router is being weird. I would go for a firmware upgrade (and factor reset, after backing up traffic data or anything else you want to keep).

Just be sure to download the current firmware in case the newer firmware doesn't work so well. I upgraded the firmware on a DIR-615 and the wireless died, so I had to flash it back to 14xxx instead of 21xxx.

---

### Post by watchpocket on 2014-02-14
Minor update to this problem:   
 
Going into my router's dd-wrt web interface, under [COLOR=blue]Administration --> Management[/COLOR], if I ***uncheck*** the "[COLOR=brown]Info Site Password Protection[/COLOR]"  checkbox (disabling it) I've discovered that when I go to a nonexistent  web address, instead of the HTTP auth prompting me for  Username/Password, I am immediately shown my router's [COLOR=blue]Status --> System Information[/COLOR] page. 
 
From there, if I click on any other tab, I am ***then*** prompted for the router's Username/Password. 
 
I decided to go back to having "[COLOR=brown]Info Site Password Protection[/COLOR]" enabled. 
 
I've also disabled "[COLOR=brown]Web GUI Management[/COLOR]" ***remote access***.   I don't need remote access activated and it will obviously be safer to  keep it disabled. (Changing this setting did not affect the problem of  the prompt, one way or the other.) 
 
I pass this along in the hope that it may help someone figure out how  I'm getting the prompt on wrong and/or nonexistent URLs.  I do plan to do a  router firmware upgrade when I get a chance.

(P.S. I get the same problem in the GNU IceCat web browser.)

---

### Post by CharlesA on 2014-02-14
It sounds like any traffic that is being passed thru the router is being filtered. Do you have content filtering or a proxy enabled on it?.

If you haven't reset it to factory defaults, you could try doing that to see if that resolves the issue.

---

