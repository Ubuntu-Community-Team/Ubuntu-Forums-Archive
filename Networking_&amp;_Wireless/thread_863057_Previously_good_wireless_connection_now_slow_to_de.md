---
title: "Previously good wireless connection now slow to dead"
date: 2008-07-18
forum: Networking &amp; Wireless
---

### Post by sofasurfer on 2008-07-18
Belkin Wireless G router. Linksys wusb54gc.

Heres my current status. With a wired internet connection there is no problem. But with wireless the connection is stalled.

With the pc in the same room as the router I will get messages that data is being transferred and connections have been made. Sometimes the page will load after a few minutes and more often than not, I give up waiting for it.

Now if I take the pc to the other room, on the other side of the wall from the router, and only about 6 feet away, the web pages always time out. There is no connection.

This problem started a few days ago. Until then I had a good internet connection.

Did my wireless adapter go bad?

Where do I begin?
I'm using automatic configuration, WPA personal, disabled roaming.

---

### Post by schmildo on 2008-07-18
Hmm...
Be wary of interferrance from other devices. 
Cordless phone handsets/basestations & microwaves & hairdryers can give you grief. When i'm testing wireless faults like this I even turn off lights and electric heaters. Wireless interferrence can come from anywhere. A friend of mine has found that his digital TV reception goes astray every time his neighbour mows the lawn!

Changing the channel that your wireless router uses might help.They often default to channel 11, or 'auto'. Try something different like 1 or something. You might find that your problem is simply that a neighbour has just bought and turned on thier own router.

The problem could of couse also be the wireless card in the laptop/desktop you're using, but that will involve more hassle. Using a tool like 'kismet' might help you identify bad packets being sent over the air, and indeed even find if someone else in your area is using the same channel.

But if yo have the oportunity; always fault-find the hardware first, it is so much faster. (so if you have a spare usb wireless adapter try it out)

Oh and when you're testing the connection, i'd suggest using 'ping' from the console, and not a web browser, that way you can watch it update constantly and you can reduce the likleyhood that the problem is software related.

Rock on.
:guitar:

---

### Post by sofasurfer on 2008-07-18
You are a genious. I changed to channel 1 and my connection was back and working good, or as good as it ever did. This was in the same room as the router. When I took it out of the room, to the other side of the wall from the router, the connection was still vastly improved, although it did slow down. 

Before I consider this a 'fixed situation' I will monitor it for a day or two.

I do not think a 'good' connection should slow down at all over a space of a few feet, which has always been the case for my connection. So I assume that I still have a problem that I would like to fix. I shall try differant channels and also I will try unplugging the phone, etc.

What other things might I try, and also, is there a web site or a method that tells me the true speed (actual, not theoretical) of my connection so that I might be able to be sure of any improvements or unimprovements that I might make? 

I have read of people wanting to have a wireless network spread out over a hundred feet or more. What kind of distances can you have between computers on a wireless network and still have a reasonably good speed?

Thanks.

---

### Post by schmildo on 2008-07-18
LOL. You're right a good connection should not slow down like that at such a short distance.

I've asked the same question about getting a speed tester. And everyone just looks at me like i'm and idiot and says "Just transfer a file." I got sick of this response and one day I went looking for a program to do wireless speed/quality checking. What I found was an ancient cruddy console program that was difficult to use.
  I gave in and tested the network by sending a video file across the network and timing it to calculate the speed.

*Googling it now....*
(Well i just found out how to do it in windows; and in doing so found a tool i'll be sure to use in the near future)

MSDOS COMMAND:
fsutil file createnew test.txt 1024

LINUX COMMAND:[COLOR=#C20CB9][B]
dd[/B][/COLOR] [COLOR=#007800]if=[/COLOR]/dev/zero [COLOR=#007800]of=[/COLOR]test[COLOR=#C20CB9]****[/COLOR].txt [COLOR=#007800]bs=[/COLOR]1024 [COLOR=#007800]count=[/COLOR][COLOR=#000000]10[/COLOR]The dos command creates a file of 1024 bytes.
but the linux command creates a file of 10 meg= 1024Kb*10.

So just be wary that the linux command is working in kilobytes, multilpied by some count. You can change either the 'bs' or the 'count' value to create a file of any size.

So make a filesize large enough that you can run from one computer to the next with a stopwatch. (I use my phone's stopwatch) And it also needs to be large enough that you'll get a decent calculation of your average transfer rate.

Then you should be able to calculate the number of meg/kilobytes per second. If you wanted to match it up with how fast your wireless can go you have to do another calcuation. Routers are designed by engineers who seem to work in the horrible Bits per second world. And their definition of Mega is differnt from mine. They use the mathematical definition of 1000*1000=1,000,000 and not 1024*1024=1,048,576 as you can see the difference is not insignificant.
  The link below has some info on expected speeds. "It is fairly common in homes for 802.11g connections to made at 36 Mbps, 24 Mbps, or even lower numbers."
[http://compnetworking.about.com/od/wirelessfaqs/f/howfastis80211g.htm](http://compnetworking.about.com/od/wirelessfaqs/f/howfastis80211g.htm)

Later today I'll try to test out my own connection here to give you a real-world example. Unfortunatly i can't do it right now because i'm logged onto a domain, and the other computer isn't.

It's hard not to feel like an olympic coach, with a whistle & track-suit pants, encouraging his atheletic packet data to race across the network.

---

### Post by sofasurfer on 2008-07-18
I seem to remember a web site that was devoted to "ping". I'm trying to find it. It was a huge pile of information on useing "ping". I bet there is some way to use "ping" to test speed.


EDIT::
I just did a search for "ping" and it CAN be used for testing and troubleshooting connections. Here are a few good looking links for anyone who wants to learn how to use it. It looks to me like a tool that we all should have some knowledge of.

[http://www.livinginternet.com/i/ia_tools_ping.htm](http://www.livinginternet.com/i/ia_tools_ping.htm)
[http://www.more.net/technical/pingtrace.html](http://www.more.net/technical/pingtrace.html)
[http://www.ping127001.com/pingpage.htm](http://www.ping127001.com/pingpage.htm)

---

### Post by sofasurfer on 2008-07-19
This is rediculous. My connection was fixed when I changed channel but shortly died again. I can connect with a wired connection to router but wirelessly I am dead. I get "connecting" messages and "transferring" messages but nothing ever loads. I tried more channels and it makes no differance. Why did it make a differance at first when I changed to channel 1? Could my adapter be dead? Its a linksys WUSB54GC.

I hate to have to get a new adapter and go throught he configuration stuff again. But if I do I will get a pci this time. Any recommendations for a quick and easy install?

---

### Post by schmildo on 2009-02-07
SOrry ; late reply...  i'm not sure what hardware would be easier to deal with... 
i hope you have got it fixed.

---

