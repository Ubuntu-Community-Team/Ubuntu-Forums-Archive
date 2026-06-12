---
title: "Remote Desktop On LAN - set up router required?"
date: 2010-11-30
forum: New to Ubuntu
---

### Post by demonboy on 2010-11-30
I have two machines running 10.10. I would like to be able to use Remote Desktop between them. So far I have set up a wireless network on MACHINE 1 where MACHINE 1 can see MACHINE 2 under 'Networks'. The set-up on MACHINE 1 is as follows:

```

**WIRELESS**
Mode: Ad hoc
BSSID/MAC: all blank
MTU: automatic

**SECURITY**
None (for the time being)

**IPv4 SETTINGS**
Method: Shared  to other computers
'Require IPv4 addressing' is ticked

**IPv6 SETTINGS**
All blank

```My understanding is that both machines need to be given independent IP addresses in order to talk to each other across the network. I think it is DHCP that does this.

To get me started I would like to know:

1. Is this wireless network my Local Area Network by default?
2. If these two machines are connected to the network already, how come their IP addresses are the same? I'm guessing these are internal IP addresses and DHCP is not giving them individual IP addresses on this network.
3. If I have to enable DHCP as the IP4V connection method then I lose my ability to connect to the wireless network AND be online via Mobile Broadband. Spiky01 and I discovered that you have to have 'Method' set up as 'shared to other computers'.
4. Does this then mean I have to assign IP addresses manually across a range? What is that range?
5. Can I use Remote Desktop across this connection without being online?
6. Do I have to set MACHINE 1 up as a router? 
7. If so, is _[this guide]("https://help.ubuntu.com/community/Router")_ what I should be following? It looks quite involved and I am only setting up a three-PC network with no real security requirements
8. The alternative appears to be _[Easy Router]("https://help.ubuntu.com/community/EasyRouter")_, but do I really have to install Ubuntu Server? If so can I install this over the top of an already existing 10.10?
9. One of the guides suggests running MACHINE 1 in 'Master' mode. What is this? I don't see this option.

Thanks for any assistance given.

---

### Post by demonboy on 2010-11-30
Guys, just looking for a nod to see if I'm heading in the right direction here...

It seems I should actually be installing DHCP3-server on one machine, and DHCP3-client on the others (think that's already installed), in order for me to get this Remote Desktop up and running on my network.

Is that correct?

EDIT:
It's now a complete mess. I went ahead and installed DHCP3-server on MACHINE 2, which disables the Network applet. Also I lost wlan0 as one of my network devices. I uninstalled DHCP3-server but the applet is still missing. I have searched and searched on this subject including [here]("http://newyork.ubuntuforums.org/showthread.php?t=1469625&page=3") and [here]("http://practicalswitchtoubuntu.blogspot.com/2009/02/restore-missing-network-manager-applet.html") but they do not solve the problem of the missing applet. When typing sudo edit /etc/NetworkManager/nm-system-settings.conf it comes back with:

```

Warning: unknown mime-type for "/etc/NetworkManager/nm-system-settings.conf -- using "application/octet-stream"
Error: no "edit" mailcap rules found for type "application/octet-stream"

```

Please, I just need a bunk-up here. I'm not asking for someone to do it for me, I would just like to know if I'm even in the right ball-park. This is a very important function for me. Thanks.

---

### Post by QLee on 2010-11-30
> Guys, just looking for a nod to see if I'm heading in the right direction here... Sorry Jaimie, I can't offer a nod, it looks to me like you aren't.

I'm going to again "speak"(write) frankly to you, at the risk of offending you again. I received your PM that the last time I spoke frankly you thought I was being sarcastic. There's no gain for me in that.

The same advice that I have offered previously, applies here. You need to learn before you attempt advanced things in an operating system that is relatively new to you. How many other valuable and useful things in your life did not require learning. This current thread, to me, seems to illustrate how impatience is not your friend. As I have mentioned previously, I do understand the concept of, I want it all, I want it right now, and I don't want to learn or pay anything for it, it's just that I consider those unreal expectations. A boating analogy I might use in the current case: You ask for help getting into a safe anchorage, five hours later, after dark, you come back and state, I really need help, I see from the chart I found that I'm in the middle of shipping lanes in a narrow channel, I'm new at this, I don't know what shipping lanes mean, but there are a bunch of boats and ships around and they are all sounding their horns at me, why, I promise I'll read about navigation when I have anchored, but I've found something referring to red and green lights but I don't know what that means, should I turn mine on, I just have the masthead white light on now because I want to anchor. Can you just tell me in one or two simple sentences what I need to do?

The current situation, you posted a complex question, actually a bunch of questions, then 5 hours later you come back with your system all mucked up. So, anyone wanting to help you, has to first straighten out the mess. How long do you figure the most knowledgable and most able to help you users are going to continue replying to your posts. People will continue to reply but they might just answer the questions you ask, rather than what you need to know because most of them won't know either. I hope you can take my point without being offended.

A couple of points:
Running a wireless adhoc network with no security, is asking for a whole lot of trouble, and you don't have the knowledge or experience to even recognise it, others nearby will be onto you very quickly and they probably won't have good intentions.

You need more than a "bunk up" and you are asking for someone to do it for you, look where you've already managed to get yourself.


At this point, you should probably restore your system from your backup, from before you started changing things. Then, I would try getting ICS (Internet Connection Sharing) working from Network Manager. [I've never used NM for this, but I would expect it to handle giving IP addresses to each discrete client (it has to know where to route returning packets), I also don't know if it can handle more than one client.] If this all works as I expect, you could then try to establish your remote desktop. That's the approach I would take if I was trying to do what you have detailed.

On the other hand, Windows would likely be point and click for this stuff, I think they try for "zeroconfig" but there might be virus and/or malware issues. I do know XP ICS does issue individual IP addresses, I've setup a system like that, for someone who did not have a router but that was years ago before I retired. I don't use Windows now.

I truly do wish you good luck, that is not sarcastic. I realise this post is and sounds patronising. I can't help it, I'm older than you, probably even older than your father, just view me as a crabby old guy and please forgive me. Perhaps I should have put this in a PM, however, more than us might read it and if anyone learns from it, that would be a blessing.

QLee, on computer Leto, over and out.

---

### Post by tkelito on 2010-11-30
I'm just going to ask a few questions of the OP here myself.


Why are you trying do an an Ad hoc network?  Do both of these machines already access the internet through a router or is just 1 able to access as it is plugged directly into a modem?  Setting up remote desktop is quite simple, it just seems that you have taken the mountain path instead of the mole hill on this one.

Why not simplify the entire situation for yourself and setup both on a LAN using a router ($40?) and then install VNC Server and VNC viewer and access via the IP Address by running "ifconfig" on the machine you want to access.  If you want to take it a step further you can set it to a Static IP so that it never changes.  Option 3 would be to just setup a DHCP reservation in the router so that it is assigned an IP by using the reservation function.

---

### Post by pricetech on 2010-11-30
I would suggest, as an alternative to VNC, you use NX from nomachine dot com.  It gives you a nice GUI and has always just plain worked for me.

---

### Post by demonboy on 2010-12-01
@tkelito
Thanks for your response. Yes, you were right, I had taken a wrong turn and started to complicate things unnecessarily, so questions 2 to 9 weren't relevant. I wasn't sure if I could run Remote Desktop on my wireless LAN without being online. I set up a new wireless network on the ship's computer, which is the one that's always on, rather than mine. Dunno if that stability helped but I'm now connected, securely, across three computers. I do have a router/AP but it requires power and I live on a boat that  runs on 12v so power can be an issue (I have to run the router on an  inverter). This is no longer relevant anyway. Thank you for your help.

@QLee
 A lot of energy went into your post that could have been better spent  helping me out. You appear to have a personal issue with me so it's  probably best to PM me rather than having a go in a public forum.  Cheers.

@pricetech
The problem wasn't the interface, it was the setup. I'm happy with Vinagre and my needs are quire simple, but thanks for the suggestion. I'll bear it in mind.

---

### Post by QLee on 2010-12-01
[QUOTE=demonboy]...
@QLee
 A lot of energy went into your post that could have been better spent  helping me out. You appear to have a personal issue with me so it's  probably best to PM me rather than having a go in a public forum.  Cheers.
...[/QUOTE]
I think you are misinterpreting my advice, I meant it just as I wrote it. I have no issue with you, Jamie. It the best advice an old guy like me can offer in your situation. All you needed to take away from it was, impatience is not your friend.

---

