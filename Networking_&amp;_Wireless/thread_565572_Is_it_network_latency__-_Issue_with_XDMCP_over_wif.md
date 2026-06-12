---
title: "Is it network latency ? - Issue with XDMCP over wifi"
date: 2007-10-02
forum: Networking &amp; Wireless
---

### Post by jamcdona on 2007-10-02
Hi I'm running Fiesty on a home server and have Exceed 7.1 running under XP pro on my laptop.

I'm currently using gdm and have the xdmcp enabled etc. I'm able to issue an xdmcp query from my laptop and login to gnome without any problems whilst using a wired 100Mb connection via a netgear DG834 router, however, when I switch to wireless on the same router I do get the gdm login box , albeit very, very, very, slowly. I can see it render whilst watching and it takes well over 5 mins before the gdm login dialog renders the "username" textbox. I can then enter a username (although the display cant keep up) and eventually after another 5 mins get the "password" text box, again I hit return but thus far havent had the patience to wait to see if the mystical splash screen will appear.

The activity LED's on the router are flikering like billy-oh whether using the 100Mb wired connection or the wifi connection so clearly there is a lot of activity.

My laptops wifi is only 802.11b but even with my laptop on the same desk as the router with max signal strength and an apparent 11Mb connection.

My question is this, am I being over optimistic about being able to run Gnome (or for that matter KDE) over wifi ?  I realise there are a few more bells and whistles but back in the day I used to run X (CDE/fvwm etc) over a 14.4K modem.

I'm struggling to find any documentation about recommended connection speed for running remote Gnome or KDE sessions.

I have seen reference to the use of a proxy (EnableProxy=True) in th gdm config. If I got the gist of the concept correct I assume you can push some of the load back onto the server and minimise the chatter between client and server.

Lastly, I can run vnc and (dare I say) remote desktop over WIFI so I'm reluctant to believe that running remote gnome/kde sessions over wifi is a non-starter.

Any help would be very much appreciated.

Jamie

---

### Post by jamcdona on 2007-10-02
Wow, I'm talking to myself now :o)  ....but I have just seen this post and it looks like it might fulfill what I want to do, especially given VNC seems to work fine: [http://ubuntuforums.org/showthread.php?t=122402&highlight=gdm+wifi](http://ubuntuforums.org/showthread.php?t=122402&highlight=gdm+wifi)

That said, this will continue to bug me and keep me awake at nights so if anyone can shed some light on this please do.

Jamie

---

