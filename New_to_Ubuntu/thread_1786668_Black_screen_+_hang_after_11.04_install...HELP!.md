---
title: "Black screen + hang after 11.04 install...HELP!"
date: 2011-06-20
forum: New to Ubuntu
---

### Post by doctorbighands on 2011-06-20
I'm just about at my wit's end with the Nasty Narwhal. Maverick was a masterpiece; 11.04 feels like an enormous, disappointing step backward.

/rant, and on to my issue...

No matter what I try, I can't get 11.04 to boot up all the way after a fresh install and the installation of nVidia drivers. I'm using the amd64 version on my Athlon64 x2 CPU.

I have to use the "nomodeset" option just to get the LiveCD working (which I believe I should NOT have to do - major bug!!). Once that's up, I can install onto the hard drive without issue. I reboot, hold shift to enter Grub and use "nomodeset" once again, and I can boot into my installed system. I then open System -> Administration -> Additional Drivers and install both of the nVidia graphics drivers listed (I tried installing just one driver, same results). I reboot, get an empty purple screen, then an empty black screen, and it hangs and won't go farther than that. Using "nomodeset" doesn't help any more at this point.

I have no idea what to do, and I'm really frustrated and disappointed with this version of Ubuntu. I've been a loyal Ubuntu user and evangelist since Feisty, and I've never seen a release as buggy as this one. It's really sad.

Any help you can offer would be wonderful. All I want is a working system!

Thank you!

---

### Post by Redblade20XX on 2011-06-20
Does this happen immediately after the bios screen or do you get to see the boot screen?
If this occurs after installing the nvidia drivers, can you post your graphic card info and the versions of nvidia drivers installed?

---

### Post by doctorbighands on 2011-06-20
> **Redblade20XX said:**
> Does this happen immediately after the bios screen or do you get to see the boot screen?
If this occurs after installing the nvidia drivers, can you post your graphic card info and the versions of nvidia drivers installed?

My boot process goes
BIOS screen -> empty purple screen -> empty black screen -> hang

I don't see the boot splash, and adding "nomodeset" to grub doesn't help.

The card is a GT218 (GeForce 210). I don't know how to tell you what drivers I installed now that I can't get into the system. I'm sorry. I installed the two available options in System -> Administration -> Additional Drivers.

---

### Post by Redblade20XX on 2011-06-20
I'm guessing you used the same drivers for maverick and it worked perfectly. Pardon my ignorance, is this an update or a fresh install? Also does ctrl+alt+ f2 on the black screen brings up anything?

---

### Post by doctorbighands on 2011-06-20
Per the suggestion in [this]("http://www.warp1337.com/content/ubuntu-1104-natty-segmentation-fault-nvidia-geforce-9-series-kernel-failure-solved") thread, I tried adding "vmalloc=192MB" to the Grub boot string. It had no effect.

Also, something odd: If I eliminate "quiet splash" from the boot string, it doesn't give me a verbose boot. I also tried a CTRL+ALT+F1 when the purple screen pops up, and no luck there either. Without those, I have no idea how to even view any potential error messages!

MAN, this is frustrating! I'm thinking the best solution at this point would just be to find an iso of Maverick and install that. The trouble with that is if I ever wanted to upgrade this machine, I'd have to go through 11.04 to do it, and that would clearly bork my system.

*sigh*

---

### Post by doctorbighands on 2011-06-20
> **Redblade20XX said:**
> I'm guessing you used the same drivers for maverick and it worked perfectly.
Yep. Maverick was a dreamboat for me on every machine I installed it on.

> **Redblade20XX said:**
> is this an update or a fresh install?
Fresh install. I've tried installing twice now.

> **Redblade20XX said:**
> Also does ctrl+alt+ f2 on the black screen brings up anything?
I've tried CTRL+ALT+F1 through F6, and none of them bring up anything.

---

### Post by Redblade20XX on 2011-06-20
If you want, you can make separate partitions for your root and home and when you want to move on, you just have to overwrite the root partition to the newer distribution while keeping intact your home (your data).

---

### Post by Brushstroke on 2011-06-20
I had this problem too. It booted the first few times but then it just...stopped booting entirely. Not to mention I hate the new Unity interface. So you know what I did?

...I went back to 10.04 Lucid Lynx. It's a Long Term Support (LTS) release which means it's a lot more stable. A lot of people have been reverting either because 11.04 isn't booting or they find Unity to be too unstable, or they don't like the way it functions...the list goes on. Personally, I'd suggest you roll back to 10.04 and keep yourself updated with PPAs and maybe use the backported Maverick kernel if you want (but the one Lucid is on is just fine in my opinion). That's what I'm doing and it's working great. 

So, you could do that instead of reinstalling Maverick. Your call bro.

---

### Post by Redblade20XX on 2011-06-20
Also if your willing to reinstall 11.04, can you install these drivers from nvidia to see if it works?

[http://www.nvidia.com/object/linux-display-amd64-256.53-driver.html](http://www.nvidia.com/object/linux-display-amd64-256.53-driver.html)

---

### Post by doctorbighands on 2011-06-20
> **Brushstroke said:**
> I had this problem too. It booted the first few times but then it just...stopped booting entirely. Not to mention I hate the new Unity interface. So you know what I did?

...I went back to 10.04 Lucid Lynx. It's a Long Term Support (LTS) release which means it's a lot more stable. A lot of people have been reverting either because 11.04 isn't booting or they find Unity to be too unstable, or they don't like the way it functions...the list goes on. Personally, I'd suggest you roll back to 10.04 and keep yourself updated with PPAs and maybe use the backported Maverick kernel if you want (but the one Lucid is on is just fine in my opinion). That's what I'm doing and it's working great. 

So, you could do that instead of reinstalling Maverick. Your call bro.

This strikes me as sound advice. I'm indifferent to Unity, but my wife absolutely loves it, and this is her HTPC I'm working on. I suspect, though, that she can live with plain old Gnome until the dev team gets their act together, as long as she at least has a working system.

Here's hoping the devs don't screw the pooch twice in a row with Oneiric!

Thanks for your help, folks.

---

### Post by wildmanne39 on 2011-06-20
> **doctorbighands said:**
> My boot process goes
BIOS screen -> empty purple screen -> empty black screen -> hang

I don't see the boot splash, and adding "nomodeset" to grub doesn't help.

The card is a GT218 (GeForce 210). I don't know how to tell you what drivers I installed now that I can't get into the system. I'm sorry. I installed the two available options in System -> Administration -> Additional Drivers.
Do you have two drivers installed at the same time?

---

### Post by doctorbighands on 2011-06-20
No matter what I do, I can't get Ubuntu to work with nVidia graphics.

I tried installing 11.04, 10.10, and even the 11.10 alpha. Same story with all of them.

I can boot after a fresh install if I add "nomodeset" to the boot string. Once I install proprietary nVidia drivers, the "nomodeset" doesn't help any more. I also tried blacklisting nouveau - didn't help.

No matter what I try, I end up with an empty black screen and a hung system before I can even get to a login screen. The only thing that works at that point is ctrl+alt+sysrq+reisub.

I'm downloading 10.04 as an absolute last resort right now, but I'm not holding out much hope. I just dumped win7 in favor of Ubuntu on this particular machine, and I don't want to put win7 back, but I need a system that, y'know, AT LEAST BOOTS UP. I have NEVER had this much trouble with Ubuntu.

What is going on here? I've spent 4 hours failing, and I'm exasperated. Please help.

---

### Post by jtarin on 2011-06-20
You wouldn't have a card model number would you? What is your results from the command "lspci"

---

### Post by jtarin on 2011-06-20
[Your not alone]("http://www.google.ru/search?q=Black+screen+on+startup+with+nVidia+driver&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a#sclient=psy&hl=ru&newwindow=1&client=firefox-a&hs=5oa&rls=org.mozilla:en-US%3Aofficial&source=hp&q=Black+screen+on+startup+with+nVidia+driver+ubuntu+natty+11.04&aq=f&aqi=&aql=f&oq=&fp=576b8d9128a54ba6&biw=1366&bih=639").....look amongst them as there are ones that have been solved......and on this forum.

---

### Post by s.fox on 2011-06-20
Please do not create duplicate threads. Thank you.

Threads merged.

---

### Post by mastablasta on 2011-06-20
Perhaps you should use AMD/ATI card :twisted:
 
anyway, have you already tried using drivers from nvidia site instead?

---

### Post by doctorbighands on 2011-06-20
> **mastablasta said:**
> Perhaps you should use AMD/ATI card :twisted:
 
anyway, have you already tried using drivers from nvidia site instead?

I downloaded and installed the driver from the nVidia site. It says it installed properly, and I believe it, because now I have a whole NEW problem!

I hate this.

Anyway, now, when I boot, I get dropped to a shell prompt. If I login and execute "startx", it gives me the following error:

```
Error inserting nvidia (/lib/modules/2.6.35-22-generic/kernel/drivers/video/nvidia.ko): No such device
```

Also, I have overscan now, so it's cutting off the first 7 characters of each line on the left side of the screen and several lines at the bottom, so I'm flying blind when executing commands.

"sudo nvidia-xconfig" seems to do its job, but doesn't help me boot up.

Any more ideas?

---

### Post by doctorbighands on 2011-06-20
Okay, riddle me this:

When I start in recovery mode, I get the standard prompt that says it's running in "low graphics mode", but there's massive overscan on my desktop. That didn't happen before I installed the nVidia driver. So, does the driver work or not? Does this mean that if I boot into recovery mode, the driver loads properly, but if I boot normally, it fails?

Another thing: When I open System -> Preferences -> NVIDIA X Server Settings, a box pops up that says "You do not appear to be using the NVIDIA X driver". I don't believe that, though, because there's overscan now.

???

---

### Post by doctorbighands on 2011-06-20
I blacklisted nouveau. Now I'm back to square one with the old black screen/hang problem.

So, I boot into recovery mode with low graphics, and the overscan is fixed. Now, here's the really weird thing: before I blacklisted nouveau, it showed up in the list when I typed "lsmod". Now, when I type "lsmod", nouveau is gone, but nvidia is there.

In low graphics mode.

I'm lost.

---

### Post by Redblade20XX on 2011-06-20
Can you give us the manufacture and model of the computer your failing to get ubuntu installed on?

---

### Post by doctorbighands on 2011-06-20
> **Redblade20XX said:**
> Can you give us the manufacture and model of the computer your failing to get ubuntu installed on?

It's not an OEM machine. I built it myself. Here are the specs:

Mobo: AMD690GM-M2
CPU: AMD Athlon64 x2 6000+
RAM: 4GB DDR2-800
GPU: nVidia GT218 (GeForce 210)
HDD: 500GB master, 1.5TB slave
DVD: DVD RW DRU-800A
LAN: BCM4306 802.11b/g

It also had a Hauppauge WinTV tuner card in it. I read in another thread that someone had a conflict with their nVidia driver and their WinTV card, so I removed it. It didn't fix my problem, but it's still removed from the system.

---

### Post by doctorbighands on 2011-06-20
bump

---

### Post by doctorbighands on 2011-06-20
The more I read, the more it looks like it isn't possible to fix this problem. Also, with all the poking around I've been doing on this system, I realized that I don't have any sound output either, because the sound passes through HDMI which (surprise!) won't work if the video card doesn't work.

An HTPC with low-quality video and no audio is useless. I thought nVidia was the better choice in Ubuntu; people say that all over the place. Experience seems to show that that's DEFINITELY not true.

There are two possible solutions I can see to this issue:

1) Replace the video card with an ATI one
2) Replace the operating system

I don't want to do either of those, but I just don't see an alternative. I've tried all the solutions I've found in forums and blogs, and all the things I can think of, and all the things mentioned in this thread, and nothing has made any difference so far. Can anyone point me to an answer using the system I already have?

---

### Post by doctorbighands on 2011-06-20
Ok, more to add to the list of things I tried. I'm kinda flying blind here, since no one seems to want to help, but I thought I'd post what I've done anyway.

Installed 10.04.2, same problem.

Removed/purged nouveau, then tried the following:

Installed nvidia-173. Doesn't support my HW. Removed.

Installed nvidia-96. Doesn't support my HW. Removed.

Installed driver that I downloaded directly from nVidia website. Boots to black screen and hangs. Removed.

Installed nvidia-current. Boots to black screen and hangs.

That's where I am right now. 4 different distro versions (10.04, 10.10, 11.04, and 11.10), 4 different driver versions, still no progress.

Please help if you can.

EDIT: Other than a first boot after a fresh install, adding "nomodeset" to the grub boot string has no effect on this problem. I have also tried passing "acpi=off", "nouveau.modeset=0", and "intel_iommu=off" to the kernel at boot time. None has had any effect.

---

### Post by doctorbighands on 2011-06-20
I should also mention that I know this video card is fully functional, because I had it running full-tilt in win7. This is not a hardware malfunction that I'm experiencing, that much I know.

---

### Post by jtarin on 2011-06-20
[Here are some ideas that worked for others in 10.04]("http://askubuntu.com/questions/4954/how-to-get-nvidia-geforce-gt-210-drivers-working-on-lucid-lynx/4962#4962") [and here.]("http://askubuntu.com/questions/4954/how-to-get-nvidia-geforce-gt-210-drivers-working-on-lucid-lynx")

---

### Post by kidknapp on 2011-06-20
Have you tried running through the paces of using this HTPC after a fresh install without installing any additional video drivers? I'm curious because you said Maverick had worked like a dream initially but now your problem seems to be version agnostic...Even though you had used the same drivers earlier with Maverick? Maybe I've misunderstood something here but I would question how necessary proprietary drivers are for your system.

---

### Post by jtarin on 2011-06-20
Another query here: When doing these new installs are you selecting to preserve your "/home/username" directory when asked?

---

### Post by kidknapp on 2011-06-20
I will say though, I was very disappointed with the upgrade from Maverick to Natty....It failed pretty miserably; Once finished all I could ever get to was a blank screen with a stuck cursor on it. After poking around to get it to boot to a desktop it came up in gnome-classic but AWN became a white block, the wireless wouldn't come on and the touchpad and USB mouse would not respond. Went back and retrieved my home with a fully working thumb drive of Maverick(not LIVE) and proceeded to do a fresh install of Natty. After a fresh install it worked flawlessly. But I have since went back and made gnome-classic the default login; I gave Unity a chance, and while it is a neat concept, it is not my cup of tea. I have had too many years to play with the Gnome\AWN\Compiz combination of possibilities and thus Unity tries to hold my hand more than I like - plus ya' get used to what ya' get used to, ya'? 
     :P

---

### Post by doctorbighands on 2011-06-20
> **kidknapp said:**
> Have you tried running through the paces of using this HTPC after a fresh install without installing any additional video drivers? I'm curious because you said Maverick had worked like a dream initially but now your problem seems to be version agnostic...Even though you had used the same drivers earlier with Maverick? Maybe I've misunderstood something here but I would question how necessary proprietary drivers are for your system.

You're right to question that. As I was thinking about it, I realized that I must've had Maverick running in a VM inside win7. Maverick DOES run beautifully on all other machines I've tried, including several in my office.

As far as using the FOSS driver, it runs the video well enough, but I can't get HDMI audio to work without the proprietary one. I have my HDMI running into a 46" HDTV, and the sound runs from the TV to a 6-channel receiver. So, no HDMI, no sound. An HTPC kinda loses its HT-ness without sound, y'know? :)

---

### Post by doctorbighands on 2011-06-20
> **jtarin said:**
> Another query here: When doing these new installs are you selecting to preserve your "/home/username" directory when asked?

I have /home on a separate partition on disk, so it doesn't get touched with each new install.

---

### Post by doctorbighands on 2011-06-20
> **kidknapp said:**
> I will say though, I was very disappointed with the upgrade from Maverick to Natty....It failed pretty miserably; Once finished all I could ever get to was a blank screen with a stuck cursor on it. After poking around to get it to boot to a desktop it came up in gnome-classic but AWN became a white block, the wireless wouldn't come on and the touchpad and USB mouse would not respond. Went back and retrieved my home with a fully working thumb drive of Maverick(not LIVE) and proceeded to do a fresh install of Natty. After a fresh install it worked flawlessly. But I have since went back and made gnome-classic the default login; I gave Unity a chance, and while it is a neat concept, it is not my cup of tea. I have had too many years to play with the Gnome\AWN\Compiz combination of possibilities and thus Unity tries to hold my hand more than I like - plus ya' get used to what ya' get used to, ya'? 
     :P

I agree with this completely. I'm on the verge of no longer recommending Ubuntu at all because of the move to Unity, and it pains me to think that way - I've been pushing Ubuntu to anyone who would listen for years. I have been and still am a Gnome/AWN/Compiz die-hard, and when 11.04 came out and broke Compiz and bricked a machine in my office, I just about gave up on Ubuntu completely. I'm still there, more or less - I'm shopping for a new distro for this HT machine as we speak, and if I find something I like, I may abandon ship on all my machines (which is a fairly substantial number). Ubuntu wasn't "broke", but they tried to "fix" it anyway, and now it IS broke. As I mentioned before, it's really sad.

---

### Post by kidknapp on 2011-06-20
The good news is you have a ton of options distro-wise. Natty runs great now that I've put it back to classic, but I wholly understand what you mean about recommending Ubuntu to people. I think Unity will be excellent when all of the low-level bugs come out from more experience in use, but it seems so heavily targeted at newer users and boxed in in terms of customizability. While I can see some improvements in ease of use, I don't need another paradigm shift in my desktop environment....

While its based heavily on the same codebase, I would try MythBuntu first. Its aimed specifically at HTPC/MCPC. After that XBMC, but thats also a drastic shift in operation...

---

### Post by doctorbighands on 2011-06-20
> **kidknapp said:**
> The good news is you have a ton of options distro-wise. Natty runs great now that I've put it back to classic, but I wholly understand what you mean about recommending Ubuntu to people. I think Unity will be excellent when all of the low-level bugs come out from more experience in use, but it seems so heavily targeted at newer users and boxed in in terms of customizability. While I can see some improvements in ease of use, I don't need another paradigm shift in my desktop environment....

While its based heavily on the same codebase, I would try MythBuntu first. Its aimed specifically at HTPC/MCPC. After that XBMC, but thats also a drastic shift in operation...

"I don't need another paradigm shift in my desktop environment..."
Especially not one that is restrictive and less customizable. It's the very same garbage that keeps me far away from OS X - the whole "don't worry, we'll take care of that" attitude, feeling like I'm forced into hand-holding. I do understand the need to evolve, and I also understand an attempt to carve out a market niche, but it's looking like this isn't the way. Talk about a move away from core principles!

I have Mint downloading as I type this. I'm hoping it doesn't take me too far out of my Gnome/'buntu comfort zone. :) I'm also hoping (REALLY hoping) it plays nice with nVidia.

---

