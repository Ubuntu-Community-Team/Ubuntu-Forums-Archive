---
title: "ATI binary X.Org driver QUESTION"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by pjmed on 2009-05-11
Hello.

I am currently running Ubuntu 8.10. It is my first time running Linux/Ubuntu. I installed Ubuntu 9.4 first but it did not run smooth. It was jumpy and made my laptop hot. After trying to find some fixes someone suggested I install 8.10. I did and it runs 10 times smoother and faster than 9.4. I now have a question. When I look in HARDWARE DRIVERS there are no drivers present. If I look under ADD/REMOVE APPLICATIONS I find the ATI binary X.Org driver which apparently mentions my graphics card (its a Mobility Radeon 9200) My question is, will my video performance improove if I install this? I ask because when I was attempting to fix the poor video performance I installed something similar (I don't remember what) and when I restarted the computer I would not get the desktop. Instead I would get a mess of lines and dots, which would suggest it was the wrong driver. In order to fix it I had to reinstall Ubuntu since I don't have any knowledge of how to fix things in ubuntu. So again, will  ATI binary X.Org driver improove my performance? If it doesn't, or if it has adverse effects, how do I remove it?

Thanks in advance.

By the way, did I do the correct thing by installing 8.10 or where the poor performance and video problems I had in 9.04 fixable? Thanks again and I apologize for the many questions.

---

### Post by ktmom on 2009-05-11
I am also a bit new, but....

ATI does not work smoothly under Jaunty (9.04).  It's due to the updates to the Xorg server and the lack of Linux support from ATI.  Both of my systems have ATI cards, one the Radeon 9200 and the other an X300 series.  

On my 8.10 system is the X300 and I installed the ATI Catalyst Control Center through the Add/Remove Applications menu.  Everything has worked without problem (although I don't push the graphics very hard).  All of the compiz eye-candy is working.

The Radeon 9200 is on my 64 bit system which I am trying to get up and running with Mythbuntu.  That has been a difficult process.  Partly because I am new and largely because the ATI drivers don't play well with Linux and I started with the Jaunty release of Mythbuntu.  I am now retrying with the 8.04 release of Mythbuntu, but I haven't gotten very far ;)

All of the above sums to, I think you should be fine under 8.10 with your Radeon card, but will be unable to move to Jaunty until ATI provides support for the newer version of Xorg server.  There may be other solutions, but I have yet to get the TV out working with this card.

NVidia video chips are better supported but as you are on a laptop, changing out the graphics card isn't likely to be an option.

[http://ubuntuforums.org/showthread.php?t=1133931&highlight=Radeon+9200+SE]("http://ubuntuforums.org/showthread.php?t=1133931&highlight=Radeon+9200+SE")

---

