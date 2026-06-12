---
title: "Websites don't display properly, if at all"
date: 2010-03-01
forum: New to Ubuntu
---

### Post by doctorbighands on 2010-03-01
Hi there,

My wife and I just moved. At our new house, we're having problems with websites either not rendering properly, or some not even able to connect at all. Some sites connect and display just fine, and I can't find any pattern between the sites that display and the ones that won't. For example: google.com gives me a "server not found" error, facebook.com and yahoo.com display as plain text only, but this site is working fine.

Another example of the weirdness: Earlier today, I could navigate to bing.com and it displayed properly. Now, I get a "server not found" error.

To make matters worse, when I boot my machine into Windows, there are no problems at all with browsing the web. The same is true for my wife's machine: Problems in Ubuntu, no problems in Windows.

I tried disconnecting and reconnecting to the wireless network, I tried closing and restarting Firefox, I tried using another browser (Opera), and I tried rebooting the machine, and nothing has helped. This one has me totally stumped!

Any help is appreciated! Thank you!

EDIT: I am connected to a WEP-encrypted wireless network. I am not behind any firewall or proxy. If there's any other information I can provide that might help troubleshoot, please let me know.

EDIT 2: I should mention that when we first connected to the network yesterday, we were having no problems. We both began experiencing problems just today. Nothing, as far as I know, has changed between then and now.

---

### Post by doctorbighands on 2010-03-01
bump

---

### Post by sandyd on 2010-03-01
> **doctorbighands said:**
> Hi there,

My wife and I just moved. At our new house, we're having problems with websites either not rendering properly, or some not even able to connect at all. Some sites connect and display just fine, and I can't find any pattern between the sites that display and the ones that won't. For example: google.com gives me a "server not found" error, facebook.com and yahoo.com display as plain text only, but this site is working fine.

Another example of the weirdness: Earlier today, I could navigate to bing.com and it displayed properly. Now, I get a "server not found" error.

To make matters worse, when I boot my machine into Windows, there are no problems at all with browsing the web. The same is true for my wife's machine: Problems in Ubuntu, no problems in Windows.

I tried disconnecting and reconnecting to the wireless network, I tried closing and restarting Firefox, I tried using another browser (Opera), and I tried rebooting the machine, and nothing has helped. This one has me totally stumped!

Any help is appreciated! Thank you!

[B]EDIT: I am connected to a WEP-encrypted wireless network. I am not behind any firewall or proxy. If there's any other information I can provide that might help troubleshoot, please let me know.
[/B]
EDIT 2: I should mention that when we first connected to the network yesterday, we were having no problems. We both began experiencing problems just today. Nothing, as far as I know, has changed between then and now.
how far aways the router?

any metalic objects in between?

---

### Post by doctorbighands on 2010-03-02
The router is on the floor above me - I'm directly beneath it. There are no metallic objects between it and my computer.

Plus, remember: Whatever is happening is only affecting Ubuntu, not Windows. An obstruction between router and PC would affect both.

---

### Post by doctorbighands on 2010-03-02
Update: Today, I can now connect to google sites, but facebook (and other sites) still won't render properly.

This is really weird.

---

### Post by doctorbighands on 2010-03-02
bump

I just confirmed this problem on a third Ubuntu machine. Does anyone have any ideas?

---

### Post by Arijit_Kundu on 2010-03-02
do you know what network card you are using? it may be a problem with the driver. Run 'iwconfig' (without quotes) in a terminal (accessories > terminal), and post the output

---

### Post by doctorbighands on 2010-03-02
> **Arijit_Kundu said:**
> do you know what network card you are using? it may be a problem with the driver. Run 'iwconfig' (without quotes) in a terminal (accessories > terminal), and post the output

I don't recall the exact model of WiFi card I'm using in this machine, but it's an Intel card.

Here is the output of iwconfig:
```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"Strauser Household"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1E:E5:33:B2:1B   
          Bit Rate:36 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=72/100  Signal level=-56 dBm  Noise level=-92 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:4

```

---

### Post by doctorbighands on 2010-03-02
I just swapped out the router with a newer, better one, and the problem still isn't solved.

---

### Post by asmoore82 on 2010-03-02
I would try manually setting the Channel on the router to something odd like 3 or 9.

The seem to always "auto-select" 6 or 11.

Maybe there is an interference filter in the Windows driver that's not in the Linux driver yet:confused:

I have Intel wireless on this laptop and am running the Ubuntu 10.04 Alpha.
I noticed on it that my Wifi used to be eth1 or ath1, but now its wlan0:
```
**$** iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"reidsvillecs"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:11:95:4D:8A:BB   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-38 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by doctorbighands on 2010-03-05
This problem is continuing, and it's getting frustrating.

Today, I have no access to search engines (no Google, Yahoo, Ask, or Bing), facebook still renders as text-only, and no access to eBay.

However, I discovered that I CAN access my Gmail via a POP3 app like Thunderbird. No http access to anything within the Google domain, but POP3 is fine.

What is going on here?

EDIT: Just to be sure, I contacted my ISP to ask if they had any idea why this might be happening. The guy I talked to had no idea, and said as far as the ISP is concerned, there's no reason for this. They do block incoming access to open ports, which makes me furious, but that's another issue entirely...

---

### Post by PRC09 on 2010-03-06
Have you tried connecting via cable.Just thinking here and trying to find what all your machines have in common,apart the fact that they all have the same problem, could it have been a buggy update or something.If they still cant render the pages properly when cabled in then it might not be your wireless at all...Just a thought......

---

### Post by doctorbighands on 2010-03-06
> **PRC09 said:**
> Have you tried connecting via cable.Just thinking here and trying to find what all your machines have in common,apart the fact that they all have the same problem, could it have been a buggy update or something.If they still cant render the pages properly when cabled in then it might not be your wireless at all...Just a thought......

As far as I know, the only thing these three machines have in common is the fact that they're running Ubuntu. One is a laptop, one is a netbook, and one is a desktop. They're all running different kernel versions. 

I tried plugging the netbook into the connection directly, bypassing the router, and nothing changed. I didn't think it would make a difference, because the problem is the same on three different machines with three different wireless adapters, and I've tried connecting through two different routers. It was a good thought, though...

Any other ideas?

---

### Post by PRC09 on 2010-03-06
The pages you mentioned I think all use Flash pretty heavily so maybe it could be that.I have Adblock Plus installed and it plays havoc with some web pages and I have to disable it to view them.Also Flashblock and No Script will do the same.To Test the flash version here is the link....

[http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/)

May as well try which java version as well....

[http://www.javatester.org/](http://www.javatester.org/)

Hope this will help.....

---

### Post by PRC09 on 2010-03-06
Just something to try is go directly to the following link(Google.com.)

[http://74.125.53.99/](http://74.125.53.99/)

For Bing.com

[http://64.4.8.147/](http://64.4.8.147/)

For Facebook....

[http://69.63.181.12/](http://69.63.181.12/)

See if you can connect and render properly....

---

### Post by RedRat on 2010-03-06
What you may want to try is uninstalling Firefox completely. This also means going into your home directory and turning on "Show Hidden Files". Find \.mozilla (noted the dot in front of mozilla. Merely rename the file to something like .mozillax or xmozilla. This way you preserve you profile. Now go and reinstall Firefox. Oh, yeah, remember to say your bookmarks. I had a similar problem and I am directly wired to my modem.

---

### Post by objem on 2010-03-06
I am having exactly the same problem. Also with an intel wireless card. Wireless works sometimes but not others and refuses to connect to sites such as even google and facebook.

It must be a recent update as it was fine about a week ago. Maybe the new kernel?

I know it is not hardware related because if I boot into windows the wireless is very snappy.

---

### Post by objem on 2010-03-06
Tried different kernels. That did not help. 

In the logs there are many repeats of wpa_supplicant: CTRL-EVENT-SCAN-RESULTS.

I think its a new bug in some update related to wpa_supplicant. Problem is recent for me.

---

### Post by doctorbighands on 2010-03-07
> **objem said:**
> Tried different kernels. That did not help. 

In the logs there are many repeats of wpa_supplicant: CTRL-EVENT-SCAN-RESULTS.

I think its a new bug in some update related to wpa_supplicant. Problem is recent for me.

So, to test this theory, is there a way I can revert to a previous version of wpa_supplicant? I'm pretty sure I can't just remove it altogether.

As for uninstalling Firefox: I've tried using two other browsers (Opera and Chrome), and I get the same problems with all of them.

It's comforting to know that I'm not the only one having this problem, btw. At least I know it isn't limited to my computer or connection.

---

### Post by steindor2 on 2010-03-07
EDIT: nervermind

---

### Post by PRC09 on 2010-03-08
I just re-read your post and if the problem exists while cabled in then I dont think the wpa problem would affect how your web pages load as wpa only applies to wireless and not a cabled in connection....In my previous posts were direct links to those pages you had mentioned.If you could connect directly to those links and they rendered properly it could mean that your ISP is having dns server problems.Also is there any chance that your modems/routers is still trying to use your old ISP DNS settings......

---

### Post by doctorbighands on 2010-03-08
> **PRC09 said:**
> I just re-read your post and if the problem exists while cabled in then I dont think the wpa problem would affect how your web pages load as wpa only applies to wireless and not a cabled in connection....In my previous posts were direct links to those pages you had mentioned.If you could connect directly to those links and they rendered properly it could mean that your ISP is having dns server problems.Also is there any chance that your modems/routers is still trying to use your old ISP DNS settings......

That makes sense about wpa_supplicant. One more thing ruled out...

I feel that if my ISP was having DNS issues, it would affect me no matter what OS I booted. Same thing if my router was using old DNS settings from my previous ISP (which it isn't - I checked :) )

Just to be sure, though, I went ahead and used your direct links, and sure enough, still a problem.

Thank you for the ideas, though!

Still hoping someone can save me...

---

### Post by PRC09 on 2010-03-08
I am at a loss as to what the difference between Ubuntu and windows connecting and displaying could be.Maybe try the latest Live cd of Mint or Super OS (they have Flash and Java on the Live cd) and see if the problem still exists.Maybe its something that was configured specifically for your previous isp....I am just guessing again........

---

### Post by doctorbighands on 2010-03-09
> **PRC09 said:**
> I am at a loss as to what the difference between Ubuntu and windows connecting and displaying could be.

That makes two of us, my friend. :)

This one is a total stumper. It's more or less forced me to keep booting into Windows, which I DO NOT like. I really hope I can manage to fix whatever's going on soon.

---

### Post by anthonyrossbach on 2010-03-09
I have had this problem running 8.10 but when I upgraded to 9.10 it stopped. But to get it to work in 8.10 I use the cable on the computer the wireless would not work on our network or any protected network but would on a open network.

You are running wireless right for it? Have you tried connecting it to the modem by cable?

---

### Post by objem on 2010-03-09
Fair enough with the wpa_supplicant. I have been searching for a while about this and worked out a fix that worked for me. It's not a 'proper' fix but it works.

I read somewhere there is a bug in network manager related to changing channels on the router. Someone suggested setting one channel on your router instead of the default (automatic). I set it to one channel permanently. 

Internet immediately went back to normal and is as snappy as it is in Windows again.

---

### Post by doctorbighands on 2010-03-09
> **objem said:**
> Fair enough with the wpa_supplicant. I have been searching for a while about this and worked out a fix that worked for me. It's not a 'proper' fix but it works.

I read somewhere there is a bug in network manager related to changing channels on the router. Someone suggested setting one channel on your router instead of the default (automatic). I set it to one channel permanently. 

Internet immediately went back to normal and is as snappy as it is in Windows again.

I had my router set to channel 1. So, to test, I set it to "auto," and the problem remains. I tried a couple other channels with no success.

Unfortunately, I can't blame network manager in this case, because one of the machines in the house is running Wicd, and it's having exactly the same problem as the rest.

I'm glad something worked for you. I wish I could say the same!

I'd file a bug report, but I don't even know what's buggy!

---

### Post by doctorbighands on 2010-03-09
I think I might be on to something here (thanks to a tip from PRC09)...

I think this issue might have to do with flash player! The flash website renders as TEXT ONLY. Not only that, but I can't connect to the youtube.com server, and hulu.com videos won't play. Facebook is rendering today, except that it won't display any profile pictures, which I'm beginning to suspect are flash based.

So...how do I properly troubleshoot this? I obtained the version of flash player that I have from get.adobe.com/flashplayer. I don't really know how to uninstall it, and I don't really know how to replace it with another version.

Any help is appreciated!

---

### Post by LintonHanes on 2010-03-09
[http://www.ubuntugeek.com/fix-for-flash-not-working-after-jaunty-upgrade-64bit.html](http://www.ubuntugeek.com/fix-for-flash-not-working-after-jaunty-upgrade-64bit.html)

                                                       !purge!

---

### Post by doctorbighands on 2010-03-16
I purged Flash and reinstalled. It didn't seem to help - the original problem persists.

I'm back at square one, and really frustrated.

---

### Post by yeats on 2010-03-16
So when you say that the websites don't "render" properly, what exactly does that mean?  When you say that Facebook is just text, for instance, do you mean that the images are not showing up? (An example screenshot or two may help). Facebook does not employ Flash on its default page, so that wouldn't bet the issue...

Also, you mentioned that you recently moved - does that mean that you have new equipment, a new ISP, etc.?

From what you're describing, sounds like the following is true:

1. You are able to connect to the Internet.

2. Some sites, but not all, are not coming up in the browser (or any browser).

3. Some sites, but not all, are rendering incompletely somehow (this is where I would want more clarfication).

Can you ping (from the terminal) the sites that are not displaying in the browser?

Are you sure that UFW or another firewall program is not running?  Jaunty and Karmic seem to have it enabled by default (which caused me problems with certain connections - though not Internet).

---

### Post by RedRat on 2010-03-16
> **doctorbighands said:**
> I purged Flash and reinstalled. It didn't seem to help - the original problem persists.

I'm back at square one, and really frustrated.
I believe someone else might have recommended this but you might try installing Opera and/or Chrome browsers. Now if they display properly, then the problem resides in Firefox. If the sites continue to not display properly at all, then there are some deeper issues perhaps involving your graphics card/driver.

---

### Post by Trandre on 2010-03-16
Could you run [www.pingtest.net](www.pingtest.net) to rule out jitter and Quality of service?

Also ping the router and and post it?

Trandre

---

### Post by doctorbighands on 2010-04-18
Okay, I've discovered the problem. Only thing is, I don't really know how to fix it! Let me explain:

The issue lies with Network Manager placing an improper IP address into my /etc/resolv.conf every time I connect. Why is it doing this? I'm not certain, but I suspect it has to do with my router, a Linksys WRT160N. In the router settings, under the Status tab, there are three suspicious entries: 1) the "Internet IP Address," which reads as 192.168.100.101, 2) the "Default Gateway," which reads as 192.168.100.1, and 3) the "DNS 1," which also reads as 192.168.100.1. This is suspicious because the address that Network Manager is writing to my resolv.conf is 192.168.100.1!

So, my temporary solution has been to open resolv.conf every time I boot, change the address to 192.168.1.1, and everything works fine.

That's all well and good, but I'd like to answer three questions:

1) What can I do to get Network Manager to pass the proper IP address to resolv.conf? I don't want to continue to have to edit that file every time I connect.

2) How do I change the settings on my router (if it's even necessary to do that)? I've consulted the Linksys website and restored factory settings, and nothing has worked so far.

3) The one that puzzles me the most: Why is this a problem only in Linux, and not Windows? Why does Ubuntu care what the DNS settings are on the router, and Windows doesn't? If I can figure out what the difference is, it might go a long way toward resolving the issue in Ubuntu.

I'd really like to get this problem solved. Any help from you nice folks out there is much appreciated, as always!

Thank you!

---

### Post by gmxgeek on 2010-04-18
What is the actual address of the router? 192.168.1.1, or 192.168.100.1?

---

### Post by doctorbighands on 2010-04-18
> **gmxgeek said:**
> What is the actual address of the router? 192.168.1.1, or 192.168.100.1?

I assume you're asking for the address I type into a browser to view the router settings.

That address is 192.168.1.1.

192.168.100.1 only shows up under the Status tab on the router settings, and I have no idea where it's getting that address from.

---

### Post by doctorbighands on 2010-04-19
Anyone have any ideas? I'm still lost.

---

### Post by cholt45 on 2010-11-28
Hey!
I had the same problem on maverick (10.10). Facebook was displayed faulty, as it had no css or something. I remember that i had the same problem 2 versions ago on karmic.
I solved the problem after i put in the DNS ip-s in my router. I use google dns (8.8.8.8,8.8.4.4).
If you have this problem try it.

---

