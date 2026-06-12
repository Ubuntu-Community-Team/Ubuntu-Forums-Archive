---
title: "A problem with sound and a bit of a rant"
date: 2009-08-02
forum: New to Ubuntu
---

### Post by andypearce on 2009-08-02
Hi... when I start my computer the ubuntu tune only works one in seven or so start ups. Sometimes it starts up and becomes a clicking sound half way through, sometimes the tune does not play. If the tune does not work normally the computer will not play dvds, cds or flash. I can get on youtube but the flash bit will not play. I am using a toshiba satellite pro L100 that I wiped XP off and installed Intrepid then upgraded to Jaunty. The problem was there with Intrepid as well. I have tried to solve this problem by going through all the stickies for multi-media that I can find, I have posted this problem in other bits of the forum and done all suggested but it has not worked or the person making the suggestion disappears so I cannot follow up what I am to do. I have probably spent fifty or sixty hours on this so far. I have now concluded that
1. I do not understand most of the language used so I think I am probably still an absolute beginner (English is my native language... I am English...but the jargon defeats me...) So I am going to re post my ongoing and very annoying problem on this bit of the forum
2. Ubuntu is not a straight forward OS (I know what OS means now...)like windows and is probably not suited to ordinary folk with little computer knowledge. The only computer in my school in 1979 did not work, so no one could learn about it..well the teacher could not be bothered..he probably knew less about it than the average infant school child does now!. I can operate a computer, install programmes etc. that is easy, but if you have to do something to it.... well the first non standard word throws you. On this there is a terminal that some people call a kernel..it took me ages to work out they were the same thing.. more or less... well in terms of doing things to the OS.
3. The problem my computer has is too difficult for anyone on the forum to solve so I am going to give up.
All the best
Andy Pearce the totally lost:confused:

---

### Post by llamabr on 2009-08-02
You're right that linux contains its own esoteric language, and has a learning curve, although ubuntu mitigates these better than both.

In the end, though, a computer and its os is just a tool to accomplish some task.  If ubuntu is not doing the job for you, and there's one you like better, there's no good reason (besides the 250 dollars or so the next most popular alternative sets you back) to go with it.

Weird about the sound issue.  Since it's not constant, it sounds like a hardware issue, not software.  Maybe a loose connection.  Have you tried to see if the sound works properly through the headphones jack, rather than onboard speakers?

Regarding youtube and flash,  you need to install the firefox plugin, by doiing:

```
sudo apt-get flashplugin-nonfree
```

It's not enough to have flash installed, only.

best wishes,

---

### Post by j.bell730 on 2009-08-02
> **llamabr said:**
> 
```
sudo apt-get flashplugin-nonfree
```


I believe you mean
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by andypearce on 2009-08-02
Hi I already have that plug in thanks... It does not work because of something that either does or does not happen at start up... and the indicator of that is the start up tune. I have no idea what.

Thank you very much for your replies.

Andy

---

### Post by CatKiller on 2009-08-02
Are you using PulseAudio or ALSA for your sound? PulseAudio is supposed to re-start gracefully if it crashes; I'm not sure that ALSA is.

The [Terminal]("http://en.wikipedia.org/wiki/Terminal_emulator") and the [kernel]("http://en.wikipedia.org/wiki/Kernel_%28computing%29") are very different things.

---

### Post by andypearce on 2009-08-02
Hi Catkiller, how would I know....I thought pulse automatically installed when the upgrade to jaunty happened... I dont think I have told it not to, but I have kind of lost track of all the things I have done to this.
Ta
andy

---

### Post by Sidewinder1 on 2009-08-02
I know how frustrating sound issues can be. That was the only problem that I had with my initial Ubuntu install; after searching the forums and reading and trying everything suggested,...no sound. I got so pissed off I tried something 'off-the-wall', I plugged my speaker plug into the fourth jack on my sound card; It worked! The amazing part is that Winbloze sound worked in that fourth port too, when it had been working fine in the initial port for years. Go figure.  Don't know if this could be a solution for you or anyone else....Take it for what it's worth...
Side

---

### Post by wpshooter on 2009-08-02
Andypearce:

When you initially installed Ubuntu, did you check the integrity of your Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu ?

Also, I do NOT recommend trying to upgrade from one version of Ubuntu to the next version of Ubuntu (some others may have different opinions about this) but recommend installing each subsequent / later version of Ubuntu from scratch.  I believe if you follow this recommendation, you will have a better chance of having a satifactory installation of Ubuntu.

Also, I take it that your machine is a laptop, in which case the sound function is built into the motherboard.  Have you checked a sound/audio related settings in the BIOS to make sure they are properly set ?

P.S. - As far as Flash is concerned, you do NOT want to install the flash plugin that is found in Synaptic, instead you want to install the COMPLETE Linux TAR version of the Linux Flash program which you can download from the REAL (not one of those fake) Adobe website.

---

### Post by andypearce on 2009-08-02
Hi all.... thanks for the information I will work through the suggestions. As far as the intrepid disk I used, my daughters boyfriend downloaded it onto CD from the net... he has done a subsequent install and all is fine with his on his (better) toshiba laptop. I will go to the adobe site as suggested but will have to work out what a BIOS is.

Thanks to all
Andy

---

### Post by CatKiller on 2009-08-02
> **andypearce said:**
> Hi Catkiller, how would I know....I thought pulse automatically installed when the upgrade to jaunty happened...

Actually, I think it was Hardy that brought the installation of PulseAudio by default. It wasn't that popular a decision, since the configuration included at that time was a bit rubbish.

As to how you'd know, System &#8594; Preferences &#8594; Sound allows you to configure which method you're using for a bunch of things. The test button there might help you to isolate where the problem lies.

(As an anecdotal data point, I've been upgrading rather than re-installing since Hoary with no problems. Some people swear by nuking their install, though.)

---

### Post by andypearce on 2009-08-02
Gone to look at sound... tested all and they make a clicking noise... same as happens to the welcome tune most boot ups....

---

### Post by kansasnoob on 2009-08-02
Regarding the sound issue, since this was an upgrade from Intrepid to Jaunty, I'd follow only section **Part A: Common instructions** of this guide:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Since you're a noob (consider my moniker is kansasnoob) I'd copy-n-paste all terminal output into an Open Office word document and save it - you can name it anything you like (I use Abiword but Open Office is installed by default) that way you can post the results here if something fails.

Regarding flash, Jaunty is the simplest yet! Go to System > Administration > Synaptic Package Manager and click on Search (not Quick Search or Rebuilding Search) and type "flash" (without the quotation marks). The only two packages that should be installed are "adobe-flashplugin" & "ubuntu-restricted-extras 31". All "swf-dec" and/or "gnash" should be marked for complete removal.

Also, please continue to post questions here because you'll get a wide variety of responses, but you may also PM me if you wish.

---

### Post by andypearce on 2009-11-28
Hi all upgraded to 9.10 and it now works perfectly
Thanks
Andy

---

