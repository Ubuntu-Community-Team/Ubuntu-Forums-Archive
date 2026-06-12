---
title: "[Help] Ubuntu --&gt; Xbox Shares not Working"
date: 2007-09-16
forum: Networking &amp; Wireless
---

### Post by -emory- on 2007-09-16
***_FIXED!! Check Page 3 for my mistake, follow directions on Page 1 and 2 for best results ;-) _***

Hey guys. I've been running xubuntu on my laptop for almost a year now, and just this wekend I finally was able to get wireless working on my desktop (a much more powerful machine than my laptop) so i've been setting up compiz, awn, all the goodies, and I. Am. Loving it. There is one FINAL thing that is stopping me from switching completely and reformating that other 100gigs on my harddrive allocated to windows. XBMC. Mainly I have an xbox at the other end of my room that I stream all of my music and videos to and I can't for the life of me figure out how to do it on this box. I have been trying *literally* all day. I've read countless forums and actually already posted on xbmc forums. Anyways, heres my problem:
My network is set up like this:
router ---->my computer---(crossover cable)--->xbox
       \--------My dad's computer
        \------>my laptop
On my desktop I can, under network places, SEE my dad's computer ( can't access any files though). On my xbox, regardless if I have it in automaticly find ip adress or manually assign it a static ip, I still can't ping it/ftp it on my desktop, and it won't see the shares I have on my desktop. I am at wits end. I've tried installing firestarter, tried going through the tutorial here: [http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html#more-182](http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html#more-182) 
but I stil lcan't get it to work. (of course, I only THINK that I'm doing everything that tutorial says  correctly) I'm at the point where I'm considering just setting up remote desktop and letting someone else help me that way :-/. Can anyone give me a hand? Any and all help is MUCH appreciated.
thanks in advance,
emory

---

### Post by JinxAu on 2007-09-16
Gday emory,

So, you're wanting to share files from your computer to the Xbox, which is running XBMC?

If this is the case, you just need to setup some Samba shares on your Linux Desktop to share out to the network (assuming you have not already done this). You should be able to do this via System -> Administration -> Sharing.

Getting back down to basics, can the Xbox ping your Ubuntu Desktop and vica versa?

Are you also looking at sharing the Internet out to the Xbox via your Ubuntu Desktop?

Cya round
Jinx

---

### Post by -emory- on 2007-09-17
I think the main problem is that I <i> can't </i> ping the xbox. It's weird. I definitely want to share an internect connection between them, but I can't even get an ipadress on the xbox. I'm not even sure if samba is the problem, I've set that up (I think) through system-->admin--> sharing. For some reason I can't share my connection to the xbox. Oh one last thing, the connection between the router and my computer is wireless, and the xbox is connected to my computer with a crossover cable. Thanks for your help.

---

### Post by JinxAu on 2007-09-17
Gday Emory,

Sounds like you will need to setup a static IP address on your Ubuntu LAN Adapter (connected to your Xbox), and if possible - set a static IP on the Xbox. Then, try pinging the addresses.

Make sure it is outside of your Wireless network's subnet (eg. If it is using 192.168.0.0/255.255.255.0, use 192.168.1.0/255.255.255.0).

Maybe try something like 192.168.8.1/255.255.255.0 for the Ubuntu LAN (System -> Administration -> Network) and 192.168.8.2/255.255.255.0 for your Xbox.

Then let us know if 192.168.8.1 and 192.168.8.2 can ping each other?

Cya round
Jinx

---

### Post by -emory- on 2007-09-17
check and check, but I still can't ping it. I set up my eth0 to have a default ip address of 192.168.0.1, and the xbox's ip adress as 192.168.0.2. Unfortunately I still can't ping/ftp the xbox.

---

### Post by -emory- on 2007-09-17
Oh by the way my wireless ip adress is 192.168.1.5, with a default gateway of 192.168.1.1, so I know it's not interfering with that.... Any ideas?

---

### Post by -emory- on 2007-09-17
WOW. Big update. Sorry for the (tripple) post but I just reconfigured it and I can now ftp/ping the xbox. I CAN'T however share folders to it, nor can I use internet connection sharing (ICS), but I feel like i'm getting closer! Don't give up on me now!:guitar:

---

### Post by JinxAu on 2007-09-17
It may be because of the firewall on your Ubuntu box. I haven't used Firestarter before, but I know it's a frontend to "iptables", so you should be able to clear your firewall rules temporarily to try and get sharing going. Try running the following commands and try to access the shares from your desktop via the Xbox again.

Flush the existing Input and Output rules:
```
sudo iptables -F INPUT
sudo iptables -F OUTPUT
```

Set our policy to allow traffic in and out:
```
sudo iptables -P INPUT ACCEPT
sudo iptables -P OUTPUT ACCEPT
```

If we do a list on our tables, we should see the rules are clean:
```
sudo iptables -L INPUT -vn
sudo iptables -L OUTPUT -vn
```

The above should result in something similar to the following:
> Chain INPUT (policy ACCEPT 19 packets, 5240 bytes)
 pkts bytes target     prot opt in     out     source               destination 

Chain OUTPUT (policy ACCEPT 17 packets, 4434 bytes)
 pkts bytes target     prot opt in     out     source               destination 

Next time you reboot your Ubuntu desktop, the firewall should go back to it's original state (if it's still on).

Cya round
Jinx

---

### Post by -emory- on 2007-09-17
well Dayum! All of a sudden I CAN view shares on the xbox! Thanks! Will that work when I reboot my computer? Seems like the only thing left to do is get ics! You=Great:popcorn:
which, by the way, I have no idea HOW to do?

---

### Post by JinxAu on 2007-09-17
Glad to see that worked. :P

It is more than likely that Firestarter is blocking the Samba ports that the Xbox needs to access to view the shares on the desktop. Above was just the manual way to clear the firewall rules, but they will more than likely reset after reboot. 

After having a brief look at Firestarter, it appears it supports Internet Connection Sharing (which is cool). Try going to System -> Administration -> Firestarter, then Firewall -> Run Wizard.

Set your Internet Connected device as your Wireless Adapter (allow IP Address Assigned by DHCP). Then, enable Internet connection sharing on your LAN Adapter (eth0?). Then, click "Save"... you should see the Firestarter menu again.

Under the "Policy" tab, click on "Add Rule" (make sure it's set to edit the Inbound Traffic Policy). Add your Xbox Network of "192.168.0.0/24", with a comment of "Allow XBox LAN". Apply the Policy and Stop and Start your Firewall.

On your XBox, check to see if you can access the shares... hopefully this works. You will also need to add the Ubuntu Desktop as your gateway and your Internet router's IP as your DNS (also see if you can ping it from your XBox). From here, you should now have Internet access on your Xbox, unless we have missed something along the way. 

Let us know how you go.

Cya round
Jinx

---

### Post by -emory- on 2007-09-17
hmm well I can still access my shares on my xbox, can't access internet though... Under firestarter though, under which tap in policy should I add that rule? "Alloc connections from host" or "Allow Servce-Port-For"?  Also, I enabled internet conenction sharing under the wizard, unfortunately it doesn't seem to work... Is there any way I can just get rid of the firewall? Will that have a detrimental effect on my sharing abilities? I just don't see much use if it can't work to get internet connection sharing working

---

### Post by JinxAu on 2007-09-17
Sorry, under the Policy Tab, enter the 192.168.0.0/24 network (which is 192.168.0.0/255.255.255.0 network) by right clicking on the "Allow Connections from Host" area and selecting "Add Rule".

You need the Firewall to be enabled if you want to share your Internet connection using the Firestarter ICS. The other way you can do it is via a script, if you're happier doing that.

So, the Xbox has the following network settings?

IP: 192.168.0.2
Netmask: 255.255.255.0
Gateway: 192.168.0.1
DNS: <wireless gateway> <--- can also try your ISP's DNS IP Address(es).

Cya round
Jinx

---

### Post by -emory- on 2007-09-18
Hi, I'm at school right now, so I can't check, but I'm pretty sure I already did that and it didn't work though.Question: why would I want to enter 192.168.0.0/24? My xbox's ip is 192.168.0.2 and my computers eth0 ip is 192.168.0.1. It's wlan0 is 192.168.1.5. I guess I'm just a bit confused about how this works....

---

### Post by -emory- on 2007-09-18
Yeah I followed your advice ( I think correctly) but I still can't access internet on the xbox. I can still view my shares, but I can't change any of the network settings on it that I know of that won't mess that up... Any ideas?

---

### Post by JinxAu on 2007-09-19
Probably should have explained the "192.168.0.0/24" a little more. Basically, this is a shorthand method of saying "all addresses in the 192.168.0.0/255.255.255.0 subnet range". So, that would be addresses 192.168.0.1 - 192.168.0.254 (this includes the Xbox, the Ubuntu Desktop and any other devices you might add later). 

If it is possible, can you post your iptables (firewall rules)? To do this, run the following commands:
```
sudo iptables -L FORWARD -vn
sudo iptables -t nat -L POSTROUTING -vn
```

Just copy and paste the results into a post.

We could just make up a basic firewall script that forwards the Internet to your XBox and drop Firestarter if you want?

Try saving this script to a file (name it something like firewall-xbox.sh):
```
#!/bin/sh
#
# Firewall script to share the Internet to the Xbox via our Desktop.
#

# Variables
LAN=eth0
LANNET=192.168.0.0/24
WIFI=wlan0
WIFINET=192.168.1.0/24

# Flush our existing forward rules and apply our default policy.
iptables -F FORWARD
iptables -P FORWARD DROP

# Enable forwarding if it is not already enabled.
echo "1" > /proc/sys/net/ipv4/ip_forward

# Allow Internet and WIFINET requests FROM the LANNET.
iptables -A FORWARD -i $LAN -o $WIFI -s $LANNET -j ACCEPT

# Allow Established and Related Internet traffic TO the LANNET
iptables -A FORWARD -i $WIFI -o $LAN  -d $LANNET -m state --state \
 ESTABLISHED,RELATED -j ACCEPT

# Allow traffic to LANNET, FROM WIFINET
iptables -A FORWARD -i $WIFI -o $LAN -s $WIFINET -d $LANNET -j ACCEPT

# Masquerade all LANNET traffic to our WIFI address.
iptables -t nat -A POSTROUTING -o $WIFI -s $LANNET -j MASQUERADE
```

Don't forget to make the script executable before trying to run it:
```
sudo chmod -x firewall-xbox.sh
```

You can execute this script by running:
```
sudo sh firewall-xbox.sh
```

The above might seem  a little daunting, as there is a lot to take in, but once you get your head around it, iptables is a very effective tool. As I mentioned before, Firestarter is a frontend to iptables - though it does make it a whole lot more friendlier.

If you still find your Xbox is not getting Internet traffic, I would check it's network settings as mentioned in my last post... it needs a valid Gateway (being 192.168.0.1) and DNS to work.

Cya round
Jinx

---

### Post by -emory- on 2007-09-19
Hey, thanks for the help, I'm still working on it, and I'm just doing the first step now, so here are the results of the two commands you told me to run:
emory@HAL:~$ sudo iptables -L FORWARD -vn
Password:
Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5 
    0     0 TCPMSS     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x06/0x02 TCPMSS clamp to PMTU 
    0     0 ACCEPT     tcp  --  wlan0  *       0.0.0.0/0            192.168.1.5         tcp dpt:1337 
    0     0 ACCEPT     udp  --  wlan0  *       0.0.0.0/0            192.168.1.5         udp dpt:1337 
    0     0 OUTBOUND   0    --  eth0   *       0.0.0.0/0            0.0.0.0/0           
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            192.168.0.0/24      state RELATED,ESTABLISHED 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            192.168.0.0/24      state RELATED,ESTABLISHED 
    0     0 LOG_FILTER  0    --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        0    --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Forward' 
emory@HAL:~$ sudo iptables -t nat -L POSTROUTING -vn
Chain POSTROUTING (policy ACCEPT 1 packets, 242 bytes)
 pkts bytes target     prot opt in     out     source               destination         
  135  6545 MASQUERADE  0    --  *      wlan0   0.0.0.0/0            0.0.0.0/0           

Does that help?

---

### Post by JinxAu on 2007-09-20
Gday Emory,

Firestarter's firewall rules look a bit different to rulesets I am used to. However, it does look like the rules for Internet Connection sharing are there:

> pkts bytes target prot opt in out source destination 
0 0 OUTBOUND 0 -- eth0 * 0.0.0.0/0 0.0.0.0/0 
0 0 ACCEPT tcp -- * * 0.0.0.0/0 192.168.0.0/24 state RELATED,ESTABLISHED
0 0 ACCEPT udp -- * * 0.0.0.0/0 192.168.0.0/24 state RELATED,ESTABLISHED 

pkts bytes target prot opt in out source destination 
135 6545 MASQUERADE 0 -- * wlan0 0.0.0.0/0 0.0.0.0/0 

This is assuming that OUTBOUND is a chain defined by Firestarter.

One thing I did pick up on is that you don't seem to have a packet count on any of the FORWARD rulesets. This suggests that the Xbox is not trying to use your Desktop as a Gateway (maybe check the Xbox and make sure the gateway is set to 192.168.0.1).

See if you have any more luck with that script... should tell us if forwarding is working.

Another thing to look at is /var/log/syslog, as Firestarter logs any FORWARD requests that are not matched as "Unknown forward".

Try running the following whilst trying to access the Net from the Xbox (should see requests being logged):
```
sudo tail -f /var/log/syslog
```

Cya round
Jinx

---

### Post by -emory- on 2007-09-20
hmm
under network settings I have it set up thus:
ip adress: 192.168.0.2
gateway: 192.168.0.1
dns: 192.168.1.5 (my wlan0 ipadress)
still nothing. IS that the right thing I should be  putting in for dns?

---

### Post by dysolve on 2007-09-20
I had this setup working on my network about 6 months ago, but when the hard drive died in my ubuntu box i had to steal the drive from my xbox to get it working again, I got a new drive during the week so i will be setting it all up again. I will see how I go and post any setting changes i had to make.

thanks
David.

---

### Post by JinxAu on 2007-09-20
> **-emory- said:**
> hmm
under network settings I have it set up thus:
ip adress: 192.168.0.2
gateway: 192.168.0.1
dns: 192.168.1.5 (my wlan0 ipadress)
still nothing. IS that the right thing I should be  putting in for dns?

The DNS IP address needs to point to a valid DNS server. Maybe see if 139.134.5.51 works. It's an Australian DNS server, but should work from other countries. You can verify this by doing:
```
dig www.ubuntulinux.org @139.134.5.51
```

The above should return something like:
> ; <<>> DiG 9.3.4 <<>> [www.ubuntulinux.org](www.ubuntulinux.org) @139.134.5.51
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 17689
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;[www.ubuntulinux.org](www.ubuntulinux.org).           IN      A

;; ANSWER SECTION:
[www.ubuntulinux.org](www.ubuntulinux.org).    599     IN      A       91.189.94.158

Also, try and ping the DNS IP aswell... see if you get a response back.

Cya round
Jinx

---

### Post by -emory- on 2007-09-20
yeah i can definitely ping it from my desktop, and I got the same output when i tried that command you told me, but i'm getting nothing on the xbox :( Should I have my wlan0 ip adress for the gateway instead of the eth0 (the one that is connected to the xbox)? I'm just sort of grasping for straws I guess.... You say that according to the firewall it *is[* forwarding my internet though? Maybe that's the problem, I just wish i knew how to.. UNproblem it :P Thanks for helping

---

### Post by -emory- on 2007-09-23
So, after a week of school I'm back on the subject... I still for the life of me can't figure it out. It SHOULD work. I have firestarter up and configured I have all the right settings ( I think on teh xbox) I just don't know. One question: Under dns server on the xbox, should I set it as the dns that my wlan0 uses or just my wlan0 ip adress? Thanks for sticking with me on this thread.

---

### Post by JinxAu on 2007-09-23
You need to set it to a valid DNS server (like the 139.134.5.51 address)... your wlan0 IP is not a DNS address (as you're not running a DNS server on your Desktop). Try the Xbox with the same DNS address that is listed in /etc/resolv.conf on your Desktop and/or with the 139.134.5.51. 

Can you ping 139.134.5.51 from your Xbox? This will tell us whether the forwarding is working (which, as you say, *should work*).

Cya round
Jinx

---

### Post by warduke on 2007-10-01
Um, this may seem stupid but it was something I missed.

I run both Wireless and Wired connects.  Sometimes both at the same time. 

Do you have the DNS  Server setup in Ubuntu for your router?  The one your xbox is on.

System/Administration/Networking

Then DNS tab.  Add your DNS


I only bring this up because my dumbarse didn't have the DNS there for both my wireless and wired connections.  Thus I never showed up on xbmc as a share.

I had 192.168.0.1 there but not 192.168.1.1

So if I plugged in the wired connection.  I lost my wireless heh.  

Anyways, my point was to make sure your routers default DNS address was listed in that DNS tab.

That was all I had to do and my shares started to work for me.

---

### Post by -emory- on 2007-10-01
yeah thanks, I've got shares working fine, for some reason i still can't get internet connection sharing working though... otherwise it's working fine :-/

---

### Post by -emory- on 2007-10-07
okay after yet another period of inaction, i've decided to reapproach the issue. I just downloaded dhcp, hoping to set up firestarter using dhcp, still had no luck... Is there any way to test if my computer is sharing my connection, so that I can limit the problem down to either the xbox OR the pc? I think the problem now is just trying to figure out which box is messing it up :P Thanks

---

### Post by -emory- on 2007-10-12
FIXED! Finally something good today! Seems the problem wasn't on my computer, rather on the xbox. Sorting through the settings, I realized that the "Use http proxy" was checked ::embarrassed:: turned it off and rebooted, it connects perfectly! Thanks to everyone for helping! Hope this helps anyone else too :-D:guitar:

---

### Post by mistseeker on 2008-07-08
Excellent info on this thread, guys, you all helped a lot.

N.

---

### Post by .Ix on 2008-07-12
Hey guys. i hope you don't consider this thread necromancy, because my problem is very similar to this one, but i'm pretty sure the instructions on this thread won't work for me because my setup is different.

I can't ping, FTP, or access the xbox. I'm running an XBMC uPnP server on the xbox, and i'm trying to access the share using XBMC on ubuntu hardy. it doesn't work. gFTP and the ping command both tell me the host is unreachable. (i dual boot into windows. i can FTP over there. :(  )

here's my setup:

i have a Router (linksys wrt54g, IP 192.168.1.1, dns 192.168.1.1, gateway 192.168.1.1)

Router is connected to Xbox (192.168.1.17) through a crossover cable.

Router is connected wirelessly to laptop (ubuntu hardy, 192.168.1.13).

I've tried changing my laptop's wireless IP to something like 192.168.0.13, but i lose connectivity altogether. :confused:

---

