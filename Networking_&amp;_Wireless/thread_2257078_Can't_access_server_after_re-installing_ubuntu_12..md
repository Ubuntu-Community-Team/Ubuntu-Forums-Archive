---
title: "Can't access server after re-installing ubuntu 12.04"
date: 2014-12-16
forum: Networking &amp; Wireless
---

### Post by bengy103 on 2014-12-16
Hi all,
I've tried googling for an answer and tried searching this forum with that bl**dy useless search box but no luck.

I created a Ubuntu server, located in our spare bedroom. It's not intended to go on the internet, just serve us in our house. It started at Ubuntu 12 but is probably 14 by now.

It was fine, storing photos, music and such like and appeared when I browsed the network. Now it only appears under the windows network folder. Of course it was me that screwed things up when I got fed up with the idiosyncrasities of ubuntu 14 on my workhorse computer set up in a corner of my kitchen and wiped it and re-installed ubuntu 12. Now I can't get to the files. All I get is 'Unable to mount location' and 'Failed to retrieve share list from server'.

When I set the server up (with the help of Goguda in Youtube) it worked fine. I even expanded it to be a print server.
It seems that the network printers have installed OK. Or at least I can see the printers, I haven't tried printing a test page.
I can ssh to it using Terminal but it doesn't put me on the server just says 'The authenicity of the host .... ..... can't be established......ECDSA fingerprint...... Then at the end of this onesided exchange comes 'Permission denied (publickey)'.

I know I've abbreviated a lot above but to be honest I probably don't know enough to ask a sensible question.

Oh, if I smb://..... it gives me a list of my server files. Not that I can do anything with that.
Oh, Oh, I've just remembered I did something somewhere that allowed me to ssh in Terminal without having to put in my password, Unfortunately I changed my computer desk last week and my server notes seemed to have gone out with the old desk. Sorry.

regards,

brawd

---

### Post by bengy103 on 2014-12-18
Yes you guessed it, it was the good ol' name resolve order in /etc/samba/smb.conf.

I'd completely forgotten that I had to sort that out on my workhorse machine as well as the server.

Slaps head.

brawd

---

