---
title: "NETBIOS Name Makes a Difference"
date: 2017-01-02
forum: Networking &amp; Wireless
---

### Post by ttoolin on 2017-01-02
Hi folks-

I just successfully set up a home network between my 16.04 Ubuntu machine and two Windows machines.  I have been fighting this issue since I upgraded to 16.04 some months ago.  I only mention this because, even though this information may have been in the forum for me to see, I never saw it, and stumbled upon it quite accidentally, from a source outside of this forum:

The NETBIOS name (in the global section of smb.conf) cannot have special characters in it. Doing so will cause problems getting networking to work.

What I've been doing wrong for months:  I use a very old howto forum posting as a networking set-up guide, which suggests using the computer name that appears in the terminal screen (in my case, it's:   terry-ThinkPad-T60).  I've used many Ubuntu distributions on many different machines, and the default NETBIOS name (per the old howto guide), has been shorter and without special characters, until I loaded 16.04.

I am experienced enough to have been aware of this, and 95% of my dilemmas are easily answered in the Ubuntu forum.  I post this only because the answer was so simple, and I fought the issue for so long, that I hope I can help others with it.  

terry

---

### Post by TheFu on 2017-01-02
> **ttoolin said:**
> special characters in it. Doing so will cause problems getting networking to work.

While things are often possible, staying simple, all lower-case, will make your life harder.  The same applies to directory and file names.  Don't use odd characters, don't use spaces - sure, you CAN do this, but now every script written by every person who ever wrote a script has to handle that stuff correctly.  That is unlikely.

I replace all spaces in directories/names with an underscore.  I remove any shift-{number} characters and any parenthesis, single/double quotes and any funny characters.

Doing these things will make your life easier.

And usernames, groupnames, and hostnames should all be lowercase alpha-numerics too.  There is enough trouble to be found - don't go looking for it.

---

