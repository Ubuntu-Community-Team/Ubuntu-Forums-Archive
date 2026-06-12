---
title: "Ubuntu 6.1 inconsistent?"
date: 2007-01-04
forum: Networking &amp; Wireless
---

### Post by vyoufinder on 2007-01-04
I have been trying for several days to get Ubuntu online.  First I tried 6.1 and had no luck.  It recognized my adapter as being a wireless adapter but would not recognize any networks.  Then I tried installing the server edition of Ubuntu and it would not install - hangs up when I try to boot it after a "successful" install.  Then I tried a different wireless card and forgot that I still had it in the machine so I turned it off and put my Belkin F5D7000 version 5100 card back in.  Bam!  the thing magically connected to the internet and worked for a full day.  Then it stopped working the next day.  I rebooted and had the monitor disconnected through a kvm switch.  Then tried it again, this time with the monitor connected and bammo, thing connected again!  Ubuntu never recognized any wireless networks but was able to connect.  So then I decided to reproduce the results and now I can't connect again using 6.1.  Then I decided to try the older version, 6.06 and didn't even mess with anything at all.  60.6 found all the wireless networks within range by name and displayed them in a drop-down menu and connected all by itself to an unsecured right after the install.  Then I tried 6.1 again thinking it was some other issue.  Won't connect.  Anyone know hwy 6.06 had no trouble at all, I didn't even have to manually enter the ssid or dns servers but 6.1 seems to never connect no matter what I do?  Is 6.1 a beta and 6.06 is a stable version or what?  This is confusing.

---

### Post by meng on 2007-01-04
6.10 (not 6.1, it's 6.10) is more bleeding edge than 6.06. Sorry to hear it's not working for you, sounds like the easiest solution is to go back to Dapper.

---

### Post by vyoufinder on 2007-01-04
Ha- ya, you'd think so!  I just tried installing again and now this time it acts totally different!  I didn't do anything different either - weird as ever man.. weird.  Now with 6.0.6 it acts just like  6.1 - doesn't find any networks and also doesn't connect!  Using the exact same setup, same disk, everything.  What I don't understand is why the inconsistency?  Last time I installed 6.0.6 I didn't even think it was connected and only tried Firefox on a whim and was very surprised to see that it was fully connected.  Now it won't find anything, won't connect.  I tried a reboot... This is way too weird.  Any ideas?  I am wondering if when I install if Ubuntu doesn't actually format the hard drive and somehow finds residual configuration stuff.  I still have the working 6.1 that somehow (no idea how because I didn't "fix" anything) on another hard drive but I am trying to reproduce the results because I already recommended Ubuntu to a friend and told him 6.06 was a snap.. So that's why I am trying to reproduce results here.  Plus I want to know what's going on and why the extremely strange behavior..

---

### Post by meng on 2007-01-04
Okay, then let's get serious and try to solve your problem. I assume you've got GNOME/Ubuntu (I found my card worked easily with Ubuntu but not Kubuntu ... go figure!) Which card do you intend to use? Can you see it under System > Admin > Networking?
Can you show us the output of:
sudo iwconfig
(you can redact the WEP key if you're paranoid like me)

---

### Post by vyoufinder on 2007-01-04
Yes!  Let's do get serious, hehe, like your attitude and man, I want to KNOW what I am doing and not just be taking stabs at getting things working.  I am the type of person who needs to understand and so far this just doesn't make sense.. Here's what I am doing now;  I just deleted the partitions using a windows disk becuse that's what I had done originally.  I took the wireless card out completely because originally that's what I had done and eventually somehow (mysteriously) got it working.  Right now I am doing a clean install of Ubuntu 6.1 because I know it is possible to make it work, have it working on other hard drive, and prefer to live on the edge.  Besides, since 6.0.6 acted the same and seemed to have the same problem last time I installed, I figure it's not a 6.1 problem.  My intention is to install Ubuntu with no wireless card installed, then shut down, install the card, and see if that does it.  I do this because it was part of how I got 6.1 working with my wireless last time.  I want to use the Belkin card (F5D7000 version 5100) because I have had it working before and because it requires the least amount of installing/configuring of the 3 cards I have available.  Plus it comes very highly recommeded and is what my buddy will be using as well (I recommended it to him)  I also posted here: [http://ubuntuforums.org/showthread.php?p=1957162#post1957162](http://ubuntuforums.org/showthread.php?p=1957162#post1957162) yesterday while trying to get 6.1 to work originally.. So if you're as serious as you sound, you can look there for background information.  I'm willing to do whatever it takes to figure this out and who knows, maybe the developers will take notice and will help to improve instructions for the next person who has this trouble... I have 3 wireless networks available at my disposal so first I can just use an unsecured wireless in my neighborhood and no need to worry about keys or typos.. 

I'll post after the install completes with my results.

---

### Post by vyoufinder on 2007-01-04
Ok, install completed and I shut it down and installed the Belkin card.  Booted up and went to network and the card shows up fine.  Was not configured so I clicked on it and checked if it had found any wireless networks - no, none found so I typed in the name of the unsecured wireless in my neighborhood "Linksys."  It configured the card and enabled it but still no connection.  Did an iwconfig and here's a screenshot of the the result:
[IMG]http://www.vyoufinder.com/delete/1.png[/IMG]

ideas?

---

### Post by spd106 on 2007-01-04
Try **sudo iwlist ath0 scan** and **sudo dhclient ath0**

---

### Post by vyoufinder on 2007-01-04
Well.. good news but still not satisfied yet.  I got it working using the command shown (I tried this before I read your response, just as a shot in the dark):

[IMG]http://www.vyoufinder.com/delete/2.png[/IMG]

I got the idea from yesterday's help and it connected!  wow, that was cool!  The reason I say I am not satisfied yet is because it still doesn't show all the networks available and I often have to switch wireless connections.  I'm about to try your command you posted and see what that one does.  This is getting interesting....

---

### Post by vyoufinder on 2007-01-04
ok, here's the result of what you told me to type in:

[IMG]http://www.vyoufinder.com/delete/3.png[/IMG]

 Now I still need to get it to show all the networks available.  I know it's possible because on the magic install of 6.0.6 that worked out of the box it was able to find all networks in the neighborhood allowing me to select one and automatically connected to the unsecured.  I do need it to somehow scan them because of the fact that I often need to change networks and can't always be typing in commands like that (I am not the only one to use this computer..)  Plus I need to figure out what's been going on because I maintain several friends' computers and want to recommend Ubuntu to all of them as soon as I think it's a suitable replacement for Windows (very, very soon) Greatly appreciate your help!

---

### Post by spd106 on 2007-01-04
I meant try ```
sudo iwlist ath0 scan

```

Follow this for a gui
[https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

---

### Post by Henry Rayker on 2007-01-04
Just a small point of suggestion. When someone asks for the output of a command, it's a lot less taxing on bandwidth and screen real-estate if, rather than making a screenshot and uploading it, just copy and paste the text.

Another little point is, the names of the releases are very specific. 6.06 is not the same as 6.0.6 and 6.1 is not the same as 6.10. The numbering scheme, if I remember correctly, is #years.#months each from the first release. Regardless, it's something to that effect...

As for the matter at hand, I believe the command ```
iwlist [interface name] scan
```will list the available networks (with the name in the ESSID field). In your case, the command will be ```
iwlist ath0 scan
```

---

### Post by vyoufinder on 2007-01-04
that command shows:

[IMG]http://www.vyoufinder.com/delete/4.png[/IMG]
[IMG]http://www.vyoufinder.com/delete/5.png[/IMG]

looks like it's scanning networks.  I will try the gui but there's got to be a way to make Ubuntu "Networking" scan right?  It's done it before with this same hardware.. Suggestion on that issue?  I want it to be as simple and out of the box as possible.  I have to go out for the day.  I will definitely check this post later and post all results/solutions but I should be minimum priority for now.  I really appreciate all the help.  You've helped immensely already!

---

### Post by Henry Rayker on 2007-01-04
I have no idea what you want. You said you wanted a list of available networks...that command does it...it is scanning for the available networks and printing them out.

---

### Post by spd106 on 2007-01-04
Yeah, the network scan feature in network-admin was broken just before edgy was released. I think it was a gnome bug, anyway it's fixed upstream. 
See [https://wiki.ubuntu.com/EdgyKnownIssues](https://wiki.ubuntu.com/EdgyKnownIssues)

Just use the terminal command or perhaps install network manger for scanning.

---

### Post by vyoufinder on 2007-01-06
I may have figured this out - My box has this plate on the back that holds pci cards in place.. It's all bent up and doesn't fit well and going through several different installations I was having trouble even recognizing a card in there at all.  After MUCH trial and error, I figured out that the card had pressure on it from the plate pushing on it and was causing the card to not be recognized!  Man, wasted two days to figure that one out.  I am still trying to get Ubuntu to scan for networks in the Administration>Networking>Wlan0.. right now there is a drop down menu, or maybe I should say that there is supposed to be a drop-down menu where I select which network I want to connect to.  That part isn't working at all.  When I click on it I can see that it tries to open but only opens like one millimeter and can't see any networks.  It's essential that I get this working.  Other users of this computer won't want to follow a series of sudo commands just to connect to a different network.  any ideas on how to get this working?  Scan for networks all by itself and then I just select which one, put in the key and go?  Thanks for all the help fellas..


*edit* - just noticed we're on page 2 now and I hadn't seen any new responses.  Here I was thinking I had been abandoned!  Hehe, ok, checking out that bug issue and hopefully fix.. Thanks so much.  The support I've been getting here is outstanding and keeping in mind that this is for a totally free and open source os!  I don't think I ever could have gotten real help from Miscosuck anywhere near the quality I have already gotten from Ubuntu people - kudos to you guys!  Going to buy a t shirt even though I won't wear t-shirts with advertising on them normally and even though the t shirs are way overpriced compared to my usual $3 t's!

---

### Post by vyoufinder on 2007-01-06
I'm still trying to get network scanning to work.  I can't install network manager because it says there is a conflict and to be honest, I just want to fix the built in scanner.  There is rumour of a fix in the bug report but no link or information.. Maybe I have to wait for this but anyone know if there is a fix yet?  I don't really want to get into editing the core files of Ubuntu unless it's going to be a permanent fix but will the fix be released on the regular Ubuntu fixes when ready or will I need to go seeking it?  Thanks again everyone.

---

