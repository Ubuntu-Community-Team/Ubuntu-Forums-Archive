---
title: "HOWTO BandwidthD"
date: 2008-09-12
forum: Networking &amp; Wireless
---

### Post by mashcaster on 2008-09-12
Hello,

I would like to monitor my broadband usage and I found bandwidthd, but I have no idea how to use it after installation.

Please help.

---

### Post by psypher on 2008-10-21
I'm also tryin to get it working, although I'm doing it on centos. So far I had to copy all the files from /usr/loca/bandwidthd/htdocs to a new folder in /var/www/html/bandwidthd. set owner and group to apache but i think it should be www-user in ubuntu, could be wrong. And I manually had to start the /usr/local/bandwidthd process.

i configured the config file as much as I could, still not getting any graphs though. Can anyone else please help. The documentation for this app is terrible.

Thanks

---

### Post by mashcaster on 2008-10-24
I figured it out, but BandwidthD was not the answer.

---

### Post by yakupm on 2010-09-20
Hi,
I know the post is old but thought this info might still be useful.  Here's how I got bandwidthd working on ubuntu 8.04 server.


[LIST=1]
[*]apt-get install bandwidthd
[LIST=1]
[*]follow prompts, main config file is /etc/bandwidthd/bandwidthd.conf
[/LIST]
[*]apt-get install apache2
[*]cd to /var/www and create a soft link to the htdocs directory that bandwidthd uses (see /etc/bandwidthd/bandwidthd.conf)
ln -s /var/lib/bandwidthd/htdocs bandwidthd
where bandwidthd in the name of the link
[*]restart apache /etc/init.d/apache2 restart (and bandwidthd if needed /etc/init.d/bandwidthd restart)
[*]access bandwidthd
http://<localhost or IP>/bandwidthd
[/LIST]
Hope that helps someone :)
yakupm

---

### Post by MartinHansell on 2010-12-09
Yes Yakupm, 

That was very useful, thanks.  I have got most of the way, but when I browse to [http://localhost/bandwidthd](http://localhost/bandwidthd) I get the "Unable to establish a connection" error.  I have checked the permissions of the symlinks and original files, and the folders/files in both /var/lib/bandwidthd/htdocs and /var/www/bandwidthd seem fine.

I can open the link in a browser by right-clicking on it, but not by browsing to it using the URL.

Any idea what might be causing the problem?

Can I ask you one or two more questions?  A few of the people in the condo I live in have asked me to share my internet connection, which is why I am trying to set this up.  Is bandwidthd adequate to monitor all the usage through my wireless router?  When I look at the graphic output, I can see my own usage, but I know there are 3 other machines connecting through my router, and I cannot see graphs for their usage.

This may be because I have not got my settings correct.  These are as follows, based on what my router is telling me.

subnet 10.0.0.0/24
subnet 255.255.255.0/16

I read that bandwidthd cannot handle multiple sensors.... is that the same as users? machines? I'm not really sure.  Maybe I should be using the postgre version of bandwidthd?  Are you able to comment on that?

Many thanks again.
Martin

---

### Post by yakupm on 2010-12-10
Hi Martin,
Your router info is unusual:
subnet 10.0.0.0/24 is a network
subnet 255.255.255.0/16 is ?

For subnet, I would expect to see something like 255.255.255.0 OR /24  (both are the same).

Assuming you're using ubuntu, both apache2 and bandwidthd must be running.  As root check as follows:
ps ax|grep apache2
ps ax|grep bandwidthd
Both should show several processes running.

The link behavior is strange - don't know why right click would work but browsing doesn't.  Try the IP instead of localhost.

To see traffic from all users, it has to flow through the NIC you are monitoring with bandwidthd.  I do that by mirroring the traffic of interest (via a switch) to the monitoring NIC.

Yakupm

---

### Post by MartinHansell on 2010-12-11
> **yakupm said:**
> 
Your router info is unusual: 
subnet 10.0.0.0/24 is a network  [COLOR="Green"]Yes[/COLOR]
subnet 255.255.255.0/16 is ?  [COLOR="Green"]the subnet mask[/COLOR]
[COLOR="Green"]These are the standard settings from the installation except that I changed the subnet mask from 169.etc.etc.0/16 to the one above.[/COLOR]

For subnet, I would expect to see something like 255.255.255.0 OR /24  (both are the same).
[COLOR="Green"]Oh... I have now tested with those settings but cannot restart bandwidthd due to an error in those respective lines.  It only works when I have the above configuration.[/COLOR]

Assuming you're using ubuntu  [COLOR="Green"][CORRECT][/COLOR], both apache2 and bandwidthd must be running.  As root check as follows:
ps ax|grep apache2
ps ax|grep bandwidthd
Both should show several processes running.
[COLOR="Green"]Yes both are running.[/COLOR]

The link behavior is strange - don't know why right click would work but browsing doesn't.  Try the IP instead of localhost.
[COLOR="Green"]Sorry - my mistake.This machine is configured to access apache2 through port 88; I thought I had put that into the URL but maybe I had a typo or something, but it's working now.[/COLOR]

To see traffic from all users, it has to flow through the NIC you are monitoring with bandwidthd.  I do that by mirroring the traffic of interest (via a switch) to the monitoring NIC.
[COLOR="Green"]Yes I thought I was missing something else.  I don't have a switch linked to my wireless router (Netgear WRG614v7) so I guess I need to acquire one and reconfigure my physical setup to make that work.  I guess I need to buy a switch that has a mirror port so I can replicate data to a monitoring pc.  Does that sound right to you? ....although I can actually see output related to other machines connected to my router... as you can see from the attached output.  There's not much data coz I keep restarting bandwidthd.

Port forwarding is different to port mirroring, yes?  (sorry for dumb question).

Is your monitoring NIC also the same one you use for your apache2 server (as mine would be)?[/COLOR]

Yakupm

Many thanks for your help - very useful!
Martin

---

### Post by yakupm on 2010-12-13
[COLOR=Green]Yes I thought I was missing something else. I don't have a switch linked to my wireless router (Netgear WRG614v7) so I guess I need to acquire one and reconfigure my physical setup to make that work. I guess I need to buy a switch that has a mirror port so I can replicate data to a monitoring pc. Does that sound right to you? ....although I can actually see output related to other machines connected to my router... as you can see from the attached output. There's not much data coz I keep restarting bandwidthd.
[COLOR=Black][I]You could also use a hub if you can find one - they are not used much anymore because the media is then shared by all connected devices.  Results in more collisions but any device plugged into it sees ALL the traffic.  A switch with mirroring capability will likely cost more than just a simple switch.  In any case (switch or mirror), you would do something like this:
Internet -- wireless router -- switch/hub -- PCs.

[/I] [/COLOR]Port forwarding is different to port mirroring, yes?  (sorry for dumb question).
*[COLOR=Black]Yes - forwarding is taking an incoming service like ssh (port 22) and directing it to a specific PC on your network.  Mirroring is taking all the traffic on one port of a switch (in your case it would be the port that connects the switch/hub to your router) and mirroring or duplicating it all on another port (the port you would monitor with bandwidthd).  Note that with a hub you would not have to (or be able to) mirror - any one port would see all the traffic.[/COLOR]*

Is your monitoring NIC also the same one you use for your apache2 server (as mine would be)?
[I][COLOR=Black]Its better to use a separate NIC - also that NIC should be able to handle the total traffic from all PCs.  I do it at work so don't have to pay for the NIC.  It would work with one NIC but not sure of the impact on mirroring to that NIC and trying to use it for normal surfing simultaneously.

Yakup
[/COLOR][/I][/COLOR]

---

### Post by jetole on 2013-04-16
> **MartinHansell said:**
> 
subnet 10.0.0.0/24
subnet 255.255.255.0/16

I know this is old but since I found this page while looking for info for bandwidthd, I thought I would clear this up.

You have specified two network you want to use. First you said you want to monitor all traffic on 10.0.0.* (10.0.0.1 - 10.0.0.254). The second network you specified doesn't exist but I think that's because you tried to combine CIDR notation and subnet masks. The bottom one isn't a subnet mask at all nor is it a network but instead it's referring to the specific host 255.255.255.0 in a network from 255.255.0.1-255.255.255.254.

Anytime where you see an address in the format of x.x.x.x/x you do not need to put a subnet mask at all. the part after /x is the short hand, CIDR notation form of a subnet mask.
[LIST]
[*]x.x.x.x/24 is the same as saying the network x.x.x.x with the subnet mask 255.255.255.0
[*]x.x.x.x/16 is the same as saying the network x.x.x.x with the subnet mask 255.255.0.0
[*]x.x.x.x/8 is the same as saying the network x.x.x.x with the subnet mask 255.0.0.0
[/LIST]

CIDR notation takes any number from /1 (half of the entire IPv4 addresses available, 2,147,483,646 of them, to /32 or a single host. The network 10.5.22.0/23 is the same as 10.5.22.0 255.255.254.0 or 10.5.22.1-10.5.23.254.

So now that we have basic CIDR and subnet masks covered, 255.255.255.0/16 cannot be a network because the network address would be 255.255.0.0/16 and anything inclusively between 255.255.0.1 and 255.255.255.254 would be a host address where the broadcast address would be 255.255.255.255.

But it looks like you were trying to add the subnet mask as well. If you want to monitor all traffic from 10.0.0.1-10.0.0.254 then you can specify it either like you did on the first line as
> subnet 10.0.0.0/24
or bandwidthd will also take the subnet mask form in the format of
> subnet 10.0.0.0 255.255.255.0

If 10.0.0.1-10.0.0.254 is the only network you want to monitor then just remove the second line.

**I want to stress that you never use a subnet mask when the address is in x.x.x.x/x notation because /x is the subnet mask. /x or subnet masks are two different ways of stating the exact same thing so if a program gives you the choice of /CIDR or subnet then pick one or the other. If the program doesn't give you the choice and you only know one of the formats then install the app ipcalc. It's a very powerful and established console subnet calculator that's always handy to have around.**

---

### Post by codemaniac on 2013-04-16
old thread close.

---

