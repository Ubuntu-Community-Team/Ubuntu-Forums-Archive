---
title: "Problem with public BT wifi network"
date: 2013-09-24
forum: Networking &amp; Wireless
---

### Post by mattia2 on 2013-09-24
Hello! 

I am having problem connecting to BT wifi public network (using my BT account -i.e. ID and password). Actually while I always stay connected to the wifi per se, I can only browse, skype, chat, download, etc intermittently...which is very annoying...Usually to make the internet working I need to disconnect from BT wifi and then recconect till it does not work again (sometime it can be 30 seconds sometimes 10 minutes)

I know it is not a hardware problem because I have Windows also installaed on my laptop (a Dell xps M1330) and it works just fine...

I think it may have something to do with some firewall or security settings to public network (since I always connect fine to home wifi connections).


PS: for those of you might not know it BT is the main internet provider in the UK...

Thank you in advance!

---

### Post by varunendra on 2013-09-26
Welcome to the forums mattia2 ! :)

Please follow the "Wireless Script" link in my signature, download and run the script as per instruction in the linked post, and post back the report it generates. It should give us sufficient hints to figure out what may be causing the problem.

---

### Post by mattia2 on 2013-09-27
Hi! 

Thank you for your reply!

Here is the stuff you asked me to post :)

(also just so you know I tried to install ubuntu 10.04, 12.04 and also 13.04...but the interent (with the BT wifi open zone netwrok does not work).

[ATTACH]246531[/ATTACH]

---

### Post by varunendra on 2013-09-27
```
0c:00.0 Network controller [0280]: Intel Corporation PRO/Wireless **3945ABG [Golan]** Network Connection [8086:4222] (rev 02)
	Subsystem: Intel Corporation Device [8086:1020]
	Kernel driver in use: **iwl3945**
```
Aha! I love this card and this driver :D
(actually I hate it.. :|)

As you can see in the result file, it works with "iwlegacy" driver. Now the hidden meaning of "legacy" here is - *"I am an ancient junk that belongs to a museum, don't expect too much from me."* A little explanation to this is that it uses a firmware that was buggy since it was born, and Intel never cared to fix it.

But let's not scare you more with these horror stories. :)

It may be a bit comforting for you that your problem seems to be caused by some other factor, most probably the presence of 8 (or more??) access points with the same name and similar frequency/strength.

Accordingly, please try this -

Open Network Manager > Edit Connections > Wireless tab > double-click your connection (BTWiFi ??) to edit it. Under "Wireless" tab, enter the MAC ID of the access-point (that you want to connect to) in the "BSSID" field. Save and close the NM settings. Now try to connect and see if it stays any longer.

If it still breaks, please post the outputs of -
```
iwconfig
nm-tool
dmesg | grep -ie wlan -e iwl -e 80211 -e network
```

One more thing - does the initial connection get established easily? No endless efforts? Because that may be due to another reason that we better not try to fix if it is fine at the moment.

---

### Post by mattia2 on 2013-09-27
Hey!! thank you so much for your promt reply! :) :) :)

Silly question...but how do I find the MAC ID I want?

Sorry to bother you again:)

---

### Post by varunendra on 2013-09-27
No problem, I'm here because I enjoy it :)

Try the command -
```
nm-tool
```
It will show you all the available access-points with their MAC IDs, use the one you want to stay connected to.

Example line : BTWiFi:         Infra, <[COLOR="#FF0000"]MAC address here[/COLOR]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 42

---

### Post by mattia2 on 2013-09-27
mmm...there are about 6 BTwifi there! how can I know which BSSID to use (while on NM there is only 1!) :(

THank you so much again :)

---

### Post by varunendra on 2013-09-28
> **mattia2 said:**
> mmm...there are about 6 BTwifi there! how can I know which BSSID to use (while on NM there is only 1!) :(

I would choose the one whose strength seems to be strongest. For example, there are two of them like this -
```
BTWiFi:          Infra, <**MAC address A**>, Freq 2462 MHz, Rate 54 Mb/s, Strength **[COLOR="#FF0000"]24[/COLOR]**
BTWiFi:          Infra, <**MAC address B**>, Freq 2412 MHz, Rate 54 Mb/s, Strength **[COLOR="#006400"]42[/COLOR]**
```
..then I would choose **MAC address B**, because its signal is stronger (42, compared to 24 of A).

Yes it is not an optimal fix, but it is just to make sure if frequent 'roaming' from one access point to another is the cause of your problem in the first place. If yes, we may try [WICD]("https://help.ubuntu.com/community/WICD") to see if it works better than Network Manager.

On the other hand, if the above does not help making the connection stable, then the problem is something else that we'll look for afterwards. So consider it a game of pinpointing the culprit.

---

### Post by mattia2 on 2013-09-29
Hey! thank you again Varunendra!

So the way I managed to make it work is by pasting the Device MAC address that appear on NM (rather than using the command 'nm-tool') in the BSSID (as you suggested)! (see the attachment with a screen capture if I am not clear enoguh)

However, I have to do this every time I turn on my computer, or after everytime it goes to sleep, it disconnects etc... In fact as you can see from the  screen capture there are many BTwfi (1,2,3,4,5,etc)...everytime I connect to BTwifi a new BTwifi with a new number appears...is there any way to make this process automatic?

Thank you again for all your help so far...the problem is already partially solved :)

Mattia

---

### Post by varunendra on 2013-09-30
> **mattia2 said:**
> So the way I managed to make it work is by pasting the Device MAC address that appear on NM (rather than using the command 'nm-tool') in the BSSID (as you suggested)! (see the attachment with a screen capture if I am not clear enoguh)

I can't think how doing this solved your problem even partially because it is totally wrong (and probably that's why it keeps creating new connections because it can't understand this one).

What you have copied is your own WiFi card's mac address. So this configuration tells your card to connect to 'itself' !! :-\"

The SSID is the mac address of your own card, leave it untouched. The BSSID has to be the mac address of the access-point to which you want to connect. You can see that in either "nm-tool" output or that of "sudo iwlist scan".

Please try that instead. :)

---

### Post by mattia2 on 2013-10-03
Hey!! Doing it your way solved the problem completely and no new BTwifi appear!! However if I put my own mac adress this also solve the connection problem...however everytime a new BTwifi (1,2,3,4,5,6,) appears and I have to re'paste everytime my own MAC adress!  On the other hand if I leave the BSSID space blank it just keep on disconnecting!!


So i would say that the PROBLEM IS SOLVED... thank you Varunendra!

---

### Post by varunendra on 2013-10-04
Hmm.. that behaviour with its own mac address is interesting. As much as I understand, probably it detects an unusable configuration --> creates a new one --> sticks with it until next connection attempt. What I don't understand is - how does a wrong configuration help stabilizing the connectivity, even if for just one session? Perhaps it just somehow 'disables' its roaming mode, but of course this is just a wild guess. :P

Anyway -
> **mattia2 said:**
> Hey!! Doing it your way solved the problem completely and no new BTwifi appear!!

That's a great news !
We may try a couple more things if you wish, but it doesn't seem to me they will help in this kind of problem. So if you consider this workaround (definitely not a solution) satisfactory enough, please also consider marking the thread as [SOLVED] by using "Thread Tools" link above the top post.

---

