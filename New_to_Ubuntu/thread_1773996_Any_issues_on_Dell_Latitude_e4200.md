---
title: "Any issues on Dell Latitude e4200?"
date: 2011-06-02
forum: New to Ubuntu
---

### Post by sunwatt on 2011-06-02
I'm wondering if anyone is using this laptop with ubuntu? Any issues I should know about?

I got one of these on its way here, expected next week. Maybe I should have asked here here BEFORE I bought it.

Its got the 64gb SSD drive, no optical drive, Im using it as a netbook.

I'm thinking either Ubuntu 10.04LTS or LMDE.

Thanks

Jim

---

### Post by frogo on 2011-06-02
> **sunwatt said:**
> I'm wondering if anyone is using this laptop with ubuntu? Any issues I should know about?

I got one of these on its way here, expected next week. Maybe I should have asked here here BEFORE I bought it.

Its got the 64gb SSD drive, no optical drive, Im using it as a netbook.

I'm thinking either Ubuntu 10.04LTS or LMDE.

Thanks

Jim


Hi

I don't have that exact model but I think they're close enough... mine is a Dell Latitude e4310. Anyway, perhaps my experience will give you an idea.

1. my story:
I've been running ubuntu on this machine for nearly 10 months. I started with 10.04 and kept that install until a few weeks ago. Then I reinstalled 10.04 and immediately installed 10.10 (wget some deb packages --- I can't recall on top of my head but if you're interested I'll try to find how i did it). The reason I did the reinstall and switched to 10.10 is that in 10.04, I couldn't get past a kernel updated and the system had become flimsy. Now that I'm happy with the 10.10 I got from deb packages I don't do kernel updates.

2. the machine:
With respect to the machine. It was no choice of mine, but although I'm generally happy with it I would probably not go for that model if I could. There's a few very annoying spec choices: I hate the button in the middle of the keyboard, the headphone/microphone combo jack is useless, and there's only one USB port. But I think these would apply with any OS. 

3. ubuntu:
The first try outs of Ubuntu, booting from a USB without installing, went very smoothly. Perhaps that's because I wasn't trying a few things that proved problematic. 

3.1 tweaks for minor config:
The only additional bit I do in my installs is to download gstreamer related stuff from ubuntu-restricted-extra (from Synaptics manager, I think). That's for the video. And I have to tweak things in ALSA mixer in order to get microphones and sound working well enough to use Skype. With respect to software and applications, I can't think of anything that I had to particularly pay attention to in relation to this machine. 

3.2 major problems:
Now, this was for the sweet stuff. In my experience there are major problems related to power management, for all I understand. But they don't seem to be specific to Dell machines.

10.04: the machine can't suspend/hibernate --- I have never seen a fix nor a work around and frankly I have stopped looking. My machine is always on or off, never in between. You have to edit the power management stuff to make it do nothing when you close the lid or things of the sort (can't recall the command to open up the configuration editor from a terminal). This problem persisted in 10.10.

In my second install of 10.04, there was a point at which the only display I could get working was an external monitor. The laptop display would remain black, turned off or I don't know. I had not experienced that in my first install. (Maybe although I believe it was 10.04, they were two minor variants?) This is what made me go for 10.10 (based on this being one workaround mentioned here [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes))

10.10: The monitor trouble was resolved, but a new power management related issue arose. Now, I have to be careful when shutting down the machine to wait for it to seem to shut down and then press once the power button as soon as it restarts. It seems the machine has lost the ability to shut down and only knows to restart... This happens only when the machine is plugged. It doesn't happen when I'm on battery (so now I unplugged before shutting down if I need). I have not seen a workaround nor a fix and I have to say I don't really care at the moment, I can leave with that.

One final thing. The battery is crap on my machine. But I've noticed that WIFI is sucking battery juice like crazy. I seem to recall I've seen that to be well known about the kernels around 10.04---and by no means limited to Dell machines---and with no workaround. But I haven't looked into this for a while. I'm also nearly never using WIFI anymore and I have indeed gained more battery autonomy since.

Well, that's all I can think of and that I would have liked to know myself at my first install on this machine. It may not be very useful, I'm generally useless with Ubuntu as soon as it becomes a bit technical. But the main message is that for what I need the machine for, Ubuntu fits the bill. There are inconveniences, some due to the machine, some due to Ubuntu; but they are the sort of things I learnt to live with (on the other hand, I had to bite those bullets). 

There are other things you learn to live with and that you don't notice until you have to use, for example, a Vista machine. Like booting into ubuntu is unbelievably fast, real fast; it makes you want to bang your head when watching a Windows machine booting. Software installation is most of the time clean and nearly trivial or made simpler by very useful documentation (granted it can take a while to find the doc... but you get used to that too).  Well, my two cents...

Good luck and follow up if anything I mentioned re. configuration or installation sounds interesting. I'll try to find the specifics if that sounds useful.

---

### Post by dFlyer on 2011-06-02
I have a Dell Studio 1735. Not sure how close that model is to yours, but I have no problem running ubuntu out of the box. One thing I usually always do is download the current iso and roll my own dell version using dell recovery. Again it's not required but something I just do.

---

### Post by sunwatt on 2011-06-02
Thanks Frogo and  Gary, Latest iso is a good idea, I would have used the one I already have. And I'll make a bootable flash drive of 10.04 maybe the newer ones. The long term support offered by 10.04 is attractive, but. 

Maybe try those 1st rather than just install ubuntu right away over the windows 7 thats on it.

thanks again

---

### Post by sunwatt on 2011-06-06
Im using my Dell Latitude e4200 now... the wifi did give me a scare. But its solid now.

The dual processors, 64gb SSD and Ubuntu 10.04 bootup in afew seconds.. very nice.

---

### Post by BKbroila on 2011-06-06
I know this is marked solved, but I just wanted to add my 2 cents.
 
I have a Studio 1555, which has had several problems. Like frogo, my battery life is terrible under Ubuntu. I dual boot with Windows 7 and can get 4+ hours in Windows, but barely 2 hours with Ubuntu. And this is still a problem with Natty 11.04.
Also, my laptop has overheated a couple of times, which caused it to unexpectedly shut down without any notice. I've looked for help here on the forums, but it's never been resolved. The only thing I've ever been able to do is just add some temperature-recording panels. But other than that, I haven't been able to do much.
 
But then again, your laptop might be completely different and run smoothly.
 
There's a Dell help section too, if you wanted specific questions

---

### Post by sunwatt on 2011-06-06
Sorry your having that trouble, but maybe the next release will help. If 10.04.2 hadnt worked out, I'd have considered another distro other than Ubuntu, on the chance that fixed any issues.

I didnt know there was a Dell section !  Many thanks!!
 
There has got to be afew models that are immune to Ubuntu and all Linux, there should be a list of any brands and models that will not or should not run Linux.... 

I ordered this model without checking anywhere, a gamble... I think it paid off for me.

Counting time to type in my password, from start button push to online is about 33 seconds.

This came with Windows 7, I hear its nice.... but no thanks  :)

---

### Post by BKbroila on 2011-06-07
To be honest, Windows 7 is perfectly good. It's been a while since MS released that good of a satisfying OS. 
 
And if you plan on using a Netbook and Ubuntu doesn't run smoothly, I've heard Mint is a good alternative.

---

### Post by sunwatt on 2011-06-07
Thanks!!

---

### Post by interarticle on 2011-06-27
Linux can also boot slowly, but still faster than windows if on the same machine. My Ubuntu 11.04 took around 1 min to boot, thanks to the old hardware, but the Windows XP took nearly 15, so I'm not complaining here.

Windows 7 does boot fast, but after a while, well... It still suffers from the traditional Windows rot problem, especially after installing big things. Linux machines are typically snappy over long spans of operation, regardless of software installed (unless it's a heap of daemons).

Also, I do experience some problems with Ubuntu 10.04 LTS on E4200. No, I cannot vouch for it, but the laptop (which is currently not in my possession) resembles E4200 from every aspect. A major annoyance, flickering screen, but perhaps it was because I was using the system from an external Usb HDD (Not USB startup disk, but a real installation). Didn't experience any problem when booting from LiveCD.

---

### Post by sunwatt on 2011-06-27
Flickering screen... yes, mine e4200 had that... I sent it back

---

### Post by speculatrix on 2011-06-28
I've had a latitude E4200 from my employer for 6 months now. I dual boot windows7 and 64 bit linux (openSUSE 11.4, because I like KDE). It's pretty much the standard one with the 60G SSD, wifi is Intel 5100. No bluetooth, no separate "instantOn" arm board.

The only difference is that it has  a larger battery which increased the mass by 50%!

I run dual displays, with VGA to an external Dell 2408 panel (1900x1200). I would like a dock with DVI, but employer is too stingy. Actually, I originally wanted a latitude E64xx but they already had this e4200.

Windows7 is fairly solid, but I get screen corruption, I have tried different GM45 drivers and none have resolved it. It may be related to running twin-head, but since I only use W7 for testing VPN software and very occasional things that are windows-only I haven't put in too much time to sort it out.

Everything works well in linux; dual-screen is very solid, none of the corruption observed with Win7. My only aggravation is sound, I can get OSS to work but Alsa and Pulse don't, so its purely a driver issue. I came here hoping for inspiration.

As for other comments on battery life, see Phoronix:
[http://www.phoronix.com/scan.php?page=article&item=linux_2638_aspm&num=3](http://www.phoronix.com/scan.php?page=article&item=linux_2638_aspm&num=3)

---

### Post by Jinseng on 2011-08-02
I wanted to add my confirmation of what speculatrix is seeing in Windows 7.
 
We just purchased one an E4200 and are also seeing Display Corruption while running Windows 7 Enterprise x64.  It most often happens with dual monitors (laptop screen and a second monitor), and looks like pixilated horizontal lines mostly around windows title bars, scroll bars, desktop icons, and desktop image. Moving the mouse over the desktop icons clears them up for a little bit, but it comes back on its own.
 
I send Dell an e-mail and hopefully will hear back from them soon.  If I get any news, I'll pass it along here.

---

