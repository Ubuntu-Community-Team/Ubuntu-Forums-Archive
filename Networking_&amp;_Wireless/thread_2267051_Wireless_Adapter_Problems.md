---
title: "Wireless Adapter Problems"
date: 2015-02-27
forum: Networking &amp; Wireless
---

### Post by Joe_G. on 2015-02-27
I am a new Ubuntu user (first time using Linux), and I am having a bit of difficulty getting my wifi adapter (Netgear A6200 Wifi USB adapter) to work. When I was running Windows 8, I just plugged it in, and it worked immediately. Now though, it isn't even recognizing the adapter, in fact the adapter doesn't even seem on as the light that indicates that it is on isn't blinking at all.

Is there something I can do to figure out the problem? I'm running 14.10 (Utopic Unicorn)

Not to be a complete noob, but if you could provide detailed to semi-detailed instructions that would really help. :) 

I'm not at all exaggerating when I say I am completely new to this.. haha..

---

### Post by dale1944-a on 2015-02-27
[http://ubuntuforums.org/showthread.php?t=756260](http://ubuntuforums.org/showthread.php?t=756260)
 Hope this helps and you wont stay a  Newbie for long.  Google search is a wealth of information.
 I have have found a lot of the early search criteria still works,  like my search line starts with "ubuntu 14.04"  in quotation marks = this as entered must be in search.  .and.  .not.  “buy now”  is handy for eliminating items from the search.  Search string max  256 characters long.  I highlight the urrl with the cursor and press (Ctrl+c) to copy.   I paste into a note pad file named for the search , add  notes.

---

### Post by Bucky Ball on 2015-02-27
> **dale1944-a said:**
> [http://ubuntuforums.org/showthread.php?t=756260](http://ubuntuforums.org/showthread.php?t=756260)
 

Welcome. This is a VERY old thread and it is about a different device. Please disregard. Ndiswrapper is very rarely used now (although this may be one of the exceptions). 

With the dongle plugged in, open a terminal and post the output of this command, please.

```
lsusb
```

Also, just out of curiousity, also post the output of this command, with the dongle plugged in:

```
sudo lshw -C network
```

Leave the dongle in, and if you can get online with a cable, do an update (Software Updater), then check 'Additional Drivers'. Is there anything there pertaining to a wireless driver?

PS: You may also like to try the method outlined in the answer [here]("http://askubuntu.com/questions/460277/how-to-get-netgear-a6200-to-work-on-14-04"). Good luck.

---

