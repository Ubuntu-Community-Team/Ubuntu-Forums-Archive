---
title: "I put my computer to sleep and now I cannot connect to Wifi"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by RealG187 on 2009-03-24
I put my computer into suspend and when I woke up I got a dialogue box in the attachement. I cannot connect to my Wifi, only an unsecure access point somewhere in my hood. My wifi is 64 bit (I think*) ASCII WEP. * My WEP key if 5 characters so I think it's 64 bit encryption.

I can connect to unsecure wireless but not my own!!! I do not see ASCII wep. Before i suspended my Wifi worked fine, and I know it's because of that because this isn't the first time this has happpened...

---

### Post by RealG187 on 2009-03-24
[http://blog.tmro.net/2007/11/ubuntu-wireless-and-hibernation.html](http://blog.tmro.net/2007/11/ubuntu-wireless-and-hibernation.html)

I have tried that and it still doesn't work, once again I can only connect to unsecure Wifi.

---

### Post by RealG187 on 2009-03-24
[http://ubuntuforums.org/showthread.php?t=1105558](http://ubuntuforums.org/showthread.php?t=1105558)

This makes me want to leave Linux

---

### Post by presence1960 on 2009-03-24
> **RealG187 said:**
> [http://ubuntuforums.org/showthread.php?t=1105558](http://ubuntuforums.org/showthread.php?t=1105558)

This makes me want to leave Linux

Is that a hint of that underlying attitude that sends a nerve up elitist spines?

Just joking of course. There is room for all of us in here.

---

### Post by RealG187 on 2009-03-24
I am just mad I can't connect to my Wifi now

---

### Post by jbysmith on 2009-03-24
Which build are you using?  I only have two portables myself that I use very infrequently, so don't have a ton of wireless networking experience.  The one laptop I do use occasionally dual boots Ubuntu and FreeBSD.  (The other portable is a tablet and semi-locked into XP.)

I've never looked into it much as I rarely use it (IE working while watching TV on the bigscreen), but I did have a few quirks with 8.10's wireless too.  9.04 however, at least in its current form and on this particular hardware, seems to be working much smoother on it.  No issues with suspend and encrypted wireless.

---

### Post by RealG187 on 2009-03-24
I tried a manual IP and it still brings up the same screen, I checked show key and it gave a long number, I went on my other laptop that is working and it's the same key stored there.

Is there a service or something for WEP?

---

### Post by RealG187 on 2009-03-24
I am using Ubuntu 8.10 32 bit

---

### Post by jbysmith on 2009-03-24
> **RealG187 said:**
> I am using Ubuntu 8.10 32 bit

Yea, give 9.04 a spin, should be able to test that functionality just off of a LiveCD.  Alpha 6 is out, Beta is due in about two days.  See if that cures what ails you.  Definitely worth checking anyway, that Jackalope is pretty fast, and even in alpha it's actually quite stable, I'm very impressed with it. Don't have any practical possible fixes for 8.10 myself though, not using it anymore, maybe someone will have better advice in that regard.

If it doesn't do it for you, there's plenty of other quality distros to pick from too of course.  No one build will work perfectly for everyone, if you're liking Linux give another one a go.  I've typically had good results on the hardware end with openSUSE, PCLinuxOS and Arch myself, but your mileage will vary.

---

### Post by betrunkenaffe on 2009-03-24
Does wifi work before you put it to sleep?

Try checking "Enable Networking" off and then back on. It should work now.

---

### Post by RealG187 on 2009-03-24
I want to stay with Ubuntu, I just want my wireless to work. I do not want to reinstall everytime I suspend or hibernate my computer.

---

### Post by RealG187 on 2009-03-24
Wifi was working, I went to sleep and it hasn't worked since. Just now it had signs of it working, I could connect locally via the network and get to my router's IP address but not the web. Just now I get back to DHCP and I am online.

I have no idea what I did, I tried the things I said above but they didn'd work then, maybe since editing /etc/default/acpi-support I had to restart twice,

I am on battery power now, if that matters, I'll try with AC.

Is there a way to view system logs so I could post them and people who can interpret them can see what was wrong and how I fixed it.

I am not sure if I want to sleep or hiberate, I fear it could happen again...

---

### Post by sgosnell on 2009-03-25
Have you rebooted after the hibernate?  That usually works.

---

### Post by joey-elijah on 2009-03-25
> **sgosnell said:**
> Have you rebooted after the hibernate?  That usually works.

Yeah that should sort it out - Windows 7 has this problem too (can't connect to wifi most times after un-hibernating)

---

### Post by overdrank on 2009-03-25
> **RealG187 said:**
> [http://ubuntuforums.org/showthread.php?t=1105558](http://ubuntuforums.org/showthread.php?t=1105558)

This makes me want to leave Linux

I moved your post to your thread as not to high jack the other thread.:)

---

### Post by betrunkenaffe on 2009-03-25
I have the same problem the instructions I gave solve the problem.

---

### Post by RealG187 on 2009-03-25
> **overdrank said:**
> I moved your post to your thread as not to high jack the other thread.:)

It kinda had to to with that topic about leaving Linux, but I admit I was kinda high  jacking, I posted there so someone would see this thread...

And yes I did try rebooting and turning Networking on and off and it didn't work, but some time ago it randomly started working...


I am trying out my other laptop to see if I found a way to prevent it from happening.

On the topic of hibernation, it is slower and windows in Ubuntu, is there a way to speed it up or something?

---

### Post by scott2 on 2009-03-26
yes, i cant believe how hard it is to even find this thread! it shows me how few people actually have a dsl/wireless connection. Im half convinced that mine only works because the vista's internet explorer broke. the key is the wep key and you have to know the name, because it detects ones that arent yours and are nearby. However, this doesnt answer our question, which is how come we cant re-connect our dsl's when we get out of hibernation/suspend. The best way i know to answer that is the webring it makes you create a password for. it has something to do with the seahorse program, but i cant seem to install it. i think it times you out much like the display does.. which brings me to my next point: how do you control power compsumption without disruption of the normal activities? The only recourse is to restart the system, which sucks because cman takes 300 seconds to load. Hopefully the april version will be more conveinent as i need my dsl to make a living,but the power usuage is awful.

---

### Post by nowhere@cox.net on 2009-03-27
I had the exact same problem. I have been connecting to my WPA-PSK router fine for a long time right up to this morning. I checked my email, powered down the laptop and off to work. While out I used my CDMA modem directly in the USB port, I used it in my portable router (also WPA-PSK enabled) and finally suspended my machine like I have a billion times and headed home. 

Set the laptop aside suspended, did some stuff, woke it up, it connected to the router fine, but would not display any web pages or let me ping any internet addresses. I could connect to the neighbor's unsecured and surf fine, the back to my router and no joy. Disable/Enable wireless no luck, disable/enable networking no luck, reboot no luck, power down no luck, reboot the router no luck. Connect to my portable router and surf just fine. Switch back to my home router and WOW now it works! The portable router as assigned a different IP address which stuck when I switched back and for some reason it is working.  I have no idea why and I am quite sure it won't be working again soo and still won't know how to fix it LoL!

---

### Post by RealG187 on 2009-03-27
Before I would not even see any wireless networks, not even unsecure, it was like I didn't even have a wireless device in my computer, I reinstalled and it worked, happened again, reinstalled again. Happened a third time but I was able to connect to unsecure. I didn't want to reinstall for a third time so I made this thread...

---

### Post by Mr. Stabby on 2009-03-27
If you have an external WiFi chip, try taking it out and putting it back in when you come out of standby. I had the same problem, and that always works for me.

---

### Post by RealG187 on 2009-03-29
It's a laptop...

and since it's a laptop those features are more important since on a laptop you have to save battery life.

But you gave me an idea, I could use a USB one like WRT54G as a backup when the laptop's one misbehaves.

I remember I went to someones house and I couldn't connect to thier Dlink router with my other laptop's Wifi, perhaps that would have helped, although carrying a dongle on a roadtrip isn't convienient. But then I was straight Ubuntu no dual boot, and I bet Windows would have connected, perhaps it used a different driver or something.(Vista messed up, and why reinstall it and Ubuntu,  complete format was easier) but this laptop has dual boot (Vista was already installed on it, I even went through the first logon which takes like a hour "Preparing your desktop, please wait while we measure your computer's performance" so it was easier to keep Vista). Plus I was having problems with Ubuntu then so I had to use Vista. Within the next bit I should go into Vista again, it's been a while yet I had it there the whole time, I haven't even configured the Custom titles in grub for it & the HP recovery partition since reinstalling due to this issue (they both say the same thing, the real Vista the second last one, I make it the last one cuz @ grub's boot menu I can easily select the last option on the list by pressing page down...)

What's wierd is my PSP connected to thier Wifi but not the Laptop. I think I can use my phone as a dongle for Wifi and 3G connection since my phone has Wifi, 3G, and USB connectivity, I think I can even use it as a router to make a Wifi access point that connects to the web via 3G connection!

---

### Post by RealG187 on 2009-11-02
I thought this issue was fixed in 9.04, but today after I resumed from a hibernate I was having the same problems connecting to my wifi, I disabled networking and restarted twice and it still didn't work, but after I while it did.

This is really annoying and need to fixed.

---

