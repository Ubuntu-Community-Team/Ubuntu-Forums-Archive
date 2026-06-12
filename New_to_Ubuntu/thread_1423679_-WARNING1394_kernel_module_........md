---
title: "-WARNING:1394 kernel module ......."
date: 2010-03-06
forum: New to Ubuntu
---

### Post by MisFitt on 2010-03-06
I have fixed this problem thrice now and have just tried to connect my cam to kino to capture:
-WARNING:1394 kernel module not loaded or failure to read/write/dev/raw1394!
AGAIN!Now I have not altered or added to my installation since my last tussle with this Kino/capture/firewire problem(see my other threads re this very problem) and I'm after THE FIX for this,if there is one.
Is something missing or wrongly installed?
I'm currently using the Jaunty 64 bit and having the same problem as I did with Karmic 32 bit and Jaunty 32 bit(I know the bits are probably irrelevant here).
If I boot into Windows no problem except that it's not what I want to be working within,kinda defeats the purpose.
I bought and added to this computer for the ability to get into video making and am committed to one day soon having a soley Ubuntu machine and I know it means effort and a level of commitment which I certainly have no problem with but sometimes my enthusiasm gets raggedy when I'm trying to nut out so many (small) problems that are probably a breeze for the "naturals".
I try hard,I have to and I know once "conquered" I can use the energy I currently use on learning to be the creative,expressing and expanding the ideas I have as a natural painter into video which is a dream I've long had.
There,wow,a little more information than I'd intended but hey,why not?I am serious and desperately need to be able to turn the thing on and get on to new things,always learning.It's a good thing but I need this continuing hassle to cease(for the next one!)
I understand my computer is a tool that can produce wonder filled things.

---

### Post by MSich on 2010-03-06
This worked for me.  From this link: [https://help.ubuntu.com/community/Firewire](https://help.ubuntu.com/community/Firewire)

**Method 3. 'udev rule'**

 As the most straight-forward method, simply add the raw1394 specific udev rule which was left out by Ubuntu's udev maintainers: 
echo 'KERNEL=="raw1394", GROUP="video"' > /tmp/raw1394.rules
sudo cp /tmp/raw1394.rules /etc/udev/rules.d/
rm /tmp/raw1394.rulesThen unload and reload raw1394 or reboot to make this change effective.

---

### Post by MisFitt on 2010-03-07
Thankyou so much MSich.
Yes,I'm familiar with this page and have just successfully run through and it appears,well it is fixed but for how long?
As I said I've "fixed" this problems several times and it seems like it ....it's a bizarre,non sensical problem as it has returned.
I get the footage and am not able to use kino with exactly the same firewire issue.
Could it be the hardware I'm wondering though I don't see why.I don't want to have to resolve the problem regularly and from searching the forums mine seems to be unique,unfortunately,it makes no sense.Sorry for the long winded answer,I do appreciate your help,thank you so much

---

### Post by patchwork on 2010-03-07
Just out of curiousity, did you install the kernel updates that came down the pipe the other day?  If so, there's a good chance that you ran into this because the new kernel didn't yet have the firewire module loaded into it (until now).  If that isn't the case, I don't know why it is periodically dropping you.

---

### Post by MSich on 2010-03-07
> **MisFitt said:**
> Could it be the hardware I'm wondering though I don't see why.I don't want to have to resolve the problem regularly and from searching the forums mine seems to be unique,unfortunately,it makes no sense.


Your problem does seem a little unique.  I think you've been working on this longer than I have.  Maybe my problem will come back too, who know's.  I doubt it's a hardware thing.  If it worked before it probably isn't hardware.

I hope you find an answer.

---

### Post by MisFitt on 2010-03-08
I'm not 100% on that except I seek updates almost daily so.........
I guess so

---

### Post by MisFitt on 2010-03-08
oh I hope not-it's ahassle but the good news is over the last 2 days I've sorted hours of dv's,3 tapes I think and kino's only crashed maybe 6-8 times but I haven't lost a second's video.
Good luck to you

---

