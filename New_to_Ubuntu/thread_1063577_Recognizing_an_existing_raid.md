---
title: "Recognizing an existing raid"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by thirdrev on 2009-02-08
I currently have a dual boot with Ubuntu on an IDE and Windows on a SATA Raid, but when I boot into Ubuntu it shows the NTFS raid as two different drives. How do I get Ubuntu to recognize the existing raid (without re-formatting)? I looked at the dmraid documentation and it seemed to be directed at a new install of Ubuntu onto the raid; I do not want to install Ubuntu on the raid. Any help would be greatly appreciated.

---

### Post by blueridgedog on 2009-02-08
How is the raid array created? It it hardware (add-in card or motherboard hardware) or software (created by windows)?

---

### Post by Kellemora on 2009-02-08
Hi thirdrev

The ONLY THING that can see a Raid Array is the CONTROLLER that created it....  Controllers can be built-in, add-in, part of the MOBO or Software.........

If the Controller Fails and you cannot come up with an EXACT DUPLICATE, kiss your Raid Array Good Bye!

RAID is like playing with FIRE, you WILL eventually Get Burned!!!!!

TTUL
Gary

---

### Post by |{urse on 2009-02-08
uh.. Kellemora RAID is the smartest way to go in terms of data redundancy and safety. I would much rather my data was on a raid 5 + hotspare with AFRAID enabled. I'd rather rebuild than reinstall personally. Now if it's just raid 0, well thats fast and pointless. Also if you are stupid enough to set up a mission critical raid array wwithout purchasing a spare raid controller id say dont blame the technology, blame yourself.

---

### Post by thirdrev on 2009-02-09
> **blueridgedog said:**
> How is the raid array created? It it hardware (add-in card or motherboard hardware) or software (created by windows)?
I'm not entirely sure. There is a motherboard controller for it, and I went through a raid creation process through the bios. However, I still had to install manufacturer raid drivers in order for windows to recognize it. From what I've heard many of the supposed hardware controllers on motherboards are software, but how do I get Linux to recognize it? For the record it is a raid 1.

---

### Post by blueridgedog on 2009-02-09
It sounds like the raid is created more through the windows software than through the motherboard (otherwise ubuntu would see it).  What is the make/model of the motherboard?  Perhaps we can search on the raid that is build in and find an answer.

---

### Post by thirdrev on 2009-02-09
> **blueridgedog said:**
> It sounds like the raid is created more through the windows software than through the motherboard (otherwise ubuntu would see it).  What is the make/model of the motherboard?  Perhaps we can search on the raid that is build in and find an answer.

It's a PC Chips A15G
[http://www.pcchips.com.tw/PCCWebSite/Products/ProductsDetail.aspx?DetailID=407&CategoryID=1&DetailName=Feature&MenuID=123&LanID=2](http://www.pcchips.com.tw/PCCWebSite/Products/ProductsDetail.aspx?DetailID=407&CategoryID=1&DetailName=Feature&MenuID=123&LanID=2)
It does seem to be a software RAID; my only confusion in that regard comes from the disks being recognized as a RAID at POST.

---

### Post by thirdrev on 2009-02-09
According to the manual for the motherboard - it uses NVIDIA RAID BIOS to set up the RAID.

---

### Post by Kellemora on 2009-02-10
Hi Urse

I agree with you for situations that REQUIRE the speed and rebuild capabilities of a Professional Raid 5 or better system!

But a home user has little to no need for the extra speed (if any) from using a software Raid array and will normally end up losing ALL of their data because of it.

Can you imagine what the world would be like if EVERYONE drove a Tractor Trailer to work every morning and home every night instead of a car.  Just so they had ALL THAT ROOM in case they see something they want to pick up alongside the road.

So I'll repeat, using Raid is like playing with FIRE, you WILL get burned, if not today or tomorrow, then the day after!

On-board Raid only gives a FALSE sense of security!
If that controller fails (and 99% of those who use on-board Raid do not have a spare controller laying around) Not IF, but WHEN that controller fails, they are SOL and have NO BACKUP because they THOUGHT that was what Raid was supposed to do!

TTUL
Gary

---

### Post by thirdrev on 2009-02-15
**Solution**
Nothing quite like solving your own problem... 
for others out there I will explain what worked for me: 
first, I should point out that I have a bios Raid setup utility which I had used for my fakeraid ( don't know if that matters, but it may be a factor). 
Whenever I was running [COLOR="Blue"]sudo dmraid -ay -v[/COLOR] it would spit out: 
[COLOR="DarkRed"]ERROR: via: invalid checksum on /dev/sdb
ERROR: via: invalid checksum on /dev/sda
RAID set "nvidia_dadbbhhb" already active[/COLOR]
So my raid was seen, just not mounting. The only thing I found to work was creating an executable for startup to mount the drive using the mount command
run
[COLOR="Blue"]sudo gedit /etc/init.d/<myscript>

[COLOR="Black"]and insert into the file[/COLOR]
sudo mount -t ntfs-3g /dev/mapper/<myraid>  /<mymountlocation>[/COLOR]

once the file is created you need to make it executable:
[COLOR="Blue"]sudo chmod +x /etc/init.d/<myscript>[/COLOR]

then set it to run at startup:
[COLOR="Blue"]sudo update-rc.d myscript start 51 S .[/COLOR]
(don't miss the period at the end)

Note: 
the name for <myraid> should be found listed at /dev/mapper/ 
<myscript> and <mymountlocation> can both be named whatever you want, but <mymountlocation> needs to refer to an *existing* folder. 
I had been trying to refer to a folder I had not yet created and ran into errors.

BTW I'm running 8.10 32bit from the alternate install cd, 
but given the output I was getting when I was running 8.10 64bit off the regular install 
this probably would have worked to fix the problem for 64bit as well, 
but I had already reinstalled in an effort to solve the problem before I found the eventual solution.

---

