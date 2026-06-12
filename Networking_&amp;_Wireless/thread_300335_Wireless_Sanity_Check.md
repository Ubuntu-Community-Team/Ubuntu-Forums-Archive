---
title: "Wireless Sanity Check"
date: 2006-11-15
forum: Networking &amp; Wireless
---

### Post by slimpinto on 2006-11-15
I need a sanity check here...

I understand all the complexities of "wired" networking interfaces, but am having a crisis with my wireless at the moment. In OpenSuSE 10.x, it just worked, now since the whole MS/Novell deal (let's not digress) I can't get my wireless working with our new "secure network" setup here at work, for the life of me. 

I guess I would like to understand in my head how a Xubuntu (Edgy Eft) handles the wireless card. What would be MOST helpful is some sort of flow chart of the required components to make it work correctly!

I have an Intel Pro 2915 ABG card using the IPW2200 driver (not sure which firmware). I need to connect to our network AP with WPA Enterprise/LEAP. The SSID is <hidden> and we use DHCP. I do have another Thread on this subject, but the following help I want now, is different.

Which &#8220;interface&#8221; does the wireless card use?

(For my wireless) I see an &#8220;eth1&#8221; when I run an &#8220;ifconfig&#8221; or &#8220;iwconfig&#8221;, but all the documentation (or forum help) I've seen, usually discusses &#8220;wlan0&#8221;. Are they related somehow, if so, how? I do see a wlan0 section in my /etc/network/interfaces config file.

How does the wpa_supplicant play in all this? The example wpa_supplicant.conf discusses, /var/run/wpa_supplicant as the path to start it running, but I see it as /sbin/wpa_supplicant in my install. Is this the correct path to the service? 

How do you configure wpa_supplicant?
How do you get it to just run automatically?
The wpa_supplicant.conf has similar config parameters as the /etc/network/interfaces config recommendations I&#8217;ve seen. Do you need to configure BOTH?

Do I NEED to use the latest CVS snapshot of  the IPW driver/firmware, as seen in some other Threads?

Where is the latest IPW firmware loaded? (everything I&#8217;ve read discusses placing it in the &#8220;hotplug&#8221; directory, the catch is&#8230;Edgy uses UDEV!) 

AARGHH&#8230;I hope you can seem my frustration here. There are no definitive guides, or ways to keep track from one major Ubuntu revision to the next, on just how to set up wireless (maybe I haven&#8217;t looked hard enough). I bet I'm not the only here that is having this same amount of trouble though. I don't mind searching for the answers, but in the forums, they are quite spread out and not easy to put back together into one coherent answer.

Yes, I do realize the amount of differing types of hardware, software, and configurations makes this a difficult task, but there has to be some way to make a generic Wireless HOWTO!!!

I guess once you find a Linux distro that EVERYTHING you have works in, you stick with it. Switching to the &#8220;latest and greatest&#8221; has its drawbacks&#8230;Anyone want to take a shot at this? Thanks&#8230;

---

### Post by hal10000 on 2006-11-18
Hi,

maybe this link can help you:
[http://www.ubuntuforums.org/showthread.php?t=263136]("http://www.ubuntuforums.org/showthread.php?t=263136")

---

### Post by Papa-san on 2006-11-20
I understand completely!

(I can't help fix it, but I feel your pain!

wlan* and eth* seem to just interpose each other in ubuntu depending on hardware configurations and what is done to 'make it work' I started using Ubuntu with Breezy. I had a rough time getting wireless set up, but everything else worked 'out of the box'. Eventually, I was encouraged to upgrade to Dapper. I now had to re-configure my entire wireless setup, plus, now I was suffering with intermittent (2-5 times a day) hard lock-ups. My screen resolution settings seem to have had something to do with it, but I never managed to get it fixed. Needless to say, I was ready to install Edgy. However, once I did this, I was unable to use wireless at all. It defied every attempt to follow any tutorials or how-to's. Everything worked great, other than that, but the point of my laptop is to not be tethered by a wire...

So, I am posting this wirelessly on my fresh, shiny, clean Breezy install! (A few days after this was done, I found a thread that explained that the revision of Broadcom 4306 I use is not servicable with Edgy in any way. 

As to the eth/wlan thing... When I have my ndiswrapper set up properly, I know it because this is when I see the line about "wlan0 is being added" Then I just remove the eth1 references in /etc/network/interfaces, and I am good. However, I am only able to have ONE wireless configuration. I can use it at home, but there seems to be no way to get it to work at school... Even when I delete all my 'home' stuff!

(Funny you mention Suse... I am thinking about trying that one out!)

---

### Post by slimpinto on 2006-11-29
> **hal10000 said:**
> Hi,

maybe this link can help you:
[http://www.ubuntuforums.org/showthread.php?t=263136]("http://www.ubuntuforums.org/showthread.php?t=263136")


Thanks for the help Hal...I have this link bookmarked, and it is mentioned in my post. The thread you list has the reference to where wpa_supplicant is run from, and is different than my install shows, so it just adds to the confusion now!

---

### Post by slimpinto on 2006-11-29
> **Papa-san said:**
> I understand completely!

(I can't help fix it, but I feel your pain!

wlan* and eth* seem to just interpose each other in ubuntu depending on hardware configurations and what is done to 'make it work' I started using Ubuntu with Breezy. I had a rough time getting wireless set up, but everything else worked 'out of the box'. Eventually, I was encouraged to upgrade to Dapper. I now had to re-configure my entire wireless setup, plus, now I was suffering with intermittent (2-5 times a day) hard lock-ups. My screen resolution settings seem to have had something to do with it, but I never managed to get it fixed. Needless to say, I was ready to install Edgy. However, once I did this, I was unable to use wireless at all. It defied every attempt to follow any tutorials or how-to's. Everything worked great, other than that, but the point of my laptop is to not be tethered by a wire...

So, I am posting this wirelessly on my fresh, shiny, clean Breezy install! (A few days after this was done, I found a thread that explained that the revision of Broadcom 4306 I use is not servicable with Edgy in any way. 

As to the eth/wlan thing... When I have my ndiswrapper set up properly, I know it because this is when I see the line about "wlan0 is being added" Then I just remove the eth1 references in /etc/network/interfaces, and I am good. However, I am only able to have ONE wireless configuration. I can use it at home, but there seems to be no way to get it to work at school... Even when I delete all my 'home' stuff!

(Funny you mention Suse... I am thinking about trying that one out!)


I knew it!!! There is at least one more wireless sufferer out there! HEHE!

It's all good, but I have sinced moved on to Fedora Core 6...Maybe in 6 months, I'll try Ubuntu (Xubuntu) again...Thanks to everyone for the help given, it was greatly appreciated.

BTW...stay away from those "sell outs", SuSE will never grace a PC of mine ever again. Not until they dump their partnership with M$...

---

