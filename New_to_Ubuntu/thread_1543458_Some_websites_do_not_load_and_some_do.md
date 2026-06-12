---
title: "Some websites do not load and some do"
date: 2010-08-01
forum: New to Ubuntu
---

### Post by Slavek_D on 2010-08-01
Hi,
I am a new user of Ubuntu (but not new user of computers ;)).
Believe me, I have spent many hours finding a solution for my question on internet before I decided to post my thread here.
Well, after a few hours of using Ubuntu and searching Internet I realised I couldn't access some key websites such as google mail (login), eBay (login) and even launchpad.net to be registered here! Other websites worked very well.
I spent a few hours trying to find a solution but non of the advices worked (even installing Opera and Chromium did not help). I gave up and I reinstalled Ubuntu from scratch (and did the first update). 
Guess what? I still cannot access google mail, my eBay etc! What should I do to stop being frustrated about Ubuntu :(?

---

### Post by Krabby.Linux on 2010-08-01
This is a SSL Problem, you have problems encrypting the secure internet connections. This means online banking and logins (ebay amazon etc etc etc) should not work very well.

This can have lots of reasons.

Where is your notebook/pc located? At home behind a router? University?

If you need a static IP Address this might not help. But enabling DHCP works for many who have this problem. Rightclick on your network connection in the panel and edit connections, now edit your connection and enable DHCP Automatic.

---

### Post by Slavek_D on 2010-08-01
My laptop is at home.
I use standard broadband connection (a wire)
Everything is perfectly fine on my second laptop I am using now (with Vista installed)
I don't use any wireless connection.

Any idea?

---

### Post by Krabby.Linux on 2010-08-01
Did you tried enabling DHCP ?

---

### Post by Slavek_D on 2010-08-01
I am doing it now.
When I open network connections I can see a window with 5 tabs. The first  one is wired. I can see one connection but when I click edit I have  another window open:
Connection name
Connect automatically (is ticked)
and below there 4 tabs, the first one is with following settings:
Wired (MAC address:...MTU: automatic).
Should I change anything?

---

### Post by Slavek_D on 2010-08-01
There is one more tab (IPv4 Settings) and there are some HDCP settings there. Which option should I use?

---

### Post by ibuclaw on 2010-08-01
> **Slavek_D said:**
> There is one more tab (IPv4 Settings) and there are some HDCP settings there. Which option should I use?

In the **IPv4** tab, set the **Method** to 'Automatic (DHCP)'. Then disconnect/reconnect to the network.

---

### Post by Slavek_D on 2010-08-01
It is set as 'Automatic (DHCP)'

---

### Post by Slavek_D on 2010-08-01
It is set as 'Automatic (DHCP)' and my 'secure' sites don't work! Any other ideas?

---

### Post by ottosykora on 2010-08-01
under settings, last tab, encryption, are the both ssl and tls ticked?

---

### Post by Slavek_D on 2010-08-01
> **ottosykora said:**
> under settings, last tab, encryption, are the both ssl and tls ticked?

Last tab (the fourth one) is IPv6 Settings. There 'Method' there and option Ignore is chosen. I cannot find any place with ssl and tls :(

---

### Post by Slavek_D on 2010-08-01
Any ideas guys? Don't tell me you all gave up :(
I still believe it is very simple setting/solution for this...

---

### Post by sydbat on 2010-08-01
At the bottom of the Network Connections popup window, is "Available to all users" checked?

Also, what are the settings under the "802.1x Security" tab?

EDIT - What is your Internet connection? (DSL, Cable, dial-up) There might be some setting in the DSL/Cable router that needs to be changed (shouldn't, but you never know).

---

### Post by Slavek_D on 2010-08-01
Ok, answers:
"Available to all users" is checked
Under the "802.1x Security" tab nothing is checked
I have a cable broadband
I don't want to change any DSL/Cable router settings because my second laptop (with Vista) is working well

---

### Post by Slavek_D on 2010-08-03
Am I really the only Ubuntu user experiencing this problem? I did not loose my faith in you yet...

---

### Post by tas.b on 2010-08-03
Hello,
you are not the only one, here is my case ([http://ubuntuforums.org/showthread.php?p=9673068#post9673068](http://ubuntuforums.org/showthread.php?p=9673068#post9673068))
but I wonder how I can help...

---

### Post by Krabby.Linux on 2010-08-03
Thats hard to say, could be your hardware, you will have to test the connection with a new network card i think. I know some people who had this Problem or still having this under Windows AND Ubuntu, thats the strange thing.

Are you able to test the connection with a new card?

What about Firefox settings ? Is SSL 3.0 checked? What about TSL? If TSL is checked try to turn it off and restart your browser.


Another Idea: Do you use a proxy? First check Firefox Proxy and mark use system proxy. Than go to System --> preferances --> network proxy and disable eveything (mark direct connection) than push the button apply system wide and type in your su password twice. What about now?

---

### Post by Slavek_D on 2010-08-03
> **Krabby.Linux said:**
> 
What about Firefox settings ? Is SSL 3.0 checked? What about TSL? If TSL is checked try to turn it off and restart your browser.

Another Idea: Do you use a proxy? First check Firefox Proxy and mark use system proxy. Than go to System --> preferances --> network proxy and disable eveything (mark direct connection) than push the button apply system wide and type in your su password twice. What about now?

I did step one and two above (the only difference is that I don't have option 'direct connection', I have 'No proxy' , 'Auto detect proxy', 'Use system proxy' and 'Manual proxy' so I've chosen 'No proxy'). 

No changes...

Any other ideas?

---

### Post by racooper on 2010-08-06
I'm having a similar problem with my Lucid system, Firefox 3.6.8.  It is an SSL issue, and does not seem to be an issue with network settings. I am hardwired on a university network and I am also running an XP Virtual Box VM on this same system and it has no problem accessing any https websites.

The problem is not just gmail but any secure sites, including internal campus sites.  I pulled a few Wireshark captures of the interaction to one specific internal site and while I am not an expert on reading pcap logs, I'm seeing some odd series of RST packets that don't show up on either of my Windows tests (XP VM, and a standalone Win7 system).  I'm going to attach a zip of all three pcap files, if they can be a help to anyone with more experience.

It's seriously frustrating.  https sites usually seem to work after the first connection finally succeeds, but an example of how slow it is...I started a connection to our intranet (the site in the pcap files) on my Lucid box, but before it had finished I had booted a Win7 box, logged into active directory, started the browser, logged into the secure site in question, and clicked through several pages to get some info for my supervisor on the phone.  All before my Lucid system even loaded the site logon page over https. That's just...pretty bad.

---

### Post by cjack007 on 2010-08-06
well i used to have this same problem and could not even enter my routers configuration site which again required authentication but everything used to work flawlessly on my win xp. here what i did

in windows open your router configuration site in a browser
go to wan settings
check your connection mode and change it from bridging to pppoe
save and let the router reboot
now open your ubuntu delete your previous dsl connection and connect using your new wired connection make sure  you use automatic dhcp or automatic dhcp adresses only
now login to your vista and delete your previous connection reboot
now next time when you will open your vista it will set up connection automatically.

worked for me flawlessly now 100% sites work on my Ubuntu desktop

---

### Post by racooper on 2010-08-06
That's fine for a home user but I'm on a university network -- managed routers, OC3s, etc...and I don't have control over that.  I'm not using a "DSL" connection in Ubuntu, but a normal wired connection with DHCP addressing.

---

### Post by cjack007 on 2010-08-07
> **racooper said:**
> That's fine for a home user but I'm on a university network -- managed routers, OC3s, etc...and I don't have control over that.  I'm not using a "DSL" connection in Ubuntu, but a normal wired connection with DHCP addressing.

it would be much better if you find another person in your university who is successfully using all these sites(on ubuntu or some other linux distro) you mentioned are not working for you because i think he can guide you better.

---

### Post by kkraju4u on 2010-08-14
I cant load [thepiratebay.org]("http://thepiratebay.org") in ubuntu 10.04

please help me:(
browsers firefox and opera
jre installed

---

### Post by racooper on 2010-08-15
> **kkraju4u said:**
> I cant load [thepiratebay.org]("http://thepiratebay.org") in ubuntu 10.04

please help me:(
browsers firefox and opera
jre installed

Um...I don't think anybody can.  it's not an Ubuntu or browser issue, it's a Pirate Bay issue. (And this really isn't relevant to the issue of SSL connection issues with Firefox in 10.04.)

---

### Post by Slavek_D on 2010-08-15
> **Slavek_D said:**
> Hi,
I am a new user of Ubuntu (but not new user of computers ;)).
Believe me, I have spent many hours finding a solution for my question on internet before I decided to post my thread here.
Well, after a few hours of using Ubuntu and searching Internet I realised I couldn't access some key websites such as google mail (login), eBay (login) and even launchpad.net to be registered here! Other websites worked very well.
I spent a few hours trying to find a solution but non of the advices worked (even installing Opera and Chromium did not help). I gave up and I reinstalled Ubuntu from scratch (and did the first update). 
Guess what? I still cannot access google mail, my eBay etc! What should I do to stop being frustrated about Ubuntu :(?

Can we come back to my original question please?

---

### Post by Cycledoc on 2010-08-15
I gave up on Firefox, having experienced many of the issues you raised.   I uninstalled it from the computer and am using Chrome and Opera and things seem much better.

I like Firefox on my mac but not here. I've tried reinstalling and the problems recurred.  

I'm a neophyte and know little of the technical issues here but can only tell you that this worked for me.

Let us know if it helps

---

### Post by Slavek_D on 2010-08-16
Well, I have tried both Chromium and Opera but I had the same problem regardless the browsers I was using...

---

### Post by Cycledoc on 2010-08-16
Did you uninstall firefox?

I've also disabled Ipv6--too early to tell if it's helped.  This AM no issues and browsing quite quickly with chrome.

Regards

---

### Post by Slavek_D on 2010-08-17
> **Cycledoc said:**
> Did you uninstall firefox?

I've also disabled Ipv6--too early to tell if it's helped.  This AM no issues and browsing quite quickly with chrome.

Regards

I don't really know if uninstalling Firefox is possible in Ubuntu :(

---

### Post by oneadvent on 2010-09-25
everything is possible in ubuntu.

write that one down.

---

