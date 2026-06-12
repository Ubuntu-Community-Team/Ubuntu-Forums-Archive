---
title: "frustrated with 9.10 and linksys usb wireless"
date: 2010-02-20
forum: New to Ubuntu
---

### Post by dreamer565 on 2010-02-20
i am fairly new regarding using linux (ubuntu or otherwise), I have a long background with computers and networking.
I really like ubuntu, but I have more issues with it than anything, which is very frustrating.  I ran 9.04 for about a year and after struggling for 3-4 months trying to resolve an ugly dual boot issue with XP, i finally got it.  And thought all was great.  Then I applied an update.  From that point on, 9.04 no longer displayed on either of my monitors.  I tried all sorts of things, booting to recovery mode, or one of the older versions listed in the grub list.  No luck.  I posted a thread asking for help - got nothing.  So I gave up.  Went back to just using XP.  I didn't have time to troubleshoot and fight all the frustration.
Then I saw 9.10 was out.  I thought, ok I really liked using the ubuntu better than XP so I'll try again with that.  I tested it and it worked on my display - great! I didn't notice it hosed my wireless.  Or it could be that on the original run cd it worked, I just know at this point it doesn't.  I installed 9.10 and it runs, the display works.  I still have my dual boot (I learned a few things from the original struggle).  But now the problem is that if I boot to 9.10 I have no wireless.  no internet. 
I've searched threads to see if I can find anything.  I find somethings about dell pc's and broadcom wireless - mine is a dell with a linksys usb and those suggestions don't help.  I tried following the network wireless troubleshooting guide and get lost.  If i do a lshw -C network, i see the wireless network, it doesn't appear to load a driver.  If i open System - Preferences - network connections, and click on the wireless tab it shows no available networks.  However, if i look at the top menu bar, and click on the network symbol and see Wired Network - disconnected, Wireless Networks - disconnected, Available - linksys (locked and not mine), - NETGEAR (not locked, also not mine, and I can't connect to it), and I don't see mine (slj-wireless) listed at all.  I tried adding it manually no luck.
I know the wireless works.  I boot to XP and it works wonderful.  For that matter it used to work great in 9.04 before I lost the option of seeing any thing on my display.
I tried following some suggestions but they don't seem to apply or made no difference.  I don't have an option to connect wired to pull down any updates so that isn't an option.
So if anyone out there has any suggestions, I'd greatly appreciate them.  I'm really tired of having to watch my machine boot so that I can catch grub menu in time to have to scroll down to pick the XP option - so I'm about ready to make that the default and give up.

---

### Post by laidback on 2010-02-20
Don't give up, well not yet anyway.
Unfortunately I don't have the answer for you but I have seen other threads on this issue and believe that it is possible to put the XP driver for you Linsky/USB wireless in a parcel called Ndis Wrapper and then run it in Ubuntu. No guarantees but it might be worth searching the forum or Google for help. 

There are other here who are far more knowlegeably than I.

---

### Post by dreamer565 on 2010-02-20
Here's part of my frustration - I didn't have to install any special drivers to get this wireless to work in 9.04 and I'd still be running 9.04 if i hadn't lost access to the display and desktop.  That is a different issue.
 
Also, if the wireless driver isn't working, why do I see other people's wireless networks in the list? where does that come from?
 
So is it really my wireless NIC that is broke or is it that I can't see my wireless router? which happens to also be a linksys.
 
I did see some posts regarding using a NDIS wrapper, but they pretty much lost me.
 
My other concern is that I'm not sure I can rely on Ubuntu even if I get it working.  Due to what happened with the 9.04 install.

---

### Post by dreamer565 on 2010-02-20
Ok.  I now have it working.

I'm not exactly sure how or why, or if it will be a sporadic thing or not.

I followed the steps in [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/408165](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/408165) esp comment # 38.

Interesting thing was that I was apparently getting a driver (that didn't work) and could see other people's wireless but I couldn't see my WRT610N Linksys router's network (any of them).

After following the steps, I had to reboot to be able to connect to my own network.

If this breaks I'll repost but otherwise I believe this solves it.

---

### Post by biomedtech on 2010-02-22
I have installed the Unbuntu 9.10 on my Eee PC 901, and have not had any major issues so far, with Lucid Lynx Alpha.  The one item that didn't work was Hulu, but after updating Adobe Flashplayer according to the instructions on Adobe's web site, I was able to access a restricted universe, and apt-get was able to install an updated Flash, and now Hulu displays just fine.  My internet works, my wireless works, my ethernet works, Open Office 3.2 works, it is all very fine at this stage. My netbook boots faster, and I have alot more free hard drive space than I did with Karmic (about 1.2GBs vs. 750MB).  Lucid Lynx is going to kick even more Butt!

MY ONLY COMPLAINT IS THAT FIREFOX IS STILL DOG SLOW.  WHY DO THEY KEEP USING THIS?

---

