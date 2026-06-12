---
title: "LAN/WLAN vs. Internet lags"
date: 2020-10-12
forum: Networking &amp; Wireless
---

### Post by lnewlfe on 2020-10-12
Running 2 computers from my home, a dedicated Lubuntu 20.04 server and a windows PC. Server's only purpose to run a a MUD server (text based game), as well as compile code and draw from bitbucket as myself and various admin's make changes to the code. I am using no-ip to host my static IP. Before updating from Lubuntu 17 to 19, I had no lag when SSH'ing into the server from either my work or from my windows PC, using the no-ip website as my connection instead of the 192.168.0.*. The server, which uses telnet protocols, also had no issues nor did the server generated website. after updating to 19, I had issues with SSH files, X11 forwarding, as well as other issues but lag was still not an issue. With the release of 20.04 LTS, I did a proper fresh Lubuntu install, and setup SSH, mySQL, the compilers etc and the server is up and running with no hassle, other then...

Anyone other then my own home network can connect to the server via the no-ip redirect with no issues. I can do it from work, connecting either to the website, the game server or SSH, no issues. But when I try it from my own home I get horrid lag on all services running. SSH is slow, the website is horrendous,  and the telnet game lags. As a test, I tried this from my cellphone at home while connected to the Wi-Fi, results like I said. As soon as I disconnected Wi-Fi and ran off the cellphone data speeds were good across all platforms running. The Lubuntu server itself suffers no issues with connection to the internet and it is plugged directly into the router and not over Wi-Fi.

Any ideas as to what changed from version 17 to 20 that could have caused this? I can only assume I am overlooking some local network setting I do not know about.

Thank you and Happy Canadian Thanksgiving!

Joe T.

---

### Post by TheFu on 2020-10-12
Check the dns settings.
See that the results returned are the same now as they were pre-OS change.  Wrong DNS results can cause problems for ssh connections. Are other protocols impacted? Non-ssh based protocols, that is.

---

### Post by lnewlfe on 2020-10-13
Yes telnet is also slow, as is http to the server website. DNS seems to be the same, and nothing changed regarding the router settings for each computer.

---

### Post by TheFu on 2020-10-13
Are both name.fqdn and name queries supported?
Do you have a domain-search setting in the DNS settings?
Have you tried just putting the correct names+IPs in the /etc/hosts files for each system?

Some routers don't allow 
   in--> out --> in 
connections. You probably would have seen that previously. Just something to be aware about.  So what may be happening is the external connection is timing out and an internal-only connect is being used, somehow.

---

### Post by lnewlfe on 2020-10-13
At this point I'm in new territory... looking up terms and commands now, but any help with what I should be looking at vs. What I might have set up would be appreciated and shave hours off this, lol.

Thanks for all the help,

Joe.

---

### Post by TheFu on 2020-10-13
**dig** is for DNS queries. The manpage has all the options. Try name.fqdn and just name in the dig queries. Many want to point at external DNS servers and your internal DNS server. There's an option for that.  I don't recall. I'd need to check the manpage too.

As for DNS domain search settings, that's part of the DNS setup in the network connection stuff.  In a server config file, there would be a line in the netplan yaml file. I have no idea how to set that in any GUI. I don't use GUIs for network stuff.

The /etc/hosts file is a way to shortcut all this DNS stuff 99.9% of the time.  The /etc/hosts file is looked at first - or it should be looked at first.  Some browsers choose to override OS standards and do something for grandma to be happy, but those techniques screw with people running internal servers.  Firefox started doing this a few months ago with their default DoH DNS stuff. Google firefox settings for that, if you care.  I do DoH manually on 2 systems and have firefox's built-in version disabled.  I don't remember how - I'd have to google that answer too.  I really need to get that setup on my pi-hole, so it works for every device on the network here.  
The firefox DoH stuff wouldn't impact ssh or telnet, so that probably isn't the root issue.

When you ssh in, have you looked at the sshd logs?  Anything funny?
What about **ssh -vvv ... ** anything funny there?  But if telnet and http are impacted too, I'm back to DNS being the issue.

---

### Post by The Cog on 2020-10-13
Is the connection laggy once it has been made? I'm thinking particularly about telnet or ssh here because it's basically a packet for every keystroke. If the lag is is during normal typing then you can rule out DNS because DNS is only used as the connection is being established. On the other hand, if it's just the initial connection establishment that's slow then DNS would be quite a strong suspect.

If it's laggy all the way through the connection then I would try to figure out if they are talking directly to each other, or whether they are conversing via the router.  
Am I right in thinking the Windows PC and the server are on the same home network, with addresses 192.168.0.*?
Am I right in thinking that there is no lag if you connect to the server using its 192.168.0.* address, but there is a problem connecting to the server's public IP address?

That's a total of 3 questions that I think will help clarify what the problem is.

---

### Post by lnewlfe on 2020-10-14
You are correct it is laggy throughout typing in both telnet and SSH. Yes they are all on the same home network, and yes it is far quicker if I connect via 192.168 then public. If I am at work or someone else connects there is no issue with the public connection.

Thanks!

---

### Post by The Cog on 2020-10-14
I would suggest that you content yourself with using the local address when you are on the same network as the server. Edit your hosts file and add an entry for the name with the local address if the web service keeps redirecting you to its name which will normally resolve to the public address.

This is something related to the fact that you are abusing the router's NAT process. It is designed to translate your internal address to its public address (and back) as your traffic passes between home and the internet. Routers are not designed to do NAT on connections that pass in and out of the same interface. With some routers it works, but with most it doesn't work at all. I'm surprised that you are getting halfway between those - working but laggy. It suggests that there is a lot of packet loss. I don't think you will be able to do much about it. 

If you really, really want to understand the problem, then I think you need to use wireshark, preferably on both PC and server at the same time, so you can account for every packet. Examine the MAC addresses to be sure which device sent them, and work out which packets are being lost, and whether any packets are not being NATted when you wnat them to, or whether some are simply disappearing (towards the internet perhaps). A potentially very interesting but time consuming investigation. And even when you know exactly what is happening, you probably won't be able to do anything about it.

Not very helpful, I know. Sorry about that.

---

### Post by TheFu on 2020-10-14
For ssh, you can use a ~/.ssh/config file to make connections and any special options automatic for all ssh-based systems.

I have 2 stanzas for my internet-facing systems with ssh.  One for LAN use and the other for internet use when I'm away.  Plus, the one for internet use will use IP addresses, not DNS, when I'm in countries known to be not-so-nice for internet freedom.  I've found that some block domains, but don't block IPs for some reason.

Sorry, not an answer from me either.  At least we know it isn't DNS if stuff is slower after connection. 

Just because something is possible, doesn't mean it is a good idea.  If you need to test outside connectivity, perhaps using a cellular data connection or cheap VPN would work?  I use the VPN method a few times a year - or use it as an excuse to phone-a-friend. ;)

---

