---
title: "Ubuntu 7.04 Cannot Connect to Internet"
date: 2007-04-26
forum: Networking &amp; Wireless
---

### Post by WhoDeyInDaNati on 2007-04-26
Hey Guys.  New to Linux.

I downloaded Ubuntu 7.04 and can run it off of the Live CD.  I want to Install but not until I can get the Internet to work.  I have searched all over the forums and google but have not found a solution.

I have a new computer that came preloaded with Vista.  I am pretty sure my Network Adapter is a Intel(R) PRO/100 VE Netork Connection (That's all I could find in the Device Manager that sounded right).  My Internet is a DSL that runs through the Power Lines.  It is directly wired into my computer.  Everything runs fine in Windows Vista.

When in Ubuntu, the network connection thing in the top right says it is searching for a network address.  I have tried setting it up as a static ip, but that was a no go.  Tried some other random things that I found posted in the forums but nothing seems to work.  I am a noob when it comes to Linux, so I don't really no what I am going.  But I have taken computer programming classes, so I understand what most of these commands are trying to do.

Any help would be greatly appreciated.

---

### Post by WhoDeyInDaNati on 2007-04-26
bump

---

### Post by Sensei_V on 2007-04-26
I'm pretty new, too, and I had a similar problem.  The network worked fine when I first installed Edgy (6.10) about a month ago, but when I upgraded to Feisty (7.04) this week my ethernet connection went down.  I tried all kinds of things, and what finally worked was to do a complete shutdown and then reboot.  Simple restarts did not work.

Granted, this doesn't help you much since it seems you are running off the Live CD.  For other reasons, I decided to do a clean reinstall from the Live CD, and my network connection worked then, while still booted from the CD.

I've used "sudo dhclient" at the terminal to search for a new IP address while troubleshooting my wireless connection (still no success with encryption, though), that you might have already tried.  You should check with your ISP as to whether they allow static IP addresses, I know mine doesn't.

If I were you, I would go ahead and install Feisty, perhaps dual-booting with Vista (for now) so that you can still access the web for help, unless you have another machine you can do that from.  From the Live CD, I don't think there is any way to make any changes you make to files or settings stick, especially on reboot.

Good luck, and let me know if you have any pointers on WPA!

---

### Post by WhoDeyInDaNati on 2007-04-26
I guess I will try installing to the Hard Drive.  I will post update when I am done.  Thanks for the reply.

---

### Post by Sensei_V on 2007-04-26
> **WhoDeyInDaNati said:**
> I guess I will try installing to the Hard Drive.  I will post update when I am done.  Thanks for the reply.

Good luck.  You won't look back!

---

### Post by geno the man on 2007-04-26
I am also new to Linux and of course ubuntu.  I did not try to connect the CD runtime OS to the Internet but I have had success connecting various older computers running the installed 7.04 to the Internet and even connecting using wireless adapters.

My view right or wrong is that if the computer boots from the CD then it should work after the install.  Now for five installs that theory has worked.  You might try switching Ethernet cards but I have not found any to be a problem.  With wireless connecting is a different story.  I have been able to connect using only two wireless adapters out of six, one from Netgear and the other an old Dlink 811-B.  

I hope you can configure the Internet -  I ordered a book from Amazon which is in route but I found by just messing with the OS and the interface, I was able to set up the card.   For wireless, I used a terminal command iwconfig and if it shows a connection then usually it will connect after some exploring.

I hope a more knowledgeable user with get back to you, as my experience is about two days old.  As a side, 7.04 works well with 800GHz and above and OK on my old HP 700Ghz.
  

Gene

---

### Post by WhoDeyInDaNati on 2007-04-26
All I can say is HELL YEA!

I am now able to access the internet from FireFox.  I did the Install and fired it up.  Internet did not work.  Shut it down and started back up.  Still no luck.

So I setup internet as static ip.  I could then bring up google using their ip address but not [www.google.com](www.google.com).

So I put in my IP's DNS server and bam everything works now.

I guess you were right about the Live CD not being able to save any of my changes.  Because when i did this same process on the Live CD it did not work.

THANKS ALOT!

---

### Post by Sensei_V on 2007-04-26
Congratulations!  Enjoy Ubuntu.

By the way, I got WPA to work, but only by a stroke of luck ... or it could have had something to do with the burnt offerings I made to the computer gods and my Windoze voodoo doll I've been stabbing all day ... For future reference, if you're having WPA problems, try something with the keyring.  I just tried to connect to my router and for the first time a window came up asking for a new keyring password.  After supplying one, I was connected.  We'll see whether it sticks ... if not, I guess it's back to burnt offerings.

---

