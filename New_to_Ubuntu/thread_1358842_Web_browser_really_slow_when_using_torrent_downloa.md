---
title: "Web browser really slow when using torrent downloader"
date: 2009-12-18
forum: New to Ubuntu
---

### Post by mattguitar on 2009-12-18
HI. Im new to ubuntu and it works great, its easily customizable and I love it. never going back to windows if I can help it. 

Problem is that the web browser slows to a crawl when using the transmission bit torrent. 
when dowloading torrents transmission might be going at 100-150 Kb/s but the mozilla firefox will take 15-60 seconds to load a simple page such as yahoo.com. as soon as I pause my transmission, the web browser returns to normal speed. even when I might not have alot of seeds and transmission is going slow like 10 Kb/s, the web browser is still slow till I pause.  any ideas why this is or could you recommend a different bit torrent program? Ive tried vuze and its too much crap, I want a simple program to download my torrents. 

speedtest.net reports my connection as 3.02Mb/s down, 0.32Mb/s up, 80ms ping
when things are working right I usually get 300-350k downloads regularly. 
I am using a belkin USB 1.1 wireless G.  linksys router, earthlink.

thanks for your help!    :guitar:

---

### Post by herbertportillo on 2009-12-18
Slow browsing while using a torrent is normal. The faster your computer's upload speed, the slower your download speed will be for browsing.

You can limit the upload speed in Transmission by clicking the gear icon at the bottom left and select the Limit Upload Speed menu and choose your desired upload speed instead of an unlimited upload speed. That should improve your browsing speed. Cheers.

---

### Post by lovinglinux on 2009-12-18
You need to limit your UPload speed to 80% of your bandwidth UPload limit. See why and other tips at [BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923).

---

### Post by themusicalduck on 2009-12-18
A more lightweight torrent downloader is Deluge which is what I use. Transmission is good too, and maybe even slightly more lightweight. I personally prefer Deluge though. Both are in the software centre.

---

### Post by joes7 on 2009-12-18
That is, as said by previous posters, something completely normal;torrent downloaders use a high percentage of resources, including browsing speed.

---

### Post by nortym on 2010-01-22
I have such problem me to, but i didnt have it for a week ago :(
I have dual boot, and when i start in windows i can download witch full speed and brows pages in chrome...
my internet connection is:
100 Mbit/s down, measuerd 99.94 Mbit/s
10 Mbit/s up, measured 9.97 Mbit/s

I use utorrent in windows and i have tryed transmission, qbitorrent and ktorrent with the same result in ubuntu...
I have the same settings in both ubuntu and windows:
Max upload speed: 400 kB/s
Max connections: 800
Max connections/torrent: 125
Max upload slotts: 25

now for about 2 days i have problems opening pages i a browser... sometimes it opens after a long while but often its no connection... and torrent downloads just in max 80kB/s, upload is as i limited 400kB/s.
In windows i have no such problems, downloading ~7 Mbit/s uploading as limited 400kBit/s and browsing pages without any problems...
annoying :(

---

### Post by earthpigg on 2010-01-22
> my internet connection is:
100 Mbit/s down, measuerd 99.94 Mbit/s
10 Mbit/s up, measured 9.97 Mbit/s

that may be your connection from your computer to your router, but i doubt your ISP lets you have that much bandwidth.

according to [this]("http://www.matisse.net/bitcalc/?input_amount=100&input_units=megabits&notation=legacy"), that would mean you can download things at 12.5 mB/s and upload at 1.25 mB/s. that would mean you can download two or three .mp3 files ***per second***. 

confusing the issue between bits and bytes is a marketing scheme.

what is the fastest you can actually download or upload a torrent (or anything), if no other internet activity is taking place?

that is the ***only*** relevant way to measure how fast your connection is.

the fastest i have ever seen is 1 mB/s down when i was in Finland.

> **nortym said:**
> 
now for about 2 days i have problems opening pages i a browser... sometimes it opens after a long while but often its no connection... and torrent downloads just in max 80kB/s, upload is as i limited 400kB/s.
In windows i have no such problems, downloading ~7 Mbit/s uploading as limited 400kBit/s and browsing pages without any problems...
annoying :(

windows is getting in the middle and slowing your torrent speeds, ignoring what you told it to do. the only other possibility is that windows is magically conjuring up bandwidth.

ubuntu assumes that if you tell transmission it can upload at x speed and download at y speed, that you ***mean*** it. if you are giving it a limit that is greater than your max effective, then you are effectively giving it no limit... meaning you are giving the .torrent 100% of your internet bandwidth.

> Max upload speed: 400 kB/s


do you ***really*** ever upload things at speeds greater than 400 kb/s? if not, then you may as well have your max upload speed set to 'unlimited'. it's like setting a highway speed limit at 400 miles per hour. effectively, that means there is no speed limit.

its a matter of choice. i prefer my OS ***not*** to muck about with what i tell it to do, and to do ***exactly*** as i tell it.

---

### Post by nortym on 2010-01-22
First of all, thank you for the very fast answer :)

> **earthpigg said:**
> that may be your connection from your computer to your router, but i doubt your ISP lets you have that much bandwidth.

according to [this]("http://www.matisse.net/bitcalc/?input_amount=100&input_units=megabits&notation=legacy"), that would mean you can download things at 12.5 mB/s and upload at 1.25 mB/s. that would mean you can download two or three .mp3 files ***per second***. 

My max download was 12mB/s it was from a ubuntu server :)
> 
confusing the issue between bits and bytes is a marketing scheme.

Yes it is confusing, but i know what i have at home :) hehe
> 
what is the fastest you can actually download or upload a torrent (or anything), if no other internet activity is taking place?

that is the ***only*** relevant way to measure how fast your connection is.

the fastest i have ever seen is 1 mB/s down when i was in Finland.

i am in sweden, and i also upload in about 1 mB/s
> 


windows is getting in the middle and slowing your torrent speeds, ignoring what you told it to do. the only other possibility is that windows is magically conjuring up bandwidth.

Everything works fine in windows, and i dont know how it can come in the middle and slow down my torrents in ubuntu... i run them separatly one at the time
> 
ubuntu assumes that if you tell transmission it can upload at x speed and download at y speed, that you ***mean*** it. if you are giving it a limit that is greater than your max effective, then you are effectively giving it no limit... meaning you are giving the .torrent 100% of your internet bandwidth. do you ***really*** ever upload things at speeds greater than 400 kb/s? if not, then you may as well have your max upload speed set to 'unlimited'. it's like setting a highway speed limit at 400 miles per hour. effectively, that means there is no speed limit.

it's prefered to have the upload limit at max 80% of your bandwith, even downloading needs some upload bandwith to communicate...
> 
its a matter of choice. i prefer my OS ***not*** to muck about with what i tell it to do, and to do ***exactly*** as i tell it.

my choice is also ubuntu :) i just love it, thats why it is annoying with this...

---

### Post by earthpigg on 2010-01-22
damn you nordics and your socialist utopias. :P

---

### Post by nortym on 2010-01-22
> **earthpigg said:**
> damn you nordics and your socialist utopias. :P

Yeah, but you have a cheap Nexus one, here one cost 1 070 USD ! ;)

---

### Post by earthpigg on 2010-01-22
> **nortym said:**
> Yeah, but you have a cheap Nexus one, here one cost 1 070 USD ! ;)

if you mail me some of that extra bandwidth, ill mail you a nexus one.

---

### Post by nortym on 2010-01-22
> **earthpigg said:**
> if you mail me some of that extra bandwidth, ill mail you a nexus one.

ok ;) i just sent you 2 buckets LOL
i am gonna have 100Mbit/s upload in april :) then i can send you 4 more buckets :) hehe

---

### Post by SocialEvil on 2012-02-09
hah, guys.. dont know where you are from but in bulgaria for 15 euro you download with 10mb and upload with 3mb as mega-byte, not bit. bulgaria is in top 3 countries in the WORLD for cheap and fast net.

---

### Post by oldos2er on 2012-02-09
Closed, necromancy.

---

