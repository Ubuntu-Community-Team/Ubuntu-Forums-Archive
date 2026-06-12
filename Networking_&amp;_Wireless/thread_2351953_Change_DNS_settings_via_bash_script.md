---
title: "Change DNS settings via bash script"
date: 2017-02-08
forum: Networking &amp; Wireless
---

### Post by dahayward on 2017-02-08
Hi There

I'm using Ubuntu 16.04 Desktop on my laptop and was wondering if there was a way I could create bash scripts that would change my DNS settings on eth0 whenever I needed to.

This is mainly for the purposes of jumping between two different DNS servers depending on my networking scenario at any one time.

I know I could simply modify the DNS via Network Manager but I think 2 scripts (1 for 1 DNS, 1 for the other DNS) would be better as it would be able to flush the DNS cache too when changing over as well as make all this happen at the click of a button.

I've been searching around but so far I see no forum discussion that gives a clear working answer to this for me.

If someone could help me with this I'd really appreciate it!

---

### Post by TheFu on 2017-02-09
Welcome to the forums.

Don't know how to do this, but ....

* use the nmcli tool. [http://manpages.ubuntu.com/manpages/trusty/man1/nmcli.1.html](http://manpages.ubuntu.com/manpages/trusty/man1/nmcli.1.html) I've never used it and actually purge network manager from my systems (it used to be really terrible, imho).
* normal bash scripting should work. "absg linux" will find a guide.
* flushing the dns cache isn't really done on Unix my past research has found. Even restarting the process won't flush it.

Reading that link - seems to say that saving 2 different profiles with the settings you want and swapping between them would be easiest.

I won't write the script for you (too much like a homework problem), but if you post it then people can help.

---

