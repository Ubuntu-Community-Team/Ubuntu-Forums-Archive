---
title: "no wireless option!!"
date: 2006-12-26
forum: Networking &amp; Wireless
---

### Post by thistransition on 2006-12-26
I am trying to use a d-link wireless extender to be able to use my desktop wireless upstairs.
The D-Link extender is receiving information from wireless networks, but I do not know how to configure it to access a certain network.

IN THE HELP SECTION, IN THE PICTURE OF "NETWORK SETTINGS" THERE IS A WIRELESS OPTION BUT IN MINE THERE IS NOT!!
I think that is the main problem.

When I go to Network Settings, the only options are Wired Connection and Modem Connection, but I want to use wireless.

I downloaded "network manager" from add/remove programs but it just directed me to the Network Settings.

I tried to access the extender and router by typing their IP's, but it said no connection was found.

What should I do? thanks

---

### Post by W3ird_N3rd on 2006-12-26
The extender seems to be a sort of wireless repeater. Do you have a wireless card in your PC? If you do, what brand and chip does it have? If you don't, go out and buy one. Try to pick one that works good with Linux in that case. [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported) has a list that says what cards work well.

---

### Post by thistransition on 2006-12-26
why is there an ethernet slot in the extender then?
i just connected it directly to my PC
i thought it would just work as a wired connection but it doesnt connect..
wifiradio doesnt work either..

any ideas?
im thinkin ill have to buy a wireless card and try that

---

### Post by Hyuuga on 2006-12-26
i've got the same problem.
I have a d-link dwl-520+ wireless card and when i type lspci in the terminal it shows up as fully functional but absolutely NO wireless options are found ANYWHERE on the OS.

I remember it worked perfectly in 6.06. and i think i'll revert to that. 6.1 has been *pure* problems, i haven't experienced anything positive about 6.1 over 6.06. Just to let you know, maybe it'll help you too.

---

### Post by W3ird_N3rd on 2006-12-26
You don't have the same problem, you have a wireless adaptor for PC that *should* show up as a wireless device, thistransition connected a repeater to his ethernet port and shouldn't have any wireless options in the OS.

So I'll go look up the manual, something you also could have done yourself (you have the paper version), it must give some instructions. At least you could tell us why the troubleshooting part didn't work for you.

Okay. You should connect the repeater with the ethernet cable to your network card. Change the IP from your network card to 192.168.0.5.

Now I don't know exactly what model you have because you didn't mention it, so I'll just assume you have the DWL-G710. Please read the forum rules and give all information you have so we can help you properly.

If my model/type guess was right, you can now visit 192.168.0.30. If you can't something is wrong.

That way you can configure the device. I am however not so sure if the computers connected to the ethernet port will actually be connected to the network or if the port is just for configuring. You'll have to try that for yourself. It is an extender, so there is a chance it really only extends the range of your wireless network and is NOT capable of connecting more wired computers to the wireless network.

It looks like what you really wanted to buy is something like the Asus WL-330g - an accesspoint that's capable of running in "adaptor mode". You connect it to your ethernet port and it bridges the ethernet port to the wireless network. I don't know if that really works, I always used mine as an AP, but the manual says it can do that.

---

### Post by FLPCGuy on 2006-12-26
> **thistransition said:**
> I am trying to use a d-link wireless extender to be able to use my desktop wireless upstairs.
The D-Link extender is receiving information from wireless networks, but I do not know how to configure it to access a certain network.

IN THE HELP SECTION, IN THE PICTURE OF &quot;NETWORK SETTINGS&quot; THERE IS A WIRELESS OPTION BUT IN MINE THERE IS NOT!!
I think that is the main problem.

When I go to Network Settings, the only options are Wired Connection and Modem Connection, but I want to use wireless.

I downloaded &quot;network manager&quot; from add/remove programs but it just directed me to the Network Settings.

I tried to access the extender and router by typing their IP's, but it said no connection was found.

What should I do? thanks

 Are you accessing the extender from the router by plugging in it's RJ45 connection [that's all it is for]?  Older models used a default address of 192.168.1.30.  This gives you a web server interface for you to program it.  If it was already reprogrammed, you can reset it to the firmware default by shorting the jumper in the tiny hole with no power on.  Since this is an extender, it will by default retransmit all traffic it sees on it's network thus amplifying a weak signal to the max. 1/2 watt transmission from it's location.  In theory, this should work great but Dlink makes crap and my extender added little or no distance to effective network range.   If that's what you did, your firmware needs updating.  They may or may not have a fix on their website.  Avoid Dlink next time!  ...an old network engineer

---

### Post by thistransition on 2006-12-27
sorry about leaving out some information.
i am using the d-link DWL-G710 and am running ubuntu 6.10

w3ird n3rd, what will changing the ip to my network card to 192.168.0.5 do?

if that doesn't work, im just going to go out and buy a network card.
are there any recommendations for cards that integrate well with ubuntu linux or linux in general?  i'm looking for a mid-range card, one that will work but not too expensive

---

### Post by W3ird_N3rd on 2006-12-27
> **thistransition said:**
> sorry about leaving out some information.
i am using the d-link DWL-G710 and am running ubuntu 6.10

w3ird n3rd, what will changing the ip to my network card to 192.168.0.5 do?
It puts your network card in the same IP range as the extender, so you could reach the configuration page.
> if that doesn't work, im just going to go out and buy a network card.
are there any recommendations for cards that integrate well with ubuntu linux or linux in general?  i'm looking for a mid-range card, one that will work but not too expensive
I already gave the link, here it is again: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by thistransition on 2006-12-27
yeah i looked at that
most of those are pretty expensive though, in the $40 to $50 range. (at least the d-link ones)
my router and extender are both d-link - should i stick with a d-link network card? or does it not matter?

i know there are cards out there for 10 to 20 bucks, will any of those work ok with my machine?

---

### Post by W3ird_N3rd on 2006-12-27
That mostly depends on the chips they use.

You don't have to stick with D-link, I mix 'n' match many different adaptors/chips and AP's. There is a reason they came up with the 802.11b/g standard, they did that to make sure you could mix 'n' match AP's and different brands of cards.

---

