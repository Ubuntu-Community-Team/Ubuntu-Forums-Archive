---
title: "Wireless connection lost after an hour"
date: 2006-12-25
forum: Networking &amp; Wireless
---

### Post by W3ird_N3rd on 2006-12-25
Ok, let's go..

[size=+1]The hardware[/size]

Safeway 8 port 10/100mbit switch (old name Sweex)
Asus WL-330g 802.11g "world's smallest" accesspoint configured to use WPA(1) with a PSK and TKIP
Dell Latitude CPt with Celeron 500 and Asus WL-107g cardbus wireless card (Ralink chip, RT2500)
Asus Centrino with Intel 2200BG minipci card

[size=+1]The software[/size]

The Dell is running Ubuntu 6.10 Edgy, configured using [this Ralink RT2500 guide]("https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500") so it is using iwpriv for WPA.

The Asus Centrino is running Ubuntu 6.06 Dapper, configured using network-manager-gnome. Network-manager-gnome is as far as I know partly a front-end for wpa_supplicant, so it's using something else for WPA than the Dell.

Both use the drivers shipping with Ubuntu by default and are configured to use DHCP to get an IP.

[size=+1]Problem and symptoms[/size]

First I turn on the accesspoint. From that moment on I can get on the network perfectly - for an hour. After that the connection is lost, on both laptops *at the same time*. I can do two things when that happens:

[list][*]Kick the accesspoint, or to be precisely, reboot it. The connection immediately works again after that.
[*]Wait for approx. 18 minutes. The connections comes back all by itself but I have to wait.[/list]

Symptoms: the WL-107g cardbus card has two LEDs, act(ivity) and l(i)nk. They both blink when the connection is lost, they are lit for I think 3-5 seconds, dark for 1 second or so, and they do that in a loop.

On the Centrino, I see the bars from network-manager-gnome also blinking, all blue for some time and for approx 1 second all grey. I also see the signal strength going from all green 100% to very low-yellow in the same rhythm. The rhythm from the LEDs on the Dell and the network-manager-gnome and signal strength on the Centrino could very well be the same, but I'm not sure.

[size=+1]Everything that DIDN'T work[/size]
[list][*]Using a static IP.
[*]Taking "strange" characters out of my WPA key like " ' !
[*]Using a different (Belkin) accesspoint with the same settings
[*]Trying a different switch (I already thought that wouldn't be the problem, but tried nonetheless)
[*]Check internet connection - no, the wired computers were still connected and I also couldn't reach the local network on the laptops
[*]Wireless hardware broken or microwave on a timer somewhere near - nope, than rebooting the AP wouldn't make sense, and the dominant operating system from this world doesn't have any trouble staying connected to the wireless LAN.
[*]Does the entire AP fail? No, even when Ubuntu lost it's connection, another laptop running "that other OS" is still connected.
[*]It's that known bug in network-manager! - no, because the Dell doesn't use network-manager-gnome but iwconfig/iwpriv instead.
[*]Shouting
[*]Crying[/list]

I couldn't find much on the forum either, maybe not using the correct words to search. I need some input from someone else, a fresh idea. I ran out of ideas.

This text might make you think something else but I'm still a complete Linux-n00b so don't speak complicated complicatedness, I won't understand it. I do have experience with computers, but not much with Linux. The verb "to compile" scares me, ok? :p

---

### Post by W3ird_N3rd on 2006-12-25
Some new info, somebody suggested running dmesg after the connection was lost. This is what it said:

```

[17179652.996000] ieee80211_crypt: registered algorithm 'TKIP'
[17179669.508000] eth1: no IPv6 routers present
[17179886.248000] TKIP: ICV error detected: STA=00:15:f2:06:cf:75
[17180062.240000] TKIP: ICV error detected: STA=00:15:f2:06:cf:75
[17180063.252000] TKIP: ICV error detected: STA=00:15:f2:06:cf:75
[17180064.264000] TKIP: ICV error detected: STA=00:15:f2:06:cf:75
[17180065.276000] TKIP: ICV error detected: STA=00:15:f2:06:cf:75
[17180066.292000] TKIP: ICV error detected: STA=00:15:f2:06:cf:75
[17180071.556000] TKIP: ICV error detected: STA=00:15:f2:06:cf:75
[17180072.568000] TKIP: ICV error detected: STA=00:15:f2:06:cf:75
[17180073.580000] TKIP: ICV error detected: STA=00:15:f2:06:cf:75
[17180074.592000] TKIP: ICV error detected: STA=00:15:f2:06:cf:75
[17180075.604000] TKIP: ICV error detected: STA=00:15:f2:06:cf:75
[17180080.872000] TKIP: ICV error detected: STA=00:15:f2:06:cf:75
[17180081.884000] TKIP: ICV error detected: STA=00:15:f2:06:cf:75
[17180082.896000] TKIP: ICV error detected: STA=00:15:f2:06:cf:75
[17180082.924000] TKIP: replay detected: STA=00:15:f2:06:cf:75 previous TSC 000000000001 received TSC 000000000001
[17180090.188000] printk: 2 messages suppressed.
[17180090.188000] TKIP: replay detected: STA=00:15:f2:06:cf:75 previous TSC 000000000003 received TSC 000000000002
[17180093.224000] printk: 2 messages suppressed.
[17180093.224000] TKIP: ICV error detected: STA=00:15:f2:06:cf:75
[17180099.500000] printk: 1 messages suppressed.
[17180099.500000] TKIP: replay detected: STA=00:15:f2:06:cf:75 previous TSC 000000000005 received TSC 000000000002
[17180102.540000] printk: 2 messages suppressed.
[17180102.540000] TKIP: replay detected: STA=00:15:f2:06:cf:75 previous TSC 000000000005 received TSC 000000000005
[17180108.816000] printk: 2 messages suppressed.
[17180108.816000] TKIP: replay detected: STA=00:15:f2:06:cf:75 previous TSC 000000000009 received TSC 000000000002
[17180112.868000] printk: 4 messages suppressed.
[17180112.868000] TKIP: replay detected: STA=00:15:f2:06:cf:75 previous TSC 000000000009 received TSC 000000000006
[17180118.132000] printk: 1 messages suppressed.
[17180118.132000] TKIP: replay detected: STA=00:15:f2:06:cf:75 previous TSC 00000000000b received TSC 000000000002
[17180127.448000] printk: 4 messages suppressed.
[17180127.448000] TKIP: replay detected: STA=00:15:f2:06:cf:75 previous TSC 00000000000c received TSC 000000000002
[17180128.460000] TKIP: replay detected: STA=00:15:f2:06:cf:75 previous TSC 00000000000c received TSC 000000000003

```

I'm posting it here so I can also show it to him, but I'll also search on these errors, I don't know what they mean but at least I have a new lead.

This was on the Centrino, haven't tried the Dell yet.

[edit]Tried on the Dell. No errors there, iwpriv apparantly doesn't report anything, at least that's my guess. Looked the error up on Google, it doesn't mean anything. Everyone gets these errors for random reasons. It doesn't make anything clear. Well, it makes clear that *probably* there's something with WPA. Then again, why does the Dell also suffer from it?

No progress made.

---

### Post by W3ird_N3rd on 2006-12-26
I have no idea what the kicking/bumping policy on this forum is (can't find any information about it), but my topic seems to be clearly out of sight, so I think I can bump it safely now.

I still have no idea where to look.

---

### Post by W3ird_N3rd on 2006-12-28
The post is far out of sight again, so bump..

I made a little progress. I still don't have a solution but I'm about to find out the source of the problem.

In the accesspoint there is a setting "WPA Re-key Timer". The manual says that the lower this value the more safe your network. By default it is set to 24 hours. I didn't think it would have anything to do with my problems, because my problems occur long before 24 hours have past.

However I tried changing it. Lowering the value (making the network more secure) causes the connection to fail faster. When the re-key is being done, the connection "hangs" for a moment, long enough to make a shoutcast stream stop playing. So setting the re-key to 30 minutes isn't exactly practical..

So that wasn't much success. So I tried increasing the value. Remember that with the default 24 hours value my connection would work for one hour, blackout for 20 minutes, come back for an hour and so on. After changing the value to 48 hours, I was connected for two hours! And then.. Blackout, for 40 minutes!

Everything twice!

Now I **could** in theory increase the value to 68 years, and in theory that would make the connection work for almost three years (and then it would blackout for a year!). I could live with an accesspoint reset once every two years. But alas, according to the manual that would make the connection much less safe. I don't know if it would become crackable, but I still don't like the idea.

There just must be a solution to this. I don't want to believe I am the only Ubuntu user using WPA Re-keying at a normal rate.

Any help is seriously appreciated.

---

### Post by tturrisi on 2006-12-28
In simple terms, WPA-PSK is extra-strong encryption where encryption keys are automatically changed (called rekeying) and authenticated between devices after a specified period of time, or after a specified number of packets has been transmitted. This is called the rekey interval. WPA-PSK is far superior to WEP and provides stronger protection for the home/SOHO user for two reasons. The process used to generate the encryption key is very rigorous and the rekeying (or key changing) is done very quickly.

I'd set it to several yrs if possible & live with it.  Even the best of hackers would have a difficult time cracking WPA.  And why would they choose to target you?

---

### Post by W3ird_N3rd on 2006-12-28
Just looking at "why would anyone target me" I might as well set WEP encryption, MAC filtering and hide my SSID. I doubt anyone will do everything required to get in. I even doubt there will be any wardriver at all for say 3 years from now in my street.

Many people play in the lottery. Do you? They know they most likely will never win the jackpot or even run break-even with what they pay. Then why do they play? Because they **might** win one day, and if they do, the impact will be great!

Well same here. Most likely nobody will ever try to get in. I'll never win the lottery probably.

But IF somebody does, uploads kiddy porn, denies that the holocaust ever happened (to be sure nobody thinks that is my opinion: it DID, but denying it is illegal in The Netherlands), send out lots of junk mail and empty all my harddrives, I'm going to be seriously pissed off.

You can call me crazy or paranoid, but still half of the western world is playing in lotteries, and you can't say these people are all nuts.

And there is another reason. Ubuntu **should** be able to work with WPA. And there is no known bug that would prevent it from working in my configuration. I can't stand it if it doesn't work. It has to.

---

### Post by W3ird_N3rd on 2006-12-31
So here we are again.

I connected my laptop to the neighbours' accesspoint. That's a Netgear wgr614v6 router (yes with WPA, what else). Now I've been connected for over 4 hours continuously.

Remember that with my own accesspoint, I could never say for sure when I could connect and when I couldn't, so there was always a chance I was booting up my laptop somewhere in the middle of a 20 minute radio silence. In such a case I just wouldn't have a connection from a cold boot and have to wait till the 20 minutes are over, never knowing when they would end (could take any length of time from 20 minutes to 1 second, depending on my luck).

On the neighbours' accesspoint, I was connected instantaniously. So if the radio silence would occur here too, I could have been connected for much more time than the 4 hours I've been connected now.

4 hours would be a rekey-timer on my AP of at least 4 days. And I was immediately connected so I'm pretty sure it would have to be much longer.

Now there are four options:

[list][*]This AP doesn't ever rekey. Unlikely.
[*]This AP doesn't rekey often. Possible, but would the difference between manufacturers be that big?
[*]My AP is a piece of ****. And the Belkin too.
[*]Something else in my network is garbage.[/list]

Problem is.. I have no idea what the value of the rekey-timer is on that AP. Looking at the manual there possibly isn't even a setting available for it. As far as I know rekeying *is* required for WPA however, but I don't know at what value..

I'm going to test one more thing. I'm going to unplug the ethernet cable from my AP, then I'll associate my laptop with it, and continuously ping the AP itself.

If that fails (and I assume it WILL) I'm going to look for another AP.. Again. I'm just in doubt if I'll go for a &#8364;30 Sweex cheapass wireless router, praying I can set it up as "just-gimme-the-AP-and-go-to-hell-with-the-routing-part" and hope it's range is big enough, or a 3com.

I don't want anything in between anymore. I've seen more than once that if I'm having trouble with some part, I either need to get something as low-end as possible and that'll work excellent for me, **or** I need to get something seriously high-end or sometimes even professional to get something simple done.

Connected over four and a half hours now.

---

### Post by ritalin_kid on 2006-12-31
From what you've posted above, it seems to me like your issues are being caused by your AP, seeing as your neighbor's AP did not drop you after just an hour.

That's just my 2 cents..

---

### Post by nepenthes on 2006-12-31
Hey Weird,
I like this thread and the way you are blogging almost alone for yourself :) I can't really help you, but felt it was important to let you know that there are more people out there with a related problem. I also get  disconnects running Ubuntu Edgy with NM, WPA and PAM (this keyring silencer thing). After a disconnect I also have a hard time getting a reconnect again, even though I have moved already into the same room like my router. Sometimes it doesn't even connect after booting! Sometimes it also just works as long as I need it. Router is X-Micro 11b type and a Compaq Laptop with a Broadcom 43xx. Had a hard time getting that Broadcom driver (w fwcutter) to work properly, but it does now very well (well, relatively) since I stopped ACPI. Before even the mouse would hang for a few milliseconds regularly and I rarely finished a proper shutdown.
With XP on the other partition I never have any disconnection issues.

My suspects about these disconnections are:
1. PAM, I think before (when I still entered my same passwords 3 times ...:rolleyes: ) it was better. But I really like when my computer just boots and connects.
2. Interferences with neighboring networks on the same channel (we have up to 40 WLANs in the neighborhood...)
3. Maybe disconnection appears when the Internet is idle and some wicked-not-yet-in-the-driver-integrated power saving feature of the WLAN adapter makes that thing sleep and forgets to wake it up.
4. I find the rekeying discussion above interesting...

Anyway at least with Ubuntu computing still bears some challenges. :mrgreen:  (Connected since 30 minutes already! Yey!)

PS: I also have those TKIP ICV Errors...

---

### Post by W3ird_N3rd on 2006-12-31
ritalin_kid: the amount of an hour is depending on the rekey timer setting. I do not know what the rekey value for the neighbours' AP is.

But starting to think about it.. The Asus has 24 hours by default, the Belkin had 24 hours by default. You would start to think that possibly most APs use 24 hours.

I tried being associated with my own AP without ethernet plugged into the AP. And of course.. I was disconnected after an hour. So it's nothing in my wired network.

nepenthes: good to hear, at least somebody can enjoy all the misery :).

And yes, Ubuntu gives you some challenges :mrgreen:. On the other hand, other things are so much easier. Installing it is easier than installing that OS with a big market share. Installing my everyday applications from the repositories is insanely easy compared to visiting all the websites from the manufacturers and software websites. Installing drivers for all your stuff? If you buy the right hardware, you can just plug it in. Fighting with or even begging that bitch on the phone to convince her she should give you a code that allows you to use the product **you already paid for?**

Ubuntu gives you some challenges, but it also has it's advantages ;). That's worth going through some challenges for..

---

### Post by koandy1983 on 2007-01-05
Hello!

Same problem here.

ASUS AP WL-330g is disconnecting every 1h. The way I can reconnect to the AP is to unplug it from power source for 5secs and replug and everything working fine, and so every 1h (disgusting) . I was thinking that my AP is some how broken, but after reading this topic I've figure out that is a general problem of this model and I'am not the only one. 

I tried with a lot of wireless cards brands and on every card doing the same problem.

I use WAP-PSK, and if that time of rekey, 84600, is solving my problem somehow by increase  it, I will do it, like someone said, "I can live with that of about 3years or so" :D.

Maybe is a problem of firmware, but I have looked at ASUS website, and there is no new version of firmware, that resolve this problem.

Maybe someone discover the problem and give us a little help.

---

### Post by W3ird_N3rd on 2007-01-10
Okay, so I bought the Sweex LW050 wireless router. Pretty good bargain at &#8364;33,50. It even has a country setting for wireless, but changing this setting to USA instead of The Netherlands improves signal strength by maybe 1-2%. Maybe if I would take the laptop further away from the router/AP this setting makes sense, I might test that later. Range at default setting seems to be good enough :). I even think the connection is a little more stable than the old Asus AP.

It looks like it doesn't have too much problems running as an AP. I'll have to test it over a longer period, but so far no big problems..

I set it up with the same settings as the old Asus AP, WPA TKIP etc. It works and I've been connected continuously to my network for 90 minutes now :). I get some "TKIP: replay detected" errors in dmesg, but as long as my connection works flawless I can't be bothered.

Group Key Update Period is the only setting with a value in time that is available. It is set to 30 seconds. I have no idea if this is similar to the WPA re-key timer..

Seriously, I would have never guessed Ubuntu/Linux doesn't like certain accesspoints. Let's make a compatibility list for that too..

[edit]And the Sweex performs very well as a router too. Even the expensive Linksys I bought a while ago couldn't satisfy me, but this seems to be able to handle enough connections. Sad thing is I don't really have any more good excuse now to keep running my Freesco box..
[edit2]No, the routing part is somewhat less responsive sometimes! I have a good excuse to plug my Freesco box back in! Though it doesn't give me timeouts when I open 5 tabs at the same time like all other hardware routers I've owned did. I think it's the best hardware router I've ever had (better than expensive Sitecom, better than expensive Linksys, better than Netgear WGR614v6). If I had to use a hardware router, I would definitely go for this one.. Amazing bargain this thing. Let's see if it can prove itself over a longer period of time as an AP.

koandy1983, I don't know where you live and if you could also get the Sweex for a low price, but I would really advise you to just drop the Asus WL-330g. As bonuses you get routing, a 4-port switch, a nice black box instead of ugly white, a removable antenna and WPA2.

---

### Post by koandy1983 on 2007-01-11
Thanks for help!

I even try with key re-timing set at 200.000.000, an the same problem, just that, that the time till blocking is increase by about 4-5h, so I bought too, an MSI WIRELESS ROUTER RG54SE with wireless stick bonus at about 50 dolars and for now it seems to be ok.

I still have the 330g and mybe some will wake us :(

---

### Post by W3ird_N3rd on 2007-01-13
Good to hear you have a working connection now :).

I started a new thread for this problem: [http://ubuntuforums.org/showthread.php?t=338072](http://ubuntuforums.org/showthread.php?t=338072). This will make people able to buy compatible hardware for now, and hopefully the thread draws some developers' attention..

---

