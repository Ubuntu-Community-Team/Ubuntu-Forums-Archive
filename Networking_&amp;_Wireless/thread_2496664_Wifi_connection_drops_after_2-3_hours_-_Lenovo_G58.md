---
title: "Wifi connection drops after 2-3 hours - Lenovo G580 laptop"
date: 2024-04-07
forum: Networking &amp; Wireless
---

### Post by Linux_newbie_no1 on 2024-04-07
Very frustrating issue (which doesn't happen if I boot into Windows), I'm running Ubuntu 22.04, and after about 2 hours my wifi connection dies. Often, when I then disconnect and reconnect it fails on configuring network. if I switch the laptop off and leave it for about 20 minutes it's then fine again, (for another 2 hours or so anyway), but a quick log-off or reboot doesn't always work effectively. Additionally it seems that if I drag the Network menu down from the menu bar and hover my cursor over the connected wifi entry the connection improves somewhat, but this is not consistent. I guess it's probably either a driver problem or a power saving problem (or both), and I've trawled forums and tried various instructions but nothing has worked. Can anyone help with this? (bearing in mind I'm a complete Linux novice, I'm good at following detailed step by step instructions but have no understanding of what I'm doing or why).

---

### Post by hyperlinxe on 2024-04-11
That is a typical problem with linux distributions, which are computer operating systems composed of primarily free software, and software that empowers users to use computers and technology free of the constraints imposed by their competitors in the operating system world.

Often times there are no good explanations as to why problems occur when using linux, as opposed to windows, where as you say, everything
works. We have to be careful about reading into our superstitions however when using computers. You remember hovering your mouse over something, and when you did that, at the same time, the situation changed.  Computer software, and computer technology broadly works based on rigidly defined rules. And so when we solve technological problems, we have to go through the rules in order of precedence in order to solve these problems, but the problem is that computer programs, have a mind of their own, and our machines aren't an island in a dead world where no outside influence could possibly take place. That means we can't see most of what is happening when we are using computers, we can only see limited information, and they naturally change over time, which changes how they operate irrespective of our instincts.

If your connection drops, and then you try to reconnect, and fail, that is likely because your internet connection has dropped, not because your operating system has done something wrong. 

The first thing to do if THAT happens, is to check your router, and see if it has any error codes(blinking lights) displayed.  You might of experienced a brief network outage, and were led to believe this far reaching narrative about ghosts in the machine and felt confused by it all.

---

### Post by him610 on 2024-04-11
Well, if connecting using 2.4 G band, you might try the 5 G band, or vice versa. There are a lot of other devices that use the 2.4 G band that may emit RFI that interferes with your connection.

---

### Post by praseodym on 2024-04-11
Please run the wireless-script from the sticky thread anf show the output

---

### Post by Linux_newbie_no1 on 2024-04-12
I shall have a look at that and see if I can fathom it out, cheers.

---

### Post by praseodym on 2024-04-12
Run it when its working, and when not

---

