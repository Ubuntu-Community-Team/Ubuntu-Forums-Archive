---
title: "Wireless Hardware disappeared after system update"
date: 2008-04-20
forum: Networking &amp; Wireless
---

### Post by tendrousbeastie on 2008-04-20
Hi all,

I've just last night installed Ubuntu (7.10) on my laptop and have hit a problem. I've spent the past few hours Googling it but can't find a solution, even though it does seem to be a common enough problem.

The install worked fine, and I was very glad to note that it picked up my wifi automatically and allowed me to connect to my WPA2 encrypted network no problem.

So I spent some time on it, browsing and seting up email accounts and such and everything was good.

But this morning I was prompted to install about 230MB of system updates, which I did. This seems to have caused my Wireless Network card to disappear completely from the computer.

It didn't happen sraight away, perhaps 30 mins after the updates were installed.

Now, not only do I not have any wireless interface (I only have eth0 now), but I can find no evidence of the wireless hardware exsiting. The hardware information panel doesn't list it, lspci -vv doesn't list it, there is no reference to it that I can see in my dmesg output.

Has anybody any ideas as to what I can do? I really like using Ubuntu and don't want to have to go back to XP, but without Wifi the laptop is useless to me.

Please assume I have no Linux experience and that I will need things explaining to me.

Thanks for any help.

---

### Post by tendrousbeastie on 2008-04-20
UPDATE: It seems that Ubuntu has actually crippled the hardware. Booting back into XP (the system is set up for dual booting) show the wireless card has disappeared from the device manager and I have an 'unknown device' instead that refuses to accept any drivers. No diagnostic tool that have so far used under XP show the presence of a wifi card under that system.

So well done Linux, you've fried my computer.

---

### Post by Zorael on 2008-04-20
I'm not even sure Linux **could** cripple the hardware in the way you're describing. I'd chalk it off to unfortunate circumstances. Blame where blame's due.


> **tendrousbeastie said:**
> It didn't happen sraight away, perhaps 30 mins after the updates were installed.
This makes it seem even more plausible that it was, in fact, not the Linux handling the device wrong, but rather a hardware failure creeping up on your machine. And it just happened to occur close to an update.

---

### Post by lswest on 2008-04-20
i don't see how software can cripple hardware, unless the device was running at speeds or performance levels it wasn't intended to run at.  Chances are the card just decided to break, especially if it happened 30 minutes after an update, and i don't suppose you remember if any of the updates installed mentioned networking?

Before you blame linux, take the card out of the PC (unless it's a laptop) and check it for physical defects/broken parts.  Also, how long have you had it?  Lastly, if it's a PC, why not just keep it on a wire?

---

### Post by tendrousbeastie on 2008-04-20
Its a laptop so there's no way to test it on another system.

Seems rather a coincidence that I've had the laptop running hours everyday for a year or so under XP with no problem, and then 1 evening with Linux and it breaks down.

The reason I wasn't so surprised about the 30 minute  os so delay is that I found out from Googling the issue that several people had experienced similar issue after updates were installed, but these issues only manifested themselves

---

### Post by tendrousbeastie on 2008-04-20
Hi,

Yeah, I should probably calm down and stop blaming Linux with no evidence. Sorry. It just does seem to be a bit of a coincidence that a year of using it under XP and there's no problem, 1 evening of Ubunutu and it stops working.

Anyway, oddly enough it seems to be a BIOS issue. I've booted back into XP and flashed the BIOS with a new copy (actually the same copy of the BIOS software as was already on there), and now I have the wifi card back on both Linux and XP.

Is Linux likely to have made any changes to my BIOS for any reason that you know of, or is this just a chance event that could have happened any time? I just wonder in case it happens again.

---

### Post by mahalie on 2008-06-29
My wireless disappeared as well after doing system updates. I've been using wireless on my laptop with Ubuntu as the only OS for over a year just fine. But now it's just gone. 

I'm not sure how to flash my BIOS - can someone point me in the right direction?

---

### Post by chriswyatt on 2008-06-29
I know this might seem obvious, but have you checked you haven't flicked a WiFi on/off switch, I've accidentally switched that off lots of times, I think it's when I take my laptop out of my bag.  I remember spending ages trying to figure out how to get the WiFi to work with no avail, sometimes it's as obvious as that :P .

And, that would explain why WiFi doesn't work in both XP and Linux, although I don't think the switch actually disables the hardware through the BIOS, because I remember when I first installed Ubuntu this function didn't work :S .  Maybe it's different for different PCs/Laptops.

---

