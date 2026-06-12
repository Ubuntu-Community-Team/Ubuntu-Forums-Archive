---
title: "Ahh! /etc/hosts keeps overwriting!"
date: 2007-09-19
forum: Networking &amp; Wireless
---

### Post by wesblake on 2007-09-19
Hi. Going nuts here, I have 3 wireless networks saved in "NetworkManager Applet 0.6.4" build into Ubuntu. ONe for home, one for work, and one for my parents. I work from all 3 at times though so I have /etc/hosts entries for some work servers so I can ssh. What's driving me nuts is every time I switch between them in the NetworkManager Applet it seems to set my /etc/hosts back to default removing these entries, even if I go in as root and chmod to 444 the hosts file. Anybody know how to stop this file from changing?

---

### Post by braddock on 2007-10-03
This is driving me nuts too.

Is Ubuntu really Linux or not?  Because for 15 years I've been able to count on adding hosts in the /etc/hosts file...if the GUI guys want to overwrite the config, at least parse what I've added by hand first - it is just as valid an interface as having entered it into some widget.

---

### Post by elvis on 2007-10-03
> **braddock said:**
> Is Ubuntu really Linux or not? 
Heh.  That line was quote worthy. :)

Make /etc/hosts immutable, and nobody (not even root) can modify it:

```
sudo chattr +i /etc/hosts
```

If you ever want to modify it in the future. just reverse the process (use "-i" instead), edit it, and then set it immutable once more.  "lsattr" will show you any extended attributes on a file.  "man chattr" will give you a complete list of the attributes, and what they do.

That's the dirty hack way.  The clean way would be to trawl your /etc folder looking for the script that modifies the file, fixing it so it doesn't clobber it all the time, and then submitting it to bugfixes/launchpad as a fix.

And for the record, yes, Ubuntu really is Linux.  If every Linux distro was the same, and every Linux distro did the same sorts of things since 1997, then we wouldn't have change nor progress.  Part of change and progress is pissing people off ocassionally in the form of bugs and silly changes.  Report the fault, suggest a possible fix, and it will all be well again in the future.

---

