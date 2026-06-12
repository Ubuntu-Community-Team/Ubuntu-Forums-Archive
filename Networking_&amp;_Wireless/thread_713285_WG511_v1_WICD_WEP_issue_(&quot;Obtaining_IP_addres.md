---
title: "WG511 v1 WICD WEP issue (&quot;Obtaining IP address....&quot;)"
date: 2008-03-02
forum: Networking &amp; Wireless
---

### Post by redeemer on 2008-03-02
Hello,

I am having problems with my WG511 v1 on Ubuntu 7.04. I have posted this thread over on the WICD official forums ([http://wicd.sourceforge.net/phpbb/viewtopic.php?f=3&t=158&p=2585&sid=ccd987a4336981379388bfdd16ad6d63#p2585](http://wicd.sourceforge.net/phpbb/viewtopic.php?f=3&t=158&p=2585&sid=ccd987a4336981379388bfdd16ad6d63#p2585)), but thought here would be a good place to try too.

[paste]

I had this problem back in July, but managed to resolve it. Annoyingly, I reinstalled network-manager (for VPN reasons) and it completely ruined my wicd setup. Sad I didn't know it would do this... and am damn annoyed about it!

Even more annoying is that I can't find my thread that resolved my issue first time round.

So yeah, my original thread (at WICD forums) on this was: [http://wicd.net/phpbb/viewtopic.php?f=4&t=141](http://wicd.net/phpbb/viewtopic.php?f=4&t=141)

My setup is still Netgear WG511 v1, and I am using Ubuntu 7.04. The only difference this time is that we are using WEP and not WPA security.

Installing network-manager seemed to have the following effects:

1. lost most of the stuff in /opt/wicd and had to reinstall WICD (it works in that I can pull up the WICD GUI)
2. /etc/network/interfaces had more entries, so I commented everything out apart from (as advised to on WICD download page):

auto lo
iface lo inet loopback


I checked ndiswrapper installed drivers and the driver is still apparantly correctly installed. I have since uninstalled network-manager, but the problem still exists.

Can anyone suggest anything from here? Feel free to let me know of any command output that you need, and I'll happily oblige. I have four weeks left of my final term of BSc study, so this isn't great timing for me! The sooner I get back online, the better.

[/paste]

Thanks for any help.

Tom

---

### Post by jeffus_il on 2008-03-02
Network Manager installs dhcdbd for a dhcp client. This remains after the install and wrecks Wicd. Remove dhcpcd and install dhcp3-client instead.

---

### Post by imdano on 2008-03-02
I think NM does use dhclient, and installs dhcdbd (which looks like dhcpcd).  It stands for dhclient d-bus daemon, and it used to control within NM.  Maybe make sure that dhcdbd is uninstalled?

---

### Post by jeffus_il on 2008-03-03
Thanks for the correction, it's dhcdbd that must be removed, two many dbbdbdbdbd's, must have mild dyslexia ...

---

