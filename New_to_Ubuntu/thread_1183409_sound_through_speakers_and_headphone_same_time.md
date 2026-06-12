---
title: "sound through speakers and headphone same time"
date: 2009-06-10
forum: New to Ubuntu
---

### Post by T4K3Z0U on 2009-06-10
Hey people, new problem for you all.

I just got a new machine, installed ubuntu 9.04. When I plug in headphones so not to distract others, the sound is coming through both the speakers and the headphones at the same time. I know what your thinking, its a hardware issue. I hate to disappoint but this problem does not occur on the windows os.

Any ideas on how to fix this?

---

### Post by rlj1965 on 2009-06-10
> **T4K3Z0U said:**
> Hey people, new problem for you all.

I just got a new machine, installed ubuntu 9.04. When I plug in headphones so not to distract others, the sound is coming through both the speakers and the headphones at the same time. I know what your thinking, its a hardware issue. I hate to disappoint but this problem does not occur on the windows os.

Any ideas on how to fix this?



Turn the volume down on the speakers

---

### Post by T4K3Z0U on 2009-06-11
> **rlj1965 said:**
> Turn the volume down on the speakers

24hrs and this is the only answer I get? Is this really such an uncommon problem? Must be since there were no other threads detailing anything even remotely similar, and since 9.04 is relatively fresh.

You'll have to forgive the sarcasm, but how is turning down the volume going to solve this problem?

---

### Post by hessiess on 2009-06-11
> **T4K3Z0U said:**
> Thanks but the speaker and headphone volumes are not separate, so how is turning the volume down going so solve this problem?

Tern the volume down on the physical speckers or unplug them. if you are on a laptop open a terminal, type ``alsamixer'', hit enter and try hitting m to mute some of the channels.

---

### Post by gradinaruvasile on 2009-06-11
Do you have something like that in my screenshot? 
Just press the sound icon from the taskbar, select volume control. Click on the preferences tab, tick everything. And hope you have a Switches tab...:)

---

### Post by T4K3Z0U on 2009-06-12
> **hessiess said:**
> Tern the volume down on the physical speckers or unplug them. if you are on a laptop open a terminal, type ``alsamixer'', hit enter and try hitting m to mute some of the channels.

Ah my bad, I didn't say it was a laptop. I didn't think to check the sound settings. I am rather clueless when it comes to Ubuntu, but am clued up enough to not use windoze. :D

---

### Post by T4K3Z0U on 2009-06-12
> **gradinaruvasile said:**
> Do you have something like that in my screenshot? 
Just press the sound icon from the taskbar, select volume control. Click on the preferences tab, tick everything. And hope you have a Switches tab...:)

The only thing in the switches tab is the headphone thing and its ticked. I'll try getting some screenshots of the sound controls to see if anyone notices any irregularities.

---

### Post by T4K3Z0U on 2009-06-12
Here is screenshots of the 3 tabs in sound control plus the preferences place. I hope that helps.

Though now I have the screenshots I can probably play around, and if I bugger anything up, I have a reference.

---

### Post by prvteprts on 2009-06-12
On my laptop, Front controls the laptop's built-in speakers.

---

### Post by T4K3Z0U on 2009-06-12
Well I muted the front speakers which kind of worked however now it has completely buggered the laptops speakers. All I get is crackling sound, before and after changing the settings back.

I checked windoze again to make sure its not the laptop itself. The sound still works fine and the way it should.

---

### Post by T4K3Z0U on 2009-06-12
My computer just died on me, so I need to start another thread, but I got to thinking. Could this problem be due to the fact there is no 9.04 for laptop? It was a friend who insisted I install 9.04 but when I was downloading the ISO there was only 8.10 for laptop, so perhaps this is why the sound is acting odd?

---

### Post by prvteprts on 2009-06-12
Sound is pretty weird in 9.04 compared to 8.10. When I moved from 8.10 to 9.04 on the same laptop, sound was gone. It's something to do with pulse and/or ALSA or something. I had to do some minor fixes to get it to work OK.

Anyway, the crackling sound happened to me even in 8.10. But in my case, there was no need to fix anything, I just needed to get used to the sound controls. At first I thought the headphones didn't work, and everytime I plugged them in, I got the crackling sound on the speakers. I just needed to adjust the volume meters accordingly. It may seem weird, but that was just what I did.

---

### Post by T4K3Z0U on 2009-06-13
Got my sound back. Have been through every single sound setting to see if anything would change but nothing did. I am thinking perhps I need some other driver options?

---

### Post by Amilo1718 on 2009-06-13
which laptop do you use?

---

### Post by T4K3Z0U on 2009-06-15
> **Amilo1718 said:**
> which laptop do you use?

Sony Vaio VGN-FW72JGB (Japanese model) 64 bit.

---

### Post by T4K3Z0U on 2009-06-16
[CENTER]**BUMP**[/CENTER]

Well today I can't turn volume up, down or even mute it. I think there is a serious audio issue here, but I can't for the life of me, find out what the heck is going on.

---

### Post by T4K3Z0U on 2009-06-16
I followed all the instructions on [this]("http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/") webpage to install the latest ALSA, the install went flawlessly, but my sound is still screwed.

---

### Post by gabdullah on 2009-06-16
I have almost the same laptop...
It was a driver issue, if I recall. I'll post back if I can remember how I fixed it. I didn't even realize it until I was in the library one day, studying, and had my headphones on. Had tunes on random. Really loud. Nobody said anything, but I was mortified when I realized that I'd been blasting tunes for the last hour.

---

### Post by gabdullah on 2009-06-16
Here's your [solution]("http://michael.flanagan.ie/blog/index.php/19/headphone-fix-ubuntu-sony-vaio/")

---

### Post by T4K3Z0U on 2009-06-16
> **gabdullah said:**
> I have almost the same laptop...
It was a driver issue, if I recall. I'll post back if I can remember how I fixed it. I didn't even realize it until I was in the library one day, studying, and had my headphones on. Had tunes on random. Really loud. Nobody said anything, but I was mortified when I realized that I'd been blasting tunes for the last hour.

LOL I can just imagine that too. 

> **gabdullah said:**
> Here's your [solution]("http://michael.flanagan.ie/blog/index.php/19/headphone-fix-ubuntu-sony-vaio/")

I just read through the first page of posts and found some simpler instructions, however when I used the code in terminal, the page it brought up was not what I was expecting, since it is empty.

---

### Post by gabdullah on 2009-06-16
@T4K3Z0U

Click on file/open/alsa-base.conf

That should open it for you.

---

### Post by T4K3Z0U on 2009-06-16
> **gabdullah said:**
> @T4K3Z0U

Click on file/open/alsa-base.conf

That should open it for you.

Excellent, thanks Gabdullah, that has solved the speaker/jack issue.

Thanks all for putting up with a newbie that just don't seem to catch on fast.

---

