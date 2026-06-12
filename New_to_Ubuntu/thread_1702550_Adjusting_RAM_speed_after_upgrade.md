---
title: "Adjusting RAM speed after upgrade"
date: 2011-03-07
forum: New to Ubuntu
---

### Post by SebSmith on 2011-03-07
(LINUX Novice)

Ok so previously i had a 4gb 10600 1333mhz ram chip.

i just bought and installed 2x4gb 12800 1600mhz ram chips. 
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820104230](http://www.newegg.com/Product/Product.aspx?Item=N82E16820104230)

when i run memtest86+ or whatever it is it still states my ram is the same speed as the latter, however it does notice the increase in capcity.

after some google-ing i found i should alter the ram speed and timings through bios.

I do not see a ram speed adjustment option or anything of the sort. my bios says InsydeH20 at the top and in the computer specifications says Insyde F. 23.

How do i change my speeds and timings to the advertised, and make it recognized in Win7 as well as Ubuntu.

I have a dual boot configured HP Envy 14 Laptop.



Thanks in advance!

---

### Post by Learning Linux 2011 on 2011-03-07
Well, it would have to be in the BIOS.  Not all BIOS's support changing memory speeds.  Manufacturer's such as HP tend to not allow that sort of thing.  

If it isn't in the BIOS, It is possible that Memtest may not be capable of recognizing the RAM you have.  I ran into that problem once.

---

### Post by SebSmith on 2011-03-08
> **Learning Linux 2011 said:**
> Well, it would have to be in the BIOS.  Not all BIOS's support changing memory speeds.  Manufacturer's such as HP tend to not allow that sort of thing.  

If it isn't in the BIOS, It is possible that Memtest may not be capable of recognizing the RAM you have.  I ran into that problem once.


is there no way around this? software was made to make the hardware run correctly, right?

---

### Post by Jerry N on 2011-03-08
In the first place, your new memory sticks may not run as fast as advertised and, in the second place, your computer figured out how fast to run the RAM the first time it was booted up.  On a laptop computer you are really limited in what you can do to the configuration.  If you find a way to change the RAM timing, you might well find yourself with an non-operating computer.  Do I need to explain how I know that?:):)

---

### Post by Jerry N on 2011-03-08
> **SebSmith said:**
> is there no way around this? software was made to make the hardware run correctly, right?

Actually, the hardware is there to make the software run correctly:P

---

### Post by SebSmith on 2011-03-08
> **Jerry N said:**
> In the first place, your new memory sticks may not run as fast as advertised and, in the second place, your computer figured out how fast to run the RAM the first time it was booted up.  On a laptop computer you are really limited in what you can do to the configuration.  If you find a way to change the RAM timing, you might well find yourself with an non-operating computer.  Do I need to explain how I know that?:):)


...............................did i waste money?

---

### Post by Learning Linux 2011 on 2011-03-08
Well, it depends on how you look at it.  If you payed alot extra for the faster RAM then it may have been a bit of a waste, however from your post I guess you now have 8 GB rather than 4, which may not be a waste.

SOME motherboards and computers DO support adjusting RAM speeds, but generally they don't.

Software doesn't actually make the hardware run correctly.  The software doesn't actually influence the hardware.

---

### Post by slooksterpsv on 2011-03-08
> **SebSmith said:**
> ...............................did i waste money?

Not necessarily, you can also check for BIOS updates to allow for the faster RAM speeds, more options, etc. Granted that doesn't mean that you will get the faster RAM speed.

One way to avoid this in the future is to find the documentation on your computers hardware (especially if it's from an OEM like Dell, HP, Acer, etc.). Sometimes they cap the specs out, or you have to have a specific CPU to get higher speeds or what not.

Example:

My motherboard won't allow for 1066MHz RAM unless I have a specific CPU, and even then can I only install 2 chips (even though I have 4 slots) due to the limitations on the board.

---

### Post by SebSmith on 2011-03-08
> **slooksterpsv said:**
> Not necessarily, you can also check for BIOS updates to allow for the faster RAM speeds, more options, etc. Granted that doesn't mean that you will get the faster RAM speed.

One way to avoid this in the future is to find the documentation on your computers hardware (especially if it's from an OEM like Dell, HP, Acer, etc.). Sometimes they cap the specs out, or you have to have a specific CPU to get higher speeds or what not.

Example:

My motherboard won't allow for 1066MHz RAM unless I have a specific CPU, and even then can I only install 2 chips (even though I have 4 slots) due to the limitations on the board.


HP has made it known to me that they wont be able to identify specifically what motherboard i have because the tech staff doesnt even know. however, if this helps, i have an i7-740 1.73ghz processor.

where can i get bios upgrades and how can i tell if this will have the ram speed option for me? i just got this computer 2 weeks ago.  

what are some things i should look for and where to get the 1600mhz speed working like i expected?

---

### Post by slooksterpsv on 2011-03-08
> **SebSmith said:**
> HP has made it known to me that they wont be able to identify specifically what motherboard i have because the tech staff doesnt even know. however, if this helps, i have an i7-740 1.73ghz processor.

where can i get bios upgrades and how can i tell if this will have the ram speed option for me? i just got this computer 2 weeks ago.  

what are some things i should look for and where to get the 1600mhz speed working like i expected?

HP.com - You'll have to search by your computers make/model - e.g. Presario NZ9005S - or what not. That's where you'll need to get the BIOS updates, specs, etc. from. Also, if the i7 is a Sandy Bridge, make sure that you check for any recall notices, as the Sandy Bridge CPUs were recalled by Intel due to performance degradation.

---

### Post by SebSmith on 2011-03-08
> **slooksterpsv said:**
> HP.com - You'll have to search by your computers make/model - e.g. Presario NZ9005S - or what not. That's where you'll need to get the BIOS updates, specs, etc. from. Also, if the i7 is a Sandy Bridge, make sure that you check for any recall notices, as the Sandy Bridge CPUs were recalled by Intel due to performance degradation.


where do i check? and wtf is a sandy bridge? lmao.

---

### Post by Zeno Izen on 2011-03-08
> **SebSmith said:**
> where do i check? and wtf is a sandy bridge? lmao.

to get your motherboard model open a terminal and try "sudo dmidecode | more" 

look for the block that says "Base Board Information"

---

### Post by SebSmith on 2011-03-08
> **Zeno Izen said:**
> to get your motherboard model open a terminal and try "sudo dmidecode | more" 

look for the block that says "Base Board Information"

# dmidecode 2.9
SMBIOS 2.6 present.
30 structures occupying 1426 bytes.
Table at 0x000E9000.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: Hewlett-Packard
    Version: F.23
    Release Date: 11/11/2010
    ROM Size: 2048 kB
    Characteristics:
        PCI is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        Selectable boot is supported
        EDD is supported
        Japanese floppy for NEC 9800 1.2 MB is supported (int 13h)
        Japanese floppy for Toshiba 1.2 MB is supported (int 13h)
        5.25"/360 KB floppy services are supported (int 13h)
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 KB floppy services are supported (int 13h)

---

### Post by SebSmith on 2011-03-08
oh sorry..

Base Board Information
    Manufacturer: Hewlett-Packard
    Product Name: 1437
    Version: 59.23
    Serial Number: PBULT00QE0B01H
    Asset Tag: Base Board Asset Tag
    Features:
        Board is a hosting board
        Board is replaceable
    Location In Chassis: Base Board Chassis Location
    Chassis Handle: 0x0003
    Type: Motherboard
    Contained Object Handles: 0

---

### Post by Zeno Izen on 2011-03-08
> **SebSmith said:**
> oh sorry..

Base Board Information
    Manufacturer: Hewlett-Packard
    Product Name: 1437
    Version: 59.23



Well that's your motherboard, right there.  I don't know if the Version # is relevant.  I'd guess that it is.  

So you can use that info to search whether your board supports 1600Mhz in the first place, find a BIOS update, and so on.  ... even though I'm googling it myself and not finding it.

... hang on a sec

---

### Post by SebSmith on 2011-03-08
> **Zeno Izen said:**
> Well that's your motherboard, right there.  I don't know if the Version # is relevant.  I'd guess that it is.  

So you can use that info to search whether your board supports 1600Mhz in the first place, find a BIOS update, and so on.  ... even though I'm googling it myself and not finding it.

... hang on a sec


ive been having the same kind of results you are. like i fully understand when people tell me to google it, and i do, but my problems usually dead end at a certain point like this. its like nobody is ever dumb enough to run into my problems lol.

---

### Post by Zeno Izen on 2011-03-08
> **SebSmith said:**
> ive been having the same kind of results you are. like i fully understand when people tell me to google it, and i do, but my problems usually dead end at a certain point like this. its like nobody is ever dumb enough to run into my problems lol.

It's just a question of patience.  The problem here is that manufacturers do weird things that make a what should be a simple problem like this a little bit more obscure.

There are several Envy 14s... is yours say a 1090ee or something like that?

---

### Post by SebSmith on 2011-03-08
> **Zeno Izen said:**
> It's just a question of patience.  The problem here is that manufacturers do weird things that make a what should be a simple problem like this a little bit more obscure.

There are several Envy 14s... is yours say a 1090ee or something like that?


i believe it was 14-2000

sorry no its 14t-1200 CTO

---

### Post by mcduck on 2011-03-08
Amazingly nobody has stated this yet: 

If you now how all the 8GB of RAM plugged into the system, you shouldn't even bother trying to get a BIOS update for the ability to adjust RAM speed higher, it's useless. The speed would still be limited by your old RAM modules...

(And having the whole 8GB of RAM in your machine will give you better performance anyway than throwing away the old 4GB and running with only the new faster 4GB modules would, even if you were able to adjust the BIOS settings to run at their full speed)

---

### Post by Zeno Izen on 2011-03-08
> **mcduck said:**
> Amazingly nobody has stated this yet: 

If you now how all the 8GB of RAM plugged into the system, you shouldn't even bother trying to get a BIOS update for the ability to adjust RAM speed higher, it's useless. The speed would still be limited by your old RAM modules...


Some reason I assumed OP had pulled the old RAM.

> 
(And having the whole 8GB of RAM in your machine will give you better performance anyway than throwing away the old 4GB and running with only the new faster 4GB modules would, even if you were able to adjust the BIOS settings to run at their full speed)

OP would be up to 12GB at this point, right? 1x4 of the old and 2x4 of the new.  

In any case, I can't find this motherboard anywhere.  But HP.com says the 14-1200 runs at a max of 1333Mhz, so maybe the 14t-1200 cto does too.

---

### Post by mcduck on 2011-03-08
> **Zeno Izen said:**
> Some reason I assumed OP had pulled the old RAM.



OP would be up to 12GB at this point, right? 1x4 of the old and 2x4 of the new.  

In any case, I can't find this motherboard anywhere.  But HP.com says the 14-1200 runs at a max of 1333Mhz, so maybe the 14t-1200 cto does too.

Good point about the 12GB, for some reason I didn't notice that it was 2x**4**GB.

The OP said in the first post that memtest recognizes the increase in capacity, which is why I assumed he had both old and new RAM modules plugged in. Of course if there's 8GB of the new RAM then that would indeed increase the capacity even without using the old modules together with new ones... :)

Edit: I was actually just trying to find the same information about the max supported RAM speed of the motherboard, but it seems the info for 14-1200 is as close as we are going to get, the "CTO in the model name means "custom-to-order" and HP doesn't provide any specs of such machines. Anyway, 1333MHz would make sense as that's also the spec speed for the i7-740.

---

### Post by Jerry N on 2011-03-08
Even if the OP were to get the new RAM to run at 1600 I doubt that he would see a really significant speed improvement over running at 1333.  That's not a very big change and RAM speed is only one factor in overall performance.  And the various (not understood by me) RAM timing options have to be considered too.  Another factor to consider:  Most laptop computers have marginal internal temperature control and upping the RAM speed might cause the temperature to rise beyond acceptable limits.

Jerry

---

### Post by SebSmith on 2011-03-08
To clarify so confusion, i removed the old ram chip and inserted two 4gb ram chips.
the laptop only has space for 2 chips so no i dont have 12gb, i have 8.

now because the i7-740qm says it only supports 1333, does that mean i will never be able to run my ram at 1600mhz? 

what if i upgrade my processor in the future (which ive researched is possible because it is not welded in on this machine)?

---

### Post by SebSmith on 2011-03-08
> **DGINSD said:**
> Click on one of the forum titles "absolute beginner forum" which will give you a list of all threads at the top of the list theres a button for "New Thread" 

Sorry for the side track guys, carry on, I'm learnin a lots from your discussion.


this really is a great discussion, but its disappointing at the same time.. i paid a lot for this nice ram. id love for it to work at potential

---

### Post by DGINSD on 2011-03-08
I feel your pain sucks to pay good money for something and not have it work as you expected, even though as someone else stated the performance gain would me minimal with the RAM speed increase.

What I'm taking away from this is do diligent reaserch first and upgrade second. Even still there always seems to something that gets over looked.

Even still 4G to 8G wooooo hoooooo game on!

---

### Post by Zeno Izen on 2011-03-08
> **SebSmith said:**
> this really is a great discussion, but its disappointing at the same time.. i paid a lot for this nice ram. id love for it to work at potential

Ok here's a few suggestions:

1.  dmidecode seems to have turned up bunk info for your motherboard.  Since your machine is new, you might actually still have the physical documentation.  Try to find your motherboard docs, they should have the exact model info.  Once you have that, contact HP and simply ask "What's the fastest RAM motherboard xyz can support."

2.  If you find that you board only supports 1333 not the full 1600 that you bought, check newegg's return policy.  They might possibly trade it in for the slower RAM.  

3.  Unless I'm mistaken upgrading your CPU won't help your max RAM speed.  It's the Northbridge on the motherboard that limits you.  

Honestly, based on what the other posters have said, I'd lay my money on the probability that you're not capable of the full 1600 with this motherboard. And trying to tweak your gear up to match the RAM isn't really worth the trouble or risk. 

I would go straight to deciding whether you want to try to recoup your money.  Is the price difference between the 1600 sticks and the 1333s really that great?  Like I said, Newegg might let you swap them.  Or, if it really comes down to it, you can buy the slower RAM and try to sell the faster ones on eBay, or something like that.

---

### Post by jocko on 2011-03-08
> **I_am_trainee said:**
> Don't see what you say below. Can you provide suitable link/graphic image for what I should be looking for because I just don't see it? Try a print screen screenshot.
[Here.]("http://ubuntuforums.org/attachment.php?attachmentid=185495&stc=1&d=1299618835")

---

### Post by sydbat on 2011-03-08
> **Zeno Izen said:**
> 3.  Unless I'm mistaken upgrading your CPU won't help your max RAM speed.  It's the Northbridge on the motherboard that limits you.This. 

[FSB]("http://en.wikipedia.org/wiki/Front-side_bus") (Front Side Bus) is what controls the speed at which your motherboard can process the RAM frequency. This setting is configured below the maximum for good reason. However, it also allows the manufacturer to release BIOS updates to marginally increase the speed if they find that new CPU's or RAM require it.

Also, BIOS updates are only released / needed if something is not right with the original BIOS or if it will add functionality (as I mentioned above). Therefore, at this time, I would imagine that the OP will not find an updated BIOS from HP. 

As for the RAM the OP bought, why not just run it as is. It has been mentioned that there is little performance difference between 1600 and 1333, and because you have doubled the RAM in the first place, you will see an increase in the availability of system resources.

---

