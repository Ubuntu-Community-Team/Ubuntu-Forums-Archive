---
title: "random freezing"
date: 2010-12-23
forum: New to Ubuntu
---

### Post by uveryames on 2010-12-23
i was on youtube browsing through videos when suddenly my screen froze and the sound was repeating the same clip.  i waited 5 mins to see if it would get itself fixed but it was just still frozen.  

later that night i was checking my email and the same issue came up...the compy just froze.  

never had this happen on win7 on this laptop.  any settings that might be making it freeze?  any ideas?

using a core 2 duo t9800 2.93
4 gigs ddr3
500 SATA II HDD
geforce 130m

...i dont think its the hardware....

---

### Post by theasprint on 2010-12-23
Hi,

In fact. I do suspect the hardware, especially the Graphics card.

As my signature suggests, I can help.

Here have a look at [http://ubuntuforums.org/showthread.php?t=1648734](http://ubuntuforums.org/showthread.php?t=1648734)
The user here has a similar problem about lagging and freezing when playing video.

In fact I would also suspected that you installed the Nvidia drivers UBUNTU PROVIDED you.
The drivers Ubuntu provides are not up to date and may not be fully compatible.

So I suggest you should follow my steps. (Just as in the link I gave you)

1. Uninstall/Do not use the Nvidia Drivers that UBUNTU PROVIDED.
Go to hardware drivers and disable them.

2. Go to nvidia.com and download the latest drivers for your graphics card model.
Remember to download the Linux/Ubuntu version.

3. Turn off your gdm (graphics mode) by executing:
```
sudo service gdm stop
```

4. Install the Nvidia drivers you downloaded by executing:
```
sudo bash <your Nvidia driver's directory>
```

5. Turn on your gdm by executing:
```
sudo service gdm start
```

If you want further details or if this doesn't work, try going to the link in my signature (not the bootinfoscript one) and look for the post by TheRawGod.

Good Luck :D

---

### Post by uveryames on 2010-12-23
thanks for the swift reply. 

i tried your steps.  when i try to sudo bash the file i get an error: something about a binary file.

i have the latest nvidia driver for my card downloaded to my desktop.  

sudo bash /home/uveryames/Desktop/filename.exe

---

### Post by uveryames on 2010-12-23
i deleted the file and downloaded it again.  ran the commands that you provided....annndddd ....success!

thank you :D  runs much cleaner now too.  

woooot

thank ya thank ya thank ya

---

### Post by miegiel on 2010-12-23
With random crashes I'd normally suspect the hardware, starting with the power supply. However I have just had a random crash period too, on average 1 crash a day. I never did figure out the cause, but the [Adobe Flash Player 10.2 Beta]("http://labs.adobe.com/downloads/flashplayer10.html") was one of the last suspects in my list. Now I'm using the 10.1 flash player again and I don't get random crashes anymore. But a lot has changed on my machine the past 2 weeks, I'm test driving xubuntu 11.04 at the moment, So it's hard to say what fixed the crashes.

I **don't recomend** that you try the 11.04 alpha. But, if **theasprint**'s suggestions don't fix the crashes, you could consider trying 10.04 (lucid lynx), it's the previous ubuntu and a longtime support version (will get updates till april 2013).

> **uveryames said:**
> i deleted the file and downloaded it again.  ran the commands that you provided....annndddd ....success!

thank you :D  runs much cleaner now too.  

woooot

thank ya thank ya thank ya
Heh :D great! Random crashes are a pain.

---

### Post by amjjawad on 2010-12-23
> **miegiel said:**
> I **don't recomend** that you try the 11.04 alpha.

That's exactly why you could always use the LiveCD/USB ;)

I created a LiveUSB for 11.04. Got some errors and didn't like the new Desktop. No changes were made to my machine.

---

### Post by theasprint on 2010-12-23
Hi,

Congrats.

* Just a note, I noticed something.

> sudo bash /home/uveryames/Desktop/filename.exe

It can't possible be filename.exe could it? .exe files are for Windows and Windows only.

Its ok, I'm not criticizing you. 

BTW, if you know anyone with similar problems and with an NVIDIA card, you can carry out and teach the same procedure I thought you.

By installing the latest Nvidia driver, I suppose you may also have an Nvidia X Server manager installed. Its just like the Nvidia Control Panel in Windows.

---

### Post by uveryames on 2010-12-23
> **theasprint said:**
> Hi,

Congrats.

* Just a note, I noticed something.



It can't possible be filename.exe could it? .exe files are for Windows and Windows only.

Its ok, I'm not criticizing you. 

BTW, if you know anyone with similar problems and with an NVIDIA card, you can carry out and teach the same procedure I thought you.

By installing the latest Nvidia driver, I suppose you may also have an Nvidia X Server manager installed. Its just like the Nvidia Control Panel in Windows.
i wrote .exe by habbit.  i downloaded the linux file .run lol...but thanks

ok now i have an issue.  installed the driver from nvidia and everything was working great.  i just rebooted into ubuntu again...and it wont boot into graphics mode.  just stuck in the terminal.  

i have my "hybrid" graphics disabled..which was the problem i had at first.  when hybrid graphics was enabled it would only boot into term.  soooo noooww whatttt lol :(  

ctrl + alt + f7 doesnt switch into the grahpical mode.  and sudo service gdm start doesnt work either.  

hellllpppp!!  

ty for all the help so far!

---

