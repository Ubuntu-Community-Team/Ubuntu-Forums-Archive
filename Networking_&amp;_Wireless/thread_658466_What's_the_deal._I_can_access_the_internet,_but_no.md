---
title: "What's the deal. I can access the internet, but not my router webpage, won't ping"
date: 2008-01-04
forum: Networking &amp; Wireless
---

### Post by Mysticle31 on 2008-01-04
Alright, this does not make any sence.

I have DCHP enabled on my router.  My desktop gets an address of 192.168.1.103.  I can access the internet, and write this little post.  However, I can't access my router webpage.  I can't even ping it.  Notice, that I am getting a DHCP address from the same router I can not ping, and accessing the internet.

I also have a Tablet running Ubuntu.  I simply unplug my desktop from the router, plug in the tablet to the same port, wait for the address (usually 192.168.1.103) and I can access the routers webpage just fine.

Everything is the same in connection information on my tablet and desktop except for one thing.

My desktop uses Tulip, my tablet uses e100

Why? What's going on?


On a side note.  I have been having networking issues.  If I download a torrent, the internet grinds to a haut, but only on some webpages such as IMDB, California Water (I like to check the levels of the lakes with the rain)..etc.

---

### Post by Lostincyberspace on 2008-01-04
It might be set to refuse connections from wireless signals I have mine set up that way for security reasons.

---

### Post by Mysticle31 on 2008-01-04
I'm using the ports.  Hard wired.  Not wireless.

The desktop and tablet are on the same port when I try to access.  Plug in desktop, gets address, does not access router but accesses the Internet.  Unplug desktop, plug in tablet, gets address, can access the router.

Thanks for the response though.

---

### Post by Lostincyberspace on 2008-01-04
Check to make sure the mac address isn't blocked from accessing the page still.

And could you post a screen shot of the error when you access it in a web browser.

---

### Post by Digger78 on 2008-01-04
removing avahi-autoipd will fix the problem, it assigns address in the range 169.254.x.x to the like of your router and other network devices

```
sudo apt-get remove avahi-autoiopd
```

then reboot and test

---

### Post by Mysticle31 on 2008-01-04
No error, just forever connecting.  I think I've waited 13x seconds in Firefox.  I can't even ping the router.

I just checked for blocked macs.  None.  I disabled all port forwards too.

---

### Post by Lostincyberspace on 2008-01-04
Check to make sure that it isn't getting blocked by IP tables or some other program.

Also can you ping google and if you able run ```
sudo tracert www.google.com
```

---

### Post by shad0w_walker on 2008-01-04
What is the IP address our are using to access the router? The bulk of routers ship using 192.168.0.X  I'm not sure if this router happens to be the exception to the rule but have you tried manually assigning an address using 192.168.0.X for your PC and then accessing the router when using that network setup.

---

### Post by Digger78 on 2008-01-04
Just in case you missed my post above.....

removing avahi-autoipd will fix the problem, it assigns address in the range 169.254.x.x to the like of your router and other network devices

```
sudo apt-get remove avahi-autoiopd
```

then reboot and test

---

### Post by Mysticle31 on 2008-01-04
I just tried removing avahi-autoipd.  All it seemed to do was make it so I had to use a static address to get access to the internet.  Even with a static address, I can not access my router.

I ran the tracert.

Hop 1 Hostname: 192.168.1.5 IP: 192.168.1.5 (my computers static address I gave it to get on the internet)

Hop 2 Hostname: no IP: reply

Hop 3 Hostname: no IP: reply

Hop 4 Comcast's router in oakland

Hop 5 Comcast's router in sacramento

I find it interesting it goes to oakland than sacramento being that I live in sacramento.  Anyhow, beside the point.

Then a couple more hops to google.

---

### Post by Digger78 on 2008-01-04
OK, Did you reboot?

Try removing avahi-daemon too and purge any config files then reboot

I had the same problem a few months ago, removing avahi and purging config files solved it.

removing avahi should not effect your internet connection.

---

### Post by Digger78 on 2008-01-04
What is your output from

```
route
```

---

### Post by Mysticle31 on 2008-01-04
My output of route is 
192.168.1.0    *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.1.1    0.0.0.0         UG    0      0        0 eth0

I'll try to purge avahi-daemon and avahi-autoipd.

---

### Post by Mysticle31 on 2008-01-04
Update: I will try to purge avahi-autoipd.  if I remove avahi-daemon apt-get wants to also remove banshee and ubuntu-desktop.

---

### Post by Digger78 on 2008-01-04
OK,i dont use banshee or ever had it installed, but i did allow it to remove Kubuntu-desktop  and i have never re-installed it.

I would allow apt-get to remove them, you can always reinstall later.

---

### Post by Mysticle31 on 2008-01-04
purge did not make it work.

Basically:  I can not access or ping my router.  I can not ping my tablet.  I can ping the loopback and my own IP.  I can ping internet addresses.

It's like I don't exist.

---

### Post by Digger78 on 2008-01-04
Did you reboot?

---

### Post by Mysticle31 on 2008-01-04
Yes, I rebooted.

I just looked at my IP Tables.

steve@Desktop:~$ sudo iptables -L
[sudo] password for steve:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     0    --  anywhere             anywhere            
moblock_in  0    --  anywhere             anywhere            state NEW 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
moblock_fw  0    --  anywhere             anywhere            state NEW 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     0    --  anywhere             anywhere            
moblock_out  0    --  anywhere             anywhere            state NEW 

Chain moblock_fw (1 references)
target     prot opt source               destination         
NFQUEUE    0    --  anywhere             anywhere            NFQUEUE num 0

Chain moblock_in (1 references)
target     prot opt source               destination         
NFQUEUE    0    --  anywhere             anywhere            NFQUEUE num 0

Chain moblock_out (1 references)
target     prot opt source               destination         
NFQUEUE    0    --  anywhere             anywhere            NFQUEUE num 0


that's about as anywhere to anywhere as it gets!  Do you see anything wrong?

---

### Post by Digger78 on 2008-01-04
ah moblock on gutsy i presume?

After a recent update of moblock on my gutsy laptop i did notice that i couldnt connect to my desktop

I just removed it since i didnt really need it.

You will need to whitelist your lan

edit /etc/moblock/moblock.conf

```
################################ Whitelist IPs ################################

# Whitelist either a network name, a hostname (please note that specifying any
# name to be resolved with a remote query such as DNS is a really bad idea), a
# network IP address (with /mask), or a plain IP address.
# The mask can be either a network mask or a plain number, specifying the number
# of 1's at the left side of the network mask. Thus, a mask of 24 is equivalent
# to 255.255.255.0.
# Seperate several entries with whitespace (" ")

# This section works only for IPTABLES_SETTINGS="1"
# Do a "moblock-control restart" when you have changed these settings.

IP_TCP_IN=""
IP_UDP_IN=""
IP_TCP_OUT="**192.168.1.0/24**"
IP_UDP_OUT=""
IP_TCP_FORWARD=""
IP_UDP_FORWARD=""
```

I think something like that should do it, you may need to add it to the IP_UDP_OUT line too

after you save the changes, restart moblock

```
sudo moblock-control restart
```

then re-test

---

### Post by Digger78 on 2008-01-04
I just installed moblock on my gutsy laptop

My iptables are the same as yours and i CAN access my router.

What version of moblock are you running?

---

### Post by Mysticle31 on 2008-01-05
you know, I forgot what mobock was and that I even had it!  I looked it up now.  It's version 0.8.

I whitelisted my network and it worked quite well.

The only other problem I'm having is that I run mythweb (port 80) and I can't access it from the internet now.  How do I whitelist that?  I tried doing port 80, no luck.  I'm still very new to this :)

Thanks guys.

---

### Post by jre on 2008-01-05
> **Mysticle31 said:**
> you know, I forgot what mobock was and that I even had it!  I looked it up now.  It's version 0.8.
Always tell the complete version number (0.8-39+gutsy), sometimes that's important info (not in this case, but anyway). Further I have to warn you to do again these configuration changes after the next moblock update or you will have the same problems again. From moblock 0.9 on you will have the possibility to do such user specific changes in /etc/default/moblock and so will have an easier update experience.

> **Mysticle31 said:**
> The only other problem I'm having is that I run mythweb (port 80) and I can't access it from the internet now.  How do I whitelist that?  I tried doing port 80, no luck.  I'm still very new to this :)
Nearly the same procedure as whitelisting outgoing traffic, but here you provide the server, so it's ingoing traffic (I don't know mythweb, but I guess it's only TCP):
```
IP_TCP_IN="80"
```

@digger78: you're probably not having any problems because your routers' IP is not in the blocklist.

---

### Post by Digger78 on 2008-01-05
Hi jre

I'm using version 0.8-39+gutsy, was there an issue in a previous version that blocked local connections? (i assume so, since whitelisting the LAN worked for mystical)

 Unfortunately I didn't even try to investigate the problem, I just un-installed with the intention of retrying at a later date. 

Keep up the good work! ;-)

---

### Post by jre on 2008-01-05
digger78, now I'm a bit confused if you are having problems or not.

Anyway, because of another bug I changed the blocklists in 0.8-33. Since then many users have problems because their LAN/router is blocked.
Further, updating to this version was a pain. I finally fixed that in 0.8-39 (the current version).

The problem that the router/LAN is blocked is not a bug - it's the feature of MoBlock to block all IPs in the blocklist. Everybody is having different IPs, some are behind routers, some not - so I can't provide you with a configuration that fits for everybody and therefore can't release a fixed version.
So for people having this problem (and I know that this is a severe problem) there's only the solution to whitelist the IPs or ports just to their needs.

---

### Post by Digger78 on 2008-01-05
Sorry for the confusion, I don't have any problems with the current version. :)

I dont remember what version i had at the time, but when i upgraded to it, thats when i was unable to access local addesses but the moblock log _did not_ show the IP's being blocked -thats why i assumed it was a bug - sorry

If my routers IP was in the blocklists when i was having the problem, should it not still be in the lists? (im using the same lists and have not whitelisted my lan)

sorry to be a pain in the erse.

---

### Post by Mysticle31 on 2008-01-05
For me, at some point in time, I installed firestarter to help find and solve the problem.  I had forgotten I had moblock then.

I purged moblock and firestarter.  Then everything worked.  I could access my router and ping every IP on the network.  When I installed moblock again.  I could not ping my router or any IP on the network except myself.  I did not try accessing mythweb at this time.

Then when I whitelisted the lan I could access the router and ping addresses on the network AND I could access mythweb and use different ports whithout having to whitelist them.

As to why I could not access mythweb (and other ports) with moblock installed + whitelisted lan and firestarter.  I don't know.  However, purging firestarter solved it.  I haven't tried reinstalling firestarter to see if the issue was  firestarter vs moblock, or just a configuration issue.

My moblock version is moblock-nfq 0.8-39+gutsy.

I didn't realise that there was more to the version.  I got the just 0.8 from running moblock and seeing what it said, I got 0.8-39+gutsy from looking at the package manager.

So I, for the moment until the next update, seem to be golden :guitar:  thanks guys.

It may be important to note, that when accessing mythweb I did it by the internet, not localhost which worked all the time.

---

### Post by Mysticle31 on 2008-01-07
It seems I spoke too soon.  Bridging for virtualbox does not work.  Windows (being run in virtualbox) won't pick up an address. 

How do I fix this?

I've already whitelisted 192.168.1.0/24 on both in and out.

---

### Post by jre on 2008-01-08
> **Mysticle31 said:**
> It seems I spoke too soon.  Bridging for virtualbox does not work.  Windows (being run in virtualbox) won't pick up an address. 

How do I fix this?

I've already whitelisted 192.168.1.0/24 on both in and out.

Which IP does your machine have in virtualbox? Maybe there's another range that you have to whitelist, too.

When you couldn't access mythweb from the internet most probably that internet IP was blocked- in this case whitelisting the LAN can't help.

Don't use firestarter and Moblock (0.8 ) together! (I know you don't do this anymore currently) When traffic was checked by MoBlock 0.8 it was either ACCEPTed or DROPped, therefore all the following firestarter ipotables rules weren't used anymore. Of course, this doesn't explain your described MoBlock/Firestarter problems ...
MoBlock 0.9 with the possibility to MARK packets should be possible to be used together with firsestarter.

> **Digger78 said:**
> I dont remember what version i had at the time, but when i upgraded to it, thats when i was unable to access local addesses but the moblock log _did not_ show the IP's being blocked -thats why i assumed it was a bug - sorry

If my routers IP was in the blocklists when i was having the problem, should it not still be in the lists? (im using the same lists and have not whitelisted my lan)
Every IP blocked by Moblock should indeed be in /var/log/moblock.log. Otherwise it would be a new bug :-/
I can only imagine that the moblock's iptables rules were inserted but MoBlock itself din't start. Then all NEW (not only local) traffic would be stuck forever in NFQUEUE where its fate should be decided by MoBlock. But since MoBlock isn't running ....
Are you sure that there weren't any other iptables rules that blocked your local traffic?

---

### Post by Mysticle31 on 2008-01-09
The virtualbox IP is definitely on the same subnet.  I gets 192.168.1.6 static DHCP.  I purged moblock, and it worked.

I've done all kinds of neat things to this Ubuntu installation trying to make things work.  I'm about ready to reformat.  I'll try it all again and see how it goes.

---

### Post by jre on 2008-01-09
> **Mysticle31 said:**
> The virtualbox IP is definitely on the same subnet.  I gets 192.168.1.6 static DHCP.  I purged moblock, and it worked.
I think  you also need to whitelist the FORWARD for your virtualbox because your Linux box is the router for the virtualbox. Is the virtualbox traffic blocked by moblock (see moblock.log)?

---

### Post by Mysticle31 on 2008-01-14
OK sorry for the delay.  I had other issues pop up.  I reformated my computer to get rid of any potential old stuff I had still laying around from playing with other things that could be mucking things up.

Here is a recap..
Whitelisting my LAN works great.  I can access my router, I can access the web, I can access mythweb and other things from the internet.

Forwarding the LAN worked great.  My Virtualbox XP installation using a bridged network connection got an address perfectly.

 My "Whitelist IP" section of /etc/moblock loos like this

> WHITE_IP_IN="192.168.1.0/24"
WHITE_IP_OUT="192.168.1.0/24"
# This is an example to whitelist the range 192.168.178.1-192.168.178.255:
# WHITE_IP_OUT="192.168.178.0/24"
WHITE_IP_FORWARD="192.168.1.0/24"


No problems with ineffective blocking or anything with this, correct?

This also works as a firewall?  It is safe for me to place the computer in front of my router (hook directly to the modem).  I'll have to enable DMZ and try a shields up test.

---

### Post by jre on 2008-01-14
Glad to hear that whitelisting also the forwarding solved your problems with Virtualbox XP.
> **Mysticle31 said:**
> This also works as a firewall?  It is safe for me to place the computer in front of my router (hook directly to the modem).  I'll have to enable DMZ and try a shields up test.
No, MoBlock does not work as a firewall. These are to seperate things!
MoBlock only blocks all traffic with the IPs in the blocklist (unless you whitelisted something).
Moblock 0.8 is (in most cases) not usable together with other firewalls (only known solution is firehol).
MoBlock 0.9 is usable together with other firewalls (I currently package the release candidate 1, it's not fully released and tested yet).
Instead of using a firewall application you can of course make your own firewall with iptables, but the above said is still true for such custom firewalls.

---

### Post by Mysticle31 on 2008-01-14
ok, that's interesting.  Why is the 192.168.1.0/24 in the block list then?

Also it occurs to me, if I install moblock on one of my laptops and take that to another place.  How can I whitelist that LAN?

I can't access Last.fm, so it's in the blocklist too.



An outside questions is I'm finding things being blocked like BBC and a server at MIT.  And I'm not even doing anything.

---

### Post by Digger78 on 2008-01-14
you need to edit your **/etc/moblock/moblock.conf**


in the whitelist ports section

```
WHITE_TCP_OUT="http https"
```

save it and then do

```
sudo moblock-control restart
```

;-)

---

### Post by jre on 2008-01-17
Ranges in blocklists: Have a look at /usr/share/doc/moblock/README.blocklists.gz to understand which ranges are in the blocklist and why they are there.

Whitelisting the LAN: Insert every LAN range in the ```
WHITE_IP_IN=""
WHITE_IP_OUT=""
```

Last.fm (I guess that's web radio, how does it work?) Either whitelist it's port, like Digger said or whitelist its IP in ```
WHITE_IP_OUT=""
```. (See /var/log/moblock.log to learn which IP was blocked when you tried to access it).

---

### Post by jre on 2008-01-17
> **Mysticle31 said:**
> ok, that's interesting.  Why is the 192.168.1.0/24 in the block list then?
Have a look at /usr/share/doc/moblock/README.blocklists.gz to understand which ranges are in the blocklist and why they are there.

> **Mysticle31 said:**
> Also it occurs to me, if I install moblock on one of my laptops and take that to another place.  How can I whitelist that LAN?
Insert every LAN range in the ```
WHITE_IP_IN=""
WHITE_IP_OUT=""
```

> **Mysticle31 said:**
> I can't access Last.fm, so it's in the blocklist too.
Last.fm (I guess that's web radio, how does it work?) Either whitelist it's port, like Digger said or whitelist its IP in ```
WHITE_IP_OUT=""
```. (See /var/log/moblock.log to learn which IP was blocked when you tried to access it).

> **Mysticle31 said:**
> An outside questions is I'm finding things being blocked like BBC and a server at MIT.  And I'm not even doing anything.
Well, if it are OUTgoing connections (see the logfile again) then something on your machine is doing something ;-) That's quite normal. But you can go into it: check "top" to see the running processes and analyze the traffic with "wireshark"

---

