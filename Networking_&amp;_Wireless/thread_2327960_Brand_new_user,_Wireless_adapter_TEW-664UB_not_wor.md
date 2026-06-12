---
title: "Brand new user, Wireless adapter TEW-664UB not working"
date: 2016-06-16
forum: Networking &amp; Wireless
---

### Post by Zamexil on 2016-06-16
Today using left over computer parts from older build, I put together a secondary computer and decided to install Linux on it. Everything worked great until I plugged in my Trendnet USB TEW-664UB wireless adapter. I did not work at all. I spent hours searching for a solution to no luck. If anyone knew how to do make this work it would be great. I plan on having this computer where in a place without an ethernet connection, so wireless is fairly important. I looked at this thread: [http://ubuntuforums.org/showthread.php?t=2255349](http://ubuntuforums.org/showthread.php?t=2255349) which I feel like could help, I just dont know how to do everything said in it. Thanks for the help!

---

### Post by howefield on 2016-06-16
Thread moved to the "*Networking & Wireless*" forum.

---

### Post by X-RED_Tech on 2016-06-16
Brand new and version 2 as well? The solution won't work for V1 (Ralink chipset) and no fix should be needed for V1.

[https://wikidevi.com/wiki/TRENDnet_TEW-664UB_v2](https://wikidevi.com/wiki/TRENDnet_TEW-664UB_v2)

---

### Post by briandennis16 on 2016-06-16
I sort of had the same issue with wireless connectivity issue but with an internal chipset not a usb adapter, I am wondering though have you checked your BIOS setup to make sure you have some of the appropriate settings in place, because that was my issue and now it is working just fine! I have a post similar in the networking & wireless forum as of now I'm the only one who has replied to it.

---

### Post by Zamexil on 2016-06-16
What exactly did you check in your bios settings? I looked in mine and didn't find anything related to this.

---

### Post by Zamexil on 2016-06-16
Ok good news. When I was first searching for a solution, I found this solution on a different forum ([http://askubuntu.com/questions/434073/trendnet-tew-664ub-not-recognized-in-ubuntu](http://askubuntu.com/questions/434073/trendnet-tew-664ub-not-recognized-in-ubuntu)) and tried it but it didn't work. Then this morning after looking some more and various computer restarts, I tried the solution in that post again and it worked. However, it didn't work at first and I had to put in the commands a few times but eventually, after one final restart, I got it to work. I hope this helps someone.

---

### Post by briandennis16 on 2016-06-16
Thats awesome, if by chance you still need/want to know what I checked and needed to change in my situation in the BIOS. Here is a unordered list of what I changed or double checked.

1) primary boot sequence
 2) I made sure CMS was disabled
3) and I disabled UEFI first to enable Legacy first 
4) I also had to change the LAN Boot Agent to enabled for my wifi signal
5) and I just went ahead and disabled my IPv6

This is what worked for me, but your situation is a bit different. Hope it just stays working for you but if not, hope this can help if need be.

Cheers!

---

