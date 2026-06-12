---
title: "NFS Ubuntu Server --&gt; OS X Clients... Clarification Requested"
date: 2008-03-18
forum: Networking &amp; Wireless
---

### Post by Paideuma on 2008-03-18
I have pouring over the internet for days trying to figure out how to get this problem solved.  My background is that I can do a fair amount of programming (Junior in College:  Computer Engineering/Mathematics double major), but they don't go over network protocols or OS Permissions in any of the classes so I am completely ignorant in these area.  (OMG, it's frustrating to feel like a badass at school and a dunce on Ubuntu... ;) )

What I want:
To set up an Ubuntu NFS file server for use only on the LAN.  It is to connect with Mac OS X 10.4 and 10.5.  It should be accessible to the various Macs that will be signing on the LAN without having to configure them.  I'd like to see the shared directory then be able to mount it or unmount it (I do NOT want it auto mounted... this causes my Finder to hang for 15-60 seconds if it can't find the directory because I'm not on my home network).

When I take my Mac to a network with Windows machines and/or Macs, the various shared/public directories on the various computers appear under Places in finder. I don't have to type in an IP address or anything.  This is what I would like to have happen for those who sign on my LAN.  I wanna see it, mount it, use it, then eject it.  I read that this can be done with Zeroconf, but I can't start this process until I have the NFS file server set up, so I won't go there... yet.

The (main) guides I've visited:
[http://ubuntuforums.org/showthread.php?p=4387032](http://ubuntuforums.org/showthread.php?p=4387032)
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

The problems I've encountered:
1.  I don't know what the IP address of the various Macs who will be accessing the NFS Share drive will be.  The router will assign them IP addresses.

1a.  In configuring the /etc/exports file, I can't find a comprehensive syntax guide for specifying what IP addresses I want (say, if I wanted 10.10.10.1 through 10.10.10.57).  Most just give *an* example of a configuration, usually 192.168.0.0/28 (which means the first 15... why does "/28" mean the first 15???)

1b.  I've also seen people say they use host names or net groups or DNS... It was my understanding that DNS is used to broadcast the IP address of a computer to the internet.  I'm just working locally and can't count on the computers having specific IP addresses.  Does that mean I don't need DNS?

1c.  What the heck are net groups?

2.  As explained in the intro, as far as permissions go, everyone has my blessing to play with stuff all they'd like, provided they're on the LAN.  I don't want those outside the LAN to have access to the shared directory

2a.  How do I prevent those from outside my LAN from accessing the drive?

2b.  I've read about UID/GID mapping... I have no idea what the UIDs/GUIs of the people who are signing onto my LAN have.  Is there some other form of UID/GID work-around?  Perhaps a password they have to know?  How should I approach this problem.  Remember, this should require NO configuration on the part of the Macs.

Conclusion:
If you made it this far, THANKS!  It's a long post, I know.  :(  Any help you (the greater community) can render would be much appreciated!

Musings:
It appears to me that networking is the one thing that modern lay-users want.  Thus, the major OS labels have done a lot to make it as easy as possible... and they've done an awesome job!  My 10 year old nephew knows how to set up the downstairs computer so he can grab the file he wants on his mom's laptop without using a Thumb drive.

Ubuntu... my at once tortured,cruel, teasing, inviting, sensuous and seductive love affair... you are delicious in so many ways, and positively indecipherable in others.  One day, I will understand you.

---

### Post by madjr on 2008-03-18
> Ubuntu... my at once tortured,cruel, teasing, inviting, sensuous and seductive love affair... you are delicious in so many ways, and positively indecipherable in others. One day, I will understand you

hehe
:lolflag::lolflag:

---

### Post by Eiríkr on 2008-03-19
Hey there Paideuma --

I understand your frustration about how complicated it can be to set up sharing.  Part of the issue, though, is a fundamental difference in philosophy.  Windows in particular went the route of ridiculous ease and convenience, which is great -- except it also applies to the bad guys.  

Ubuntu's (and to a greater extent Linux's / Unix's) approach is more security conscious, which unfortunately inevitably makes things more complicated and difficult.  (Apple is steering a middle path, with some success.)

But now to get down to your brass tacks :):

> **Paideuma said:**
> (OMG, it's frustrating to feel like a badass at school and a dunce on Ubuntu... ;) )
Heh, reminds me of my first-ever Linux install, RedHat 7, when it took me several days to find out what happened to my CD drive.  :mrgreen:

> **Paideuma said:**
> ...I read that this can be done with Zeroconf, but I can't start this process until I have the NFS file server set up, so I won't go there... yet.

Right you are, and right too that it makes more sense to put the horse before the cart and get NFS up and running first.  

> **Paideuma said:**
> The (main) guides I've visited:
[http://ubuntuforums.org/showthread.php?p=4387032](http://ubuntuforums.org/showthread.php?p=4387032)
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

The former was actually something I wrote a while back after (*finally*!) getting Lin -> Mac NFS sharing to work.  Let's see if we can't reproduce that for you here.  :)

Okay, there's quite a bit here to start, so let's dive in.  

> **Paideuma said:**
> The problems I've encountered:
1.  I don't know what the IP address of the various Macs who will be accessing the NFS Share drive will be.  The router will assign them IP addresses.

Not knowing the IPs of your clients ahead of time is still do-able.  As you note tangentially in 1a, we can instead specify a subnet range that can coincide with the range of addresses the DHCP server will  be handing out.  


> **Paideuma said:**
> 1a.  In configuring the /etc/exports file, I can't find a comprehensive syntax guide for specifying what IP addresses I want (say, if I wanted 10.10.10.1 through 10.10.10.57).  Most just give *an* example of a configuration, usually 192.168.0.0/28 (which means the first 15... why does "/28" mean the first 15???)

Incidentally, the number after the IP address slash tells us how many bits of the address are the same for this subnet.  Each IP address triplet represents eight bits (2 to the 8th, or 256 in total -- or values 0 through 255), so the whole four-triplet address is 32 bits in total (4 triples by 8 bits each = 32).  Another way of specifying loopback in these terms is 127.0.0.1/32, because all 32 bits of this address are locked down.  192.168.0.0/24 tells us that the first three triples (24 / 8 = 3) are locked down.  Your example of 192.168.0.0/28 specifies the first 28 bits are the same, which means the values up through 192.168.0.15 are locked down (24 for the first three triples leaves 4, 2 to the 4th = 16, or values 0 through 15), and thus (if I understand this aright) IP addresses from 192.168.0.16 through .255 could be used.  There's more regarding how subnets are defined [over on Wikipedia](http://en.wikipedia.org/wiki/Subnetwork).

So as it stands, I think you can only really specify the lower bound of the IP address range you want to share to.  Sharing to addresses over this won't be much of an issue though, as explained below for 2a.


> **Paideuma said:**
> 1b.  I've also seen people say they use host names or net groups or DNS... It was my understanding that DNS is used to broadcast the IP address of a computer to the internet.  I'm just working locally and can't count on the computers having specific IP addresses.  Does that mean I don't need DNS?

DNS is definitely **not** just for the internet -- it's for name resolution on any IP-based network.  I've got a home LAN totally separate and inaccessible from the web, and I've got my own DNS server (partially for caching purposes, partially to learn how it works) that handles hostname resolution within my LAN.  Host names can also be handled the old-fashioned hard-coded way with the /etc/hosts files, but this doesn't sound like it would work in your setup since you're dealing mostly with highly mobile laptops.  So no, you don't need DNS.  

(I've also heard tell there's supposed to be some way of combining DHCP and DNS functionality for a dynamically configured DNS setup, basically zeroconf DNS, but I've yet to find the time to really hunt that down and get into it.)


> **Paideuma said:**
> 1c.  What the heck are net groups?

I don't know what net groups are either.  :)


> **Paideuma said:**
> 2.  As explained in the intro, as far as permissions go, everyone has my blessing to play with stuff all they'd like, provided they're on the LAN.  I don't want those outside the LAN to have access to the shared directory.

2a.  How do I prevent those from outside my LAN from accessing the drive?

Not a problem -- so long as your [font=courier]/etc/exports[/font] file does not specify an address range for outside of your LAN, no one out there will be able to access it without some serious cracking to get into your LAN in the first place.  Generally safe LAN address ranges look like:
```
192.168.xxx.xxx
172.16.xxx.xxx
10.0.0.xxx
```
Have a look at [the Wikipedia article on classful networks](http://en.wikipedia.org/wiki/Classful_network#Special_ranges), specifically the ranges shown here that are shown with a purpose of "Private IP addresses" -- anything in these ranges is specifically non-internet.  


> **Paideuma said:**
> 2b.  I've read about UID/GID mapping... I have no idea what the UIDs/GUIs of the people who are signing onto my LAN have.  Is there some other form of UID/GID work-around?  Perhaps a password they have to know?  How should I approach this problem.  Remember, this should require NO configuration on the part of the Macs.

Since you don't know any of the UIDs or GIDs ahead of time, this could get tricky -- but thankfully, NFS provides just the mechanism needed.  You'll want to use the [font=courier]all_squash[/font] option in your [font=courier]/etc/exports[/font] file.  As noted in [font=courier]man exports[/font]:
> **User ID Mapping**

**nfsd bases its access control to files on the server machine on the uid and  gid  provided in  each  NFS  RPC request.** The normal behavior a user would expect is that she can access her files on the server just as she would on a normal file system. This requires that  the same uids and gids are used on the client and the server machine. This is not always true, nor is it always desirable.

< ... snip ... >

Here&#8217;s the complete list of mapping options:

< ... snip ... >

**all_squash**

Map all uids and gids to the anonymous user. Useful  for  NFS-exported  public  FTP directories,  news  spool  directories,  etc. The opposite option is no_all_squash, which is the default setting.

< ... snip ... >

**anonuid** and **anongid**

These options explicitly set the uid and gid of the anonymous account.  This option is primarily useful for PC/NFS clients, where you might want all requests appear to be  from  one  user.  As an example, consider the export entry for /home/joe in the example section below, which maps all requests to uid 150 (which is supposedly that of user joe).

**EXAMPLE**
```

       # sample /etc/exports file
       /               master(rw) trusty(rw,no_root_squash)
       /projects       proj*.local.domain(rw)
       /usr            *.local.domain(ro) @trusted(rw)
       **/home/joe       pc001(rw,all_squash,anonuid=150,anongid=100)**
       /pub            (ro,insecure,all_squash)
       /pub/private    (noaccess)
```


You'll have to figure out what user and group IDs you want to use for your share.  Let's assume you have a fresh username / groupname combo such as [font=courier]shares:shares[/font] with UID / GID of 1005:1005.  Let's also assume you're granting your friends' Macs IP addresses via DHCP in the range of 192.168.0.100-254.  In this case, an example for your [font=courier]/etc/exports[/font] file might look like this:
```
/pub/macshares    192.168.0.0/24(insecure,all_squash,anonuid=1005,anongid=1005)
```

The [font=courier]insecure[/font] option is needed to allow clients to connect using an insecure port (i.e. a port number higher than the "secure" range of 1-1024).  Mac and Konqueror both require this to allow browsing.  

The [font=courier]all_squash[/font] option means **all** user connections are mapped to the anonymous user / group, which in this case we specify should be "shares".  Naturally, this user / group should have ownership or at least r/w/x permissions on the shared directory and any required subdirectories.  

----------

Anyway, I hope this helps.  Try this setup and see if it works along the lines you expect and need, and then try the Avahi setup procedure described in the linked post.  Let me know if you have any questions.

Cheers,

Eiríkr

---

### Post by netztier on 2008-03-19
> **Eiríkr said:**
> 
Your example of 192.168.0.0/28 specifies the first 28 bits are the same, which means the values up through 192.168.0.15 are locked down (24 for the first three triples leaves 4, 2 to the 4th = 16, or values 0 through 15), and thus (if I understand this aright) IP addresses from 192.168.0.16 through .255 could be used.  

That is completely wrong. 

*Edit: Or rather: **exactly wrong** ;-) Im extending this article a bit so that it my serve as reference... *

You are right in saying that /28 says that the first 28 bits of the IP address are "fixed". If you wrote /28 as a subnet mask, it would be:  255.255.255.240

Writing 255.255.255.240 as binary, you'd get 1111'1111.1111'1111.1111'1111.1111'0000 - count the ones. You'll get 28.

With such a subnet mask of length 28 and a subnet address of 192.168.0.0, you must keep the first 28 bits fixed, and you can vary the last four bits. With four bits, you can count from 1 to 16 or 0 to 15. 

Therefore, the valid addresses for subnet **192.168.0.0/28** are **192.168.0.0-15** . 

192.168.0.16 would be outside this subnet. In it's binary representation, we would have:

```

192.168.0.0     = [COLOR="Navy"]1100'0000.1010'1000.0000'0000.0000[/COLOR]'0000
192.168.0.1     = [COLOR="Navy"]1100'0000.1010'1000.0000'0000.0000[/COLOR]'0001
192.168.0.2     = [COLOR="Navy"]1100'0000.1010'1000.0000'0000.0000[/COLOR]'0010
192.168.0.3     = [COLOR="Navy"]1100'0000.1010'1000.0000'0000.0000[/COLOR]'0011
...
192.168.0.13    = [COLOR="Navy"]1100'0000.1010'1000.0000'0000.0000[/COLOR]'1101
192.168.0.14    = [COLOR="Navy"]1100'0000.1010'1000.0000'0000.0000[/COLOR]'1110
192.168.0.15    = [COLOR="Navy"]1100'0000.1010'1000.0000'0000.0000[/COLOR]'1111
192.168.0.16    = [COLOR="Navy"]1100'0000.1010'1000.0000'0000.000[/COLOR][COLOR="Red"]1[/COLOR]'0000
192.168.0.17    = [COLOR="Navy"]1100'0000.1010'1000.0000'0000.000[/COLOR][COLOR="Red"]1[/COLOR]'0001
...
255.255.255.240 = 1111'1111.1111'1111.1111'1111.1111'0000

```

All addresses from .0 to .15 can be written with the 28th bit set to zero; to write .16 in binary, we must set the [COLOR="Red"]red[/COLOR] bit to [COLOR="Red"]1[/COLOR]. Since this bit now has changed, it is falls out of this range. 

Note: The the subnet mask does not mandate that all bits covered by a "1" in the mask must be zero, it just says that all IP addresses that have the same bit pattern in the first **n** bits (where the subnet mask is **n** bits long) are within the same subnet. 

Seen from the other side: to be sure that an IP address is in the same subnet as another one, you have to make sure that their first **n** bits are identical, where the subnet mask is **n** bits long. 

Or from yet another perspective: to find a subnet mask that spans a subnet to hold any two given IP addresses, find how many contiguous bits (counted from the left) of the IP addresses are identical. The number of bits will be the number of 1s in your subnet mask.

Lets look at an another example:

Let's have 3 IP addresses and their binary representations. The subnet mask shall be 255.255.254.0 or /23, i.e. "23 bits long". You can see that 192.168.2.129 and 192.168.3.194 have the same bit pattern in their first 23 bits, therefore, they can be on the same /23 subnet. 192.168.0.1 has a different 23rd bit, therefore it can't be on the same /23 network.

```
192.168.0.1   = [COLOR="Blue"]1100'0000.1010'1000.0000'00[/COLOR][COLOR="Red"]0[/COLOR]0.0000'0001
192.168.2.129 = [COLOR="Blue"]1100'0000.1010'1000.0000'001[/COLOR]0.1000'0001
192.168.3.194 = [COLOR="Blue"]1100'0000.1010'1000.0000'001[/COLOR]1.1100'0010

255.255.254.0 = 1111'1111.1111'1111.1111'1110.0000'0000

```

If we changed the subnet mask to be /22 or 255.255.252.0, it'd look like follows. All three addresses have the same bit pattern in their first 22 bits, therefore, they all can be on the same /22 subnet:

```
192.168.0.1   = [COLOR="Blue"]1100'0000.1010'1000.0000'00[/COLOR]00.0000'0001
192.168.2.129 = [COLOR="Blue"]1100'0000.1010'1000.0000'00[/COLOR]10.1000'0001
192.168.3.194 = [COLOR="Blue"]1100'0000.1010'1000.0000'00[/COLOR]11.1100'0010

255.255.252.0 = 1111'1111.1111'1111.1111'1100.0000'0000

```



Reverting to the initial example, you can of course write an IP address like this: 192.168.0.16 /28. In that case, the valid address range is 192.168.0.16 to .31 (remember - you can only count from 0 to 15 with 4 variable bits.)

And the next ranges with a /28 mask would then be 

```
192.168.0.32 to .47
192.168.0.48 to .63
192.168.0.64 to .79
192.168.0.80 to .96
etc.

```


Of course, we tend to make life a bit easier, and we often choose our subnet mask length to fall onto the "natural" byte-boundaries:

255.255.255.0 becomes 1111'1111.1111'1111.1111'1111.0000'0000 in binary, and since we have 24 bits set to "1", we can write "/24" instead.

With such a subnet mask of length 24 and a subnet address of 192.168.0.0, you must keep the first 24 bits fixed, and you can vary the last eight bits. With eight bits, you can count from 1 to 256 or 0 to 255.

Therefore, the valid addresses for subnet **192.168.0.0/24** are **192.168.0.0-255** . Don't forget that you can't use the first and last addresses for a host in each range.


The whole confusion just comes from human laziness - we want to read decimal numbers, and we want byte values converted to decimal. Were we all capable of thinking in binary, we'd just see IP addresses and subnet masks as strings of 0 and 1. ;-)

regards

Marc


regards

Marc

---

### Post by Eiríkr on 2008-03-19
Thanks for the clarification Netztier, I had it wackbards apparently, based on assumptions learned from the more usual "natural" boundary /24 masks.  ;)

Cheers,

Eiríkr

---

### Post by Paideuma on 2008-03-20
Thanks for the posts guys/gals.  I've been working extra shifts so I'll give them a try tomorrow evening.  I'll repost to explain how it went.

:D

---

