---
title: "Hardware configuration for Ubuntu 9.10"
date: 2010-01-06
forum: New to Ubuntu
---

### Post by s.shinde on 2010-01-06
Hello,
      
         I am student and I heared about Ubuntu today. 
 My Computer configuration: 
Intel Pentium 4 processor
RAM 512MB
 
 
 Regards,
Shinde

---

### Post by Duck86 on 2010-01-06
Have you an onboard intel graphics card? If you do don't go with the 9.04/9.10 release. The OS doesnt support it. Try 8.10 instead. You'll find it will speed up your system no end. I wouldn't Dual Boot though with that much RAM.

Duck

---

### Post by Bright_View on 2010-01-06
Duck86 - why does the amount of ram determine whether you will dual boot?  Honest question.  My understanding is that if you have enough ram for both OSs independently, then you're fine.  Having another OS on the hard disk doesn't use any more ram than just having one, as there is only ever one OS running at a time.

---

### Post by theozzlives on 2010-01-06
> **Duck86 said:**
> Have you an onboard intel graphics card? If you do don't go with the 9.04/9.10 release. The OS doesnt support it. Try 8.10 instead. You'll find it will speed up your system no end. I wouldn't Dual Boot though with that much RAM.

Duck

Misinformation! I run Intel Graphics on my laptop with 9.04 and 9.10. Run compiz effects and my system is faster with the 9.xx versions and ext4.

---

### Post by cartisdm on 2010-01-06
I don't want to get everyone bashing Duck86, but that information is not true.  If you would like to consider Dual Booting, you will be just fine.

**s.shinde**, are you familiar with LiveCDs? All ubuntu distrobutions come on CDs that allow you to try out the OS on your computer without having to install it first.  Very cool indeed.  I recommend heading to [www.ubuntu.com](www.ubuntu.com) and downloading a copy of Karmic and trying it out for yourself (your hardware configuration looks just fine)

---

### Post by Bartender on 2010-01-06
> **theozzlives said:**
> Misinformation! I run Intel Graphics on my laptop with 9.04 and 9.10. Run compiz effects and my system is faster with the 9.xx versions and ext4.

It's not misinformation.  It's well known that Intel onboard support has been very flaky in the last two distros.  My Acer laptop with onboard Intel is also functional, and is capable of some compiz effects, so I guess it would be more accurate to say that some Intel chipsets aren't working very well and some seem to be working fine.  Since we don't know the OP's chipset, to err on the side of caution seems well-advised.

To the OP - if you have access to broadband, I imagine the best advice would be to download 9.10, 9.04 and/or 8.10 LiveCD's, then burn the images to CD.  Boot from the CD, go into "Try Ubuntu without making any changes" and see how well things work.  The OS will seem very slow while it's running off the CD so don't let that alarm you.  If you want, type 

lspci

into a terminal (Applications>Accessories>Terminal) and copy those results to a thumb drive or post directly to a post in this thread.  The results of the lspci command tells us what graphics you're running.

Here's an example of the lspci command, in this thread.

[http://ubuntuforums.org/showthread.php?t=1369680](http://ubuntuforums.org/showthread.php?t=1369680)

Take a look at posts #12, #13, and #25.

---

### Post by Duck86 on 2010-01-06
> **Bright_View said:**
> Duck86 - why does the amount of ram determine whether you will dual boot? Honest question. My understanding is that if you have enough ram for both OSs independently, then you're fine. Having another OS on the hard disk doesn't use any more ram than just having one, as there is only ever one OS running at a time.
 
:-( sorry, I was told that dual booting uses more RAM than just having one system installed.
 
> **theozzlives said:**
> Misinformation! I run Intel Graphics on my laptop with 9.04 and 9.10. Run compiz effects and my system is faster with the 9.xx versions and ext4.
 
I'm just going by my experience on that one. I installed 9.04 on my Dell Optiplex GX 270 with onboard intel graphics and it wont play any video files. Ive tried about 6 different players, trawled the Internet and tried loads of fixes through the terminal. None of them worked. Then I found this thread here:
 
[[COLOR=#444444]http://ubuntuforums.org/showthread.p...t=avi+problems[/COLOR]]("http://ubuntuforums.org/showthread.p...t=avi+problems")
 
with this post in it:
 
[COLOR=#444444]> **billgoldberg said:**
> Onboard Intel graphics cards aren't properly supported on Ubuntu 9.04. [/COLOR][COLOR=#444444]It's in the release notes of the OS, you should read those before installing.[/COLOR]
 
 
 
[COLOR=#444444]Again, sorry for any misinformation caused.[/COLOR]

---

### Post by Bright_View on 2010-01-06
I don't think an apology is necessary.  I almost never post because I'm too worried I'll give misinformation, and I'm thinking that that may actually be worse than posting misinformation some of the time.  

It's a forum, so there will be plenty of people to challenge you when you say something incorrect, and you will learn much quicker if you share what you know more freely than if you stay silent.  I think intentions count a lot on this board, so you should be commended for trying to help.  Perhaps you should explicitly identify the source of your information when applicable (e.g. personal experience vs professional knowledge) so that others can weigh what you have to say more accurately.

What does everyone else feel?  Am I wrong?

---

