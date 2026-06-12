---
title: "[SOLVED] Network connection problems on new install"
date: 2008-03-05
forum: Networking &amp; Wireless
---

### Post by DrBunker on 2008-03-05
Sorry, I tried to think of a more original post title but couldn't ;)

First things first, I've spent two days looking around this and other forums and have found loads of threads which are *similar* but that don't quite match my problem. I'm new to Ubuntu but I was comfortable with the install process and it seems like I've fallen victim to the same problem that other people have had with regards to connection via a router.

I appreciate that there are millions of posts for connection problems but as I say I can't seem to find the right info on them!

I'm using 7.10 with a Netgear cable WGR614 router with a dual boot of XP. I was happily using the router with Windows (and am also using it on the PC I'm posting from) so I'm confident that it is set up correctly. I can ping the router in Network Tools *if* I set the IP address to Static in Network Settings but as soon as I revert to DHCP I can't. I can't ping Google or open the router page in Firefox.

I've tried turning IPV6 off but that didn't work (as I thought it wouldn't as that appears to be a fix for DNS resolution issues). Running ifconfig tells me that the NIC has:

--an inet address of 192.168.1.1 (which is the same as my router)
--a Bcast of 192.168.1.255 (not sure where this comes from)
--no IPV4 address (which I assume is a problem)

When I look at the router page on a working machine I cannot see the Ubuntu machine's IP (as set in Network Settings) but I've set it in the correct range.

I've got a feeling (from experience) that this is one of those problems where I'm very close to a fix but  I just can't put my finger on what it is and after two days of searching I caved and decided to post on here!

Thanks in advance


Doc

---

### Post by chili555 on 2008-03-05
> an inet address of 192.168.1.1 (which is the same as my router)This will never work. When you ping 192.168.1.1, you are not getting the router, you are just pinging yourself. Sort of like chasing your own coat-tail.

Are you trying for a wired, ethernet connection, or wireless?> very close to a fixCorrect.

---

### Post by DrBunker on 2008-03-05
Thanks for the quick reply

> **chili555 said:**
> This will never work. When you ping 192.168.1.1, you are not getting the router, you are just pinging yourself. Sort of like chasing your own coat-tail.
In Network Settings I've set localhost to the router's address and home (the local machine) to 192.168.1.8. Does this still mean I'm trying to ping myself? Do I need to add these two lines? I deleted all of the ip6 lines which were in there when I first installed - was this a bad idea (it wasn't working before).

I've only got one DNS server atm, the main router IP address - does this matter? Also, are the host name and domain name fields required on the General Tab?

> **chili555 said:**
> Are you trying for a wired, ethernet connection, or wireless?
Wired via ethernet.

Cheers



Doc

---

### Post by chili555 on 2008-03-05
localhost 127.0.0.1
chili-laptop 127.0.1.1  <---or whatever your local machine is called.

I know these look wacky, but they are correct. The ipv6 lines should have remained. > I've only got one DNS server atm, the main router IP address - does this matter?No, as long as you have one that resolves correctly, and your router usually will.> Also, are the host name and domain name fields required on the General Tab?The host name, chili-laptop, for example, is needed. Domain can be blank.> Does this still mean I'm trying to ping myself?Setting the local machine to 192.xyz is just wrong. 

Please amend and then open a terminal and do:```
sudo dhclient eth0
```Let us know the result. We don't need any more than 'timed out' or 'connected, whoopee!'

---

### Post by DrBunker on 2008-03-06
OK, I'm at work now but I'll have a go at your suggestions when I get home.

I saved a copy of the connection settings with the ipv6 options so I'll revert to that but can I assume that the IP addresses you gave are for example only and should be replaced with ones from my range?

Also, does the host name need to be something specific or can it just be anything as long as it's unique on the network?

Finally, why is it wrong to use an IP of 192.xxx? This is the range as specified on the router? The other PC on the network is working off the same range. :confused:

---

### Post by schmildo on 2008-03-06
*sorry i dunno how to use the quote yet*

No. leave the ip addresses as he specified here:
----------------
localhost 127.0.0.1
chili-laptop 127.0.1.1
------------------------------
The router's DHCP functionality will allocate all the other IP adresses for you. I personally didn't even do the 127.0.1.1 thingy, ubuntu's default name is 'UBUNTU'. DHCP allocates you an IP address, defines your gateway, and either gives you DNS servers or the router will resolve requests itself(asuming you've defined DNS servers on the router). It's a really cool system.

With the hostname,  you can have anything you want that isn't already on the network (and technically you could probably get away with having two with the same name.. but don't) I didn't bother defining my own hostname, it's only purpose as far as i can see is to save you from having to remember IP addresses of hosts in your network, which can be usefull when you're using DHCP because the IP addresses will change. (but i've only got two pc's in my network at the moment)

and with the 192.xxx; I think he's just saying you shouldn't have to specify an IP address when DHCP is supposed to do it for you. So you're right in assuming you should have an IP address in the range specified on the router, but you shouldn't have to set it yourself, the router will pick an appropriate one for you. (DHCP = Dynamic Host Configuration Protocol)

good luck!

---

### Post by DrBunker on 2008-03-06
> **schmildo said:**
> I think he's just saying you shouldn't have to specify an IP address when DHCP is supposed to do it for you. So you're right in assuming you should have an IP address in the range specified on the router, but you shouldn't have to set it yourself, the router will pick an appropriate one for you.

See, that's what I thought but it was this bit that confused me "*Setting the local machine to 192.xyz is just wrong.*" He seems to be referring to the actual address not the fact that there is an address there in the first place.

I know that it doesn't work if I set it to DHCP so do I need to do something at the router (I shouldn't think so) or within Network Settings?

---

### Post by chili555 on 2008-03-06
> Also, does the host name need to be something specific or can it just be anything as long as it's unique on the network?It needs to be the name of your specific computer. Open a terminal and you will see something like mine:```
chili@LAPTOP60:~$ 
```This tells me the logged in user is *chili* and the name of the computer; that is, the host name; is *LAPTOP60.*

The attributes you are changing are actually a GUI way to change a file in the system, */etc/hosts.* You could just as easily edit the file by hand, with sudo gedit, for example. Here is my /etc/hosts file for reference:```
127.0.0.1 localhost
127.0.1.1 LAPTOP60

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```The 127.xxx numbers are required and the same for every Linux machine I have ever seen, and I have messed with most distributions.

The place for the static IP address you want, if you want static, is */etc/network/interfaces.*I strongly recommend DHCP, since with static, you will see an IP address in *ifconfig* whether you are actually connected or not, but with DHCP you will only see an IP if you are actually connected.

Here is my */etc/network/interfaces* file for reference:```
auto lo
iface lo inet loopback

#auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid GBR9
```In my case, eth0 is ethernet and is not usually used, so the 'auto eth0' is commented out. eth1 is my wireless.

Please make the changes and then see if you can connect. A reboot might help.

> do I need to do something at the routerNope. I think once we get our Network Settings corrected and reboot, you will connect properly.

---

### Post by DrBunker on 2008-03-06
[QUOTE=chili555]It needs to be the name of your specific computer.[/quote]
OK, I'll try that.

[QUOTE=chili555]The 127.xxx numbers are required and the same for every Linux machine I have ever seen, and I have messed with most distributions.[/quote]
So, does it not matter what I've got set up on my network at the moment?

[QUOTE=chili555]I strongly recommend DHCP, since with static, you will see an IP address in *ifconfig* whether you are actually connected or not, but with DHCP you will only see an IP if you are actually connected.[/quote]
I will put it back onto DHCP and see if it works with the changes above after a restart.

Cheers

---

### Post by DrBunker on 2008-03-06
> **schmildo said:**
> *sorry i dunno how to use the quote yet*

I thought I'd give a little back ;)

To quote

1. click the quote button after someones post (this is the easiest way and you can edit the text afterwards) 

2. highlight text in your message and click quote (the speech bubble button) 

3. use **['quote]** (without the apostrophe) at the beginning of text followed by **[/quote]**. If you want to add their name just add **=theirname** after the first quote.

Hope this helps. :)

---

### Post by schmildo on 2008-03-06
Ok lets see....

> **DrBunker said:**
> 1. click the quote button after someones post (this is the easiest way and you can edit the text afterwards) 
bdafdaf

> **DrBunker said:**
> 
2. highlight text in your message and click quote (the speech bubble button) 

fdasfdagagd

> **DrBunker said:**
> 
3. use **['quote]** (without the apostrophe) at the beginning of text followed by **dfafdaafasdfafda**. If you want to add their name just add **=theirname** after the first quote.
dfafdasfa
Hope this helps. :)

fdasfadsfdasfjka

...Fingers crossed...
Yey! thanks!

Oh, and speaking of which how the heck do i use that 'thanks' thing? somone thanked me but I don't know how to do it back?

---

### Post by DrBunker on 2008-03-06
> **schmildo said:**
> Oh, and speaking of which how the heck do i use that 'thanks' thing? somone thanked me but I don't know how to do it back?

No problem. To thank someone just click on the medal next to the quote button.

---

### Post by schmildo on 2008-03-06
> **DrBunker said:**
> No problem. To thank someone just click on the medal next to the quote button.

Done!

thanks.

---

### Post by chili555 on 2008-03-06
> So, does it not matter what I've got set up on my network at the moment? No sir. That's the magic of DHCP. It says, in effect, to your router, 'Hi, may I please have an IP address and DNS addresses in whatever range you use here? Thanks!' Your router does the exact same thing with the outside world, your ISP.

Good luck and let us know.

---

### Post by DrBunker on 2008-03-06
OK, I've set it to DHCP now and changed the addresses back to 127.XX and rebooted.

My interface file looks like this now:

```
auto lo
iface lo inet loopback


iface eth1 inet dhcp

auto eth0
```

It did say the following after dhcp but the lines disappeared after rebooting:

```
address 192.168.1.1
netmask 255.255.255.0
gateway 192.168.1.1
```

and the hosts file:

```
# The following lines are desirable for IPv6 capable hosts
127.0.0.1 localhost
127.0.1.1 home
ff00::0 ip6-mcastprefix
fe00::0 ip6-localnet
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
::1 ip6-localhost ip6-loopback
ff02::3 ip6-allhosts
```

So that looks better but...I still can't ping any address and I can't access sites on Firefox. The difference is that FF doesn't just fail as soon as you enter the address, instead it spins for a good thirty seconds thinking about it and then it says  "**Server not found**"

Is this a good development?

---

### Post by chili555 on 2008-03-06
> the lines disappeared after rebooting:Good! We don't want them.

Your *interfaces* file should look like this:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```Please amend with sudo gedit, and then open a terminal and do:```
sudo dhclient eth0
```Then let us know if you timed out or connected.

Your *hosts* file looks great, assuming you computer is named *home* as evidenced by the wording when you pop open a terminal, for example:```
user@**home**:~$
```

We're getting really close.

---

### Post by DrBunker on 2008-03-06
[QUOTE=chili555]Your *interfaces* file should look like this:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```[/QUOTE]

Yep, it does now.

[QUOTE=chili555]Please amend with sudo gedit, and then open a terminal and do:```
sudo dhclient eth0
```Then let us know if you timed out or connected.[/QUOTE]
It goes through a series of "**DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval XX**"  and then it says "N**o DHCP offers received, No working leases in persistent database. Sleeping**". Still no ping and nothing in FF...:confused:

[QUOTE=chili555]Your *hosts* file looks great, assuming you computer is named *home* as evidenced by the wording when you pop open a terminal, for example:```
user@**home**:~$
```[/QUOTE]
It is so that's another thing sorted!

[QUOTE=chili555]We're getting really close.[/QUOTE]
I hope so and, again, I really appreciate your help with this. I don't want to fall at the first hurdle.

Thanks

---

### Post by DrBunker on 2008-03-06
\\:D/  Got it!!

I was trying to think what could be the problem as your advice was so thorough and yet it wasn't working. I knew that the internet worked in Windows but I double-checked the NIC and there was no light. I searched for help regarding the driver in question and pretty quickly came across [**_this_**](http://ubuntuforums.org/showthread.php?t=538448). As soon as I read the detail it clicked. 

I logged into Windows, made the changes and, bang, the internet works.

It's pretty slow (at least in FF) but at least I've got it working!!

Thanks for all your help and sorry for wasting your time (at least it helped get me familiar with using the Terminal window...).

Cheers


Doc

---

### Post by chili555 on 2008-03-06
Fabulous! Glad it's working. I didn't consider it a waste at all: you learned a lot, I had fun and made a new friend and some other guys will search this forum for Realtek 8168/8169 and we will have helped them, too. Good stuff!

Some clues as to performance may be gained by running:```
sudo ethtool eth0
```Look for autonegotiation issues and post back if we can help.

---

