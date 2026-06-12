---
title: "You can ping but you can't surf with dns"
date: 2006-11-23
forum: Networking &amp; Wireless
---

### Post by stream303 on 2006-11-23
A quick summary on how to fix the most common **dns issues** when using **dhcp** behind an inexpensive router and why editing **/etc/resolv.conf** manually _doesn't work for long_:

When manually adding a nameserver to /etc/resolv.conf, it is only a temporary solution since dhclient (actually dhclient-script) overwrites this file on re-lease or reboot.  This only happens when using dhcp.  Thus manually editing resolv.conf might only be useful during a "live-cd" session or when you are running a static ip.

Various tricks like changing the permissions of resolv.conf eventually fail because dhclient runs as root and overwrites it. Other tricks like making the file immutable (using chattr) are also not recommended.

Of course one could always run static where nothing overwrites resolv.conf, but the following is what I recommend for the anyone behind an inexpensive router running dhcp when they only see their router's dns server (actually a dns forwarder masquerading as a dns server in many cases) in resolv.conf

**Option 1:** place your isp's primary and backup dns server addresses in the router setup page.

**Option 2:** Uncomment and edit (as root, ie sudo) the **PREPEND** line of **/etc/dhcp3/dhclient.conf** and place your isp's dns nameserver(s) there. In case of multiple nameservers, be sure to separate them with a comma and end the line with a semicolon.
[B]
Option 3:[/B] Edit (as root) **dhclient-script** and remove all the commands in the mk_resolv.conf{} function so your edited resolv.conf won't be overwritten.  Not recommended as option 1 or 2 usually suffices and many of us (myself included) can mess up the edit.

After applying one of these fixes, you should bring your interface down and up again, or maybe the easiest is to just reboot.

**IPV6** - even after all this sometimes our inexpensive hardware may have trouble with IPV6.  Normally I don't recommend disabling it, but if you feel you should, you can disable it globally by creating a file titled "bad_list" in **/etc/modprobe.d** directory.  **bad_list** can contain just this line:

**alias net-pf-10 off**

You can also disable IPV6 in Firefox by putting
about:config
in the url bar.  Once the configurations are found, in the filter bar, search for IPV6.  Once found, doubleclick the search result to change the boolean value from false to true.  Restart Firefox.

Hope this helps...

---

### Post by awbassett on 2006-11-23
Nice job on this. This should probably be moved to the Tips, Tricks, & Howtos section.

---

### Post by veeravalli on 2006-11-26
Thanks a bunch!  Option 2 worked for me and not having to set Network Settings each time I use Synaptic Manager is a big relief! (I could however browse any site I wanted to with Firefox without any fuss).

---

### Post by stream303 on 2006-11-27
I'm glad it seems to be working!  I have placed it into the HOWTO forum for easier reference:

[http://www.ubuntuforums.org/showthread.php?t=307758](http://www.ubuntuforums.org/showthread.php?t=307758)

---

### Post by handy on 2007-01-24
> **stream303 said:**
> I'm glad it seems to be working!  I have placed it into the HOWTO forum for easier reference:

[http://www.ubuntuforums.org/showthread.php?t=307758](http://www.ubuntuforums.org/showthread.php?t=307758)

I wish you had have done this how-to last October (or before) when I laboriously made my how-to for the same things, & not as well, because the guts of it was based on a post made by you (with credit given :) ) possibly months before that date!

Anyway, for such a common problem we can't have too many ways to solve it, or access (roughly) the same information.

Apart from the credit I have given you **Stream303** in different posts, where I have pointed to my how-to, & on my how-to itself, I will (one last time) say thankyou, because your ***prepend*** info' has saved so many people a lot of time. :KS

---

