---
title: "[SOLVED] Ping - Unknown Host"
date: 2007-09-29
forum: Networking &amp; Wireless
---

### Post by mlissner on 2007-09-29
Earlier today I switched from AT&T DSL to Comcast broadband. Since then, I've been having an odd problem with my two servers. 

The web server seems to have no problems hosting the website, but the mail server isn't delivering mail, and neither of them can issue a successful ping to an external location. 

If I do ping google.com, I get ping: Unknown host. If I do google's IP, thusly: ping 64.233.187.99, I get this error: connect: Network is unreachable. 

I <i>can</i> ping internally, as in ping 192.168.1.101. 

So I'm confused. My servers seem to be more or less online, yet they can't ping. I tried installing traceroute on the web server, and I couldn't connect to the repo server, so something is wrong there as well.

I've done ```
ifconfig eth0 down && ifconfig eth0 up
``` to no avail. Any other ideas why switching ISPs would cause this problem?

One other detail: my laptop has no issues at all, and it's on the same network. 

Thoughts?

---

### Post by SpiritIsReality on 2007-09-30
howdy
>One other detail: my laptop has no issues at all, and it's on the same network<
<so we know you are runnin' laptop wirelessly to the router, and it has no trouble>
<are you runnin' you're laptop wirelessly? you'd tell me if you thought I was full
of bull wouldn't you? I should certainly hope so>
 <web server and mail server wired. somethin' is takin' down the wired network
interface>
[http://ubuntuforums.org/showthread.php?p=3449703#post3449703](http://ubuntuforums.org/showthread.php?p=3449703#post3449703)
buds

---

### Post by mlissner on 2007-09-30
That's an interesting link, but I don't think the problem matches. My card is actively serving my website as we speak, but incoming traffic isn't getting delivered.

I have connected my laptop with and without a wire to the router, and it works fine in both circumstances. Though I don't think this is a hardware problem (because it was working fine on the same software before the switch from DSL), the card in both servers is this:
```
% lspci -nn | grep -i ethernet
02:04.0 Ethernet controller [0200]: 3Com Corporation 3c905C-TX/TX-M [Tornado] [10b7:9200] (rev 78)

```

Any other ideas?

---

### Post by SpiritIsReality on 2007-09-30
howdy
ok , so your laptop works wired or wireless,
no changes made to the two servers configs
the web server can serve 
wan cannot reach web server

as far as installing packages on the servers , if you get the package from
[http://www.google.ca/search?hl=en&q=packages+ubuntu.com&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=packages+ubuntu.com&btnG=Google+Search&meta=)
packages.ubuntu.com/feisty with your laptop and then transfer them and install
them to your server. I'm pretty sure that if you make a directory(folder) in a 
/home/user_with_sudo_rights and call it say, packages. then can use gdebi to 
install them. or sudo dpkg -i packagename

as far as any ideas about troubleshooting, I'm going to have to try to get them
from others more experienced. google  and manpages to the rescue.
could you help me wade thru this, and by all means try different searches to
try and narrow it down. we'll get ideas what better to search for after hitting
a few of these sites.
[http://www.google.ca/search?hl=en&q=linux+networking+troubleshooting+%28debian+OR+ubuntu%29&btnG=Search&meta=]("http://www.google.ca/search?hl=en&q=linux+networking+troubleshooting+%28debian+OR+ubuntu%29&btnG=Search&meta=")
once on a web page, if it's a long page and have trouble finding a term, I click on edit at the top of firefox, click on find in this page, type term in box at bottom, hit next. watch for message in bottom bar at right, been around once.
we can always try typing in the google box,
site:ubuntuforums.org "error message"
if we can figure out what var/log to look in and what to grep for.

edit: I forgot to mention it might help to ask the new dsl provider for a troubleshoot.

rendezvous here later.
all the best
buds

---

### Post by noob12 on 2007-09-30
Are you configuring these statically or by DHCP?  Have you set the gateway?

Take a look at the output of **route -n**.  Look for a line with UG in the Flags column.  If it is missing try this command to add a gateway and see if things improve.

```

# This assumes your router is at 192.168.1.1
sudo route add default gw 192.168.1.1

```

If that works to give you external access, we need to check why you aren't getting a gateway in your configuration.

---

### Post by mlissner on 2007-09-30
@fmat:
Hmmm...I did some research on this already, and couldn't figure it out. That's why I posted. I'm well aware of the man pages, google and finding things within pages. 

As for the broadband provider, they're useless. I've tried that too. I guess I should reiterate that the problem isn't installing packages (though I appreciate the suggestion), it's that Internet isn't functional.

@noob12:
route -n yielded:```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0

```

So I ran the command you specified, restarted eth0 with ifconfig eth0 down, up, and still no progress. Other thoughts? Do I need to undo the route addition we did there now?

Thanks.

---

### Post by noob12 on 2007-09-30
That command does not install a package; it sets a route.  Try it.

---

### Post by mlissner on 2007-09-30
I did try it! It didn't work! I was askng if we needed to run something to remove the route now that we added it and it still didn't work. 

I am not trying to add packages at all. I was ONLY mentioning it because it seemed like a good example of how incoming traffic isn't functioning.

---

### Post by mlissner on 2007-10-02
I've done some more trial and error tonight. I took the cable from each of the servers, and plugged it into my laptop. Each time it worked, but I had to change my wired connection to "roaming mode," which I don't think I had to do before.

Nevertheless, the Internet should be going into and out of the servers, so that's good. I also learned that somehow when I access my domain while I'm on the same network, DNS is smart enough to make me short circuit the Internet, and just access the server locally (i.e. I just went to 192.168.1.101, instead of the actual location of the server). 

This was also a clue to me to ping my server from a computer that wasn't on teh network, and sure enough, my servers aren't actually working, so no internet in, no internet out. They just aren't working. 

Any ideas why they would both decide to stop working yesterday? Comcast didn't touch them, I promise.

Thanks.

---

### Post by SpiritIsReality on 2007-10-03
howdy
If I read noob12 right, I would,
1.run the sudo route add command.to add a gateway
2.run route -n
3.try pinging router, and try pinging an internet site, or run sudo apt-get update, to see if the internet is reachable., and if it is,
4.run sudo /etc/init.d/networking restart
5.run route -n
6.run sudo apt-get update
7.if internet is unreachable after running sudo route add ...and before restarting networking. ? :-k 
edit : lots of good stuff here [https://help.ubuntu.com/7.04/server/C/](https://help.ubuntu.com/7.04/server/C/)
[http://rute.2038bug.com/node28.html.gz#SECTION002840000000000000000](http://rute.2038bug.com/node28.html.gz#SECTION002840000000000000000) except for
/etc/network/options --> /etc/sysctl.conf  here [http://www.google.com/custom?cx=002165917076592449621%3Ay8jmiivon3o&q=%2Fetc%2Fnetwork%2Foptions&sa=Search&cof=AH%3Aleft%3BCX%3ALinux%2520search%2520Engine%3BDIV%3A%23cccccc%3BFORID%3A1%3BGFNT%3A%23666666%3BL%3Ahttp%3A%2F%2Fwww%2Egoogle%2Ecom%2Fcoop%2Fimages%2Fgoogle_custom_search_sm%2Egif%3BLH%3A55%3BLP%3A1%3B&adkw=AELymgWgVto3CtUEwaZemv2AAQrXTjTcRpIG-k-RU4t-gfF1mh4oQy8BNtHbwb6uGg1-9v-DKnEgQ8Z5t6O1qBoSnEl7YW5XsdrHu4oJ9GfCfkjJgZ1lNRcbOjUByKUbw7YrzMjr4Wo8FAWgo1y7Wx6SH3AQ4YzCb3X9OhRno1DTVfvOHhmBTByjX7wJ75OM88cDbKajmNbOp2s8rYkI3QmHFCkzpT7YWQ&client=pub-7825705102693166&channel=3833691868](http://www.google.com/custom?cx=002165917076592449621%3Ay8jmiivon3o&q=%2Fetc%2Fnetwork%2Foptions&sa=Search&cof=AH%3Aleft%3BCX%3ALinux%2520search%2520Engine%3BDIV%3A%23cccccc%3BFORID%3A1%3BGFNT%3A%23666666%3BL%3Ahttp%3A%2F%2Fwww%2Egoogle%2Ecom%2Fcoop%2Fimages%2Fgoogle_custom_search_sm%2Egif%3BLH%3A55%3BLP%3A1%3B&adkw=AELymgWgVto3CtUEwaZemv2AAQrXTjTcRpIG-k-RU4t-gfF1mh4oQy8BNtHbwb6uGg1-9v-DKnEgQ8Z5t6O1qBoSnEl7YW5XsdrHu4oJ9GfCfkjJgZ1lNRcbOjUByKUbw7YrzMjr4Wo8FAWgo1y7Wx6SH3AQ4YzCb3X9OhRno1DTVfvOHhmBTByjX7wJ75OM88cDbKajmNbOp2s8rYkI3QmHFCkzpT7YWQ&client=pub-7825705102693166&channel=3833691868)

my route -n
Kernel IP routing table
Destination.....Gateway ......Genmask ........Flags .Metric .Ref .....Use ...Iface
192.168.0.0 ....0.0.0.0 ........255.255.255.0 ...U ........0 .......0 ........0 .......eth0
169.254.0.0 ....0.0.0.0 ........255.255.0.0 .......U .....1000 ....0 ........0 .......eth0
 0.0.0.0 ..........192.168.0.1 .. 0.0.0.0 ...............UG .....0 .......0 ........0 .......eth0

more or less a bump 
buds

---

### Post by mlissner on 2007-10-06
I finally figured this out today. It seems I needed to inform the modem of the mac address of one of my computer's NIC via the router. Once that was done, apparently the modem likes the router, and all is good to go.

What a pain!!!

Thanks for all the help.

---

### Post by SpiritIsReality on 2007-10-06
howdy

mlissner ... ftw

buds

---

### Post by SpiritIsReality on 2007-10-06
howdy
If you get a chance I'd sure like to know how it went, but I guess I'll have a tough time following you even if you did post it. back to ch4 at rute for me.
buds

---

### Post by mlissner on 2007-10-06
Essentially, I went to my router config page at 192.168.1.1, went to the page for MAC Address Clone, enabled it, his the "Clone your PC's Mac", and then it worked after that. 

From what I understand, that sends the MAC address of your computer to the router, and from there, to the modem, thus making everything happy. Once this is done, you'd think that the one computer alone would work, but somehow it makes all the computers OK on the network....don't ask me why...

---

### Post by SpiritIsReality on 2007-10-07
howdy
thanks pardner
buds
hay, I suppose you know or don't need me sayin anything about how to keep track of whqt's going on at the forum, heck i barely know, but man was I fortuanate to see some great threads go bny today. I clicked on todays posts at the top of the page, and it was really good.
if you want to catch up on some pretty good in my opinion threads, just go by the titles. have a quick look. advanced search, fmat in the user box. search.
I'll bet RAV TUX would be a great one to use that on, and matthew, and aysiu, and lots of others.

---

