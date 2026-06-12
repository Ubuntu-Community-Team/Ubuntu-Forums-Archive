---
title: "Problems installing dial-up modem (Pentagram Predator USB modem on Feisty)"
date: 2008-02-02
forum: Networking &amp; Wireless
---

### Post by Monika on 2008-02-02
I've been cut off from my regular internet connection and have to use a dial up modem for a while. I've never had to configure any hardware under linux before as all my hardware has worked out of the box on Ubuntu uptil now.
The tutorials I've looked at are very confusing to me :confused:

From what I can make out I'm supposed to use a script called scanmodem and then make use of the ModemData.txt file, but I don't understand the output at all.
If I've understood the purpose of running the script (finding out what kind of drivers I need?) I don't need to make use of that script anyway because linux drivers are included on the modem installation CD, so surely those should be ok?
There's a README file with the linux drivers which has instructions on how to do the installation, but I get stuck at this point:

> 3. Review and edit (if need) 'Makefile'.

   Note: Probably you will want to correct in Makefile path to your
         local linux kernel header files:

         	KERNEL_INCLUDES=/path/to/linux/include


I have absolutely no idea where the kernel header files are. I tried the path /usr/src/linux-headers-2.6.20-16/include , but apparently I got it wrong because when I try to do step 4 (run the make command) I get lots of C compilation errors.

Finally, from what I can make out, it sounds like I should have to re-compile the kernel (which I've never done before either) to get any sort of hardware working. But nowhere in the README instructions does it say anything of the sort.
That said, at the moment it seems like I can't re-compile the kernel because I need a working internet connection in ubuntu to be able to install the ubuntu kernel source files - unless there's another way of getting them?

Any help would be much appreciated :) I've attached the make errors, the makefile, the README and ModemData.txt to this post in case I've not gone wrong with what I've done so far (though I rather think I have :-P ).

---

### Post by linux-addict on 2008-02-02
The quickest,  easiest solution - look at buying a very cheap linux compatible modem.  I used a Dynalink 56K e-modem V90 modem out of the box and it connected via a serial port - just plug & play.....  Now on wireless - dialup modems are practically given away on TradeMe or EBay?:)

---

### Post by Monika on 2008-02-04
> **linux-addict said:**
> The quickest,  easiest solution - look at buying a very cheap linux compatible modem.  I used a Dynalink 56K e-modem V90 modem out of the box and it connected via a serial port - just plug & play.....  Now on wireless - dialup modems are practically given away on TradeMe or EBay?:)

I'm hopefully only going to be off-line for 2-3 weeks, so I'm not sure I want to fiddle around with buying new hardware, finding out that doesn't work either etc. (AFAIK this dial-up modem *is* linux compatible - or else why would the vendor include linux drivers?).
Also, we're not talking about a wireless modem - I need one that works with the landline (unless wireless modems do? I have no idea, never used one). The last time I had to use dial-up (which was about a year ago) this was pretty much the only linux compatible dial-up modem I found (I didn't manage to set it up on ubuntu then either).

There may be modems which are easier to use with linux, but the real problem for me is that I cannot make any sense of the instructions I've found :( I'm sure a similar situation will happen in the future and I'd really like to finally learn how to deal with stuff like this. I still have no idea where the kernel headers are in a typical Ubuntu Feisty installation (I've googled that and searched on this forum and came up with no answers about this! everyone seems to expect people to just know - well I don't :-P and they don't seem to be in the standard place or the Makefile would have worked the way it was originally).

---

### Post by Bartender on 2008-02-09
I believe scanmodem is just to help you identify your modem chipset.  The fun part begins after that.  For most of us, especially if you aren't skilled with Linux tasks, getting winmodems to work is a long uphill slog.

Unlikely you'd figure it out before the two or three weeks you mention is gone.

---

