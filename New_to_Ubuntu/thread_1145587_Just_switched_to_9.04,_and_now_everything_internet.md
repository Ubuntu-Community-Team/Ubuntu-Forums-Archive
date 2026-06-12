---
title: "Just switched to 9.04, and now everything internet related is slow."
date: 2009-05-01
forum: New to Ubuntu
---

### Post by androsphere on 2009-05-01
Hello, it's been awhile since I have used Ubuntu. But after getting fed up with Windows and BSODs I decided to switch back to Ubuntu. I pulled out my flash drive with 8.04 and installed. Just a few minutes into playing around I was hooked, I have no clue why I left the Ubuntu world. I found out about 8.10 so I upgraded to that. Then I found out about 9.04, so I upgraded to that. Everything up until this point was fine. Internet was nice and speedy like usual, and all was happy like. But a little while after switching things got bad.

Everything went from Heaven to Hel.. well it's not that bad. It takes a minute or two to load a page in firefox. It's also a pain to watch things I youtube. I looked in the hardware drivers and found an alternate atheros driver, so I tried that. It was a little faster, but not much. I restarted my computer and now I can't even connect to my home network. It just keeps asking for my WEP key. 

I am now using the 8.04 live cd and right now the internet is nice and speedy like before.
I don't know what to do, please help :)

---

### Post by Cybie257 on 2009-05-01
Any specs on your computer? By asking for a WEP key, I am assuming you are using wireless?

I'm using 9.04 on 2 laptops and two towers. Laptops using WIFI, towers using Ethernet. I have not experienced those issues. 

Maybe more info will help if others had the same problem(s) with there similar equipment as it sounds like a hardware issue rather than Ubuntu itself. 

-Cybie

---

### Post by sandyd on 2009-05-01
try lowering your bitrate

its an old ..... well bug, if you can call it. I expected this to vanish magically in jaunty, but i guess my expectations were short lived :D

---

### Post by pirepox on 2009-05-03
Androsphere
I suffer from this exact problem.Have you figured it out yet?

---

### Post by thismuchiknow on 2009-05-03
**carlee**

Could you explain what you mean by 'lowering your bitrate', i'm a bit of a novice..

Thanks

---

### Post by vitriolix on 2009-05-08
I'm having this trouble too, Just plugged in to make sure it wasn't wifi.  same problem on wired.  other computers in the house get blazing fast load times, < 1 second to load news.google.com ... on this 9.04 laptop it literally takes 5-10 seconds of blank white page with spinner going to load.  

I just loaded Epiphany and same problem, so its not a broken firefox build or something.

---

### Post by vitriolix on 2009-05-08
I'm looking around now and it looks like this is related to IPv6 causing problems with some peoples routers, mine is a WRT54GL which apparently has this problem.  The reason its happening now with 9.04 is the IPv6 is now compiled into the kernel and is no longer an option module.  Not sure what the fix is yet...

[https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/313218](https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/313218)

---

### Post by Benboom on 2009-05-08
Could you need to add some DNS server entries? I had that problem in 6.10 and when I added a couple the issues went away. 

BTW, the servers I added were:

208.67.222.222
208.67.220.220

---

### Post by vitriolix on 2009-05-08
nice, that worked!  snappy internet again :)

weird that 9.04 forces this on the users though, this is a pretty hacky solution as I won't be able to override the DNS settings on other peoples wifi routers though.

thankds!

---

### Post by HammerheadNC on 2009-05-22
I found this command in another forum and it worked for me:

echo 1 | sudo tee /proc/sys/net/ipv6/conf/all/disable_ipv6

the output is the number 1 

I rebooted and the internet is fast again!

Hope this helps someone!

Hammerhead

---

### Post by HammerheadNC on 2009-05-22
> **HammerheadNC said:**
> I found this command in another forum and it worked for me:

echo 1 | sudo tee /proc/sys/net/ipv6/conf/all/disable_ipv6

the output is the number 1 

I rebooted and the internet is fast again!

Hope this helps someone!

Hammerhead

This actually did not work - it just appeared to the first time I checked the speed - sorry!

---

### Post by polytropos on 2009-05-22
Cheers to Hammerhead for that fix - it helped speed up my internet use a lot.  I'm still having minor speed issues, though: specifically, if I'm watching a streaming video in Firefox and try to expand the video full screen, the video stream gets choppy (though the audio remains fine).  I didn't have this issue prior to upgrading.  Thoughts?

---

### Post by polytropos on 2009-05-22
Well, again, Hammerhead's recommendation seems to have improved my computer's performance.  I still need advice about full-screen video streaming.

---

### Post by polytropos on 2009-05-23
If anyone else is having the fullscreen video streaming issues I described above, check out this thread:

[http://ubuntuforums.org/showthread.php?t=1165338](http://ubuntuforums.org/showthread.php?t=1165338)

Some people have found that entry 5 in the thread solves their problem, but not me.

---

### Post by Rogue_ Agent on 2009-08-21
I have been trying to find a solution for my UBUNTU 9.04 internet problem. I think I found something that seems to work in my instance anyway. I Have an EEE netbook and I am using the netbook edition of Jaunty everything other then the slow loading of the internet and streaming videos has been great. What I did find that seemed to make it better was the Firefox performance tweaks. I found this on the EEEUbuntu sight and followed there directions. I did add more available memory then what they recommended from 16 to 32 megs and I think I might double this again. My wife could not use her farm town application at all and now its usable but just a little slow and videos stream very well at full screen. The next step was going to Google Chrome which I may still try out for the heck of it.

[http://eeebuntu.org/wiki/index.php/Fasterfox](http://eeebuntu.org/wiki/index.php/Fasterfox)

I hope this helps it did for me I can now use streaming video at full screen and she can play her farm Town application on Facebook. :popcorn:

---

