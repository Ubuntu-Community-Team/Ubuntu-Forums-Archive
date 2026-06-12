---
title: "please help a linux noob set up his studio!"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by jitup on 2009-02-22
Hello,
I just inhaerated a gatway laptop with a pentium 1.6 GHZ 4 processor in it(I don't know what it is rated from the box but that is what I clocked it at) . I know ubuntu should run on it, I am just not sure If I should use the 64 bit or the 32 bit version. Also how much ram am I able to use (32 bit= 4 gb 64 bit = 8Gb?) 
Is there really any advantage for me to run the 64 bit if it is compatible since I have a slow speed intel?

Also, what is the absoulute best free ware DAW for ubuntu? Is ardour good?

I have an EMU 0404 usm 2.0 sound card, it works well on my xp system and I love the sound quality. I did a google for linux drivers and found there was one in development in 2007, was it ever completed and if so where can I download it?

Sorry for all the questions, they probably have been answered several times else where, and I just can't find them. If this is the case, please respond with the corresponding links. 
Thank you for all your help.

---

### Post by Temposs on 2009-02-22
hi jitup,
   The maximum amount of RAM you can use with a 32-bit OS is 3gb. Any more than that and you should install the 64-bit version. Given that it's a P4 machine, I'm guessing the motherboard only supports a maximum of 2gb, and if that's the case, then you should install the 32-bit Ubuntu.

You should see if the sound card works well by default. The way drivers work often in Linux is that they are included as part of the linux kernel, so you don't generally have to download any drivers separately, like you do in Windows. Ubuntu tries to include support for as much hardware as possible. Just try it out and see.

As for DAW software, the audio software I have the most experience with is Audacity. I like it for editing and combining tracks and such. It has a lot of nice abilities. You should check it out. It runs on Windows as well. I don't have experience with anything else.

---

### Post by ibuclaw on 2009-02-22
1) In my opinion ... I prefer 64bit computing over 32bit, so if your Laptop is 64bit compliant, I say "go for it".

2) How much RAM usage each architecture supports isn't really a question to be asking, although, yes, your are correct that the theoretical RAM Size limit for 32bit (2³²) machine is 4GB ...  And no... the limit for 64bit isn't 8GB (think 17.2 billion GBs, or 16EBs).
With todays recording needs, I'd say at least 1GB is needed, but 2GBs+ would be advantageous.

3) The best Free DAW out there is Ardour, by far. You'll want to lookup **jack** and **qjackctl** for setting up your audio device for low-latency.

4) For your EMU0404, my best suggestion would be to install **alsa-firmware-loaders** and give it a try.
If it doesn't appear to pick up the device in sound properties, open a terminal and type in
```
lsusb
```
and post the output.

Also, again, in my honest opinion, I wouldn't choose UbuntuStudio as my Studio OS. If you get something setup in Ubuntu, may do just fine. But bare in mind that there are other OS's that are tailor made for Audio Recording too.

A year ago, I would have recommended [64Studio]("http://www.64studio.com/") but it has since gone outdated (still runs on Etch).
But recently, I have discovered [A/V Linux]("http://www.bandshed.net/AVLinux.html"), and on paper, it looks the part. But I have not gotten round to testing it yet (my current studio setup is being built on Debian Lenny+extraneous audio packages).

Regards
Iain

---

### Post by stefangr1 on 2009-02-22
Pentium-4 processors don't support 64-bits at all. And I assume that a laptop with an 1.6Ghz P4 processor doesn't have more than 4GB RAM, such that the choice between 32 or 64 bits isn't really an issue: you need the 32 bits version.

---

### Post by jitup on 2009-02-22
thanks alot for all your help so far.
I looked at the A/V linux, and I think I will try that.
I don't understand what the mean about the adour being vst compatiible, I thougntyou could download the adour and it was already vst compatible. I am fimaliar with recording stuff, I have Cubase LE and Sonar LE on my windows system, but I have out grown them and need somtheing better and linux seemed to be the way to go. so can some one please explain the vst thing at the bottom of the A/V linux link?
Thank you,

PS- you guys are very helpful and I appreciate the patients.

---

