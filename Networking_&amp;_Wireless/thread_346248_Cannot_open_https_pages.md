---
title: "Cannot open https pages"
date: 2007-01-25
forum: Networking &amp; Wireless
---

### Post by cudjoe on 2007-01-25
I cannot open https website with my fresh Ubuntu Edgy.
Connections time out.
Normal http pages are working very well.

I have no Firefox add-on.
I deleted my Firefox profile, created a new one, reinstalled Firefox (with Synaptic),... without success.

I installed lynx, and faced the same problems.

I can connect to ssh servers though, but compared to Ftp login attempts, Ssh login prompts are very slow.

Do you guys have an idea about underlying libraries that could affect the whole system ?

With many thanks,
Thumb up for you guys, I enjoy Ubuntu sooo much !

---

### Post by jimbren on 2007-01-25
What about Konqueror or Galeon?

I don't know which desktop you're using, but I'm curious to know if they have the same problem.

jimbo

---

### Post by cudjoe on 2007-01-26
Thanks Jimbren for replying, I am running Gnome. 

I tried Galeon and faced the same problems.

It must be a common library or component. 

I can´t figure it out...

---

### Post by Noiano on 2007-01-26
> **cudjoe said:**
> I cannot open https website with my fresh Ubuntu Edgy.
Connections time out.
Normal http pages are working very well.

I have no Firefox add-on.
I deleted my Firefox profile, created a new one, reinstalled Firefox (with Synaptic),... without success.

I installed lynx, and faced the same problems.

I can connect to ssh servers though, but compared to Ftp login attempts, Ssh login prompts are very slow.

Do you guys have an idea about underlying libraries that could affect the whole system ?

With many thanks,
Thumb up for you guys, I enjoy Ubuntu sooo much !

try to install openssl...maybe this fix...

---

### Post by cudjoe on 2007-01-26
(thanks Noiano) openssl is installed already...

I found a solution !

I disabled IpV6 in Firefox and now I can open Https pages !
( Open **about:config** in Firefox, filter on IPv6, and set disable ipv6 to **true**. Restart FF )

However, this might reveal a deeper problem in my network configuration.
My connection is quite slow here, that may explain why IPv6 is not working well.
Maybe I should modify my configuration (routes,etc) but I don´t feel comfortable with that...

Should I set my thread to solved ? I guess I can do better than just disable it in FF.

---

### Post by jimbren on 2007-01-26
Disabling IPv6 occurred to me, but I didn't think there was any kind of a connection and figured I was just grasping at straws.  I'm curious, since disabling IPv6 in Firefox, have you tried browsing https sites in Galeon?  It shouldn't be a global configuration, to my knowledge, so theoretically you should still have the same problem in FF.

I came across some speed tweaks a few weeks ago, and one of them has to do with disabling IPv6 on a global level.  If I'm right and you are unable to view https pages in Galeon, you should be able to disable IPv6 globally and then view them.  

The page I'm referring to is [here.]("http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed")  Go down to the heading IPv6 and follow the instructions.  That will disable IPv6 on the whole system, and then it shouldn't matter what browser you're using.  

Incidentally, the section right above the IPv6--called Broadband Internet--speed up my system in a big way.  You might want to check it out if you have a slow connection that you want to optimize.

I don't know if you even care about the global settings or not...I'm just curious to get to the meat of the problem and haven't heard of IPv6 disabling https browsing before.

jimbo.

---

### Post by cudjoe on 2007-01-27
Thanks Jimbren, I disabled IPv6 and it now works with Galeon. 
Gaim can now connect to MSN.
The trick given in the link you gave did not work. 
But [this thread]("http://ubuntuforums.org/showthread.php?t=6841") gives the right instructions.

My problem is solved.
Thank you so much !

---

