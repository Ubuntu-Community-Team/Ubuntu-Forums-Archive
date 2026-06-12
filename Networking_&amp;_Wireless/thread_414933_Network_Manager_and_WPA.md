---
title: "Network Manager and WPA"
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by seeklinux on 2007-04-20
I installed Feisty from scratch and although my wireless was blinking, I did not see the Network Manager anywhere and when I went to System->Administration->Network it did not show WPA as an option for the wireless card, just WEP.  I thought this would automatically be handled in Feisty but I had to go back to the instructions in [Enable WPA Wireless access in Ubuntu Linux]("http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html").

That is, I needed to do the following:[LIST]
[*]sudo gedit /etc/network/interfaces[/LIST][LIST]
[*]Comment out everything other than “lo” entries in that file and save the file[/LIST][LIST]
[*]Create a file called /etc/default/wpasupplicant, add entry ENABLED=0 and save the file[/LIST][LIST]
[*]sudo touch /etc/default/wpasupplicant[/LIST][LIST]
[*]Reboot your system[/LIST]After this, the Network Manager showed wireless networks and I was able to select and configure WPA.

---

### Post by jhpope on 2007-04-20
tasty, i'll have to try this when i get home...what wireless card do you have?

---

### Post by seamless on 2007-04-20
Strange that Network Manger didn't show when you first installed...

---

### Post by regomodo on 2007-04-20
He's not alone. Just installed feisty. It detects my rt61 and can find all the local networks. just can't connect to mine as it uses wpa. i only have the 2 wep options

EDIT: grr, just followed those instructions and nothings changed

when it says "comment out" does it mean placing # at the start of everything including empty lines?

---

### Post by jhpope on 2007-04-20
yes that is how you comment out. i have an rt61 card as well. network manager installed fine when i installed. i can click on it and i see all the wireless networks but when i try and connect to them i have 3 wep options but no wpa...hopefully this will solve it but i can't try till later today

---

### Post by seeklinux on 2007-04-20
Yes, sorry, use "#" to comment out lines.  Also, when you get things working don't go back in and uncomment them. I mistakenly did that for the ethernet entries (eth0, eth1, etc.) and then my boot up time was slow as it tried (for some reason) to start the wireless during start-up , which was not possible until I logged in and entered the key ring password anyway.

By the way, I am not using ndiswrapper on this machine (this time I have a machine that does not require it).  I have had to deal with ndiswrapper in the past. You can look for one of my earlier posts where I explained how I was able to get  a previous wireless card working with ndiswrapper. That was on Edgy though. Maybe things are different/easier with ndiswrapper on Feisty now though.

---

### Post by mruncieman on 2007-04-20
I have the same problem with a DWL-650+ using ndiswrapper.  In Edgy i was able to connect to my company's WPA wi-fi using this card and ndiswrapper.  In Festy, I don't get the option of WPA, only 3 WEP options.

Unfortunately, this solution didn't work for me.  Hopefully someone will come up with a solution soon.

---

### Post by nukie77 on 2007-04-20
Will my ethernet connection work after this since I have to comment it out?

---

### Post by seeklinux on 2007-04-20
Are you using Network Manager or System->Administration->Network? The former is accessed via an applet on the control panel (by default at top of screen). That is how I had an opportunity to select the wireless network and then enter the WPA information.  So look for the Network icon and try right clicking on it if you haven't already.

If you try to use System->Administration->Network I think you have to do things more manually in various files.

---

### Post by jonno on 2007-04-20
Same problem for me (fix didn't work). I have a Ralink RT2600.

---

### Post by seeklinux on 2007-04-20
Well, so I guess the story is a little more complicated.  My new laptop does not require ndiswrapper so if I comment out the wlan0 entry in /etc/network/interfaces  the Network Manager finds it with not problem. But looking at what I did on my older laptop on Edgy using  ndiswrapper with a card that required it, I **did** need an entry in **/etc/network/interfaces** for wlan0 because otherwise the card would not get started at all and Network Manager never saw the device.

So to summarize, if ndiswrapper is not needed for the wireless card, I could comment out wlan0 (actually everything but l0) in /etc/network/interfaces.  However, if ndiswrapper was needed, I had the following in my /etc/network/interfaces:

[B]iface wlan0 inet dhcp
auto wlan0[/B]

The downside to this is that at boot up time it would briefly hang a while the system tried to start the wireless connection with DHCP, which of course won't work because I had to login in first and provide the key ring password.

Needless to say, if you are using ndiswrapper, you need to go through all the steps to make sure the module is added and loaded first.

I haven't upgraded the older laptop to Feisty yet so it is possible things have changed in Feisty, but I suspect that the real change is the inclusion of Network Manager by default (previously you had to add the package yourself).  The disappointing thing about all this is mandriva a couple of years ago offered you the option when you configured the wireless device to install and help you configure ndiswrapper if needed.  

Although including Network Manager is an improvement, I think ubuntu needs to provide more assistance to those using ndiswrapper (not just documentation), because a lot of people are stuck using it.  When I bought my previous wireless card I even *tried* to find one for which there was a Linux driver, and I thought I had, but it turns out there were different versions of the card and the version I ended up with would only work with ndiswrapper and the windows driver.

---

### Post by sdonahoe on 2007-04-20
Did the new kernel drivers for Intel Ipw2100 mess up WPA?

About to install Feisty from the Desktop CD on a Thinkpad t41, so first booted into the Desktop CD to test hardware support.  My home router (a Linksys WRT54GS running DD-WRT) has WPA enabled.  Upon Feisty booting up, network manager was up there and all the local networks were detected.  It knew which ones to ask for WEP keys for (the neighbors), and to ask for a WPA key for my network.  Pretty slick.

But after entering the passphrase, it took forever to get an IP and a connection, and then ultimately failed to do either.  Huh.

Removed the CD, went back to XP, went into the router's admin pages and disabled all wireless security.  Re-booted off of the Feisty Desktop CD and network manager found all of the same networks, and it connected like a charm to my network without WPA.

Still going to install before Feisty before taking the laptop on a roadtrip.  A lack of WPA support at hotspots shouldn't be a problem, to put it mildly.  But it would be nice if this was fixed in a month or so.  Either I'll figure out a workaround or an update might take care of it before then...Any ideas?

---

### Post by jhpope on 2007-04-21
this didn't do anything for me

---

### Post by richardeng2005 on 2007-04-21
This is ridiculous. Why does Linux make you jump through hoops to *TRY* to get WLAN working???

I just downloaded and installed Feisty Fawn, but I simply cannot get WPA for my D-Link DWL-520+ card, which according to this forum should "just work." I see the access point (ESSID "Galactica") but I only get 3 WEP options, no WPA.

I tried following the above posted instructions but to no avail. Ubuntu refuses to show WPA as an option. WTF?!

Listen, folks. If you hope to ever have Linux widely adopted by the public, Linux has to solve the WLAN support problem. The current situation is completely unacceptable. Getting WLAN working should not require jumping through so many hoops, or such arcane commands.

In Windows and Mac OS X (I use both), I've never had problems getting WLAN to work. What...is...wrong...with...Linux?

---

### Post by seeklinux on 2007-04-22
richardeng2005, I am not an expert but one thing to do is make sure you are looking at the Network Manager.  Again it is **not** System->Network.  The Network Manager is represented as a little icon. You right click on it and it should show wireless networks it found. To my knowledge using System->Network will always show just WEP and not WPA.

So I guess the question is when you say you see WEP options only, where are you seeing this. My apologies to you (and others) if you are looking in the right place.

There are multiple ways to configure your network for wireless. The Network Manager is typically less manual.

---

### Post by richardeng2005 on 2007-04-22
seeklinux, indeed, I am using the Network Manager icon.

I don't mean to dump on Linux, I really am rooting for it. But this continuing thorn of WLAN support will limit Linux's success. That's okay if you're happy with 6% PC marketshare forever. I understand the technical issues that Open Source developers face, and I sympathize with them, but they have to do better in the area of WLAN. Wireless networking should be PRIORITY #1 in their roadmap...

---

### Post by seeklinux on 2007-04-22
Can you  bring up Synaptic Package Manager and search for "wpa"and see if you have **wpasupplicant** installed?  I also see I have **wpagui** installed; you might want to try installing that one too.

If you didn't have **wpasupplicant** installed, make sure to go back to the initial post and see the description of initializing the **/etc/default/wpasupplicant** after installing wpasupplicant.

BTW, I assume you are using **ndiswrapper **with your wireless card?

---

### Post by regomodo on 2007-04-22
meh, sod it. Given up again trying to get wireless to work with linux for the dozenth distro. back to xp for it until this issue is sorted

---

### Post by jarrett on 2007-04-23
Hi, I had the same problems with connecting to a access point with WPA encryption.
I got it working fine by compiling the latest source of ndiswrapper (1.42)

---

### Post by seeklinux on 2007-04-23
regomodo, I see from earlier posts you have an** rt61**.  If that is what you are trying to get working from what  I read its driver does not work with **wpasupplicant**.  Perhaps you should look at the steps [here]("http://ubuntuforums.org/showthread.php?t=392415&highlight=feisty+ralink"), although they do not appear to be trivial.  I was going to suggest you could try using ndiswrapper but it appears people have had more luck using the ralink linux driver instead.  I guess for your card you should go into Synaptic Package Manager and uninstall **wpasupplicant**, since your driver is supposed to support WPA without that.  I don't know if this means Network Manager will display the WPA options anyway, or it may mean you can't use Network Manager and must do more manual configuration. 

You said you tried dozen distros?  Have you tried Mandriva and PCLinuxOS which *might* do a little better job supporting your wireless card out of the box? At least they do with cards requiring ndiswrapper. In the case of your card I don't know. 

Good luck. I hope you don't give up on Linux. Maybe buying a different card (maybe refurbished so you could get it cheap), would be an option?

---

### Post by xjimtx on 2007-04-24
That little comment out trick worked for me, my problem was I was fooling around with the network manager and  hit manual and then I was stuck there with only WEP options. But commenting those lines out got me back to the default way before I messed it up

---

### Post by regomodo on 2007-04-25
Hi, cheers for the link. I did find that before but had previously tried an even longer guide that didn't work so i couldn't be arsed.

I've tried Mandriva but it's the same problem with that too. Tried Zenwalk but it didn't even know that my card was in (i like zenwalk, shame my lappy doesn't have enough videos guts to run xfce). 

So far Ubuntu and Mandriva are the only ones that have managed to get my card working properly, minus WPA. 

I did buy this card for £20 (~$40) because i had a prism chipset card before. Don't really want to by another one. I think i may have to. I'll look around for the best supported card. Not for X/Ubuntu mind you, video issues with the xfce and gnome, unless fluxbox is an option.

BTW, i haven't given up on Linux. I have Fiesty on my Desktop (i did give up for a while with that too until i found virtualbox). Just can't get my lappy to be happy with Linux

---

### Post by seeklinux on 2007-04-25
regomodo, I know how you feel. I actually researched a lot before buying my previous wireless card and I was sure it would work natively in Linux. But when I bought it (online) it did not say it was version 2 of the card. Turns out version 2 used a totally different chip set from version 1. So I ended up having to use ndiswrapper. It worked, but using ndiswrapper brings along additional issues, not to mention the political ones.

When my ethernet port on my previous laptop stopped working I was able to find a PCMCIA refurbished Netgear card for about $10.  Something to consider.

Good luck.

---

### Post by blunto on 2007-11-08
I am having the same problem - with a little research I found that certain revisions of this card don't support WPA.  Most likely a hardware issue, not software.  

[http://support.dlink.com/faq/view.asp?prod_id=1401](http://support.dlink.com/faq/view.asp?prod_id=1401)

---

