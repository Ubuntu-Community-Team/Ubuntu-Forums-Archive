---
title: "Wireless Stopped working"
date: 2008-07-22
forum: Networking &amp; Wireless
---

### Post by searayman on 2008-07-22
After a long long time I finally got wireless workign on my dell.I got it workign because of this converstaion:

[http://www.mediafire.com/?kjdttzeqdnm](http://www.mediafire.com/?kjdttzeqdnm)

it worked flawlessly for a week or so and last night I wa son it, then I woke up in the morning and booted into linux and bam its not working anymore....

I don't have the icon on ubuntu hardy that jus comes up in the top  right that allows me to pick a network, and I am nto online...

any help would be great!

Thanks

---

### Post by superprash2003 on 2008-07-22
follow this [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by searayman on 2008-07-22
> **superprash2003 said:**
> follow this [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

i used the wrapper and had everythign workign etc. it just suddenly stopped.

I noticed the internet thingy from the top right on the gnome panel is gone, where i could choose what wireless network I wanted to go on etc.


How can I get that back? I also lost the battery thing that was up there too, and when i unplugg the message that apears under the battery applet now apperas at the far left instead of where it was at the top right?

Even when I am plugged into the internet the internet applet still inst there... any idea?

---

### Post by BlackholeZ on 2008-07-22
I think I'm in the same boat, but my situation is a little different. My wireless has been working since I upgraded to Gutsy a few months ago. I've upgraded to Hardy since, and kept current on all updates. Everything has been working fine for months until last night. The network icon shows up, just with no available networks. To me it looks like a virus, but through searching it sounds like that is not the case. I am going to start through the fix posted above, but I wanted to post incase there is something else wrong.

This is all on my HP dv8000 using the Broadcom B43 and ATI flgrx drivers through restricted drivers.

---

### Post by searayman on 2008-07-22
i solved my problem it was because my notification area was some how taken off. Once I put that on I was all good again!

---

### Post by Friccy on 2008-07-22
Hi! I had the same problem.
It looks like Broadcom is not supporting Linux, so you have to use the Windows drivers.
Follow this thread and hope will work for you as it didd for me. It saved Ubuntu on my new laptop. I was so nervous, that I wanted to uninstall it.
[http://ubuntuforums.org/showthread.php?t=813363](http://ubuntuforums.org/showthread.php?t=813363)
Good luck!

---

### Post by searayman on 2008-07-22
> **Friccy said:**
> Hi! I had the same problem.
It looks like Broadcom is not supporting Linux, so you have to use the Windows drivers.
Follow this thread and hope will work for you as it didd for me. It saved Ubuntu on my new laptop. I was so nervous, that I wanted to uninstall it.
[http://ubuntuforums.org/showthread.php?t=813363](http://ubuntuforums.org/showthread.php?t=813363)
Good luck!

if you want the step by step way you can follow a discussion I had in the irc channel, I saved it for you all. 

[http://www.scribd.com/doc/3972618/Wireless-Diver-dell-Ubuntu-How-to](http://www.scribd.com/doc/3972618/Wireless-Diver-dell-Ubuntu-How-to)

I recommend reading through it first before following it, cause the first thing we tried didn't work, but the second did.

---

### Post by BlackholeZ on 2008-07-22
So, I can't download any of the modules needed because my laptop can't get online. Is there any way to download the needed software and transfer it to my laptop? 
Sorry, I'm learning as I go. 

-Dan

---

### Post by searayman on 2008-07-22
> **BlackholeZ said:**
> So, I can't download any of the modules needed because my laptop can't get online. Is there any way to download the needed software and transfer it to my laptop? 
Sorry, I'm learning as I go. 

-Dan

download it, then burn it or just use a flash drive to move it to your laptop

or plug into an internet connection

---

### Post by BlackholeZ on 2008-07-23
> **searayman said:**
> download it, then burn it or just use a flash drive to move it to your laptop

or plug into an internet connection

I just realized that the wired connection still works. I just installed a fresh copy of 8.04.1. I have the wireless icon, just can't find any networks. I'll plug my laptop in @ work tomorrow and try the ndiswrapper thing. Thanks for your help. 

-Dan

---

