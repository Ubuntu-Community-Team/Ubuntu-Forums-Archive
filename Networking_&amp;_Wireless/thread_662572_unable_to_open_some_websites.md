---
title: "unable to open some websites"
date: 2008-01-09
forum: Networking &amp; Wireless
---

### Post by Dytech on 2008-01-09
Hey everyone,

I got a strange problem, i can't seem to open all websites. most sites work without a problem but soms i just can't reach.

When i ping, dig, or nslookup them i get results but when opening them in firefox it won't work.

On this ubuntu box i also have a virtual machine running windows XP which CAN open those sites.

I found a similar thread on this forum and followed the steps to disable ipv6 

[http://ubuntuforums.org/showthread.php?t=138861](http://ubuntuforums.org/showthread.php?t=138861)


Code:

sudo gedit /etc/modprobe.d/aliases

find the line that reads

Code:

alias net-pf-10 ipv6

and comment it out.

Code:

# alias net-pf-10 ipv6

also, add the following lines (I added mine below the existing entry which you just commented out)

Code:

alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ipv6 off

Reboot your box after making this change.

Check your firefox config, too, & disable IPv6

1. In Firefox, type about:config in the address bar and click Go.
2. Type ipv6 in the Filter box. This should show you the config option, "network.dns.disableIPv6".
3. Double-click network.dns.disableIPv6 to change it from false to true.


But this did not do the trick for me :(

Is there a way i can check ipv6 is really disabled, and maybe someone has got another idea how to solve this??


Thank you very much!!

---

### Post by Vixis on 2008-01-09
install firefox addon [User Agent Switcher]("http://addons.mozilla.org/en-US/firefox/addon/59") and choose IE, it may help for some sites.

---

### Post by SeanHodges on 2008-01-09
Can you provide some example URL's that you can't visit?

Personally I've had no trouble browsing the Web with IPv6 left on, I dont think you should be finding multiple websites inaccessible just because of IPv6.

---

### Post by Dytech on 2008-01-09
by example nvidia.com / hi.nl  / macromedia.com i can't visit.

strange enough i do see the title of the site in the title bar.

---

### Post by SeanHodges on 2008-01-09
Interestingly, all 3 of your examples contain Flash content.

Have you installed a Flash player at this point? and if so, is it the Adobe one or Gnash?

Could you also confirm if there are any sites containing Flash content that you ARE able to visit? I suspect this might be the source of your problems...

---

### Post by Dytech on 2008-01-09
That's not the problem, i got the adobe one.

But also installed opera and that's the same problem. I can see there that 45% of nvidia.com can be loaded.

[www.menaddwork.nl](www.menaddwork.nl) also contains flash and i can open that without a problem.

i'm really curious what this problem could be.

---

### Post by SeanHodges on 2008-01-09
Can you try just downloading the homepage using wget, if this fails we'll know the problem is network-related:

```
wget www.nvidia.com
```

You should end up with home.html in your working directory, if it was successful.

If this succeeds, I think the problem is likely to be some component failing to load correctly, and causing the browser to stop rendering the page.

Just to rule out Flash completely, could you install the "Stop Autoplay" extension in Firefox [https://addons.mozilla.org/en-US/firefox/addon/1765]("https://addons.mozilla.org/en-US/firefox/addon/1765"), then restart Firefox, and try visiting the offending sites again?

---

### Post by cubicsilver on 2008-01-14
There is a bug in the newest kernel that stops websites from loading

try this:

edit the sysctrl.conf

```
sudo gedit /etc/sysctrl.conf

```
add these lines and save:

```
net.ipv4.tcp_wmem = 4096 16384 131072
net.ipv4.tcp_rmem = 4096 87380 174760

```
make the changes by typing in

```
sudo sysctrl -p
```

your website should work now.

---

### Post by Dytech on 2008-01-14
Whoaw it worked!

Thank you very much!

I just typed it in, but i really didn't have the slightest clue of what i was doing :)

What did i just do? And why did i have to do this? I couldn't imagine all ubuntu users have to do this right?

Anyway Thanks a million!

---

### Post by cubicsilver on 2008-01-16
It only seems to affect some people behind certain routers.  Glad it worked for you.  :grin:

---

### Post by nightwolf2k5 on 2008-07-12
Hi guys.
I have the same problem. But when i follow all the instructions and type

```
sudo sysctrl -p
```, 

i get the following message

```
sudo: sysctrl: command not found
```,

what do i do?

---

### Post by Dytech on 2008-07-12
try sysctl ;-)

---

