---
title: "Xterasys xn-3135g"
date: 2007-11-17
forum: Networking &amp; Wireless
---

### Post by K3l3v on 2007-11-17
I've got a fresh, clean install of Ubuntu 7.10 running on a Compaq Presario 2100.  I'm trying to get it to recognize and use an Xterasys XN-3135G 802.11b/g card.

Right now, I have downloaded the manufacturer's RT73 driver from [here]("http://www.xterasys.com/support/drivers.htm").  Then I installed the build-essential package as noted [here]("http://www.linuxquestions.org/questions/ubuntu-63/anyone-know-how-to-install-make-on-ubuntukubuntu-460161/").  Finally, I opened the README file and proceded to follow the instructions (novel, I know).

The problem occurs when I run the command "sudo make config".  The error message is "No rule to make target 'config'".  I'm not a n00b, but I'm also no hacker...  I looked in the Configure file to see if I could spot the problem - no dice.

I have heard about and tried ndiswrapper already - with no luck.  I've tried three or four other ways of getting this thing to work (prior to the current install) on a clean install of Ubuntu 6.06.  I'd prefer at this point to get the friggin driver to install - since I'm not a fan of ndiswrapper, and the company was nice enough to code a Linux driver.  I've looked on this forum and elsewhere, tried everything that was suggested, and am still at ground zero.

I feel like there's a quick and simple solution to this problem, but I don't know what it is.

Thank you in advance for your help.

---

### Post by K3l3v on 2007-11-17
Update:

I got desperate...  I went back to ndiswrapper - got it to install correctly.  But, I needed an rt73.inf and rt73.sys file to load...  Manufacturer doesn't supply either, and the linux driver wouldn't compile for me.

So, I downloaded a generic rt73 driver from [here]("http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads"), and compiled using the build instructions in the bundled README.

Next, I was able to configure using the instructions contained in the README.

Unfortunately, I still do not have access.  I believe that it's a router issue at this point (ubuntu recognized hardware, has loaded correct driver, and recognizes router).  Router is a friend's (who is not instate at present), and he is only routing to MAC addresses programmed into the router (using software on his computer which is with him, out of state).

Hope that helps someone in the same boat.

---

