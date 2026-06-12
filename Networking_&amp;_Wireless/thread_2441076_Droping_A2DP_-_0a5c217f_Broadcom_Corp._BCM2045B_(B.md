---
title: "Droping A2DP - 0a5c:217f Broadcom Corp. BCM2045B (BDC-2.1)."
date: 2020-04-19
forum: Networking &amp; Wireless
---

### Post by charles-scoville on 2020-04-19
Hello,

I have an issue that is apparently exactly identical to [this  problem]("https://bbs.archlinux.org/viewtopic.php?id=238407") over at the archlinux.org forums, only I'm on Kubuntu 18.04 LTS.
[B]
Short version:[/B]
- Bluetooth adapter as reported by [FONT=fixedsys]lsusb[/FONT] is: 0a5c:217f Broadcom Corp. BCM2045B (BDC-2.1)
- System abruptly drops A2DP SBC audio every 10-20 mins, but still thinks all is good.
- Media keys on the headset resurrect the audio if pressed reasonably soon after the drop.
- Failing that, turning the headset off and on causes it to reconnect, and we go back to the start.
- Even with everything even remotely resembling power saving/autosuspend disabled, the problem  still persists.
- There is basically nothing in the logs to post, system thinks everything is fine. (This screams FW to me)

I'm wondering what the latest word is on this? Does this sound familiar to anyone? Is there anyone here that can help? Is there a more proper place to bring this to get attention? Where do I file a bug report? (inb4: Just buy a new adapter. :/)

**More info:**
The only apparent differences with the above thread and my situation are that I'm on Kubuntu 18.04 LTS, and I'm on a ThinkPad Edge e520, not a T420 (though, by my inspection, they are very similar). Based on the fact that I am having this same issue on Kubuntu and not Arch, I think it's safe to rule out a distro specific issue. Even so, I'm here now as it's the place for the distro I'm using. As for another key point, I tried some PPA's for different pulseaudio  versions/builds and that changed basically nothing. I feel this is  reasonable enough to support elimination of pulseaudio as the suspect,  though I concede this could easily prove to be premature. If anyone knows a more conclusively way to eliminate pulseaudio, please do let me know.

I more or less suspect it's kernelmod/firmware issue. I think the most obvious clue here is the Bluetooth dongle. Aside from the fact that it's broadcom (which is known for being trash fire tier) these specific units are pretty much exclusive to ThinkPads of this same generation as far as I know. Both the other people with this problem also have ThinkPads of similar era, and the OP in that thread has the exact same Vid/Pid as I do. So I think that is the lowest common factor. 

Now, to be honest, I *DO* have an external USB dongle, and it is much more well behaved. However *believe it or not* it also has almost the same problem, only it takes quite a bit longer for it to happen. It is, unfortunately, also a broadcom chipset, so it doesn't much help to rule out broadcom firmware. It does, however, bring up an interesting point about possible related bugs and a link in the chain of possibly fixing more than one. Lastly, it's just plain annoying as hell to have a USB port tied up on my already lacking laptop, so I would like to have the built in unit working. Though that last part is small potatoes frankly.

That all being said, if there is any community interest in fixing this I can certainly help do some tests. One thing I thought would probably be a good thing to figure out is the exact frequency that this  happens. This could prove useful if there is a precise timing pattern to this. Another thing I figure could be tried is keeping the mouse moving, to see if it has something to do with inactivity, which may further relate this to a power saving issue, albeit tangentially. In the linked thread, someone suggested WiFi interference, and I would like to eliminate that as a possibility. Unfortunately, this laptop has a $#!77y whitelist, of course, so I can't simply install a 5.8Ghz unit. I may just bite the bullet and take out the WiFi card for a day or so, and see if that changes anything.

All in all, could be a fun bug hunt. Though, to be honest, I'm really not interested in doing this if it's all by myself. I'm also mostly hoping for a miracle, and that someone just happens to already have a fix for this. :Fingers crossed:

Thanks for your assistance.

---

### Post by charles-scoville on 2020-04-21
:Bump:

Literally one (1) view....

---

### Post by wildmanne39 on 2020-04-21
The view count is broken, this thread has five views.

---

