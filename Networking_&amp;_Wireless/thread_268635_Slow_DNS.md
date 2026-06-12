---
title: "Slow DNS?"
date: 2006-09-30
forum: Networking &amp; Wireless
---

### Post by jrohde on 2006-09-30
Hi,

I have just  bought a new router/switch/firewall, a Belkin Wireless G+ Router.

I have a weird problem with it: it takes many seconds to access a new site, but when it is loaded, further browsing on that site is ok. It seems like its very slow to resolve the address. Can it be a DNS-problem? It's the same problem on both the laptop and on the pc.

Any ideas?

Jakob

---

### Post by darth_vader_ca on 2006-09-30
have you tried to ping the website? also do you know what your dns ips are so they can be statically set, as well are you currently using dhcp on your node, if so try setting an ip and gateway as well as dns statically, you should notice a difference.

cheers.

---

### Post by jrohde on 2006-09-30
Hi darth_vader_ca

I have tried to use static ip-address, but that doesn't change anything.

The problem occurs on all websites and on both wires and wireless connections. 

There is no problem in Windows, which makes me think its due to some specific setting in Ubuntu - not in the router.

Jakob

---

### Post by xolot1 on 2006-09-30
i have a similar situation.

for example, i connect to speakeasy speed test (dl/upload bandwidth test), and it takes on the order of 7-8 seconds for firefox to show any signs of connection, but once connected, i can dl/ul around 740.6 KB/sec and 864.6 KB/sec.

im using a hawking wireless g router w/ubuntu 6.06.

seems like this post is a post of support and not diagnosis, but im willing to test solutions that anyone can come up with.

---

### Post by jrohde on 2006-09-30
Hi again,

I am now using the old router, a D-LINK DI-614+, and everything works perfectly! In other words, the problem were in the router. Maybe it's some setting, but I have checked and re-checked - and reset to factorysetting. Nothing works.

So I guess I will retur the junk on monday.

If anybody has a magic trick that makes the Belkin Wireless G+ Router work, I'm all ears.

Regards,

Jakob

---

### Post by mips on 2006-09-30
Have a look here at DNS & IPv6. Manually spcify your dns servers and disable ipv6

---

### Post by jrohde on 2006-09-30
Hi mips,

Was I supposed to be able to follow a link in your post?

Jakob

---

### Post by eXSiR on 2006-09-30
you should read this howto, maybe it will help.
[http://www.ubuntuforums.org/showthread.php?t=87798&highlight=slow+internet](http://www.ubuntuforums.org/showthread.php?t=87798&highlight=slow+internet)

And one more thing for dapper to disable ipv6, use this commands:
if you have ubuntu:
> sudo gedit /etc/modprobe.d/blacklist

if you have kubuntu:
> sudo kate /etc/modprobe.d/blacklist

than add this line to the blacklist file:
> blacklist ipv6

restart your pc. i hope this will help you but, i am not sure :)

---

### Post by handy on 2006-09-30
> **xolot1 said:**
> i have a similar situation.

for example, i connect to speakeasy speed test (dl/upload bandwidth test), and it takes on the order of 7-8 seconds for firefox to show any signs of connection, but once connected, i can dl/ul around 740.6 KB/sec and 864.6 KB/sec.

im using a hawking wireless g router w/ubuntu 6.06.

seems like this post is a post of support and not diagnosis, but im willing to test solutions that anyone can come up with.

Are you using DHCP or Static IP address?

I know I used Static IP when I should have been using DHCP & it gave the same symptoms as you describe.

Just my 2 cents worth...

All the best...

---

### Post by Derspankster on 2006-09-30
I'm having exactly the same issue. I've tried everything that's been mentioned so far with little or no effect. I'm beginning to believe it's Ubuntu itself. I'm wired to my router but the same thing happens even if I bypass the router.

---

### Post by jrohde on 2006-10-01
Hi

Let me try to clarify things.

I have two routers: the new "Belkin Wireless G+ Router" and the old "D-Link DI-614+".

When I use the Belkin, I have the symptoms on the laptop (wireless) and the stationary pc, but _not_ in Windows.

When I use the old D-Link, none of the pc's or OS'es have any problems.

In other words, it can, IMO, only be due to an error in, or misconfiguration of, the Belkin router, right? Or maybe the Belkin has introduced some fancy new technology, that causes clients not configured for this to have trouble resolving domain names.

Regards,

Jakob

---

### Post by mips on 2006-10-01
> **jrohde said:**
> Hi mips,

Was I supposed to be able to follow a link in your post?

Jakob

Jakob,

No, I was hoping you would use the search.

---

### Post by mips on 2006-10-01
> **jrohde said:**
> 
In other words, it can, IMO, only be due to an error in, or misconfiguration of, the Belkin router, right? Or maybe the Belkin has introduced some fancy new technology, that causes clients not configured for this to have trouble resolving domain names.


No, could be other things as well. Just like different firmware versions on the same router might cause issues different brands could behave differently. I doubt the router is faulty.

What I could recommend is:
Upgrade the firmware of the belkin to the latest release.
Disable IPv6 system wide
Manually configure you DNS settings

---

### Post by ralanyo on 2006-10-19
My problem is kind of strange. My DNS seams to be working alright at home. However, when I bring my laptop into the office. The dns is slow to resolve domain names. 

I can type the IP address in the URL box and it works great, but when i type a domain name it sometimes takes 15-20 seconds before the page loads.

It is not just firefox either. I use evolution for my pop mail and it takes forever to resolve the smtp and pop settings. It also effects apt-get, and other applications that have to resolve addresses. 

Could it be something with my work name servers?

Does any know how to fix this?

---

### Post by bait on 2006-10-20
Are the DNS servers listed as the routers ip address on your client or the ISP's DNS servers?

---

### Post by Tyrel on 2006-10-20
HEY GUYS... ](*,) :mad: :p :D 
THANKS A BUNCH!!!!!
I have been trying to figure out why my internet connection was acting so funky.. i.e. updates whould go at broad ban speeds while firefox whould run at dialup speeds if at all.  Meaning some sites would work while others continuously timed out.  I figured IT OUT it was ip version 6 (ipv6) that was causeing the problem. This is what I did to fix it.

1. system>Administration>Networking>Hosts
   Delete all ipv6 addresses.
2. open terminal
   sudo gedit /etc/modprobe.d/blacklist
3. In Text Editor add the following to the end of the file and save.
   blacklist ipv6
4. Restart the PC.

CURE HAS BEEN FOUND:)

---

### Post by handy on 2006-10-20
That's great... :) 

Mips indicated disabling ipv6 in Posts 6 & 13... ;)

---

### Post by curtwalker55 on 2006-10-20
I tried your solution, and it worked for Firefox, but GAIM, adding programs and update still either don't work or work so slowly I will die of old age before they finish.  Any suggestions.



> **Tyrel said:**
> HEY GUYS... ](*,) :mad: :p :D 
THANKS A BUNCH!!!!!
I have been trying to figure out why my internet connection was acting so funky.. i.e. updates whould go at broad ban speeds while firefox whould run at dialup speeds if at all.  Meaning some sites would work while others continuously timed out.  I figured IT OUT it was ip version 6 (ipv6) that was causeing the problem. This is what I did to fix it.

1. system>Administration>Networking>Hosts
   Delete all ipv6 addresses.
2. open terminal
   sudo gedit /etc/modprobe.d/blacklist
3. In Text Editor add the following to the end of the file and save.
   blacklist ipv6
4. Restart the PC.

CURE HAS BEEN FOUND:)

---

### Post by mips on 2006-10-22
> **curtwalker55 said:**
> I tried your solution, and it worked for Firefox, but GAIM, adding programs and update still either don't work or work so slowly I will die of old age before they finish.  Any suggestions.

How is your DNS configured ?
What router do you have ?

---

### Post by zal91 on 2006-10-28
I have the same problem on with Edgy Eft, I have disabled ipv6 multiple ways with no prevail. DNS resolution in Windows XP on the same box however is fine, I have a DI-524 router. 
When I first installed ubuntu (last night) everything was fine, now it doesn't seem to want to resolve the addresses fast.

Here is what I have tried,

Disabling ipv6

Changing the DNS servers to: My routers IP, my modems IP and finally my ISPs DNS address.

Thanks goes to whoever helps.

Edit: I did nothing and it seems to work, it may had been a problem with my ISP.

---

### Post by stream303 on 2006-10-29
Arg - these windows-centric routers trying to be dns servers :)

I'd have a look at your /etc/resolv.conf file, and I'll bet that your router's dns is listed first in the list - which usually causes the dreaded timeout before it gets to your ISP's listed dns addresses.

There's a fix for this if this is the case - and it *isnt* making that file read-only :)

---

### Post by trubblemaker on 2006-10-30
for faster browsing in firefox with bad ipv6 routing you might can turn off ipv6 in just firefox,

see this post for more help

[http://ubuntuforums.org/showpost.php?p=481573&postcount=12](http://ubuntuforums.org/showpost.php?p=481573&postcount=12)

---

### Post by howardcheng on 2007-01-04
> **stream303 said:**
> Arg - these windows-centric routers trying to be dns servers :)

I'd have a look at your /etc/resolv.conf file, and I'll bet that your router's dns is listed first in the list - which usually causes the dreaded timeout before it gets to your ISP's listed dns addresses.

There's a fix for this if this is the case - and it *isnt* making that file read-only :)
Okay, as soon as I removed the router as the first entry of resolv.conf everything is working fast again.

What is this fix?  I do not want to edit the file every time.  I suppose I can write a script to do that after ifup is run...is there an easy way?

I have disabled IPV6 but it does not help.

---

### Post by trubblemaker on 2007-01-05
I have read the answer but can't remember it as it didn't pertain to me there is another file that you can right to that will make the change for you... sorry dont 'remember the name but it isnt' resolv.conf ..... sorry don 't mean to repeat the answer but it was in another thread that I can't find right now.

Google these forums as the answer is out there.

---

### Post by mips on 2007-01-05
> **howardcheng said:**
> Okay, as soon as I removed the router as the first entry of resolv.conf everything is working fast again.

What is this fix?  I do not want to edit the file every time.  I suppose I can write a script to do that after ifup is run...is there an easy way?

I have disabled IPV6 but it does not help.

[http://ubuntuforums.org/showthread.php?t=128254](http://ubuntuforums.org/showthread.php?t=128254)

You can also go into your routers config and manually specify the isps dns servers instead of the router getting them via dhcp. In theory your router should now pass these settings onto your pc.

---

### Post by gideon07 on 2007-08-28
I was having a similar problem.  Slow DNS, SSH login, ls command on an NFS mounted share.  I found a solution that seems to work

In /etc/nsswitch.conf change the line 

> hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4

to

> hosts:          files dns

I am not sure what mdns4_minimal is, but it was really slowing things down for me.  Now the network is back to lightning speed

---

### Post by mips on 2007-08-28
Try adding your loopback as the first entry to your hosts file.

---

### Post by lamak12 on 2007-10-30
I've tried everything what you've written here, but nothing helped me.  Do you have any other idea what to do when I have problems with DNS translating?

When I change to WIN XP, everything works OK...on the same PC and with the same browser. But in Ubuntu [and also Kubuntu on my sister's PC] I have to wait for example 5 seconds until web page starts loading...I just see "Looking for the server".

Here is the list what I've tried to solve it:
-disable IPv6 in ubuntu and Firefox
-manually set IP adresses and DNS servers


Thank you very much for any help or idea.
Petr.

---

### Post by lamak12 on 2007-10-30
I have found solution for my problem. It was my mistake, that I did not recognizes it earlier. 
On my server where runs DHCP I had in dhcpd.conf two DNS servers from my ISP. But first of them did not work yet. So I put the second one to the first position and after restarting DHCPD, internet became faster on both my computers.

But WIN XP have no problem with this, there is no important in which order you have your DNS servers. It can probably choose the right one quickly.

I write this post just for people who don't know this..like me before...

Bye

---

### Post by Dennis N on 2007-11-02
This may help some people, but be unrelated to the problems of others.

A few days ago, my laptop with 7.04 began having a 4-5 second delay while "looking up" the address of every web site. Previously, everything had worked fine. Since I had made no changes to my system, I figured it must have something to do with the DNS service - something had changed. My router uses the DNS provided by my ISP.  My Windows XP machine connected to the same router did not experience this issue. Disabling Ipv6 did nothing. 

Every image and ad coming from another source was adding  its own 4-5 seconds delay to the time before the entire web page is loaded. 

The solution was to use Open DNS. I did it by changing the router settings for DNS server. Nothing had to be done to Ubuntu.  It solved the delay problem completely.

---

### Post by gweaver on 2007-11-04
I had the slow DNS problem with my Ubuntu 7.10 installation and D-Link 504 router.

I know the problem was IPv6 related because disabling IPv6 in Firefox solved the problem in Firefox. The problem still occurred in other apps though, most annoyingly in Synaptic.

I tried the blacklist IPv6 approach, but that didn't solve the problem. So then I thought the problem might be the router and updated the firmware. Unfortunately the firmware update died and I had to resort to using a serial cable and hyperterminal to revive it with the latest firmware! Having revived the router I still had the same problem, so I had a good look through the router settings and found the problem...

The D-Link 504 acts as a DNS proxy by default - it uses to DHCP to tell your computer that it (the router) is the DNS server and it forwards DNS queries from your computer to your ISPs DNS servers. This would be fine, but the router doesn't seem to play nice with IPv6, so there is a delay of a few seconds while something presumably times out and resorts to using IPv4.

The solution was simple:[LIST]
[*]Note down the DNS server addresses found by your vintage D-Link router
[*]Disable the DNS proxy function of the router
[*]Alter the DHCP settings on the router to give out the DNS server addresses noted above
[/LIST]

You'll need to change the DNS addresses given out by your routers DHCP server if you change ISP or if your ISP changes the address of its DNS servers.

Now all my software can connect to t'internet in a timely fashion, without having to mess about with blacklisting kernel modules or internal software settings.

Thats it - easy. I recommend that anyone with a D-Link router and internet connection problems try the steps above before messing with system files.

---

### Post by JayvJay on 2007-11-04
Disable  IPv6

[http://kb.mozillazine.org/Network.dns.disableIPv6](http://kb.mozillazine.org/Network.dns.disableIPv6)

Look at this and make the changes assuming you are using firefox.

luck!

---

### Post by salvador24 on 2007-11-06
Posted this in another thread as well, but I spent hours surfing the forums trying to find a solution to this issue as disabling IPv6 either globally or in FF didn't work for me and neither did changing DNS to OpenDNS.  However, in my searching I did find this known bug which has a fix that hasn't made it out of the proposed repositories yet:

[https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/156720]("https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/156720")

Turns out this is exactly the problem that we are having!  So, I enabled the -proposed repository in Synaptic/Aptitude and downloaded the "libc" updates only (I then disabled the -proposed repository again), and the internets were fixed!  My DNS lookups are now blazing fast again and everything works just like it used to.  I hope this fix works for others...

---

