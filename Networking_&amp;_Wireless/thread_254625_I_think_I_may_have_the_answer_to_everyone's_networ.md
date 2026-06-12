---
title: "I think I may have the answer to everyone's network connection prob"
date: 2006-09-10
forum: Networking &amp; Wireless
---

### Post by 0be1 on 2006-09-10
There seems to be a lot of posts regarding the problem of not being able to connect to the Internet on 6.06 (server at least). I have posted along with many others and no one seemed to have a solution, until possibly now.

I have done what everyone was posted (blacklist ipv6, modify this, modify that) and nothing worked. The last thing I have modified was my /etc hosts file, and now I am working.

Note: since I do not want a DHCP addy on this particular comp I am running static. I have not tested it on DHCP. and if someone could and please post the results. It would be much appreciated. I am not going to break mine now that I am working.

But here is my theory on why many people are currently not working. Let's take a look at my host file before and after. Then you can try to modify your's and see if you can get on the net as well.

Original hosts file: xxx.xxx.xxx.xxx for security purposes. Be sure to change xxx.xxx.xxx.xxx to your comps static ip addy. If running DHCP my guess is to copy the line of your routers internal ip addy 192.168.xxx.xxx. i.e) 192.168.1.1 or 192.168.0.1

127.0.0.1 localhost blackstar

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
xxx.xxx.xxx.xxx someone.hsd1.tn.comcast.net. someone

Now, notice that in my original hosts file my configuration (not done by me) has my network configuration info located in the bottom half of the file listed in the ipv6 section. Well, if I blacklisted ipv6 how is my comp. going to get out on the net? Well now look at my modified hosts file.

Modified file:

xxx.xxx.xxx.xxx someone.hsd1.tn.comcast.net. someone
127.0.0.1 localhost someone

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
xxx.xxx.xxx.xxx someone.hsd1.tn.comcast.net. someone

Notice I took my very last line out of my host file ipv6 section and made it my very first line out of the ipv6 section. I rebooted, and wala, I have been on the net every since. And quite fast I might add.

So during installation of the software the config script put my local info in the hosts file in the IPv6 section which I cannot use. ***Developers, why not have the script put the local network info in both sections for compability purposes?***

Ipv6 will be a wonderful thing, but not until all the bugs and extensive testing is done. For now we need to keep these OS defaulted to IPv4. My guess is the reason everyone else was getting gentoo, yellow, and other distros to work is becuase IPv6 was not the default config,

Here's to (hopefully) happy connectivity :o) I know I am much happier now that I can work.

OPS, if this is the solution, could you please consider making it a sticky so there is not a lot of cross postings. I appreciate it

regards...

0be1

---

### Post by deleted1028 on 2006-09-10
I don't know what the solution is or why but my internet is working fine today. I took a look at the file and mine is already written like that.

127.0.0.1 localhost omega
127.0.1.1 omega.client.mchsi.com omega

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

I don't get it,... yesterday I had no internet while using Ubuntu, not on my cd or my install but now i do. I haven't done anything different. I haven't even used linux today. Yesterday I had to read these post from my Mac osX partition.

---

### Post by 0be1 on 2006-09-10
deleted1028;

One thing I do not understand is how you are getting internet access on 127.0.0.1 when that is a loopback address. That IP address should be anything else but that number. That's what I don't understand.

But if you have problems again, at least you know which file to check, and what numbers you should possibly change.

regards...

0be1

---

### Post by JonParis on 2006-09-10
I'm afraid that it hasn't done anything for me.

My hosts file was already in that sequence.

I have tried both with the DHCP approach and with a fixed IP.  

Nada .  

The only difference is that previously when I used a fixed IP I could ping my own IP.  But with this setup both my own IP and the rest of the network is invisible.  I simply get "Destination Host Unreachable".

I used the Administration -> Networking tool to set the IP.  But no entry appears in the hosts file.  Is this stuff stored in more than one place?

For me this change (unabvle to pind own IP) is a backward movement, but maybe the fact that something changed will give someone inspiration!

---

### Post by 0be1 on 2006-09-10
JonParis;

Please post your config files (changing part of the address for security reasons) as well as following the instructions in the others posts (if IPv6 is blacklisted or not, your pci output, dmesg output) anything that may help us help you get it fixed.

If your host file is already in this order, what about the order of how addresses are resolved.

Hopefully we can get you fixed up ;)

regards...

0be1

---

### Post by JonParis on 2006-09-11
Thanks for the offer - be happy to post the files, but it will take me a while as without network support there is a lot of messing about to do.

Other than the hosts file, which others do you need to look at?

---

### Post by elpuerco on 2006-09-12
Could this be the answer to my problem at:

[http://www.ubuntuforums.org/showthread.php?t=255937](http://www.ubuntuforums.org/showthread.php?t=255937)

If so I am not sure I fully get what you say requires adding to the host file?

---

### Post by Slim Odds on 2006-09-12
Obe1, I know that you're very excited that you got your network working. But, there is no such thing as an "IPV6 section" in the hosts file. IPV6 addresses have a different syntax than IPV4 addresses. Therefore, they can be mixed in the hosts file.

[http://en.wikipedia.org/wiki/IPv4#Addressing](http://en.wikipedia.org/wiki/IPv4#Addressing)
[http://en.wikipedia.org/wiki/IPv6#Addressing](http://en.wikipedia.org/wiki/IPv6#Addressing)

---

### Post by 0be1 on 2006-09-13
Slim Odds;

I do not know what your host files says, but the default one from the latest 6.06 LTS server live CD has the following.

# The following lines are desirable for IPV6 capable hosts
::! ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

And when my network was auto detected it was added to the very last line. And I noticed that none of this is commented out.

I am also not trying to be difficult, but merely pointing out that the tops section of the default host file is in IPv4 notation and the bottom is in IPv6. By moving my IPv4 info to the top of the file and rebooting took care of my problem.

There also seems to be quite a few posts with people having network problems with the lastest release and no permanent solutions. So how would you suggest the problem be solved as many are having problems. And a small thing (yet a main function) of the OS could give this distro a bad name (even though it is the best I have used) for a newbie.

regards...

0be1

---

### Post by bogl on 2006-09-14
Nope, this solution doesn't work for me either.  Two network cards installed, neither are working despite every incantation this thread & many others here can offer

Does *anyone* have any idea what the problem is?  I can't find a bug formally lodged on this - have I just missed it?

Is something so broken about networking in Ubuntu that it can't be fixed? 

I have wondered whether my problem is the Ubuntu Server install: perhaps things would work better if I did a full install, then added server packages?  

I realise the insecurity of this BTW.  It would be nice to have a server serving though, regardless of the insecurity.

---

### Post by Slim Odds on 2006-09-14
> **0be1 said:**
> 
I am also not trying to be difficult, but merely pointing out that the tops section of the default host file is in IPv4 notation and the bottom is in IPv6. By moving my IPv4 info to the top of the file and rebooting took care of my problem.


Calm down Ode1,

Did you even follow the links that I sent? 

Often people will say, "Well, I did .... and it worked for me". But that's really very complete unless there is a valid explanation why it works.

My point, which you seem to ignore, it that there are **completely different syntaxes** for IPV4 and IPV6 addresses.

Therefore, there are no "sections" in the host file. They can be mixed and it does not matter.

Sorry to burst your bubble. I know that you were just trying to help.

---

### Post by tbonius on 2006-09-14
> Original hosts file: xxx.xxx.xxx.xxx for security purposes. Be sure to change xxx.xxx.xxx.xxx to your comps static ip addy. If running DHCP my guess is to copy the line of your routers internal ip addy 192.168.xxx.xxx. i.e) 192.168.1.1 or 192.168.0.1

This does not necessarly need to go into your hosts file.. it is simply the address for a default gateway.  /etc/hosts allows a computer to resolve computer/domain names into IP addresses.  Entries into the hosts file superceded DNS by default (unless the order is specified differently "man resolv.conf")


> 127.0.0.1 localhost blackstar
# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
xxx.xxx.xxx.xxx someone.hsd1.tn.comcast.net. someone

Now, notice that in my original hosts file my configuration (not done by me) has my network configuration info located in the bottom half of the file listed in the ipv6 section. Well, if I blacklisted ipv6 how is my comp. going to get out on the net? Well now look at my modified hosts file.


Your computer will continue to "get out" to the net.. it just might not resolv some names correctly (depending upon what is in /etc/hosts).  You can put a myriad of entries in here in bunk formats if you wish.. it only affects the resolver library.  You still maintain IP connectivity to your network.  You can verify this by checking the address assinged to your adapter (ifconfig) and your default gateway (netstat -rn).. but again.. the resolver library is a different story.

> Modified file:

xxx.xxx.xxx.xxx someone.hsd1.tn.comcast.net. someone
127.0.0.1 localhost someone

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
xxx.xxx.xxx.xxx someone.hsd1.tn.comcast.net. someone

Notice I took my very last line out of my host file ipv6 section and made it my very first line out of the ipv6 section. I rebooted, and wala, I have been on the net every since. And quite fast I might add.

I have a feeling something else might have been wrong with your connectivity.. maybe the DNS resolvers were not being assigned and writtent to resolv.conf.  Since this was a statically configured machine assumable with some sort of third party router/firewall that might use a DNS proxy service.. I cant tell you for sure.. but make sure your DNS entries are written correctly to /etc/resolv.conf.

> So during installation of the software the config script put my local info in the hosts file in the IPv6 section which I cannot use. Developers, why not have the script put the local network info in both sections for compability purposes?


A hosts file is a flat file with entries that is parsed by the resolver.  There are no sections.. and your localhost info is all over the file:

::1 ip6-localhost ip6-loopback

is the same thing as 

locahost 127.0.0.1

As far as putting "local network" info in your /etc/hosts file.. do you mean the IP address assigned to the ethernet adapter?  That information CAN go into the /etc/hosts file but is not necessary.. DNS allow us to put one entry in one server for resolution purposes instead of a hundred hosts with a hundred maintained /etc/hosts files.  Also.. why would you put your "local netowrk" info in /etc/hosts if you were Dynamically assigned an address from a DHCP server.  This would become cumbersome to change everytime you rebooted if your address changed.  Again.. this is what DNS is for (especially Dynamic DNS).

Due to the fact that you stopped any IPv6 services from loading (you could verify this with ifconfig on your adapter).. the resolver cannot use the entries from /etc/hosts correctly, thus if you are not using IPv6.. then remove all references to ANY V6 addresses from /etc/hosts.

> Ipv6 will be a wonderful thing, but not until all the bugs and extensive testing is done. For now we need to keep these OS defaulted to IPv4. My guess is the reason everyone else was getting gentoo, yellow, and other distros to work is becuase IPv6 was not the default config,


IPv6 IS a wonderful thing that is working very nicely.  In fact.. most of the applications and services you run on Ubuntu most likely function in a native IPv6 environment.  I have noticed quite a few posts here involving IPv6 and have noticed that a number of people do not really understand how IPv6 (or even IPv4 for that matter) works.

If you wish to remain IPv4 only for right now (in order to keep it simple) then that is great, but make sure you understand how /etc/hosts, /etc/resolv.conf, /etc/hostname and /etc/network/interfaces all work.. and be thankful that it is not as RPC dependent as Solaris . :-P

[http://www.kame.net/](http://www.kame.net/)

[http://www.section6.net/wiki/index.php/Main_Page](http://www.section6.net/wiki/index.php/Main_Page)

[http://www.bieringer.de/linux/IPv6/IPv6-HOWTO/IPv6-HOWTO.html](http://www.bieringer.de/linux/IPv6/IPv6-HOWTO/IPv6-HOWTO.html)

T

---

### Post by dad_ems on 2008-07-23
I have some information to add to this discussion. Whether it will help or not remains to be seen. I use an oldish (but quite capable) Sony Vaio machine which came with Windows ME. A week or two ago I put Ubunto on the machine (with a seperate drive.. they aren't "dual boot") It worked fine and I did a lot of fooling around with the setup .. 

About a week later.. for absolutely no good reason.. I decided to update the driver on the NIC (Realtek RTL8139(C)) .. This was done while in using ME and used the latest driver from the Realtek site (autoinstall multi OS Windows) found [**HERE**](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=6&PFid=6&Level=5&Conn=4&DownTypeID=3&GetDown=false). Clearly the *ix and the Windows do not use the same driver and I did not change the *ix driver.. this indicates that it relates to some initialization or hardware state on this and perhaps other NIC's.

After I made this change the ME worked fine.. though with no descernable change from previously.. A few days later I booted into Ubuntu and the NIC was completely useless.. It wouldn't even light up the LED for "connect" on my firewall.. (also wouldn't work if connected directly to the cable modem)

No matter what I do I cannot get the Ubuntu to connect ever again.. I can't even ping. I even rebuilt it from the ground up. I can boot into ME and the card works great, while in Ubuntu it never works now.. even though it worked fine before. 

If I get a chance I will "rollback" the driver and see if this makes any difference. The original driver was the one which came with the machine ca.2000 I realize this doesn't solve any problems, but it may give the more knowledgeable folk an added clue which may help them find a solution.

I realize this is an old thread and I hope I haven't stepped on any toes, but the problem still seems to be widespread around the web.

---

