---
title: "Linksys wusb54gc - drops out"
date: 2008-03-08
forum: Networking &amp; Wireless
---

### Post by Capri on 2008-03-08
Hi from a Ubuntu virgin

I installed Ubuntu 7.10 a few weeks ago onto a desktop computer which had a Belkin F5D7000 wireless card installed.  I tried to get the wireless card to work without sucsess and in the process installed NDISWRAPPER (I think!)

Anyway I thaught I would go for the easy option and buy a new card that was reported to work with Ubuntu, so yesterday I took delivery of a Linksys WUSB54GC.  In a bout of optimism I simply plugged the Linksys into a USB port and was amazed to see Ubuntu recognise the card and give me a list of available networks.  I selected my network and entered the WPA code and it connected up and allowed me to surf.

After around 20mins, the connection dropped (my other pc was still connected to the router at the same time and had no problems) and I could not get it to re-connect.  In the end I restarted the computer it seemed to hang up on re-start untill I unplugged the Linksys.  When the pc had re-started I plugged the Linksys back in and was able to re-connect to the network.

Now if I connect to the network and dont try surfing, the connection seems fine and stable but if I try surfing then it drops out after a variable (but always short) time.

Can anybody sugest what might be wrong and how to sort this (it would be helpful if you assume I know practically nothing about working this OS)

Also should Ubuntu boot up with the card plugged in?

Thanks in advance

Nick

---

### Post by scottro on 2008-03-08
I used it with Fedora while trying to get my wireless working and didn't have that problem. 

I did have it plugged in while the computer booted.  Is it at all possible that yours is slighty defective?  Would it be worth exchanging it and seeing if the problem persists? 

I'm sorry, I realize that's not much help.  However, I can verify I didn't have the problem.  (The hardware was also different than yours, though.)

---

### Post by kbehel on 2008-03-08
I have the same card, and I bought it for the same reason - it seemed to have native driver support. Unfortunately, my connection dies when I've had a lot of network traffic. I haven't done web surfing (I'm doing streaming video) but it seems to be related to the amount of data transfered in a short period of time (possibly buffer overflow). I can run for a long time with low data rates, but once the rates get high, it dies pretty quickly.

I do get an error broadcast to all my consoles. If you switch to one of those with CTRL-ALT-F1 do you see an error message? Mine constantly broadcasts something about rt2x00 vendor request error similar to the bug reported in:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/133486](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/133486)

so it seems that the Gutsy kernel has an error that is causing this. I've posted some messages myself about this card and haven't gotten anywhere. I've even tried installing a more recent serialmonkey driver (the wireless drivers that this card uses) and that failed completely. If you are desperate you can try that:
[http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

but I don't recommend it. My connection went from flakey to broken when I did that.

I have not tried using the ndiswrapper drivers. That might work. If it does, please post a response so others will know about it.

If ndiswrapper doesn't work, it would probably better to just take that card back to the store and find one that does work out of the box with Ubuntu (good luck with that - I haven't found a good way to tell if a card that is currently sold in the stores will actually work without trial and error).

Kevin

---

### Post by Capri on 2008-03-10
Well, I tried following the instructions on [http://ubuntuforums.org/showthread.php?t=516649&highlight=wusb54gc]("http://ubuntuforums.org/showthread.php?t=516649&highlight=wusb54gc") and so far so good.

The computer now boots up with the wireless card plugged-in and logs into my network.  So far the internet hasnt dropped out.

When I first re-started the computer after doing this installation, it came up with several errors but these seem to have gone away (we will see!)

---

