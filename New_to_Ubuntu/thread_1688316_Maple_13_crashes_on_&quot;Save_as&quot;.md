---
title: "Maple 13 crashes on &quot;Save as&quot;"
date: 2011-02-15
forum: New to Ubuntu
---

### Post by lahlh84 on 2011-02-15
Hi,

I installed Maple 13 on Ubuntu, everything seems to be working perfectly except when I press Save As it occasionally just goes to a blank gray box with the Save As title bar, as oppose to showing the file browser.  This doesn't happen every time  however  and generally I just have to close the box, and press Save As two or three more times until I get the usual file browser and I can choose to save the file wherever.

Does anybody know what could be the issue here? 

Thanks

---

### Post by lahlh84 on 2011-02-16
Another issue I've discovered is 3d plotting is terrible, in Win 7 I have the ability to freely drag and rotate a 3d plot with no freezes but in Ubuntu my system can barely do the 3d plot in the first place and crashes if I try to rotate it to view from another angle. 

Maybe my graphics card or java are  not set up correctly? I have a built in Intel Graphics Media Accelerator HD on the dell inspiron 1764 laptop, i5, 4gb ram.

---

### Post by fabricator4 on 2011-02-16
It sounds like the software is buggy.  You might contact MapleSoft and see if they have any patches or solutions that will fix your problems.  Try the Maple V14 evaluation package if it's available for Debian/Ubunutu and see if the problems have been addressed.

Chris.

---

### Post by lahlh84 on 2011-02-16
I'm not sure if it's available for linux, but the windows version you seem to have to apply and wait to be contacted. 

I don't think the software is buggy, it functions normally other than the empty GUI boxes and 3d issues, which makes me suspect either java or that my graphics driver is not quite upto speed. I know Maple ships with it's own version of java and I've attempted to follow the steps to download and install jre 6 and setup maple to use this, as seems to have helped some ppl on a google search in earlier version of Maple and Ubuntu.

Is there anyway to check if my graphics driver is the best one available to me?

---

### Post by lahlh84 on 2011-02-16
Another issue is that firefox seems to render images pretty slowly, and also flash crashes occasionally when watching iplayer/youtube etc, typically when I go to full screen and change volume, fast forward. I've tried googling this and using the tips provided with no luck.

I really like Ubuntu, but these issues are dealbreakers for me as Maple is what I mainly use the comp for in the first place, and slow internet browsing on firefox will get tiresome

---

### Post by fabricator4 on 2011-02-16
I'm wondering if there's a network problem that's affecting your throughput.  Is your data rate alright otherwise?

I think there are alternatives to Adobe flash that you might want to investigate.  I use the mainstream stuff myself so haven't needed to try them.  Maybe someone could suggest which ones are worth trying.

The Ubuntu browsing and general internet experience is a delight to me so it's disappointing that you've got problems in this area. 

The problems with Maple I'm afraid come back to MapleSoft.  You should keep trying their support to get some answers, but they may say that a version upgrade is necessary.  Also see if there's any Maple users groups out there that might be able to help.

Chris

---

### Post by lahlh84 on 2011-02-17
> **fabricator4 said:**
> I'm wondering if there's a network problem that's affecting your throughput.  Is your data rate alright otherwise?

I think there are alternatives to Adobe flash that you might want to investigate.  I use the mainstream stuff myself so haven't needed to try them.  Maybe someone could suggest which ones are worth trying.

The Ubuntu browsing and general internet experience is a delight to me so it's disappointing that you've got problems in this area. 

The problems with Maple I'm afraid come back to MapleSoft.  You should keep trying their support to get some answers, but they may say that a version upgrade is necessary.  Also see if there's any Maple users groups out there that might be able to help.

Chris

Yes data rate seems fine otherwise.  

I have attempted to get in touch with Maple about a trial version of 14 to see if that makes a difference. But in the mean time is there a way I can check I have the latest graphics card driver and java installed?

---

### Post by fabricator4 on 2011-02-18
> **lahlh84 said:**
> Yes data rate seems fine otherwise.  

I have attempted to get in touch with Maple about a trial version of 14 to see if that makes a difference. But in the mean time is there a way I can check I have the latest graphics card driver and java installed?

Yes. Go:

```

->System
    ->Administration
        ->Additional Drivers

```

and let it check your driver installations.  If it says that you're not using any proprietary drivers drivers that is fine, otherwise it should find and install anything relevant. Make sure you have software sources in the same menu set to allow any third party stuff.

If you've got Java installed already then automatic updates will load the latest available.  You might want to type Java in the search box in Install Software or Synaptic and see what it finds.  Any viable alternatives should be listed there.

Chris

---

