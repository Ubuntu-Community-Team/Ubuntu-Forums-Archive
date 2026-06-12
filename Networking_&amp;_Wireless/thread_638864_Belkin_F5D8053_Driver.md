---
title: "Belkin F5D8053 Driver"
date: 2007-12-12
forum: Networking &amp; Wireless
---

### Post by Raghallac on 2007-12-12
I tried Google-ing, like mad to find a answer to the Wireless Problem. Looked at the Ndiswrapper and am well aware that Belkin doesn't make any Drivers for Linux.

I am running a Belkin F5D8053 USB 'N' MIMO USB Wireless. Connecting to a Residential 2Wire Router. 
All the Linux information I found for Belkin was Listed as "pre-N'.

The whole wireless networking is a new thing to me, as in college it was hard Lan and before that it was multiple Ethernet from one Router. 

If there is any way to bypass this awful mess. I'd love to hear it. Tired of WinXP and Vista looks horrendous.

Also, if there isn't a way to bypass this. Is there any new Wireless Adapters, that support Ubuntu Linux?
I heard good things from, 2006 (Graveyard Posts from Google) about Linksys WRT54G the 60 Dollar Router that can be made a 600$$ Machine, or something along those lines, but  it only mentioned SuSE and, to be honest, I couldn't grasp all the details.

Any Help would be Appreciated.

---

### Post by S4T4N4S on 2007-12-12
Hello,

I've the same problem and have solved with the instructions in this site:
[http://welcometoubuntu.blogspot.com/2007/10/howto-get-airgo-based-wifi-enabled.html](http://welcometoubuntu.blogspot.com/2007/10/howto-get-airgo-based-wifi-enabled.html)

... but with the Belkin original drivers found in the CD.

I've uploaded the files here:
[http://77.91.202.10/~alpoimco/Satanas/belkin_pre-n.tar.gz](http://77.91.202.10/~alpoimco/Satanas/belkin_pre-n.tar.gz)

If you follow the instructions change this instruction:
sudo ndiswrapper -i tmimo3P.inf

to ...

sudo ndiswrapper -i NetAni.inf

Hope you solve your problem too...

Sat

---

### Post by kwalters on 2008-02-23
When I saw this post, i thought all my problems with my Belkin 8053 would be over.  I had previously had to revert to the previous USB dongle (rt2500usb) whenever I used Linux.

I worked through this very clear set of instructions, but got nowhere in the end.

Along the way, I found a couple of problems with the instructions as presented:

1.   Downloading the Belkin compressed files from the site mentioned in this post, they came as a tar.tar variant, not a tar.gz.  Changing the end of one of the instructions accordingly made progress possible.

2  As a relative newby, I found the instructions for adding bcm43xx to the blacklist a bit confusing.  I eventually worked out that the long instruction was just that, not two shorter lines.

However, at the end, not only would  nothing work, the network admin screen did not even show a wireless option.

I suspected that the problem lay in not having removed the RT2500 drivers, so I removed ndiswrapper altogether (I think) by adapting the instructions for the online procedure  (I was trying to follow the offline one as there is no hard connection in the room with this PC)

Incidentally, the NetAni.inf file was the only one available to install, so that is not the problem.

Is there, by any chance, a gap in the instructions where I ought to add the module to /etc/modules to have it load automatically?  Should there be a line like:

echo 'ndiswrapper' | sudo tee -a /etc/modules

around the stage where we add to the blacklist?


Have tried to go back to the 2500 driver but, of course, I took the whole shooting match out.  Unless anyone can see where I am going wrong, I shall have to work the same tedious process to get that one working again.  

At the first stage, the lspci line, the Belking device was found, but not in anything like the format shown in the instructions.  Is ther a clue there?

KW

---

### Post by kwalters on 2008-03-01
This problem has now been solved, although it had me tearing my hair out for several days

Furthermore it was a lot simpler than suggested by the usual suspects on this site who view any use of a Graphical User Interface as some kind of heresy (and probably a reflection on their virility.)

Having ploughed several times through the instructions earlier in this thread, I still ended up with no wireless network to configure; the driver (NetAni.sys) was installed, but the device was not recognised by Ubuntu, so no joy

Then I noticed that the long article that had solved some people';s problems but not mine (or several others) referred to a different Belkin adapter  NOT the 8053.

I also noticed (have you?) that Ubuntu 7.10 has a GUI control for ndiswrapper,  Go system....>administration......windows wireless drivers,  I used it to uninstall the NetAni driver with one keystroke.

Then I went to the Belkin install disk for the usb adapter,  I found it uses a driver  called RT2870.  I extracted 3 files from that disk:   RT2870,sys,   RT2870.inf and RT2870.cat and  copied them via a flash drive to my ubuntu home folder  (I made a subfolder called kwbelkin_pre-n to avoid confusion with the one in the long instruction and put all 3 files in it.)

I then asked the Windows Wireless Driver window to install a new driver.  It asked where the .inf file was and I told it.  Clicked on install, rebooted the system, and the wireless network was up and running with no further intervention from me (that is probably because the security WEP had already been set for the previous RT2500usb driver.)

I felt quite good after that.  Those of you who are totally sold on terminals and RSI, please carry on your way; but not me

KW

---

### Post by justinmiller87 on 2008-03-02
kwalters,

I'm very glad to hear that you were able to get your card working. On the instructions in my blog, I never listed the 8053 as one of the cards that would work following my instructions. As for what driver to use, and whether or not one wishes to use the GUI versus Terminal, well, to each their own. I personally find it is easier to use the Terminal, and many people do. But, if the GUI works for you, then I am glad to hear that your drivers are working and you are able to access the Internet. If you wanted to follow my instructions in the future, all you would have to do is replace Step 2-5 in the online version or Step 2-10 in the offline version with the line containing the driver you are using instead. If you ever want to try it again, the instructions will be there.

Justin Miller

---

### Post by kwalters on 2008-03-02
Thanks

I know you did not mention it; but your blog was pointed out by someone else under the heading of an 8053 driver problem and how to solve it.

KW

---

