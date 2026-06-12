---
title: "WRT54GS whacked-out admin page"
date: 2007-01-27
forum: Networking &amp; Wireless
---

### Post by po0f on 2007-01-27
Ok, I decided to take the plunge into wireless networking today.  Went out and bought a new router (a wrt54gs, ver 6) and wireless card (a bcm4318 based card, I can hear the groans now).  The thing is, the card isn't the problem.  It's working fine and everything.  I have successfully logged onto my neighbor's wireless network.

For whatever reason, I can't log onto my own router though.  I must confess my ignorance when it comes to anything not-wired.  For instance, from Windows, the EasyLink Advisor gave me a 6 character password (which I'm guessing is useless beyond Windows) and a 128bit key phrase.  I can't for the life of me figure out where to input this key phrase.

I'm using network-manager-gnome.  /etc/network/interfaces contains nothing but the "lo" entries.  When I click on the nm-applet and select my network, it asks for the password type (WEP128-hex, WEP128-ascii, WEP64/128-hex).  I've tried all the combinations I could think of, checking the different options, using upper- or lower-case letters in the key phrase, etc.

I'm guessing it's a simple configuration error on the router's part, but guess what:
[img]http://ubuntuforums.org/attachment.php?attachmentid=23965[/img]

Yeah, so I'm kinda irritated at the moment.  If anyone can give any insight into the problem, it would be much appreciated.

(Yes, I am currently looking into upgrading the router's firmware, hoping that will fix it.  Not with OpenWrt; yet, anyway.)

---

### Post by tturrisi on 2007-01-27
access te router from a windows box & if still looks funky then exchange the device at the store you got it at.  Could also be a fonts issue w/ the browser.

---

### Post by matthew on 2007-01-27
> **tturrisi said:**
> access te router from a windows box & if still looks funky then exchange the device at the store you got it at.  Could also be a fonts issue w/ the browser.Look again at the screenshot...oops! that is a windows box.

Start by connecting to the router with a cable, thereby bypassing the wireless encryption. If you still can't read from the router I would have to agree it's probably an installed-fonts problem, although that seems odd.

I have version 1.something of that router (well, wrt54g anyway). If you can't get it running with a cable post again with the firmware version you are using. If I'm running the same or close I'll take some screenshots of the main pages so at least you will know what the options are and we can go from there.

EDIT: The router isn't in the same room and I can't get to it right now, but I can check the firmware version. I'm using 4.20.7

---

### Post by matthew on 2007-01-27
> **matthew said:**
> If I'm running the same or close I'll take some screenshots of the main pages so at least you will know what the options are and we can go from there.

EDIT: The router isn't in the same room and I can't get to it right now, but I can check the firmware version. I'm using 4.20.7I thought that seemed a bit lazy of me since it's Saturday and I'm not working or anything right now...I still can't get to the router to get the hardware version number (my wife is napping in the room where it is and I don't want to wake her up). 

I did, however, make some screenshots to get you started...at least you should be able to figure out where to look now. If there's a specific menu you need let me know.

---

### Post by po0f on 2007-01-27
matthew,

The thing is, the only page I can access from the main one is Forward.htm (the port forwarding page).  The ampersand in the screenshot I posted is the only visible link.  I tried left-clicking and dragging the cursor all the way down the page, but besides the text that is visible, there is nothing.  If you gave me the addresses of the other pages, I'm afraid I'd still have issues deciphering what was actually on the page.  I have these issues with both Firefox and IE.

I'll try adjusting my font settings to see if it changes anything.  If all else fails, I can return it.

And just to clarify, this is from a Windows box trying to access the router from a wired connection to it.

[EDIT]

Thanks for the help so far all.

---

### Post by matthew on 2007-01-27
That's very odd. This makes no sense.

Do you have the documentation for the router? I am going to recommend you do a full hard reset. Not a soft reset, but the full one that will restore everything to factory defaults. If not, [look here]("http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1127782957298&pagename=Linksys%2FCommon%2FVisitorWrapper") to get a manual.

FYI, I looked. I have version 2.0

---

### Post by po0f on 2007-01-27
matthew,

I had already tried resetting to factory defaults to no avail.  But it doesn't matter now.  I feel so stupid, the answer was kind of obvious.  I had to turn off ZoneAlarm on my Windows box.  :)

Thanks again for the help matthew.

---

### Post by matthew on 2007-01-27
LOL. I'm glad it was something easy. Congrats for figuring it out.

If it makes you feel any better I've done far more work only to discover I've left something unplugged or had the caps lock key on or other numerous and embarrassing things. It isn't that smart people don't make these mistakes, but rather that they learn to look for these things earlier and earlier in the troubleshooting process. :)

---

