---
title: "Can't view street view in google maps"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by Captain_Glen on 2009-05-20
Hi,

When I go to google maps and load up street view all I get is a black box with no picture.  I have flash player installed because I can view You Tube videos.

I am using Jaunty Jackalope.  When I was using Hardy Heron and Intrepid Ibex it worked fine.  But now that I have upgraded it no longer works.

Any help would be appreciated.

---

### Post by Captain_Glen on 2009-05-20
Don't worry I fixed it.  I just had to uninstall swfplayer and make sure it was using the adobe flash player.

---

### Post by robbie d on 2009-05-23
You might be pleased to know that it also fixes a lot of other flash video sites too. I had the same problem.

---

### Post by singlepayernow on 2009-06-22
Sorry, I'm new to ubuntu. How does one uninstall swfplayer? I can't find it on add/remove.

---

### Post by singlepayernow on 2009-06-22
Additionally, how does one "make sure firefox is using adobe flash player"? 

In Firefox, I go into Edit>Prefrences>Applications and scroll down to Flash Video, and the default player is set to "VLC Multimedia Plugin". I take it this needs to be changed to the Adobe Flash plugin for Firefox, but I don't know how to do this. 

Any help would be appreciated.

best,
Tyler

---

### Post by beastrace91 on 2009-06-22
I am assuming this is just an Adobe issue but on my 64bit Ibex install using Adobe Flash player I get black spots in most places when trying to use street view on Google maps.

~Jeff

---

### Post by TokyoYank on 2009-08-14
copied from [http://www.google.com/support/forum/p/maps/thread?tid=08783e73a073457d&hl=en](http://www.google.com/support/forum/p/maps/thread?tid=08783e73a073457d&hl=en)

(Step 0, install Synaptic:  Applications > Accessories > Terminal > sudo apt-get synaptic)


1. Go to System>Administration>Synaptic Package Manager. 

2. Search (click the binoculars) for "flash." 

3. Mark for complete removal anything with swfdec in the title or description.

4. Mark for installation the [s]adobe-flashplugin[/s] flashplugin-installer package.

5. Restart Mozilla.

---

### Post by poikiloid on 2009-12-28
if you have 64 bit ubuntu: adobe flash is in alpha. if you want to use development version, follow this:
[http://ubuntuforums.org/showthread.php?t=1358591](http://ubuntuforums.org/showthread.php?t=1358591)

---

### Post by TokyoYank on 2009-12-28
> **poikiloid said:**
> if you have 64 bit ubuntu: adobe flash is in alpha. if you want to use development version, follow this:
[http://ubuntuforums.org/showthread.php?t=1358591](http://ubuntuforums.org/showthread.php?t=1358591)

I run 64 bit kernel 9.04 w/ firefox 3.0.16 (and 3.5.6) and haven't had a problem with the fix I posted above.

... except, I notice the package I have is now called flashplugin-installer.  I will edit my post above

---

### Post by alfu on 2010-02-10
____________________________________________________

**SOLVED: I had to go back and remove the 'swf' mozilla package; now it works.**

I have the same problem, which is frustrating, because it USED TO WORK, in 9.04.  I thought the problem surfaced when I upgraded a Toshiba laptop to 9.10, but it is also broken on a HP dv2 with 9.04.

Sadly, the Synaptic Package Manager shows nothing called a flashplugin-installer package, or anything similar to it.

[INDENT]I solved this part: Under System > Administration > Synaptic Package Manager > Settings > Repositories choose the 'Software restricted by copyright ...' option.  Then the search function will reveal the flashplugin installer.[/INDENT]

I DO NOT have flashblock installed, but flash web objects show up as gray boxes with a large 'PLAY' arrow on them.  Usually, when clicked, the flash plays.  In the Google street view, if I rightclick the black box I get a pop-up menu that has the PLAYING option checked.  When I uncheck it, the large gray play icon appears over the black box, but still no street view in either mode.

---

