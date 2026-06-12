---
title: "/etc/resolv.conf gets wiped every time I switch to wireless"
date: 2008-01-09
forum: Networking &amp; Wireless
---

### Post by tjwolf on 2008-01-09
Hi,
I just installed Ubuntu 7.10 and most stuff is working fine.  But moving from wired to wireless networking is giving me trouble: I noticed that when I go from a wired connection (at work) to wireless (at home), the /etc/resolv.conf file is replaced (maybe others too?).  So, every morning, when I get to the office, I have to go back into it and add the work DNS servers again.

What am I doing wrong?  Other than my wired connection being a static IP address and the wireless home network being dynamic, it's a straight-forward setup, I imagine.  I just upgraded from Fedora Core 5 - and I never had this issue - everything was automatic.  I'm running 7.10 on a Latitude D810 laptop.

Maybe I just don't know how to use the NetworkManager GUI tool?  The help for it doesn't give a clue as to how you're supposed to configure things between the two interfaces.

Many thanks for any help for this LInux newbie.
tom

---

### Post by HermanAB on 2008-01-09
It is the DHCP client that does that.

I suggest that you configure the DHCP server properly and always use DHCP on both the wired and wireless connection.  Otherwise, never use DHCP.  It is the sometimes you do and sometimes you don't that is causing the problem.

Cheers,

Herman

---

### Post by jhetrick62 on 2008-01-09
I use wifi-radar to manage my wireless connections and it works like a champ.  I find Network Manager not working well with my wireless connection.  You might give that a shot to see if it will control this properly for you.  I too came from FC although I still run a FC5 file-server on my home network, but 7.10 on my laptop and family computers.

Jeff

---

### Post by tjwolf on 2008-01-09
Thanks guys - I may give wi-fi radar a try.  Unfortunately, I can't take the advice of always running DHCP - at work, my machine is sometimes used as a server, so I need to have a static IP there.

After posting, I saw someone else's similar question.  The response was that one could maintain the DNS servers in the /etc/nsresolv.conf by simply editing /etc/dhcp3/dhclient.conf and listing  the wired DNS servers on the prepend line.  If that is the only thing that gets screwed up when moving between wired and wireless, than that'll probably be my best bet.

tom

---

### Post by tjwolf on 2008-01-10
Well, adding the DNS servers to that file seemed to work - but I still can't do DNS :(

My current solution is just to put the handful of machines I need access to inside the company to the end of my /etc/hosts file and at home rely on DNS.

I'm wondering before I try wifi-radar: how would it help me with this?  From the name, it seems to just handle wireless related matters.  I'm having the DNS problem at work - where I'm using the wired connection.

thnx,
tom

---

