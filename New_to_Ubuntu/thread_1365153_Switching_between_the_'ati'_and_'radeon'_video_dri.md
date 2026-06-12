---
title: "Switching between the 'ati' and 'radeon' video driver"
date: 2009-12-26
forum: New to Ubuntu
---

### Post by Pas_sa on 2009-12-26
Hi folks,

It appears it is no longer possible to edit a static xorg.conf file in Karmic Koala. How can I check which open source radeon driver I am using (either the 'ati' or 'radeon' driver) and change which one is active?

I have a Radeon 7500 and experience visual glitches and extreme lag with Ubuntu. glxgears produces 3300-ish frames and visual effects work perfectly, though very very laggy.

---

### Post by aextance on 2010-01-03
Hi Pas! 

Looks like you're trying to do something similar to me. I too have glitches with my ATI Radeon Mobility X7500 on my IBM T30 Thinkpad. See the link below for more details:

[http://ubuntuforums.org/showthread.php?p=8602595](http://ubuntuforums.org/showthread.php?p=8602595)

Thankfully I'm finding Karmic much less laggy than Intrepid. 

I have determined that my Radeon is using the ATI driver by looking at the /var/log/Xorg.0.log file. However, I would like to try using the radeon driver to see if it will solve a few problems I'm having. According to this link it should work for me:

[http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_7500](http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_7500)

Like you, the main advice I can find suggests working with Xorg.conf:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

I will give this a go and let you know how I get along. 

Cheers,
Andy

---

### Post by aextance on 2010-01-03
You'll note in the first thread above that I've sorted my problems through an xorg.conf tweak. Hope it does the trick for you too.

---

