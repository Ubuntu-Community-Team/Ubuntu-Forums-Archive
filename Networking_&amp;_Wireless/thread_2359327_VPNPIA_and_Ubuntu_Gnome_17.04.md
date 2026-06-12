---
title: "VPN/PIA and Ubuntu Gnome 17.04"
date: 2017-04-22
forum: Networking &amp; Wireless
---

### Post by russkyca on 2017-04-22
Does anyone use VPNs or ExpressVPN or PIA (Private Internet Access) VPN (this is the one I currently use)?   I suppose they all work more or less the same.   

I use PIA with Ubuntu 16.04 with no problem.   Let me quickly explain why I have TWO partitions of Ubuntu.   Well, it's precisely for this reason.   I used my (2nd) aka other partition to 'try things' - upgrades - early upgrades when the newest Ubuntu was just released.    I don't know if that is why I am having a problem but I checked the PIA forum and some people are posting about having problems connecting using 17.04.   Okay, now I'll try to explain as accurately as possible, what's happening.   

Unfortunately, I don't know all the tech. jargon or the programs/internals so I'll just describe what I see.

PIA and Ubuntu 16.04 works - I click PIA in 'Other' and then a server (location) and it connects.   Good.

But, when I try to do the same in 17.04, it 'tries' to connect and shows 'connecting' but it doesn't really.   The icon is greyed out.   Normally, it turns red to green.   

I *just* noticed all the servers are illustrated in my Network settings.   If you open the network settings (is this network manager or more specifically(?) Gnome Network Manager?), I see all the servers under 'Wired'.   I don't see this in NM in 16.04.   My settings look 'normal' in 16.04.    There's some posts in the PIA forum about something to do with network manager.   

Can anyone comment on this?   Can you recognize what's happening?  I can't.   I have no idea where to go from here.   I can only speculate and guess that something got screwed up during the configuration process when PIA was set up.   But, I just followed the instructions - they seemed pretty similar to what I did in 16.04.   

I'm not sure what to do now.
To recap:
Ubuntu 17.04 is up to date - I have internet access.... I have tried a free vpn - and it worked.   I connected to a free vpn ....so, I am able to use 'a VPN in general' so to speak
PIA works in Ubuntu 16.04 so far, for me..... it works every time.   I can try various server locations.... they work.   
I installed PIA and tried to connect in Ubuntu Gnome 17.04 - but it doesn't actually connect.   The 'app' (in red) shows 'connecting' but it doesn't.   the app turns grey but nothing shows 'connected' (obviously) and when I go to a web page, my IP is unchanged.   

Oh, I almost forgot!   I tried the servers 'under' "Wired" in the network manager gui, and they worked.   I can get them to connect.   So, it's like....when the configuration was being done, the PIA app - I don't know what to call it - they servers are only in name - they display but selecting them, nothing happens.... however, the servers got listed in network manager and they do work.   Do I make sense at all?!? :)   

In 16.04, in /etc/NeworkManager/system-connections - there's nothing there unless I created it... I tried creating a VPN.... so there's only one file there.
In 17.04, in the same direction, the files there are all the locations of the PIA servers.   I have no idea how they got there or why they were placed there.... this is really fishy so I was hoping someone recognizes what's going on and knows how to fix it....

If you require further info or want me to run any commands or use pastebin - to show what the output is, just let me know.

Thanks.

---

### Post by beckstea on 2017-05-04
[FONT=arial]I followed the suggestion here: [https://www.privateinternetaccess.com/forum/discussion/23747/pia-on-ubuntu-17-04](https://www.privateinternetaccess.com/forum/discussion/23747/pia-on-ubuntu-17-04)

sudo apt-get install net-tools

Apparently ifconfig is missing in 17.04.

I also had an issue with the task icon not being displayed which I resolved using the suggestion here: [http://www.webupd8.org/2017/04/fix-appindicator-not-working-for.html](http://www.webupd8.org/2017/04/fix-appindicator-not-working-for.html)[/FONT]

[FONT=arial]You can add the line: [/FONT][COLOR=#000000][FONT=&quot]env XDG_CURRENT_DESKTOP=Unity
[FONT=arial]
[/FONT][/FONT][/COLOR][FONT=&quot][FONT=arial]to the pia.sh script that is installed in your home directory.[/FONT][/FONT][COLOR=#000000][FONT=&quot][FONT=arial][/FONT][/FONT][/COLOR]

---

