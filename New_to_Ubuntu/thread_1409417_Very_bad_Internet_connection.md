---
title: "Very bad Internet connection"
date: 2010-02-17
forum: New to Ubuntu
---

### Post by vasiauvi on 2010-02-17
Hello all,
Until couple of days before my internet was great on Ubuntu but now I really don't understand why the connection si very very bad. To open [www.google.com](www.google.com) it's takes arround 60 seconds. I use Firefox 3.6 but the same thing is happening also in Opera. In Google Chrome no pages are loading...
I've enterred in firefox -safe-mode and the same thing!

After doing this tutorial regardin [Pulse Audio]("http://ubuntuforums.org/showthread.php?t=789578") the internet is worst...I know, it's not relevant and doesn't have any connection (also that tutorial mest up other things for me) but maybe is related....I really don't know!

Ah...I'll allmost forgot that I have a router and a PC with WindowsXP. On Windows the internet is much much better.

I use Karmic Koala!

How ca I find out if something is wrong on my system?
Thanks!

---

### Post by QIII on 2010-02-17
Are you running your connection from your Ubuntu machine directly to your router, or are you using Microsoft ICS?

That is, do you have Ubuntu set up for direct connection or through ICS?

---

### Post by 2hot6ft2 on 2010-02-17
Try these together they made a big difference for me just select your wireless connection in the first one instead of wired.
> **Fire_Chief said:**
> Here is a site that shows where to configure static DNS in wicd.
[http://wicd.net/screenshot.php]("http://wicd.net/screenshot.php")

I think you'd do well with either option (per connection/network configuration or global DNS servers setup).

Cheers!
and in this one I didn't disable IPV6 since the IPV6 DNS servers were added in the first one.
> **uboss said:**
> I was having the same problem so this is what I did just now and it really improved my speed. (Keep note of what you do in case you need to go back)

1. Type about:config in the address bar and press Enter
2. Then right click on the preferences table and select New->Integer
3. Type preference name as: **Network.dnsCacheExpiration** and Integer value **3600** (This will increase the DNS expiration cache time to 1 hour---you may decide the time you want)
4. Right click on the preferences table and select New.>Integer
5. Type preference name as: **network.dnsCacheEntries** and set its value between **100 to 1000** (By Default firefox has 20 entries I set mine at 400)
6. Type in the search and find each of the following and set their values as indicated below (Toggle will change the value like from false to true)

[B]network.prefetch-next  = true
network.http.pipelining  = true
network.http.pipelining.maxrequests  = 8
network.http.proxy.pipelining  = true
network.dns.disableIPv6  = true[/B]

7. Also right click and add another:  preference name as: **nglayout.initialpaint.delay** and set its value to **0**.

8. Plus I added the OpenDNS just as this thread mentions. 


Close the browser and restart. You are done.
I hope this helps
From this thread
[FireFox Slow in 9.10 Koala]("http://ubuntuforums.org/showthread.php?t=1310366")

---

### Post by vasiauvi on 2010-02-17
> **QIII said:**
> Are you running your connection from your Ubuntu machine directly to your router, or are you using Microsoft ICS?

That is, do you have Ubuntu set up for direct connection or through ICS?

Hello,
I am using Ubuntu directly to my router.

@2hot6ft2
I had all that options allready configured like you said. The thing is that the Internet worked very well but now is bad.

---

### Post by 2hot6ft2 on 2010-02-17
Seems to come and go for me, sometimes it will be fast and other times it will be slow. Hope it gets fixed soon.

---

### Post by vasiauvi on 2010-02-17
> **2hot6ft2 said:**
> Seems to come and go for me, sometimes it will be fast and other times it will be slow. Hope it gets fixed soon.

Yes, maybe it will be much faster after I will upgrade :), until then I will stay like this or maybe something miracoulos will happen and everything will be like before.
Ubuntu in a lot of things is a big question mark.But doesn't matter. :)

Thanks for your help!

---

### Post by 2hot6ft2 on 2010-02-17
> **vasiauvi said:**
> Yes, maybe it will be much faster after I will upgrade :), until then I will stay like this or maybe something miracoulos will happen and everything will be like before.
Ubuntu in a lot of things is a big question mark.But doesn't matter. :)

Thanks for your help!
You're welcome. Last night I upgraded network-manager from the PPA to see if it would help to stop the disconnects and it's looking good 8 hours so far without a single one. So it may help.
I got it by adding the karmic PPA from here:
[Karmic network-manager PPA]("https://launchpad.net/~network-manager/+archive/trunk/")

These are bleeding edge with the very latest bug fixes so do so at your own risk!!!
If you want to give it a try you can do it like this in a terminal
```
gksu gedit /etc/apt/sources.list
```
Add these 2 lines to the bottom
> deb [http://ppa.launchpad.net/network-manager/trunk/ubuntu](http://ppa.launchpad.net/network-manager/trunk/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/network-manager/trunk/ubuntu](http://ppa.launchpad.net/network-manager/trunk/ubuntu) karmic main
Save and close it then use this to add the key (shouldn't really need sudo in the rest but I included it just in case you take more than 15 minutes to complete it all).
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BC8EBFE8
```
Then update apt
```
sudo apt-get update
```
Install the new network manager
Here you have some choices

If you just want to **just update network manager** use this first one (this is what I used)
```
sudo apt-get upgrade network-manager network-manager-gnome
```
If you're using **pptp** use this to update it as well otherwise it's not needed.
```
sudo apt-get upgrade network-manager network-manager-gnome network-manager-pptp-gnome
```
If you're using **VPN** use this to update it as well otherwise it's not needed.
```
sudo apt-get upgrade network-manager network-manager-gnome  network-manager-vpnc-gnome
```
If you want to **update it all** use this one
```
sudo apt-get upgrade network-manager network-manager-gnome network-manager-pptp-gnome network-manager-vpnc-gnome
```
To undo it the lines added earlier would have to be removed or commented out.
Apt would have to be updated again.
And apt-get reinstall would have to be used to revert back to the previous version. May even need to use a wired connection to do it.

---

### Post by vasiauvi on 2010-03-20
2hot6ft2 thanks for the reply,
I've tried also your sugestion but is the same.
The idea is that I have a router and 2 computers connected to it: PC with WindowsXP and a laptop with dual boot WinXP and Ubuntu.
The internet on PC is great and also the system itself is more stable than on my Ubuntu. Also the dual boot WindowsXP is more stable and not such a RAM eater (I tought that Linux is using less resources but...) and also the internet is working GREAT.

In the dual boot Ubuntu the internet is crap (very very bad). I wait 2 minutes to load [www.google.com](www.google.com) :) Nice! Also the system it self is not light, Firefox is consuming in Linux more RAM than in WindowsXP. I really don't know why!

Can anyone help me to troubleshoot the internet connection?
I have Ubuntu 9.10. I've installed wicd, upgraded the network manager. The internet is not working good in Firefox, Google Chrome and also Opera....

Thank you!

---

### Post by vasiauvi on 2010-03-20
Anyone?

---

