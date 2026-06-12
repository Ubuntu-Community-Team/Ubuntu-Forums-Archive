---
title: "I used IPBlock with .dat files (updated weekly) as my firewall before now doesnt work"
date: 2021-09-08
forum: Networking &amp; Wireless
---

### Post by slaytanicprion on 2021-09-08
I tried to use the most recent dat file (no longer subscribed to the service, but I would be if I could get it to work in a linux environment again) and maybe have ufw work with it, but apparently it doesn't take dat files with iplists in the format torrent clients like qbittorrent do. I can use the dat file with qbittorrent...but I want it to be used globally over this one desktop. It installs fine, the last pdf made for it is old but it worked fine until after LM 17.3 was over with. What happens in Ubuntu Mate is that after installation, it doesn't start with the icon in the menu, I have to start it manually, it refuses to turn on when clicking Enable once the gui is there. Anybody familiar with this old but easy to use ip address blocker, especially since it comes from people doing since 21 years...the list used to be free until there was some issue within the people behind it, but its a pretty cheap yearly subscription, and I did see strange things get blocked, more so when I was using windows 7 and PeerBlock with the dat files.

Is there a way to convert such dat files (they are readable in pluma/whatever text editor one uses), there's the ip ranges with the owners commented out next to them, there's thousands of em so it would be a very long job to add one by one to ufw, so maybe it could be used by iptables? I feel a bit naked without this lol.

---

### Post by mikewhatever on 2021-09-08
It seems pointless to use a bittorrent block list for a filewall. All Ubuntu flavors come with closed ports, so there is no way to connect to your PC.
Not sure what is ipblock, and if it allows IP filter lists, but you might want to explore the hostfile option.
[https://github.com/StevenBlack/hosts](https://github.com/StevenBlack/hosts)

---

### Post by slaytanicprion on 2021-09-08
It's not just for bittorrent that those dat files are made, they can be used in IPBlock to block any sort of connections. It's mostly to catch what would be unsafe OUTBOUND connections, which I have seen happen before (it's probably been a decade), I repeat, that kind of file is good to go with a program for windows called PeerBlock too, IPBlock was its longest lasting debian equivalent (there were older ones like MOBlock but I never managed to install it, it was more friendly to non-debian OS's if I recall well, not just some torrent clients. I do all my torrenting elsewhere anyways and only bring home stuff through sftp. The program caught incoming connections that I didn't want to (I have entire country block lists also) have that somehow made it through, often because I was on one of the only p2p software left I find useful (it's for music only, I won't elaborate further), but I've seen strange stuff before and I don't want that to happen anymore, while I'm using or the desktop is idle.

IPBlock was popular around 2008-2014 I'd say, but I managed to have it work fine on LM 17.3, so well up to mid 2018.

I'll check the link out tho, thank you.

---

