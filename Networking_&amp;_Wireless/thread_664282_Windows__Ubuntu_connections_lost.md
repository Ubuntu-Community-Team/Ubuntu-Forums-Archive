---
title: "Windows / Ubuntu connections lost"
date: 2008-01-11
forum: Networking &amp; Wireless
---

### Post by 5circles on 2008-01-11
I'm not exactly sure what was working before, because it has been several months and lots of changes - my network configuration and ISP have changed a couple of times because of house moves.  But, now that I'm finally able to start working with my Ubuntu box again, I'm sure things were working better before.  And in any case, the networking certainly isn't working the way I want.  </preable>

From my Ubuntu box, I was able to see some of the systems on my network from Places | Network (Nautilus) - the Ubuntu box, a Windows XP Pro system, and a Linksys NAS 200. I wasn't able to see a Vista Premium system or an XP/Media Center.   All these systems have shared folders.  But I wasn't able to click into them - I just got a message about not being able to display the contents. Note the past tense; even this level has now disappeared - I now get a message that the folder contents could not be displayed when I try to click on the name of my network.  This latest change was after restarting.

I have been successful in making the Ubuntu system share a folder and accessing from Windows, following the instructions for smbpassword by jonandrews.

I had previously been able to mount shares from the NAS200, but they are no longer mounted.  Running mount -a manually, I see timeouts connecting to either 66.150.2.134 or 8.15.7.117.  Neither one of these IP addresses is on my network (192.168.2.xx) or the DNS.

All systems on my network have IP addresses from DHCP.

I'm stuck.  Any ideas greatly appreciated.  Thanks!

---

### Post by evanchu on 2008-01-11
You have described too many problems that can be solved at once.  I suggest solving one simple problem at a time.  The first problem you should look at is whether DCHP is serving the correct IP address to each of your machines.

Then check connectivity from each machine to other machines by using ping. After that, post your result.

---

### Post by 5circles on 2008-01-11
Sorry about the information/request overload.  I wasn't sure how much to say about what I'd already checked.

All systems are assigned IP addresses correctly (in 192.168.2.xx) by the DHCP server.  All can access the Internet.

Windows systems can ping each other and the Ubuntu system by IP address and by name.

The Ubuntu system can ping by IP address to other systems in the block, but not by name.  When I try to ping by name, I see IP addresses on the public Internet.  For some reason the same address shows up for several of the attempted Windows systems.  A different address shows up for the NAS200 - I'm guessing this was the DNS server when the connection previously worked.  But I'm probably getting ahead of myself.

Thanks
Mike

---

### Post by yxlbaz on 2008-01-11
I think that this may be relevant and a bit simpler to analyse.

I have a similar problem.  One ubuntu machine and one XP machine.  Until recently the windows XP network was accessible from the ubuntu system.  This is from the initial default ubuntu installation (7.10).  I can still see the windows network listed.  It's name is "home" and always has been, but clicking this now results in -

Sorry, couldn't display all the contents of "Windows Network: home".

Other network stuff seems OK.  I can ping the windows machine by name and I have set up (as a workaround) a samba share on ubuntu that is accessible from the windows system.  IP addresses reported by ifconfig are OK.

It's as if something has stopped the access specifically to the "windows" network rather than the TCP/IP network failing.

Oh yes - I tried switching the firewall off on XP but no joy there either.

---

### Post by 5circles on 2008-01-11
I can see some of the contents of the network - not the Windows machines, but the Ubuntu system and the Linksys NAS200.  When I click on the Ubuntu system I see the shares, but when I click on the NAS200 I see a similar error message:

The folder contents could not be displayed.
Sorry, couldn't display all the contents of 
'Windows Network: networkstorage'

---

### Post by yxlbaz on 2008-01-12
It begins to look like a Windows/Ubuntu problem I think.  Both take standard updates automatically on my systems so stuff can change without warning.

I suspect Windows, but I'm biased.

---

### Post by 5circles on 2008-01-12
I don't understand the last response.  My Windows systems are all interoperating and can also use Ubuntu.  The problem is from Ubuntu to Windows, so I think the Ubuntu configuration is where the issue lies.

---

### Post by freddyp on 2008-01-12
5circiles -- It looks like I also went into information overload in my post [HERE]("http://ubuntuforums.org/showthread.php?t=665046") and have not had any replies.  What you describe sure sounds familiar.  Are we having the same basic problem?  If so, at least you'll know what I tried....including verifying that the home network and router work fine under a Mint Live CD boot.  Yep, still just confused.:confused:

---

### Post by 5circles on 2008-01-12
Freddyp, thanks for all the useful background on what you've tried.

I'm coming back to some basic questions about my setup, and also wondering like you if it ever worked in the past.

I've hunted for troubleshooting and setup guides, but have come to the conclusion that it is hard to decode what really works.  In part, this is because these guides don't necessarily keep up to date with the changes to the OS and applications (although I'm not even running the latest).  I used to know more about RedHat and Fedora, I think because I spent more time with them.  But all the basics should still apply.

I think I might move to a static IP for the Ubuntu box to head off some other problems, but I want to keep DHCP for the Windows systems.  Unfortunately my router doesn't allow fixed IP addresses to be assigned via DHCP, but as you say the addresses are normally unchanging.  However, I just upgraded the firmware in the router, and noticed all the addresses changed.  As a test, I edited /etc/hosts to include an address for one of the windows boxes.  Lo and behold, that computer is now accessible by name and I can see the shares in Places | Network | Name.

How does Ubuntu determine the IP address if the name isn't in /etc/hosts? Isn't it like this?
[LIST]
[*]Look in /etc/host.conf.  Mine has:
```
# The "order" line is only used by old versions of the C library.
order hosts,bind
multi on
```
What does the note about the "order" line mean?  A Debian Networking guide I looked at implies the order statement means what it says.
[*]look in /etc/hosts
```
127.0.0.1	localhost ubuntubox
127.0.1.1	ubuntubox

192.168.2.102	windowsbox

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```
[*]Look in /etc/resolv.conf
```
nameserver 68.238.128.12
nameserver 68.238.64.12
nameserver 206.26.36.34
```
Mine doesn't have a search line - I presume because I don't have a domain name for this box
[*]Go to the Internet
```
host differentwindowsbox shows:
differentwindowsbox has address 66.150.2.134
differentwindowsbox has address 8.15.7.117
differentwindowsbox has address 66.150.2.134
differentwindowsbox has address 63.251.179.13
host differentwindowsbox not found: 3(NXDOMAIN)
host differentwindowsbox not found: 3(NXDOMAIN)
```


I'm going to go through some of the other steps you mentioned in your other thread, and will respond there.

Mike


[/LIST]

---

### Post by freddyp on 2008-01-12
Mike - I think I might have to move my entire home network to static IP.  But darn, I really do want to keep DHCP if possible.  As a test, I also edited /etc/hosts to include an address for one of the windows boxes, and just like you -- Lo and behold, that computer is now accessible by name and I can see the shares in Places | Network | Name.  So, yes it sounds like we could work around this by going static IP.  I simply do not know how does Ubuntu determines the IP address with DHCP period.

Just FYI --

* My /etc/host.conf looks just like yours
 * My /etc/hosts also looks like your (with appropriate computer names of course)
* And last but not least, my /etc/resolv.conf looks like yours with the name servers from my ISP.  I have tried adding the search using the network manager and it doesn't help the problem.  Just thought I'd confirm my system information so maybe it will help with your other tests.  Thanks for sharing your results so far too!

---

### Post by 5circles on 2008-01-13
Freddy,

I added a domain (the windows workgroup) which updated /etc/resolv.conf.  I wasn't sure how this would be read in, so I restarted (it didn't make any difference before the restart).   After the restart, not only was there no impovement in browsing, it had actually got worse - now I couldn't browse into the workgroup.  Also, the domain line had disappeared from /etc/resolv.conf.  I'm not sure how much was directly due to the changes I made, because some things seem to take a while to stabilize.

Perhaps the static IPs would fix the problem, but like you I'm reluctant to take that approach because of taking a notebook on the road.

Maybe it is necessary to run a local DNS server?

The extra frustrating part about this for me is that I can live without these capabilities (at least temporarily).  But I'm pretty sure I'm not getting closer to getting dokuwiki working over the LAN.

---

### Post by evanchu on 2008-01-13
How does Ubuntu translate hostname into IP address?

If you use ping on Ubuntu, it uses the DNS protocol to translate a hostname to IP address.  Therefore, you need to run a DNS server on your home network and give each machine a DNS hostname.

Now, this is important.  When you assign a name to a Windows machine, you are assigning a ["Netbios" name]("http://en.wikipedia.org/wiki/NetBIOS"), not a DNS hostname.  So ping does not understand the Netbios protocol.  Tools from Samba understand Netbios protocol.  Samba should already be installed, based on your previous description.

I wrote a small [script called Netview]("http://www.evanchu.com/linux2") that you can use to "ping" your Windows machine from a Linux machine with Samba installed.  Try that and report back.

Yes, this is confusing.  But you have to be patient.  I did and I got it working.

---

### Post by 5circles on 2008-01-13
Thanks for sharing netview.  That makes it easier than remembering the syntax for smbclient.

The only windows box that netview shows shares on is the one where I have the IP address in /etc/hosts.  The others go out to the Internet and then time out.  Same thing with the Ubuntu box - I can see shares on localhost, but not its name.

How do I get local DNS running?  I think it is already installed (according to the package manager.)  Is this 'Multicast DNS service discovery" (in Services)?

Where does winbind fit in?  How about nsswitch.conf?

---

### Post by freddyp on 2008-01-13
If I ran the script correctly after downloading (sh netview)...here's what I got in the terminal window.

netview <netbios machine name>

Yes, I can connect to the Windows computers by IP.  Have also confirmed that NetBIOS is enabled over IP on all Windows boxes.  And, I can ping all the boxes by IP but not computer name.

Thanks for the offer to help.  I'll try and respond ASAP but will be on travel this week.

---

### Post by freddyp on 2008-01-13
Ops....didn't see 5circles response.  I'll monitor the thread and watch the progress, not need to try and work this with two people at the same time :)

---

### Post by bradmayne on 2008-01-13
hey I'm having trouble also.  I was able to browse the shares on the vista premium pc on my network as of yesterday something went really wrong and i was unable to connect to the vista pc! I removed samba and everything related to it.  I then tried to download samba and reinstall. the smb.conf was basically blank! ( i went to it from gedit)  Does anyone have any ideas as what went wrong?

---

### Post by evanchu on 2008-01-14
5circles,
Can you post the output of netview when it "goes out to the internet and then times out."  That sounds very strange.

While you are at it, post the output of netview when it succeeds.  So I can compare.

I don't run DNS server on my home network, so I have no experience with it.  If I ever need to run a DNS server, I would check if my home network router (a Linksys) already has a DNS server.

---

