---
title: "Network Manager Applet doen't show wireless information when using static IP"
date: 2008-10-03
forum: Networking &amp; Wireless
---

### Post by dcviana on 2008-10-03
Hi all.

I'm using Ubuntu 8.04. I have a wireless network and I'm using Network Manager to manage this connection.

When I'm using "Roaming Mode" everything is fine. The applet icon show as a bar indicating signal potency and clicking with the left mouse button list all the wireless connections detected so I can click one of them.

But if I turn off Roaming Mode the following problems occur:

1 - It doesn't list any wireless networks anymore. I have to somehow guess the SSID so I can inform it in the configuration screen.

2 - In the same configuration screen, in the "Password Type" field, there is no option for unsecured network. After a while I discovered that I can simply choose any other type (WPA for example) and leave the password field blank. This is counter-intuitive.

3 - The applet icon no longer indicates signal potency. In fact, it seems that if I turn roaming mode off, the applet doesn't show any indication that it is connected to a wireless network.

I would like to know if there is a patch to fix those problems, or another GUI application to configure my network, as I find at this point the Network Manager extremely difficult for the beginner. I tried to convince a friend to use Ubuntu saying that it is very user friendly and when we saw the network configuration screen all we could thing was "In Vi$ta it's easier"

Thanks

---

### Post by iponeverything on 2008-10-03
nm-applet is still very much a work in progress, but is moving along quite rapidly. In Intrepid the version is very different and in my opinion -- better in many respects.

---

### Post by dcviana on 2008-10-04
So, is there a way to use Intrepid's version on Hardy? Maybe a backport.

---

### Post by SamNSane on 2008-10-04
It's possible you may find a way to work with the applet. I think it's pretty awkward, but I'm trying to stick with supported stuff on my Ubuntu installations.

That applet just works a lot better with roaming left on, but I have to use my laptop on several networks on which DHCP is not used. I imagine you may have noticed that, when you set up a fixed IP address you'll find the DNS settings from the most recent roaming connection are still there on the DNS tab. If you haven't tried it already, just go through all the settings for your fixed IP locations, then use the little hard drive icon on the applet to save the settings for each location -- with a different name for each, of course. Then, when it's time to connect to one of those locations, just choose to configure manually, unlock the applet, select the location from the drop-down, and hit the checkmark button to apply the settings.

But, otherwise, just leave roaming on. Don't turn it off in general just to be able to connect to fixed IP locations.

I hope that makes sense. At least if you do it this way you don't have to go through all of the settings every time you want to reconnect to a network with a fixed IP address.

Of course I realize that few, if any, of your real reservations about using the NM applet are answered by my suggestion. I'm just hoping you might find a way to get along with the dumb little thing. I managed, but I'm a dumb big thing that likes dumb little things.

A couple of ubuntu versions ago I tried wicd. This is a replacement for the applet which plagues you. I recall wicd being VERY nice and easy to use. But it's not in the standard repositories. You can get it at

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

There are downloads and instructions for a number of Linux distributions there, and excellent instructions -- from what I remember. Also, if memory isn't failing me, the installation instructions tell you how to remove the NM applet (and how to reinstall it, if need arises) so that the two don't wind up crossing swords.

I hope you find a way to get along with the networking front end on Ubuntu, one way or another. I've got to admit it can be pretty frustrating at first, particularly (for me) the first time I connect to a fixed IP address and have to wait for the danged system to decide that it ain't gonna get no stinking cooperation on IPV6 and falls back to IPV4. (I may be showing extreme ignorance of an easy workaround for this issue. If so, I hope some kind passer-by will put me out of my misery by striking me viciously with the clue-by-four.)

---

### Post by dcviana on 2008-10-06
Thanks for your suggestion on using wicd, will try it later.

As you said, your other suggestions unfortunately don't apply to me, as I'm using a notebook I move around a lot, and the only network I use that has DHCP is at home.

I already use the save feature to save profiles, I did notice the nm-applet keeps the last DNS settings it used when I change networks.

Overall, I think nm-applet still need a lot of work to be user-friendly. I just hope it will be fixed in Intrepid (or better yet, fixed in Intrepid alpha and backported to Hardy \\:D/ )

---

### Post by SamNSane on 2008-10-06
> **dcviana said:**
> Thanks for your suggestion on using wicd, will try it later.

As you said, your other suggestions unfortunately don't apply to me, as I'm using a notebook I move around a lot, and the only network I use that has DHCP is at home.

I already use the save feature to save profiles, I did notice the nm-applet keeps the last DNS settings it used when I change networks.

Overall, I think nm-applet still need a lot of work to be user-friendly. I just hope it will be fixed in Intrepid (or better yet, fixed in Intrepid alpha and backported to Hardy \\:D/ )

I echo those sentiments. They need to fix it or replace it -- if they want dummies like me being comfortable with the distro.

Please let me know how it goes with wicd. I hope it works for you.

---

