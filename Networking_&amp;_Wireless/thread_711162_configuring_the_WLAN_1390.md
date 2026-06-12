---
title: "configuring the WLAN 1390"
date: 2008-02-29
forum: Networking &amp; Wireless
---

### Post by serialfish on 2008-02-29
I ran across this lovely post on how-to install the WLAN 1390 Wireless Mini-Card that came standard on my Dell Inspiron 1501 laptop:

[[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)]("http://ubuntuforums.org/showthread.php?t=297092")

I followed the steps exactly as described and felt like I was getting somewhere, until I got to the part 

```
wget http://ftp.us.dell.com/network/R151517.EXE
```

This command results in something along the lines of not being able to find that particular website. If it has changed, how do I find the new one.

Also, the sourceforge code on the same thread also seems not to work:

```
wget http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.51.tar.gz
```

I see there is a code below it to use if the sourceforge one doesn't work, but since I printed out the instructions, I didn't get that code. I'll try it once I get past the dell part.

Any suggestions?

---

### Post by JoeLinux117 on 2008-02-29
The link for that file is [here]("http://support.dell.com/support/topics/global.aspx/support/downloads/en/downloads_splash?c=us&l=en&s=gen&%7Emode=popup&file=202136").  Hope that helps.

Also, it looks like they want you to compile ndiswrapper yourself if they're giving you the sourceforge website to download from.  Maybe you should give it a shot first using the ndiswrapper that can be found in the repositories (**sudo aptitude install ndiswrapper**).

If you're having more trouble, you can try another tutorial:

[http://www.learnaboutlinux.net/wireless_1390.htm]("http://www.learnaboutlinux.net/wireless_1390.htm")

I hope I was some help.



--JoeLinux
[Learn About Linux - A World Without Windows]("http://www.learnaboutlinux.net")

---

### Post by serialfish on 2008-02-29
Thanks. One question, though. I foudn the link your provided last night, but wasn't sure what to do with it. I tried

```
wget http://support.dell.com/support/topics/global.aspx/support/downloads/en/downloads_splash?c=us&l=en&s=gen&%7Emode=popup&file=202136
```

That gave me the same problem, like it couldn't find the file. I thought maybe this was because of the 'popup' part or something. Should I have converted to some ftp version or typed a different command.

I'm still very new to all of these linux commands and they are not natural for me.

Thanks again.

---

### Post by JoeLinux117 on 2008-02-29
Yea, I think that link was just meant for you to click on it.  I think that's the problem you're having with the "popup" part, like you said.

I'm not too sure about the tutorial you were looking at, but if you follow the tutorial I linked to, you should be fine.  If not, you can always contact me directly through that site and I'll help you myself.  I know that tutorial has worked on most laptops that came equipped with the Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI card.  I've seen a few problems with different revisions and such, but that's been the minority from what I've seen.

Let me know if I can help.


--JoeLinux
[Learn About Linux - A World Without Windows]("http://www.learnaboutlinux.net")

---

