---
title: "&quot;Touchpad&quot; tab (in System -&gt; Preferences -&gt; Mouse) Is Missing"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by asuastrophysics on 2009-10-30
Hey Everyone,

I seem to be missing a tab under System -> Preferences -> Mouse. 

My mouse preferences window shows only two tabs: General and Accessibility. 

However, there should be one more tab called "Touchpad" that seems to be missing. 

It was there before I upgraded to 9.10 (I was running 9.04)

Does anyone know why I might be missing this tab? Am I missing a package somewhere?

Thanks :popcorn:

---

### Post by Dark_Stang on 2009-10-30
Make sure you have xserver-xorg-input-synaptics installed.

---

### Post by JamesParnell on 2009-10-30
i dont know why this is, the only reason i am replying is to say that something must of gone wrong during the update, as my "mouse" section is fine...maybe run a 
sudo apt-get upgrade
or
sudo apt-get update
??? i really dont know.

---

### Post by asuastrophysics on 2009-10-30
> **Dark_Stang said:**
> Make sure you have xserver-xorg-input-synaptics installed.

xserver-xorg-input-synaptics version 1.1.2-1Ubuntu7 is already installed. 

I think I might just have to backup all my stuff and completely reformat my hard drive and start over. This upgrade hasn't gone so well.

Pulseaudio doesn't seem to be working, Banshee shows "X"'s next to every song I try to play, my ipod won't show up in Banshee, touchpad scrolling isn't working, middle mouse button isn't working, screen brightness is shaky...

basically all problems relating to the new "udev" hardware manager. 

I think the update was interrupted. Nonetheless:
```
root@girdy-laptop:~# sudo apt-get upgrade
Reading package lists... Done
Building dependency tree        
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@girdy-laptop:~# sudo apt-get update
Hit http://security.ubuntu.com karmic-security Release.gpg                     
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US    
Ign http://security.ubuntu.com karmic-security/main Translation-en_US          
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US      
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US    
Hit http://security.ubuntu.com karmic-security Release                         
Hit http://security.ubuntu.com karmic-security/restricted Packages             
Hit http://security.ubuntu.com karmic-security/main Packages                   
Hit http://security.ubuntu.com karmic-security/restricted Sources              
Hit http://security.ubuntu.com karmic-security/universe Packages               
Hit http://security.ubuntu.com karmic-security/universe Sources                
Hit http://security.ubuntu.com karmic-security/multiverse Packages             
Hit http://security.ubuntu.com karmic-security/multiverse Sources              
Hit http://archive.canonical.com karmic Release.gpg                            
Ign http://archive.canonical.com karmic/partner Translation-en_US              
Hit http://archive.canonical.com karmic Release                            
Hit http://archive.canonical.com karmic/partner Packages                       
Hit http://archive.canonical.com karmic/partner Sources                    
Hit http://us.archive.ubuntu.com karmic Release.gpg                            
Ign http://us.archive.ubuntu.com karmic/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com karmic/main Translation-en_US
Ign http://us.archive.ubuntu.com karmic/universe Translation-en_US
Ign http://us.archive.ubuntu.com karmic/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com karmic-backports Release.gpg
Ign http://us.archive.ubuntu.com karmic-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com karmic-backports/universe Translation-en_US
Ign http://us.archive.ubuntu.com karmic-backports/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com karmic-backports/main Translation-en_US
Hit http://us.archive.ubuntu.com karmic Release            
Hit http://us.archive.ubuntu.com karmic-backports Release                      
Hit http://us.archive.ubuntu.com karmic/restricted Packages                    
Hit http://us.archive.ubuntu.com karmic/main Packages      
Hit http://us.archive.ubuntu.com karmic/restricted Sources 
Hit http://us.archive.ubuntu.com karmic/universe Packages  
Hit http://us.archive.ubuntu.com karmic/universe Sources   
Hit http://us.archive.ubuntu.com karmic/multiverse Packages
Hit http://us.archive.ubuntu.com karmic/multiverse Sources 
Hit http://us.archive.ubuntu.com karmic-backports/restricted Packages
Hit http://us.archive.ubuntu.com karmic-backports/universe Packages
Hit http://us.archive.ubuntu.com karmic-backports/multiverse Packages
Hit http://us.archive.ubuntu.com karmic-backports/main Packages
Hit http://ppa.launchpad.net karmic Release.gpg            
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Hit http://ppa.launchpad.net karmic Release.gpg
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Hit http://ppa.launchpad.net karmic Release
Hit http://ppa.launchpad.net karmic Release   
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Sources
Hit http://ppa.launchpad.net karmic/main Packages
Reading package lists... Done
root@girdy-laptop:~# 

```

---

### Post by Dark_Stang on 2009-10-30
Yeah, upgrading has it's risks. Just do a clean install. It takes a little bit longer but you don't have any headaches after it's setup.

---

### Post by asuastrophysics on 2009-11-02
> **Dark_Stang said:**
> Yeah, upgrading has it's risks. Just do a clean install. It takes a little bit longer but you don't have any headaches after it's setup.

Problem solved! 
:guitar:

Fresh install fixed this problem.

---

### Post by Elwen on 2009-11-14
i have installed ubuntu netbook remix 9.10 and have the same problem. so it is not an upgrade issue.

any suggestions?

---

### Post by asuastrophysics on 2009-11-14
I honestly have no idea. I'm sure it's a problem with udev though. Is there anything under the "Hardware Drivers" app that you can enable?

---

### Post by Elwen on 2009-11-15
there is only something about wlan and graphics, nothing about the touchpad.

is there a new touchpad driver since 9.10? and can i install the older one anyway?

---

### Post by coffeecat on 2009-11-20
Haven't a clue why this should be, but this is partly hardware-related. On my Sony Vaio laptop the touchpad tab is present in Preferences > Mouse. But on my Acer Aspire laptop it's missing. Both fresh installs (not upgrades) of Karmic.

Does this make sense to anyone?

---

### Post by Sproid on 2009-12-03
Hello, I have to add that 9.10 is missing others tabs, preferences, customizations, etc
Really don't know why, I suppose its gnome making things simpler. but I really don't like it.
I install startup manager from repository and its missing advance tab. Then reinstall newer version from website and its the same. Also I tried to add/change login screen but it isn't the same menu, it offer me only two options, login with password or auto logging, wtf? I keeps getting the sensation of missing options, etc. If someone know why is that or how to fix it please share it here.

---

### Post by PhilipGanchev on 2009-12-04
I had the same problem, and a reboot made it go away. The touchpad works as I had set it up (disable while typing, disable mouse clicks with touch pad, enable edge scrolling and horizontal scrolling) and the Touchpad tab is there in the Mouse Preferences dialog.

---

### Post by coffeecat on 2009-12-04
> **Sproid said:**
> Hello, I have to add that 9.10 is missing others tabs, preferences, customizations, etc
Really don't know why, I suppose its gnome making things simpler. but I really don't like it.
I install startup manager from repository and its missing advance tab. Then reinstall newer version from website and its the same. Also I tried to add/change login screen but it isn't the same menu, it offer me only two options, login with password or auto logging, wtf? I keeps getting the sensation of missing options, etc. If someone know why is that or how to fix it please share it here.

These are not really relevant to the thread which is possibly about a hardware-specific problem. It was certainly only about one particular GUI tab. If you have problems with any other parts of the GUI, please do start your own help threads, but most of your points are about upstream design decisions.

By the way, you are still showing Gutsy Gibbon on your personal details visible under your name in the post. You might want to change this if you need to post your own help thread.

---

### Post by coffeecat on 2009-12-04
> **PhilipGanchev said:**
> I had the same problem, and a reboot made it go away.

That's interesting. What is your hardware? The tab is missing in Karmic on my Acer laptop, but not on my Sony laptop. I've noticed that other Acer users have reported the same issue.

---

### Post by Sproid on 2009-12-04
> **coffeecat said:**
> These are not really relevant to the thread which is possibly about a hardware-specific problem. It was certainly only about one particular GUI tab. If you have problems with any other parts of the GUI, please do start your own help threads, but most of your points are about upstream design decisions.

By the way, you are still showing Gutsy Gibbon on your personal details visible under your name in the post. You might want to change this if you need to post your own help thread.

    Thanks. I am using 9.04 on my laptop. I erase 9.10 on my desktop pc, reinstall 9.04 and everything is good. I conclude it was the way 9.10 configure the hardware (I include problems with wireless too).
    ok, I really do not want to start a thread about many problems or start many threats, (I fix the problem by downgrading the OS), I just wanted to comment missing preferences or tabs, and see this post relevant, however I apologize if I am mistaken on posting here.
    Also, would you explain what "upstream design decisions" mean? English is not my primary language and Google didn't get me a good definition.

---

### Post by coffeecat on 2009-12-04
> **Sproid said:**
> Also, would you explain what "upstream design decisions" mean?

My apologies for not being clear. Even as a native English speaker it took me some time to understand the upstream metaphor. Imagine a flowing stream (small river). Stuff comes floating down from 'upstream'. The upstream design decisions I was referring to were those made by the gnome development team. Although the Ubuntu team does some reconfiguring of the gnome desktop, these are really only cosmetic changes. The gdm login screen, which you among many do not like in gnome 2.28 (which is what comes with Karmic/9.10), is an 'upstream' coding design. There is little or nothing that Ubuntu can do about it, because the development effort to change it would be too much, or would detract from higher priorities. Or so I understand. Thus Ubuntu has to accept what comes floating in from 'upstream'.

Although I would hope that the gnome people would listen to what the Ubuntu people were saying. Ubuntu must account for a very significant proportion of all gnome users.

I'm glad that 9.04 is working for you, and sorry that 9.10 was a disappointment.

---

### Post by jernord on 2009-12-14
Im having the same issue with 9.10, no trackpad tab in mouse preferences.

---

### Post by asaturn on 2009-12-15
same issue here, why was this marked as "SOLVED"?

downgrading to 9.08 is NOT a solution!

---

### Post by joeclarkia on 2009-12-20
I have the same issue: Touchpad tab is not present.  Fresh install of Karmic on a new Asus U80a laptop.  Are there specific touchpads that are problematic?

---

### Post by asuastrophysics on 2009-12-23
> **asaturn said:**
> same issue here, why was this marked as "SOLVED"?

downgrading to 9.08 is NOT a solution!

Why was it marked solved? Because in my case, all I had to do to fix the problem was do a fresh install of Karmic. An incomplete upgrade from jaunty to karmic caused these problems for me.

And did you mean 9.04? lol i don't think there is a 9.08 ;)

You're right, downgrading to 9.04 isn't a solution. Reinstalling your current version from scratch is. You can also take care to upgrade your computer with a reliable internet connection, as an unreliable wifi is what broke my upgrade in the first place. 

If you're still having problems after following those steps, I'd suggest filing a bug report with udev:
[https://bugs.launchpad.net/ubuntu/karmic/+source/udev](https://bugs.launchpad.net/ubuntu/karmic/+source/udev)

hope that helps! :)

---

### Post by Sproid on 2009-12-24
@ asuastrophysics: Reinstalling a OS is NOT a solution eather in this case. "Oh I have virus problems, etc, well reinstall windows", they tell me.. Not giving up so easely in linux. Also I dont think downgrading to 9.04 is wrong,  simply because I did not like 9.10. I simply found 9.10 unfinished.

---

### Post by ben2talk on 2010-07-06
> **Sproid said:**
> @ asuastrophysics: Reinstalling a OS is NOT a solution eather in this case. "Oh I have virus problems, etc, well reinstall windows", they tell me.. Not giving up so easely in linux. Also I dont think downgrading to 9.04 is wrong,  simply because I did not like 9.10. I simply found 9.10 unfinished.

Here's news - I upgraded to 10.10 - and have no Touchpad in my mouse preferences either.

Furthermore, I cannot boot 10.04 liveCD on my system, and installing it fresh fails... so I am forced to install from the 9.10 alternative CD to get networking and then upgrade...

Just one more step in Ubuntu (already my HP desktop won't boot the 10.04 CD to desktop, and my highly rated ASUS K401N laptop has the same issue...)

Am I to be left behind as my hardware is now 2 years old and 7 months old respectively? 7.10 to 9.10 worked - why doesn't 10.04 ?

---

### Post by Halfling Rogue on 2010-07-31
Same problem with a fresh install of 10.4 on an Asus K70IC. No other problems with the install so far. I'm guessing hardware incompatibility problem.

---

### Post by rhigmus on 2010-08-07
fresh 10.04 install on my Asus N61Jq has same issue. No tab for touchpad. Annoying mouse redirection while typing (arrgh, during this sentence!).

everything else works great though, ati mobility gpu, intel i7 cpu, usb 3.0, hdmi out...yeaah :D

---

### Post by ThatBum on 2010-09-30
EDIT: Moved [all the stuff I typed]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550625/comments/182") to [a bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550625") I think describes it well.

---

### Post by nkhong on 2011-01-30
I had this problem.  I'm running.

Environment: Ubuntu 10.10 on Macbook Air 3,2

Problem:
At one point I had the "touchpad tab" in mouse properties.  After confguring and updating and changes, I lost this tab.

Solution: run syndaemon

References:
[https://help.ubuntu.com/community/SynapticsTouchpad/PreMaverick#shmconfig](https://help.ubuntu.com/community/SynapticsTouchpad/PreMaverick#shmconfig)
[https://help.ubuntu.com/community/SynapticsTouchpad/PreMaverick](https://help.ubuntu.com/community/SynapticsTouchpad/PreMaverick)
[https://wiki.ubuntu.com/DebuggingTouchpadDetection](https://wiki.ubuntu.com/DebuggingTouchpadDetection)

Hope this helps

---

