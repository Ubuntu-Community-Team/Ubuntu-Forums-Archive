---
title: "Malicious Commands in the Malicious Commands Thread??"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by Roger Allott on 2009-11-01
Something very bizarre and rather worrying just happened to my system.

I'm running Ubuntu 9.04 (jaunty). Details of hardware are in my sig.

I had Firefox (3.0.15) open and my File Browser (Nautilus 2.26.2) open.

I had just been saving images from a web page to a folder on an NTFS disk.

Then, I popped over to this forum, and out of idle curiosity, clicked on the link to the thread at the top of the Absolute Beginner Talk sub-forum entitled [ATTENTION ALL USERS: Malicious Commands]("http://ubuntuforums.org/announcement.php?f=326"). (I'd advise you not to follow that link until you've read the rest of this post!)

One of my concerns about Linux has always been that despite its many inherent security advantages over Windows, the encouragement (and sometimes need) for noobs to run commands in CLI, often as root, is itself a major security vulnerability. So, I thought I'd find it interesting to know what commands I should be most concerned about.

On opening the page, I noticed that some of the text was showing as gibberish - sort of a bit like Chinese characters, but not.

In the only post on the thread, the contributor has kindly pointed out some examples of malicious code, and put them into code tags for easy readability. However, the contents of the code tags were completely blank to me, although it was clear that some text was meant to be there.

That was odd, I thought, so tried to highlight the unseen code tags content, copy it to clipboard, and paste it into a text document.

I had to open my Text Editor, by going through Applications>Accessories, but all of the options in my menues now had no icons associated with them.

Things were now becoming alarming, so I thought it would be good to shut own and reboot.

I clicked on the Quit icon, and all of the options there were now 'words' with characters that were exclusively a rectangular box. Fortunately, I remembered that the Shut Down option was the bottom one, so clicked that and got the query box saying that the system would shut down in 60 seconds etc., except it didn't say that, but just more rectangular boxes.

The shut down procedure started correctly, but hung just after the wallpaper had disappeared. I was concerned that whatever had happened to my system might still be doing something I really didn't want to happen, so I forced a power-off shutdown and left it for a minute or so before booting up again.

Upon booting up, everything **appears** to be as it should be, although I haven't done an exhaustive check on my folders. My menus seem to be fine, and I'm not getting any rectangular box characters. However, the folder that was open in Nautilus, into which I had been saving images before going to the Malicious Comments thread, is now completely empty.

---

### Post by Bios Element on 2009-11-01
I'm going to step out on a limb here and say *(Assuming a vanilla-ish install)* the post was 100% totally unrelated to any bugs you encounter. In short, it was a coincidence.

The above is of course assuming you don't have some funky configuration that runs everything on the clipboard in a console or something like that.

---

### Post by Roger Allott on 2009-11-01
> **Bios Element said:**
> I'm going to step out on a limb here and say *(Assuming a vanilla-ish install)* the post was 100% totally unrelated to any bugs you encounter. In short, it was a coincidence.
The common-sense part of my brain tells me that it was coincidence too, but the coincidence of being on a page about malicious commands and some sort of nasty thing happening to my system necessitated my writing about it here to double-check.

> **Bios Element said:**
> The above is of course assuming you don't have some funky configuration that runs everything on the clipboard in a console or something like that.
I really don't think my system has a weird configuration like that - at least, I haven't **deliberately** set it up that way!

---

### Post by donato roque on 2009-11-01
I've always clicked this link.  I learned many things to avoid doing.  
Nope.  I can't reproduce what you just said.

---

### Post by peculiar penguin on 2009-11-01
I've clicked that link several times now and nothing entertaining happened. I'm very disappointed and would like to request a refund :P

---

### Post by liquidbee on 2009-11-01
There have been no Chinese characters or any other kind of commands that might be executed by copying them to clipboard. If you are not afraid from opening that page one more time, please reply with a screenshot.

---

### Post by Old *ix Geek on 2009-11-01
It was just a coincidence. I've had those Chinese-ish looking characters show up from time to time over the years, and it's never been anything but some flaky thing happening with the video/display.
> tried to highlight the unseen code tags content, copy it to clipboard, and paste it into a text document.

I had to open my Text Editor, by going through Applications>Accessories, but all of the options in my menues now had no icons associated with them.

Things were now becoming alarming, so I thought it would be good to shut own and reboot.
The act of pasting text into a text editor CANNOT cause your computer to become compromised, hence there's no need for the windoze "I must shutdown/reboot every time something goes wrong!" mentality. This isn't windoze. Rebooting is USUALLY unnecessary.

---

### Post by Roger Allott on 2009-11-01
> **liquidbee said:**
> If you are not afraid from opening that page one more time, please reply with a screenshot.

With a glug of trepidation, I did as requested, and thankfully this time the page was shown correctly. No need for a screenshot, as it would just look exactly like what you see.

Whatever the hell was happening, thankfully it's not happening now. It would be nice to know what the problem was though, to avoid it happening again.

---

### Post by Roger Allott on 2009-11-01
> **Old *ix Geek said:**
> It was just a coincidence. I've had those Chinese-ish looking characters show up from time to time over the years, and it's never been anything but some flaky thing happening with the video/display.
Seems sensible. Any idea what would cause such flaky video/display behaviour?


> **Old *ix Geek said:**
> The act of pasting text into a text editor CANNOT cause your computer to become compromised, hence there's no need for the windoze "I must shutdown/reboot every time something goes wrong!" mentality. This isn't windoze. Rebooting is USUALLY unnecessary.

Yes and no. My system was falling apart, it seemed, and was getting worse every time I tried to do something. I could have simply posted my problem here to try to get an on-the-spot resolution, but that would have meant doing something, and as doing something seemed to be eliciting a getting worse scenario, the only sensible option was to shutdown and see what the damage was.

---

### Post by Old *ix Geek on 2009-11-01
> **Roger Allott said:**
> Seems sensible. Any idea what would cause such flaky video/display behaviour?Could be any of a million things, most of which are harmless.
> Yes and no. My system was falling apart, it seemed, and was getting worse every time I tried to do something. I could have simply posted my problem here to try to get an on-the-spot resolution, but that would have meant doing something, and as doing something seemed to be eliciting a getting worse scenario, the only sensible option was to shutdown and see what the damage was.I understand why you're saying what you're saying, but I just want to impress on you that as a Linux user, you need to shed the Micro$oft "rebooting is the answer!" mentality.

I also understand that, at this point, you're probably not aware that there are other options when, as you thought, your system was falling apart. For example, you could have just restarted your X server by pressing **[ctrl][alt][backspace]**. That takes a second [or two] and you're back up and running, as opposed to the amount of time involved with rebooting or shutting down.  If it was just something flaky in your display, this most likely would've solved the problem.

---

### Post by Roger Allott on 2009-11-02
> **Old *ix Geek said:**
> 
I also understand that, at this point, you're probably not aware that there are other options when, as you thought, your system was falling apart. For example, you could have just restarted your X server by pressing **[ctrl][alt][backspace]**. That takes a second [or two] and you're back up and running, as opposed to the amount of time involved with rebooting or shutting down.  If it was just something flaky in your display, this most likely would've solved the problem.

That's a very useful thing to know! There really ought to be a sticky on this forum listing the little things like that that make the ubuntu experience so much better.

While I can accept a gremlin in the X server as being the most likely culprit in this situation, I still think it's rather important that it caused me to lose the local files in the folder I had been browsing in Nautilus.

As it happens, the folder in question only contained a few image files that are easily replaceable, but I shudder to think of the consequences if I had been browsing my /var/www/ folder, for example!

---

