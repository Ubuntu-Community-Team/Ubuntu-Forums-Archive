---
title: "Intermittent freezing"
date: 2010-05-17
forum: New to Ubuntu
---

### Post by s1wood on 2010-05-17
Ever since I started using Ubuntu 2 months ago I have had trouble with the system freezing intermittently - the mouse moves but nothing reacts, the only thing to do is to turn it off at the button. It may not happen all day or it may happen within 5 minutes of turning on, so I don't think it is overheating, it does not depend on having too many windows open, it can happen on Open Office or on Firefox. 

I hoped that Lucid Lynx might not have the same problem, but it does. The problem could be with my hardware, I installed a second-hand motherboard on this computer and have only ever used Ubuntu on it so I have no idea how it might have performed with Windows.

Memtest hasn't found any errors on the memory.

Any suggestions?

Susan

---

### Post by dearingj on 2010-05-17
Are you able to switch to a terminal using Ctrl+Alt+F1 once your computer freezes? If you can do that, then your system isn't completely frozen: you can still run some terminal commands and maybe figure out what happened.

What about rebooting using [REISUB]("http://kember.net/articles/231/reisub-the-gentle-linux-restart")?

---

### Post by _0R10N on 2010-05-17
I have a very similar problem, but it happens when some Compiz effect takes place (e.g. switching windows, etc.) It's very disappointing since I'm having since karmic.

---

### Post by Cowboybebop79 on 2010-05-23
had a similar problem but my system has 2 gig of ram so it was only being slow rather than graying out or freezing so I had a google around and found this tut through life hacker on zolved

[http://www.zolved.com/synapse/view_content/28209/How_to_make_OpenOffice_run_faster_in_Ubuntu]("http://www.zolved.com/synapse/view_content/28209/How_to_make_OpenOffice_run_faster_in_Ubuntu")

basically the guide advises increasing the memory allocation for the open office cache and disabling "use java runtime environment" presumably so that OO uses the ram more and not the processor so much.

Hope this helps

---

### Post by s1wood on 2010-06-14
> **dearingj said:**
> Are you able to switch to a terminal using Ctrl+Alt+F1 once your computer freezes? If you can do that, then your system isn't completely frozen: you can still run some terminal commands and maybe figure out what happened.

What about rebooting using [REISUB]("http://kember.net/articles/231/reisub-the-gentle-linux-restart")?

Ctrl +Alt +F1 has no effect  - what is REISUB please?

Susan

---

### Post by dearingj on 2010-06-14
> **s1wood said:**
> Ctrl +Alt +F1 has no effect  - what is REISUB please?

Susan

It's a way to reboot the system, safer than just holding down the power button. You hold down your Alt and SysRq (a.k.a. Print Screen) keys, and slowly type REISUB.

[QUOTE=http://en.wikipedia.org/wiki/Magic_SysRq_key#.22Raising_Elephants.22_mnemonic_device] unRaw      (take control of keyboard back from X),  
 tErminate (send SIGTERM to all processes, allowing them to terminate gracefully),
 kIll      (send SIGKILL to all processes, forcing them to terminate immediately), 
  Sync     (flush data to disk),
  Unmount  (remount all filesystems read-only),
reBoot.
[/QUOTE]

---

### Post by s1wood on 2010-06-15
I have now tried that - it is not easy since Alt & SysRq are on opposite sides of the keyboard and I only have two hands! It works to restart but doesn't solve the problem of why the freeze is happening.

I tried the suggestion about speeding up Open Office but I don't think that is where the problem is, the most recent freeze happened when I was on a website with no other windows open. 

It happens with no warning, it just stops between two clicks of the mouse or keyboard, sometimes it happens when I have only just unlocked the screen from suspension and haven't done anything else. The mouse moves but nothing reacts to it and leaving it while I go and have a cup of tea (which generally worked on my old computer!) doesn't help.

Any suggestions? It is most annoying - and also gives my husband (a Microsoft user) a chance to sneer.

Susan

---

### Post by dearingj on 2010-06-15
> **s1wood said:**
> Any suggestions? It is most annoying - and also gives my husband (a Microsoft user) a chance to sneer.

Ok, let's see if we can narrow things down a bit. Try running through System Testing (System->Administration->System Testing) a few times; see if it crashes at any consistent point during those tests.

---

### Post by s1wood on 2010-06-17
Right, I tried that and it freezes every time (four times) on the video test.

This is the relevant section of the report:
xrandr_cycle fail   
compiz_check pass   Gathering information about your system...   Distribution:          Ubuntu 10.04  Desktop environment:   GNOME  Graphics chip:         Intel Corporation 82845G/GL[Brookdale-G]/GE  Chipset Integrated Graphics Device (rev 01)  Driver in use:         intel  Rendering method:      AIGLX  Checking if it's possible to run Compiz on your system...   Checking for texture_from_pixmap...               [ OK ]  Checking for non power of two support...          [ OK ]  Checking for composite extension...               [ OK ]  Checking for FBConfig...                          [ OK ]  Checking for hardware/setup problems...           [WARN]  Something potential problematic has been detected with your setup:  Warning: PCI ID 8086:2562 detected.   Would you like to know more? (Y/n)   
So where do I go from here?

Susan

---

### Post by dearingj on 2010-06-17
Hmm.. What I've found on Google suggests that this may be related to visual effects; do you have such effects enabled on your computer? Open System->Preference->Appearance and click on the Visual Effects tab. I'd suggest setting it to None if it is not already. Other than that I have no ideas, so hopefully somebody else can help. Good luck.

---

### Post by s1wood on 2010-06-18
Thanks for the advice but I just checked and  it's already on 'None'.

I just trawled the motherboard manual for the graphics card - I am inclined to suspect my hardware could be at fault.
Does this info mean anything to anyone in this context?

         &#8226; Intel 845G chipset
Graphics
         &#8226; Integrated Intel® Extreme Graphics
         &#8226; 1.5 V AGP connector
         &#8226; Single AGP port via the connector or integrated graphics
         &#8226; AGP 2.0 including 1x/2x/4x AGP data transfers and 2x/4x Fast Writes
         &#8226; 350 MHz AGP Digital Display (ADD) interface cards
         &#8226; Digital Video Output (DVO) port


Susan

---

### Post by empty_spaces on 2010-06-18
I used to have similar freezing issues with 8.10.
So I kept adding new kernels to my install as and when they were released, and one of the kernels finally solved the issue.
So that is one option you could try.
You should find a lot of info on prepackaged deb files for the kernel. I'm at work, so I can't get into the details, but post back if you have any queries.

---

### Post by sydbat on 2010-06-18
> **s1wood said:**
> Thanks for the advice but I just checked and  it's already on 'None'.

I just trawled the motherboard manual for the graphics card - I am inclined to suspect my hardware could be at fault.
Does this info mean anything to anyone in this context?

         • Intel 845G chipset
Graphics
         • Integrated Intel® Extreme Graphics
         • 1.5 V AGP connector
         • Single AGP port via the connector or integrated graphics
         • AGP 2.0 including 1x/2x/4x AGP data transfers and 2x/4x Fast Writes
         • 350 MHz AGP Digital Display (ADD) interface cards
         • Digital Video Output (DVO) port


SusanI imagine it is the Intel graphics. 

Since you are running Ubuntu on an old computer, my best guess is that graphics chipset is no longer supported by Intel, and therefore has no driver support in the kernel.

The other thing it could be is hardware failure centred around the Intel graphics chipset.

Either way, it has to do with the Intel Graphics chipset.

---

### Post by s1wood on 2010-06-20
Ah well, that's not very helpful but it is rather what I expected. I'll have to live with it, it's OK as long as I remember to save frequently. 
Apart from that I'm loving using the OS, I was previously running Windows XP on a Pentium 3 so it's a vast improvement. I've tried a couple of other Linux distributions but this one has been easiest.

Thanks,

Susan

---

### Post by s1wood on 2010-11-19
OK! I installed 10.10 last month and have had no problems since . I still don't actually know what was causing the problem but it seems Meerkat is the answer. Simples!

Susan

---

### Post by Myrmidon83 on 2010-11-19
Hmm, that is interesting as I have the same intel graphics as you.

Maybe I should give 10.10 a go, hell all the other distro's have been problematic and I doubt 10.10 will change that.

On 10.10, are you able to use compiz effects?

---

### Post by Keith.McDougall on 2010-12-02
I'm using a brand new Samsung R530 laptop and have exactly the same problems, freezing screen, sticking mouse. Video freezes but sound still runs on it.
I also have an Intel chipset. I have had to revert to 9.10 to get a working machine.

---

