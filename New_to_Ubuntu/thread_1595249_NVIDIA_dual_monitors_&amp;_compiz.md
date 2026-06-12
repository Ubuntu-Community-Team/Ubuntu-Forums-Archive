---
title: "NVIDIA dual monitors &amp; compiz"
date: 2010-10-13
forum: New to Ubuntu
---

### Post by Ballzac on 2010-10-13
Ubuntu 10.10

There are plenty of threads about this, so I'm sorry for adding one more, but I've been reading through the threads and also other stuff on the web and am yet to find a suitable answer.

I have an NVIDIA 8800GT card with a Samsung 2693HM on DVI and a Toshiba Television on VGA. I installed ccsm. Then I realised I needed to install a driver for the card, so I did that. I had the NVIDIA setting on "separate x for each screen" and was amazed at the functionality. The inability to move windows from one screen to another was a small price to pay for being able to rotate the cubes on each screen separately.

After reboot, I had lost the taskbar and all compiz functionality on one of the screens. My mouse moves over to the other screen, but I can't actually do anything with it because I can't open anything on that screen. That display is now effectively useless. I checked all my settings in the xorg.conf file, and they seem right. I have also changed the settings in the NVIDIA-settings app, and updated the xorg.conf file to no avail. I can change things, but nothing seems to work how it was before. If I change it to "twin view", I lose the background on the second screen, but the mouse still moves to it. On xinerama, I can use both screens, and compiz works, but both screens form one viewport, and the rotate together as a single face of the cube. It is better than nothing, but I much prefer to have the screens working independently, and having a taskbar on each.

I have tried using xorg.conf files that others have posted online but, again, to no avail. I just end up with one useless screen again. I suspect that maybe it a ccsm setting that somehow changed on reboot as I feel I have exhausted all possibilities with setting in the NVIDIA-settings tool. Also, on "separate x" setting, the skydome image that I set for my television (which is the one that remains usable) is gone and there is just a colour with gradient. However, on xinerama, the skydome image for the synmaster monitor is there, but is on both screens. The fact that something from ccsm has changed, also indicates to me that other settings may have changed on reboot and this may be causing my problem. However, I cannot find a setting (there are a hell of a lot of settings in ccsm) that would cause only one taskbar to appear, or for compiz to be disabled on one of the screens.

As I said, there are a lot of threads about this, but I can't find any with exactly this problem, and none of the NVIDIA settings that work for others are solving my problem. Hopefully someone with more knowledge about ccsm or NVIDIA-settings will be able to suggest a solution.

So far I have solved most of my problems by simply reinstalling ubuntu, but I have spent so much time setting it up now that another reinstall would be a real setback. I have /home and /usr on separate partitions to my OS, so maybe if I reinstall it would save all my installed programs and stuff, but I'm not game to try it unless I'm sure. 

By the way, I am a complete noob regarding linux, so if there's any important info that I've left out it's because I don't know what is relevant. Please be patient with my ignorance.

Thanks in advance.

EDIT: Sorry, I just realised that it was on the twinview setting where the two screens are attached as one face of a cube. This is apparantly how it's supposed to work, so it's only the "separate x screen" setting that's not working. Compiz does not work at all on xinerama. I thought I had ruled out every possibility regarding NVIDIA setting so had begun to assume it was a ccsm setting that was wrong, but it just occurred to me that each x screen had completely separate settings on ccsm. There don't seem to be any global ccsm settings, so I don't think it can be a ccsm setting that needs changing.

---

### Post by Ballzac on 2010-10-13
Well, I ended up reinstalling ubuntu. My entire /home directory seems to be intact, but all the software I've installed through terminal is gone. I reinstalled the NVIDIA driver, got "separate x for each screen" working again. made a backup of the xorg.conf file, rebooted, and then installed ccsm again. Had it set up how I wanted and  then set wobbly windows. At this point the monitor on which I was doing this froze, although the wobbly windows was working on the tv. I left the computer for a bit and came back and the screensaver had kicked in. When I moved the mouse, the desktop on the tv came up, but not on the monitor. I rebooted, and now I am back to where I was before reinstalling ubuntu.

I have tried removing ccsm, but nothing happens when I click "remove".If I try to remove it though the terminal I get "unable to locate ccsm" or something to that effect. The ccsm effects are still working on the tv.

I'm totally stumped. I want to be able to use ccsm with different x on each screen, but the software doesn't want to play ball. It will be time consuming if I have to reinstall ubuntu each time something goes wrong. I'm thinking maybe reinstalling once more and not touching wobbly windows, and seeing if it will work without that.

---

### Post by Ballzac on 2010-10-13
While I haven't solved my initial problem, I have discovered that there is a setting that causes the two screens to rotate as two different cubes in twinview rather than comprising one larger cube. I much prefer this. It is a little annoying not to be able to rotate the two cubes independently, and to not be able to have different settings on the two cubes, but it has the added benefit of being able to drag windows from one screen to the other. As it is, I'm satisfied with this setup and will make do.

---

