---
title: "Ubuntu 8.04 REALLY slow internet"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by Xeeon on 2008-05-02
I just recently installed Ubuntu 8.04, to try out the new one, and amazingly enough (for my computer) it worked. I usually have a hard time getting Ubuntu (much less any linux distro) to install on my computer.

Even more to my surprise, my wireless adapter worked to boot! so after confirming it worked by going to google, I noticed that it took about a minute and a half to load the google home page. I thought to myself "something is not right here."

So I looked in the forums here and saw that I had to disable IPv6, and did, and copy/pasted some extra stuff to a couple of .conf files, rebooted (to be safe), and there was no difference.

I booted back to Windows to see if my internet was acting up, and no, it is fine..

I've never really had this problem until Ubuntu 7.10, and that's why I just stuck with Windows, because I couldn't find a solution.

Synaptics run terribly slow too, so I know it's not Firefox.

Would anyone give any advice, so that I can enjoy Ubuntu?

---

### Post by superprash2003 on 2008-05-02
you could try changing your DNS servers to opendns [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by Xeeon on 2008-05-02
all right I'll give that a try and get back with the results

---

### Post by Xeeon on 2008-05-02
I did what it said to do in the guide there, and it made very very little difference.

are there any other alternatives to fixing this?

---

### Post by Xeeon on 2008-05-03
Would anyone else be able to give some advice to fix this? I'd love to use Ubuntu again..

---

### Post by eighto2 on 2008-05-03
I'm experiencing terribly slow internet as well... I'm not sure whats causing it myself

---

### Post by keforex on 2008-05-07
Same here. Before upgrading to 8.04 it was super fast. I have a dual boot x64 with Vista and it's lightning fast there... (in Vista)

---

### Post by abh83 on 2008-05-07
I had the exact same issue in 7.10 and now 8.04. I solved the issue simply by installing WICD insteasd of the default network-manager.

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

[COLOR="Red"]note. this will deinstall network-manager automatically.[/COLOR]

let me know if this helps!

---

### Post by keforex on 2008-05-07
It didn't work for me. I browse fine but all downloads, including package updates, are very slow - dial up is faster :(

---

### Post by Xeeon on 2008-05-07
WICD won't affect my wireless cards, will it?

---

### Post by stinger30au on 2008-05-08
are you using firefox 2 or 3???

if i use firefox 3 i get all sorts of headaches including very slow web browsing.

dump it and install FF2 it is in the repos

---

### Post by Xeeon on 2008-05-08
Yeah... I've pretty much answered my question..

I installed it properly, made the tray icon appear at startup, and it won't even connect now...

---

### Post by Xeeon on 2008-05-08
> **stinger30au said:**
> are you using firefox 2 or 3???

if i use firefox 3 i get all sorts of headaches including very slow web browsing.

dump it and install FF2 it is in the repos
See, it's not Firefox... even synaptics are terribly slow..

---

### Post by abh83 on 2008-05-08
> **Xeeon said:**
> WICD won't affect my wireless cards, will it?


nope not that i'm aware of. I've installed it several times under 7.10 and 8.04 and it never affected my wireless card. As in no damages was done to it. It did however solve all my network issues. :)

WICD is a network manager just like the default gnome-network manager. Its a simple, lightweight and very user friendly network manager.

One thing I really like about it is that you can actually assign your default network manually so it will never randomly connect to other networks in the neighborhood. Another silly problem that I was having with nm.

---

### Post by Xeeon on 2008-05-08
> **abh83 said:**
> nope not that i'm aware of. I've installed it several times under 7.10 and 8.04 and it never affected my wireless card. As in no damages was done to it. It did however solve all my network issues. :)

WICD is a network manager just like the default gnome-network manager. Its a simple, lightweight and very user friendly network manager.

One thing I really like about it is that you can actually assign your default network manually so it will never randomly connect to other networks in the neighborhood. Another silly problem that I was having with nm.
Yes, but when I installed it, I couldn't connect at all :(

and I use 2 Wireless cards

---

### Post by abh83 on 2008-05-08
Interesting... what wirelss cards do u use anyway? Did u check to see if they are even compatible with ubunutu? did u try disabling/removing one of the cards? They could be conflicting with one another?

If you want to deinstall wicd and re-enable nm there are very clear and simple instructions in the FAQ section on the WICD site.

It seems like no one really knows what's causing this issue. Like I said I first noticed it on 7.10 and now 8.04.

Btw. I just remembered... if you are behind a router you could try to assign a new (internal) ip address to your computer. I can't explain it but a lot of my networking issues were solved by simply ditching the old ip address and assigning a new one.

---

### Post by Xeeon on 2008-05-08
I have a Linksys WUSB54G wireless card, and a Belkin N1 Network Adapter...

I've tried switching the wireless cards out, blah blah blah...

I already reinstalled NM, so it's still going slow, but at least I can connect.

I know for sure that my WUSB54G is compatible with Ubuntu, because I used it with Feisty and it worked fine and fast.

But the reason I don't go back to Feisty is because I had a REALLY hard time installing it..

it doesn't seem like IPv6 is the main problem, because if IPv6 was enabled, wouldn't IPv4 be enabled as well? ...Sort of as a backup just in case IPv6 doesn't work?

---

### Post by NW2190 on 2008-05-10
My internet connection is extremely slow too.  It seems to get stuck at "loading www.example.com..." even if I switch to OpenDNS.  My windows computers on the same network have no problems at all though...

---

### Post by Xeeon on 2008-05-15
has anyone found a way to solve this common problem?

---

### Post by alan.m.howard on 2008-05-17
Try running iwconfig in a terminal and see what the bit rate is set to. For some reason mine changed from 54 Mb/s to 1 Mb/s on my wireless card after upgrading to 8.04. Setting it back fixed things:

sudo iwconfig wlan0 rate 54M

where wlan0 is the name of the network interface.

If this turns out to be the problem you can get it to perform this step automatically by putting:

pre-up iwconfig wlan0 rate 54M

into /etc/network/interfaces.

---

### Post by Warmask on 2008-05-18
> **alan.m.howard said:**
> Try running iwconfig in a terminal and see what the bit rate is set to. For some reason mine changed from 54 Mb/s to 1 Mb/s on my wireless card after upgrading to 8.04. Setting it back fixed things:

sudo iwconfig wlan0 rate 54M

where wlan0 is the name of the network interface.

If this turns out to be the problem you can get it to perform this step automatically by putting:

pre-up iwconfig wlan0 rate 54M

into /etc/network/interfaces.

Thank you, I saw this suggestion on another forum as well and it fixed my problem.

---

### Post by age6racer on 2008-05-20
I have been using this work around for a few days and although it does speed things up my internet is still very slow (max speeds of about 35 KB/s. Usually i can get 700-800 KB/s)

There must be a proper solution to this.

---

### Post by Warmask on 2008-05-20
I may be noticing the same thing, but i'll need to do some more experimenting. My results from [www.speedtest.net](www.speedtest.net) are on par with the results i receive from a windows os (about 1250kb/s). But while downloading a torrent with lots of seeds, I was only able to download at 50kB/s.

---

### Post by Xeeon on 2008-05-21
> **alan.m.howard said:**
> Try running iwconfig in a terminal and see what the bit rate is set to. For some reason mine changed from 54 Mb/s to 1 Mb/s on my wireless card after upgrading to 8.04. Setting it back fixed things:

sudo iwconfig wlan0 rate 54M

where wlan0 is the name of the network interface.

If this turns out to be the problem you can get it to perform this step automatically by putting:

pre-up iwconfig wlan0 rate 54M

into /etc/network/interfaces.
this worked to speed up my internet, but my internet usually goes about 500-800 kB/s now it's going 30-100kB/s instead of 1-20kB/s..

we need a real solution. Actually this shouldn't happen in the first place

---

### Post by Kingsfan on 2008-05-25
my internet is also slow, but from a wired connection. it looks like everybody else is having wireless problems.

---

### Post by murph9300 on 2008-05-27
> **Kingsfan said:**
> my internet is also slow, but from a wired connection. it looks like everybody else is having wireless problems.
Agreed -- most of the issues and fixes are for wireless issues -- my wired internet connection is a problem.

---

### Post by tirithen on 2008-06-10
I had this problem before, found some forumpost that made me able to fix this (which have forgotten :-( ), and when I upgraded my hardy-dist yesterday it seem to have overwritten the things I had changed because now I have this same problem again, I now have a max speed at ~20KB/s...

---

### Post by Th3sandm4n on 2008-06-10
Ya I came home from work last night and everything is slow now. I had run 8.04 okay with no problems on internet speeds, but now everything is taking forever to load, if at all.
It seems like I can catch the page if I keep reloading, but that's pretty annoying, and it never fully loads.
> frank@franks-Laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"Omega"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1E:2A:10:65:22   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=91/100  Signal level=-37 dBm  Noise level=-89 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


EDIT:
Yeah I have a feeling it was just a bad few hours, works nice and fast at school. Or maybe some bad router settings. Oh well.

---

### Post by kbeeveer46 on 2008-06-14
I am having this same exact issue and when you search Google for it you'll find hundreds upon hundreds of people having the same issue.

It's not a browser problem. When the internet is really slow it's really slow for every application that uses it.

I've tried disabling the IPv6 settings in about:config and also tried [this]("http://www.howtogeek.com/forum/topic/extremely-slow-internet-in-ubuntu-804")

It seems to go in and out. It will be fine for a while and then get bad and then back to good again. I'd be the first one to blame it on Comcast but like other people have said, it seems to be okay in Windows etc.

---

### Post by kbeeveer46 on 2008-06-14
Okay, I may have fixed my problem but I won't find out for sure until I surf the net for a few hours to see if it comes back.

1. Left click on the network configuration icon in the tray
2. Click on **manual configuration** 
3. Click the **unlock** button and enter password
4. Select **Wired connection** and click on **Properties**
5. Uncheck **Enable roaming mode** and select **Automatic Configuration** from the drop down list.

---

### Post by epidemiks on 2008-08-16
> **kbeeveer46 said:**
> s it.

I've tried disabling the IPv6 settings in about:config and also tried [this]("http://www.howtogeek.com/forum/topic/extremely-slow-internet-in-ubuntu-804")


That worked a charm for me, immediately!! Cheers

[http://www.howtogeek.com/forum/topic/extremely-slow-internet-in-ubuntu-804](http://www.howtogeek.com/forum/topic/extremely-slow-internet-in-ubuntu-804)

---

### Post by epidemiks on 2008-08-19
> **epidemiks said:**
> That worked a charm for me, immediately!! Cheers

[http://www.howtogeek.com/forum/topic/extremely-slow-internet-in-ubuntu-804](http://www.howtogeek.com/forum/topic/extremely-slow-internet-in-ubuntu-804)

well actually, now that I've booted back to XP (first time in a while), the speed increase was pretty minimal.
FF in XP is like a rocketship compared to ubuntu, and XP's about:config is just default.

Downloading is the same, and speedtests on both are pretty much identical, its just browsing is killing me.. especially php/forums/any gnome-art etc sites
What else might be slowing things down?

---

### Post by Skofo on 2008-08-20
Sorry if this is too late, but after trying to get my WUSB54Gv4 to work for months I found out that there's a specialized driver for 64-bit systems. Try this in ndiswrapper. [http://www.savefile.com/files/246027](http://www.savefile.com/files/246027)

---

### Post by R1G0RM0RT15 on 2008-10-12
This is the first time Ive used an operating system that wasn't windows and i must say im glad I finally did. Except the whole reason I wanted a dual boot sytem with windows and ubuntu was for safer torrent downloading but instead the fastest connection ive gotten using any torrent manager was 40kibs, Vs. up to 300+kib downloads with windows bit torrent. It also streams videos slower and takes a little longer to access webpages but not much. On top of that I was losing my wireless connection, every 10 minutes and had to reboot ubuntu to get it back. I am using a NetgearWG111v2 wireless adapter. The good thing was all I had to do was plug it in. Anyways I changed my connection manager to Wicd Manager which replaces the one that comes with Ubuntu 8.04 and that fixed my connections being dropped and the connection strength stays between 80 and 90 percent now but overall speed hasn't changed at all =(

---

### Post by albesan on 2008-10-15
> **epidemiks said:**
> That worked a charm for me, immediately!! Cheers

[http://www.howtogeek.com/forum/topic/extremely-slow-internet-in-ubuntu-804](http://www.howtogeek.com/forum/topic/extremely-slow-internet-in-ubuntu-804)


hey, great that it worked.
Can you or anybody post what this how to was about?
I can't load that page.

---

