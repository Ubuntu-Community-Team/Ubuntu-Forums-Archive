---
title: "Webpages not opening"
date: 2010-10-03
forum: New to Ubuntu
---

### Post by Bakkies on 2010-10-03
I have installed Ubuntu 10.04 (partition) but for some reason only some webpages open completely, some pages will hang with a blank page whilst the browser (firefox) only says: looking up [www.google-analytics.com]("http://www.google-analytics.com")... or l.yimg.com.... never opening the page. Other pages will only open half way also showing looking up [www.google]("http://www.google") -analytics.com... or l.yimg.com... Checked my network configuration everything looks fine. I have a wired (Lan) connection. Iam new to Linux and therefore very interested in trying it out. Thanks in advance

---

### Post by PapaNerd on 2010-10-03
You may have to lower your Firefox browser security levels (enabling scripting and/or permitting cookies, for example) to see more pages.  Many website developers sacrifice security to enable whiz-bang web page features.

---

### Post by Bakkies on 2010-10-05
Still the same thing. Pages like Yahoo, Youtube and MSN won´t open. I can´t even download Adobe flash or Java from their websites

---

### Post by Sumit Bisht on 2010-10-05
Have you tried the same in other OSs ?
Also, try disabling javascript (but it'll make various sites unusable)
Have you tried hitting the escape while this is happening ?
If nothing still appears, try working offline File > Work Offline (But you'll have to again work online afterwards :)
Try installing jre, flash player from the Add/Remove programs control or their websites

---

### Post by cariboo on 2010-10-05
Check to make sure you don't have a DNS problem. Open a terminal and type:

```
ping www.google.com
```

if that doesn't work try pinging by number:

```
ping 74.125.155.106 
```

If pinging by number works, but by name doesn't, then you have a DNS problem.

---

### Post by Bakkies on 2010-10-05
I installed Ubuntu 10.10 as a virtual machine but the same problem, my host os´s internet is working fine. Sumith Bisht: Disabling java script doesnt help. Pressing escape just stops the browser. I installed jre and flash player via Software centre but the problem persists.
Cariboo907: Pinging the address and the number worked, so I don´t think it´s a DNS problem. Please keep trying guys I think Ubuntu is GREAT!!

---

### Post by PapaNerd on 2010-10-05
If would help greatly if you could post some examples of web pages that work for you and do not work (and either describe what you see or post a screen shot of the broken ones).

---

### Post by Bakkies on 2010-10-06
For some reason I don't know what but all pages are opening fine. Can it be that I didn't reboot after installing jre and flash layer??? Thanks allot guys for your help

---

### Post by PapaNerd on 2010-10-06
Happy to hear things are working for you.

Generally, rebooting is a Windoze "feature".  In Linux, you can usually just re-start a process and/or application after an upgrade.  Rebooting certainly accomplishes that as well.

---

### Post by Bakkies on 2010-10-09
I have installed Ubuntu 10.10 beta as a partition and the problem is back, I tried everything in the previous posts but nothing works. Here are a few screenshots. You can see that some pages won´t open at all and some open but keep saying looking up with some web adress. Google search works fine.

---

### Post by GabrielYYZ on 2010-10-09
if your network monitor thingy is network manager, you should see if your resolv.conf file lists your DNS server(s)

type

```
sudo gedit /etc/resolv.conf
```on a terminal and check to see if they're there. if they're not, i suggest you uninstall network manager and get WICD network manager. i sort of had the same problem as you and i had to do quite a bit of tweaking around to get it fixed.

---

### Post by Sumit Bisht on 2010-10-18
Hi Bakkies!
I think there is some problem with your ISP. Have you tried setting up a proxy server on firefox ?
Also, on virtualbox, is google.com loading fine?

IMO, try using a proxy server or onion tor network for access. If it is possible for you, please try using some other ISP on the same machine/VM.

---

