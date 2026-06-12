---
title: "Wireless wpa2 network with hidden ssid not auto-connecting"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by hoges on 2008-04-26
Hi all...
I've just re-configured my wireless router and setup hardy and all is going well. Just a couple of minor annoyances:
1) Firefox randomly freezes for short periods of time.
From what I can tell this seems to be a common problem with all sorts of causes. I've turned off desktop effects and all seems to be well for now. I'll post back if I have any issues.

2) I have to re-enter my wireless network details every time I log in.
This is a real pain. Wireless networking works fine, it's just that it doesn't pick it up on login. This seems to be due to the fact that the ssid is hidden. Due to various attempts by my neighbours in the past to access my network, I have no intention of making it visible. Does anybody know how to make it automatically connect? When I go to "edit wireless networks" from the right click menu of the nm-applet, the network is all there with the proper configuration.

So, does anybody know of a solution to this?

---

### Post by justin_acklin on 2008-04-26
I am having this same problem.  I am starting to think there's a bug somewhere.

My SSID is not hidden, but I still have to go in and re-enter my password and change it to wpa2 every time, then it connects fine.  Or I have to sudo ifdown wlan0; sudo ifup wlan0.

---

### Post by kevdog on 2008-04-27
Why dont you see if you can get everything worked out, and then the last step hide the ESSID?  I dont see how if your neighbor is trying to connect how in any way the effects you if you are using a router!  Particularly if a form of WPA is involved.  If your neighbor is particularly savvy, aircrack or airsnort will be easily able to pick up the ESSID anyways if it is hidden.  Hiding an ESSID really doesnt gain you much security.

---

### Post by jonrwads on 2008-04-27
Same problem maybe a little different details.  I have a wireless network that was working great under 7.10.  WPA-2 hidden network.  Under previous version it worked great, after the first set up, whenever I was home it would just pick it up and connect.

Under the new version this is not so, I have to tell the computer it is there and enter in the key every time (just a little annoying).  After that it connects and runs fine.  It would be nice though if I did not have to enter the key.  After all I know it has it because it shows it in "Edit Wireless Networks" dialog.  Any advice on this would be great as it is really annoying.

---

### Post by KuriKai on 2008-04-27
I always have to enter the key aswell on my 8.04 install

---

### Post by hoges on 2008-04-27
> **kevdog said:**
> Why dont you see if you can get everything worked out, and then the last step hide the ESSID?  I dont see how if your neighbor is trying to connect how in any way the effects you if you are using a router!  Particularly if a form of WPA is involved.  If your neighbor is particularly savvy, aircrack or airsnort will be easily able to pick up the ESSID anyways if it is hidden.  Hiding an ESSID really doesnt gain you much security.

I figure every little bit counts. I have other neighbours who have theirs broadcast, so they're more likely to get hit first.

I have tried setting it up without hiding the ssid, but I still have to key in the key every freaking time. It's getting rather annoying.

> **jonrwads said:**
> Same problem maybe a little different details.  I have a wireless network that was working great under 7.10.  WPA-2 hidden network.  Under previous version it worked great, after the first set up, whenever I was home it would just pick it up and connect.

Under the new version this is not so, I have to tell the computer it is there and enter in the key every time (just a little annoying).  After that it connects and runs fine.  It would be nice though if I did not have to enter the key.  After all I know it has it because it shows it in "Edit Wireless Networks" dialog.  Any advice on this would be great as it is really annoying.

Dito. Exact same problem. What's more is that I will be using the laptop at 2 different locations, so I need it to detect the networks.

---

### Post by garymansell on 2008-04-27
I get the same with Hardy and my wireless WPA network at home. When the laptop boots the wireless network is not connected. When I press the network-manager icon on the panel it lists all of the networks and I select mine and it connects. I do not have to re-enter the key at all though.

Just a bit annoying to have to do it every boot.

Any ideas?

Gary

---

### Post by jonrwads on 2008-04-29
Update, it appears that if I am patient and let my computer sit for about five minutes, it will eventually autoconnect.  The problem is, I am impatient and work from the internet so I usually can't wait 5 minutes for something that should be instantly checked on login.

---

### Post by geezerone on 2008-05-16
I can get wpa2 to work with gutsy gibbon and hardy heron but only if I broadcast ssid.

Is this always the case?
------------------------------------

Edit: Well i thought i could connect but now keep getting asked for password but can't connect.

---

### Post by lionel47 on 2008-05-17
I have reverted to Gutsy and am having one hell of a time connecting to my WPA network.  Is there an easy way to do this?  I found a howto but it is way too long...I mean, this is Linux for human beings, right?  

I first couldn't boot due to the avahi-daemon error.  I resolved that and now there is no WPA listing in the network manager. Does WPA supplicant come already installed in Gutsy?

Can someone help me with this?

---

### Post by campr on 2008-05-18
I'm having a similar problem with my Core 2 Duo notebook HP nc6400 (some Intel WLAN chipset - don't know how to find out the exact name with Ubuntu) trying to connect to my WPA2-protected D-LINK DI-524: after each login I have to open my Ubuntu Network Settings, change the 'Password type' from "WPA Personal" to "WPA2 Personal" and retype my 'Network password'.

To me as user it appears like Ubuntu is not storing the password type correctly.

---

### Post by geezerone on 2008-05-18
> **lionel47 said:**
> I have reverted to Gutsy and am having one hell of a time connecting to my WPA network. Is there an easy way to do this? I found a howto but it is way too long...I mean, this is Linux for human beings, right? 

I first couldn't boot due to the avahi-daemon error. I resolved that and now there is no WPA listing in the network manager. Does WPA supplicant come already installed in Gutsy?...

Is your SSID hidden by any chance? Supplicant does come installed.

> **campr said:**
> I'm having a similar problem with my Core 2 Duo notebook HP nc6400 (some Intel WLAN chipset - don't know how to find out the exact name with Ubuntu) trying to connect to my WPA2-protected D-LINK DI-524: after each login I have to open my Ubuntu Network Settings, change the 'Password type' from "WPA Personal" to "WPA2 Personal" and retype my 'Network password'.

To me as user it appears like Ubuntu is not storing the password type correctly.

Are you using manual configuration from the network manager applet?

I have tried wicd which is a nice GUI replacement for nm. Google for wicd and follow instructions to add site and then install from Synaptic.

---

### Post by nicedude on 2008-05-18
Just turn your essid on and name it something off the wall as the one WPA security hole available is if you use the standard essid since no matter what your password is their are rainbow tables available to increase the time required to crack your key from years to days ( The tables I have are 66 GB uncompressed though so one has to be pretty serious to be armed to do this ) If you name your essid to a name that is unique you will be more protected than with Linksys or Netgear essid and broadcast turned off since that really doesn't do squat against kismet anyway as it will find your network in short order and sniff the traffic just fine, in fact hidden networks just increase my interest in a target. 

In fact just name your essid "your a pathetic hacker you fat loser" and set to broadcast then laugh at him when you pull up everyday since he wont be getting in. One can generate custom rainbow tables if they are uber into this but if you think this dude is "that guy" just change your pass key once a week and he will get frustrated and learn nothing from his efforts :-)

Hope this helps you out and I hope I am not your neighbor ( just kiddin I know I am not ) ;-)

---

### Post by kvasimongo on 2008-05-19
I have the same problem.

Hidden SSID, WPA2 and Hardy. After every reboot have to re-enter the network details in NM to be able to reconnect.
Now turning on SSID broadcasts may be a workaround, but it doesnt solve the problem which seems to me Hardy related. It worked fine in Gutsy ^^

A solution would be nice :)

---

### Post by geezerone on 2008-05-19
If I don't broadcast SSID then I can't connect period so no option for me except to broadcast it. However, you are right, a solution would be nice.:)

---

### Post by nicedude on 2008-05-20
Not broadcasting your essid does absolutely nothing (Zero-Zilch-Nada) to secure your network it just makes it harder for you the legitimate owner to connect to it. Your non broadcasting network can easily be detected with several tools available to the general public. Well implemented security is the only way to be safe from having your network cracked by a wifi intruder and non broadcast is not part of that security as when I sniff non broadcasters ( i.e. Hidden Networks ) get my first attention ( As in I detect this easily ). 

One of the most key things you can do is to rename your essid from the factory setting to something off the wall as that will force even a determined intelligent cracker to have to compile a custom Rainbow passphrase table to attack your encrypted handshake key with. If you leave yours as Linksys or call it joe's then your essid is on lists of precompiled tables and even though you use WPA and a strong password you can be successfully penetrated. Also while it won't stop everyone you should look at configuring your router to use MAC address filtering which only allows for certain MAC address cards to connect. Although that isn't perfect either since I can change my mac in 5 seconds to represent one I sniffed and therefore just become an allowed machine. 

You see even though your network doesn't broadcast essid how do you think your laptop or other wireless devices use it, by broadcasting to and from it of course. Including the encrypted handshake which is all a sophisticated cracker needs along with the proper software and the proper Rainbow table to break your WPA key. He can sniff that one handshake and go home and start brute forcing on your encryption key in safety undetected. The cracker does not need to broadcast one byte of data at your router to do this.

So in short use several techniques to remain as secure as possible I suggest WPA + Strong passwords all around including the router for sure - combined with MAC address filtering and changing the default router essid name. This will stop all but the most sophisticated crackers but if you think your local script kiddie is that smart then just change the WPA key once a week and he will go nuts in a short amount of time and leave you alone. 

After all I find in the cities near me over 50% still use WEP or no encryption at all and I see routers all the time with username admin and password of password - so if stealing internet bandwidth is their goal script kiddies in your area have much easier targets than a MAC filtering broadcasting WPA router.

Trust me Broadcast away :-)

---

### Post by geezerone on 2008-05-21
Good info nicedude.

I do have a very strong password (hex) which isn't a dictionary type but stored on USB drives. I also use mac-address filtering and switch off the WAP when not in use, as well as renaming my ssid to nowt useful (although the mac of the hardware will point to manufacturer of course) :)

I think though that the fact the hidden ssid was working for some and now not working - would be nice if it was fixed but take on board your points. 

I know it can take a couple of years to crack a complex key so perhaps changing a key every few months may be sufficient esp given the very large amount of devices now using wireless (snap frame) technology.

Best to use ethernet imho but there are times when one hasn't a choice.

---

### Post by nicedude on 2008-05-21
I am glad my information is helpful to you geezerone but I might warn you that although thru regular brute force attacks VS a WPA strong password key will take years with a home computer ( 2 Seconds with the NSA's ) there are methods which speed this up by allot. making it crakable within weeks lets say, this is via use of a technique using Rainbow tables which are precompiled passkeys for all possible passwords ( By essid ) and by using such a table it takes allot of the computation work off the computer and lets it find the key by brute force in an exponentially shorter time. By renaming the essid to a unique one you at least force an attacker to have to sniff the essid and go home and compile a custom rainbow table for just attacking your custom essid you have picked ( which while compiling the custom table doesn't take that long for one essid, it does increase the trouble and sophistication needed to successfully attack your access point ). Also choosing a password that uses special characters in it (such as >.,?/ ) increases your security some as it means the attacker has to have bigger more complex Rainbow tables to have success against you ( almost all tables will have a-z A-Z 0-9 but some don't have special ) so keep that in mind as well. All that said you would have to made the wrong geek mad to actually have these kinds of attacks be launched against you as 98% of wifi crackers are trying to crack WEP keys and probably do not posses the technical sophistication to launch these sorts of attacks.

So use strong password and Unique essid and just don't worry, if your super paranoid then change your WPA key every week as since it takes at least a week to crack it you will just make the cracker go nuts trying to figure out why he knows he cracked your pass phrase but it never works :-)

Don't mean to worry anyone but realize that no security is bulletproof ( heck bulletproof vests are not bullet proof they are bullet resistant vests )

Use good procedures and be safe,

nicedude

---

### Post by AndyCee on 2008-05-22
I have the same issue on ONE of my two hardy machines.

My desktop connects instantly with WPA2 Personal and a hidden SSID - no questions.

My laptop takes a few minutes. Aside from hardware differences, the only obvious setting difference is that my Laptop comes with me to Uni, where we have a hidden SSID and WPA Enterprise. Always connects there.

Could it be to do with changing between networks? Just an idea...

---

### Post by nicedude on 2008-05-22
Andy it could be that it is trying the settings that are for your Universities network first ( and they obviously wouldn't work ) and it might be X amount of time before it trys your other configuration settings for your homw network. Just a guess though as I don't know what network management software you are using or which one you set it up with first. I personally prefer WICD over the standard gnome network manager and it has a configured network list I click the one I want and bam I am connected, so you might want to google and look at that as well.

---

### Post by AndyCee on 2008-05-23
> **nicedude said:**
> Andy it could be that it is trying the settings that are for your Universities network first ( and they obviously wouldn't work ) and it might be X amount of time before it trys your other configuration settings for your homw network. Just a guess though as I don't know what network management software you are using or which one you set it up with first. I personally prefer WICD over the standard gnome network manager and it has a configured network list I click the one I want and bam I am connected, so you might want to google and look at that as well.
Currently using default gnm, and would consider WICD except that I'm also helping develop a student userguide to connect to the Uni's wireless network using Ubuntu, and gnm is kind of the 'supported standard', if that makes sense.

Turns out even when not switching between networks the autoconnect doesn't work, or takes a long time, so you might be right about attempting the Uni's network first. Would be good if 'hidden SSID' network appeared (and I apologise for this) *like windows network management* and even just by supplying the name, it connects without having to reenter the password.

---

### Post by nicedude on 2008-05-23
Really gnm is just a frontend for nm which is the standard default management utility as Xbuntu & Kubuntu don't have gnm (I dont think), but while thats a kinda pointless point but since you are making guides and helping others I felt I should point that out since you will probably run into someone with an older laptop that install xubuntu or someone who likes the look of Kubuntu better so you will need to familiarize yourself with those distros network setups etc. as they may be a tad different ( I don't use Kubuntu so I have no idea what it uses ). I just found for me that network manager didn't work right ( it wasn't saving my settings correctly and was temperamental ) and while I might have been able to mess with it more and get it to work I tried WICD and it worked correctly as soon as I put my home network wifi settings in which made me like it right off the bat. So you might try it for yourself and see if it serves you as well as it does me. Once installed you can just drag it from your applications > internet pulldown menu to your top toolbar and create a shortcut to it in 5 seconds then when you boot up your laptop you just click on the wicd shortcut and choose your wifi or wireless network from the list you have setup and bam your connected. This might work better for you it might not so I leave it to you to decide whats best for your situation as all our situations are different. 

Kinda silly too that your college hides their essid as any theoretical security benefit is not worth the extra problems it will cost their students, and in fact I would/have strongly argued that there is no benefit in hiding it ( Just would make me more curious when I detect it :-) ). You might Email your college's IT guys and ask if they can tell you why they do ( I would be interested to hear that answer ).

Hope this is some help to you but for now I must get back to watching the new Indiana Jones movie :-)

nicedude

---

### Post by AndyCee on 2008-05-29
Ta mate, I'll have a look at WICD sometime after assignments. I feel like i'm hijacking the thread somewhat, so I'll shut up about my uni after this.

I work at the very bottom of the Uni's ITS department hierarchy. One of the IT support guys got a request, and he's asked me to make an unofficial guide, as the uni doesn't officially support Linux connecting to the wireless. There are a lot of factors to explain, but vanilla Ubuntu is the only distro that will be (unofficially) supported. The guys I work with are customer service oriented - half of them can't do much beyond write an email and print a Word document when they start working here. When we set up wireless on students laptops, we have guides to follow for XP, Vista, OSX and a generic PDA guide. If there's a problem not on the guide (static IP assigned, overzealous firewall etc) they turn to one of the more IT savvy staff.

Anyway, in this guide, I need the fewest options possible so not to confuse the non-technical minded. "click here, select this" etc. I'll consider making a second 'stage' in the guide, for the case where the gnm doesn't work, but it depends on the simplicity of the guide.

If a student is savvy enough to find another *buntu from campus, I reckon they'll be able to work out the settings from the gnm guide. Or they can contact me.

Yeah, I'm not sure why they hide the SSID. There are a few other SSID's appearing around campus like "Free wireless internet" which sound very unsafe.

Cheers,
-AndyCee

---

### Post by campr on 2008-06-02
> **geezerone said:**
> Are you using manual configuration from the network manager applet?
I'm not sure what would be the opposite. Attached you'll find a screenshot.

---

### Post by campr on 2008-06-10
What additional information are needed to fix this bug? Or is there a different place to report Ubuntu bugs?

---

### Post by geezerone on 2008-06-10
campr - you are using a wpa2 password I understand so when you configure the password leave the drop down menu showing wpa and then type in your wpa2 password and see if it works.

---

### Post by campr on 2008-06-15
No, that does not work. I have to use the WPA2 option.

---

### Post by dogscoff on 2008-06-16
I too am having this trouble - Hardy refuses to autoconnect to a hidden SSID. Gutsy on the same machine did it just fine, so I consider it a bug.

Where should I report this bug?

---

### Post by prj44 on 2008-06-28
Network Manager needs to be re-set on each boot.  Despite being set at WPA2 (and working very well) it is recorded as WPA.  Something is not being saved properly.  I think this constitutes a bug ... but I don't know where to report it.

---

### Post by campr on 2008-07-14
I really appreciate the Ubuntu developer support for fixing this issue. :(

---

### Post by geezerone on 2008-07-14
Out of interest, what signal strength are you getting as I found 50% isn't enough to authenticate with AP. Also, try different channel number on AP.

---

### Post by campr on 2008-07-14
My router stands 3m nearby... -> 99% power. There is no other router visible on Windows.

---

### Post by furbuntu on 2008-07-14
In response to the original poster's first question, I believe I read somewhere that turning off forgery warnings in FF3 can solve a freezing problem in Hardy. You could try it, anyway...

---

