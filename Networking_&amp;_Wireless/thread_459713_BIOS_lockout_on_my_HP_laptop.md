---
title: "BIOS lockout on my HP laptop"
date: 2007-05-30
forum: Networking &amp; Wireless
---

### Post by Mime on 2007-05-30
A few days ago I sit down with a brand new Intel 2200BG itty-bitty miniPCI card and open up the back of my laptop.  I yank out the dreaded broadcom 4318 controller with extreme joy and pop  the Intel card in only to be greeted by an indignant beep during post and the following error message.

> 104-Unsupported wireless network device detected.
System Halted. Remove device and restart.

It seems that HP/Compaq, and IBM are invoking this kind of restrictions with their laptops, and have been for the past few years.  There's a check in the BIOS that looks in a whitelist of specific PCI IDs.  If the ID of the card isn't in the list, then the machine doesn't boot.

After doing a little digging it looks like there's more than a few different ways around it, but all of them seem to have gone stale and don't work very well with current systems.  In particular, I've been looking at using ethtool to modify the EEPROM of the card in order to change the device, vendor and subsystem IDs so that the BIOS still thinks I have the broadcom controller in there.  Being a poor college student and all that's about the only choice I have since I really can't risk modifying the BIOS its self and possibly hosing the entire machine.  I've located the specific offsets I need to change, I'm just not quite sure how to change them.  I'd also have to modify the firmware of the driver in order to recognize the new IDs, which I'm not sure how to do either.  I can't believe that I'm the only one who has recently tried to trade a BCM4318 for 2200BG against this kind of restriction.  Anyone that can point me towards some more recent information on how to get this card working will have one geeks eternal gratitude.  :p

The laptop is an HP L2000, which is identical component-wise to the Presario V2000, but seems to have a slightly different bios.

---

### Post by Mime on 2007-05-31
Yay!  All better.  \\:D/

After a while spent hacking drivers and whatnot everything's back to normal again.

---

### Post by fastpakr on 2007-08-10
Can you elaborate on what method got you up and running?  I've got a Compaq F572us that I just switched cards on (from the factory Broadcom to a Gigabit brand card with an Atheros chipset).  I'm getting the exact same message and am a little leery of editing the ROM file for the BIOS flash.  I'd love to see what got you going.

---

### Post by mips on 2007-08-10
I had exactly the same issue and also hacked my Intel card so the hp laptop accepts it. The is a very long thread about this on the HP forums that explains it in detail.

[http://forums1.itrc.hp.com/service/forums/questionanswer.do?threadId=567021&admit=-682735245+1186750551124+28353475](http://forums1.itrc.hp.com/service/forums/questionanswer.do?threadId=567021&admit=-682735245+1186750551124+28353475)

-

---

### Post by fastpakr on 2007-08-10
Thanks - I spent some time reading through that.  I'm a bit at a loss though - the Gigabyte GN-WI01GT uses an AR5005 chipset which is write protected.  Also, the BIOS is not setup with a .rom file that I can open, and there's no DOS based flash utility.  I got this card because it's the only Atheros based Mini PCI-E card I found, and the Intel card (3945) doesn't appear to be consistently compatible with Linux outside of using ndiswrapper (which I'm trying to get out of by dumping the OEM Broadcom based card).

---

### Post by Prometheum on 2008-01-05
Can any of the people who solved this post how they did or links to where they got the information, as well as their hardware? I have an HP dv9700 that came with the ONE unsupported Atheros chipset, so I'm trying to replace it with my well-supported AR5BXB6. However, I'm deathly afraid of bricking my laptop, and while I've read of being able to restore it off of a floppy, I'm still not very enthused and want as much information as possible. If anyone who got this to work could post how, I'd be greatly indebted.

---

### Post by mips on 2008-01-12
> **Prometheum said:**
> Can any of the people who solved this post how they did or links to where they got the information, as well as their hardware? I have an HP dv9700 that came with the ONE unsupported Atheros chipset, so I'm trying to replace it with my well-supported AR5BXB6. However, I'm deathly afraid of bricking my laptop, and while I've read of being able to restore it off of a floppy, I'm still not very enthused and want as much information as possible. If anyone who got this to work could post how, I'd be greatly indebted.

I supplied a link above, [http://forums11.itrc.hp.com/service/forums/questionanswer.do;HP-FORUMS-S-WPA-IDX=HJDJqvBqVfKk3mp2cvbZsZxGvFz5KJxbZWTBT7HHptpJR0p1G5K5!1854719599!1430012849?admit=109447626+1200161716919+28353475&threadId=567021](http://forums11.itrc.hp.com/service/forums/questionanswer.do;HP-FORUMS-S-WPA-IDX=HJDJqvBqVfKk3mp2cvbZsZxGvFz5KJxbZWTBT7HHptpJR0p1G5K5!1854719599!1430012849?admit=109447626+1200161716919+28353475&threadId=567021)
which should provide a solution to the problem.

I personally did not modify my laptops BIOS as I have an Intel2200 wireless card of which I modified the cards firmware as per one of the solutions in the above link.

When I did this there was no laptop bios hack available at the time.

---

