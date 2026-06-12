---
title: "proliant ml370 g2 server question"
date: 2010-07-29
forum: New to Ubuntu
---

### Post by Kirkland14 on 2010-07-29
So I got a server for free.  when I try and plug it into a monitor I get no signal.  I know this server has an integrated VGA input.  I assume it doesn't work.  I thought about putting in a card and actually scored a couple older towers with cards but they don't seem to fit.  Is there a card a can get for it.  Or any other option?  I'm a noob just starting IT classes in 3 weeks so I don't know that much and everything I do is basically the first time.  I downloaded the manual but it's 152 pages.  that seems like a lot of reading so I was hoping someone could guide me in the right direction.  Thanks

Kevin

---

### Post by tgalati4 on 2010-07-29
Sometimes the internal video is turned off to save power.  Check the BIOS to see if you can turn the video on.

For an add-in card, you probably need a 1/2 height video card and they can be hard to come by.

---

### Post by Kirkland14 on 2010-07-29
but how do I check the BIOS if there's no picture?

---

### Post by anewguy on 2010-07-30
(1) Read the table of contents for the manual and see if it has a section on video, so you only need to read a limited amount of data.

(2) Check the manufacturers web site support pages.  It might tell you what type of slot sockets are on the motherboard so you can know what type of card to use.  But be forewarned - if you need to get to the BIOS to tell it not to use the onboard video (so it will use the new card) you could be chasing your tail - needing the video so you can use another video.

EDIT: just looking at HP's quick page for this product, it appears what you have available are 6 64-bit PCI slots, which do look full-height.  So, find an older PCI video card (the motherboard may not work with one of the newest ones).  Now you have to experiment a little:

- does video automatically switch to that card?
- there are 2 auto-detect and 4 non-auto-detect PCI slots, so you may have to move the board around in the slots until you find 1 of the auto-detect ones.  I would strongly suggest looking at the board and looking to see if the PCI slots are numbered, and if so, start at the lowest numbered 1.
- also, I think the first thing I would try to is to try booting an Ubuntu LiveCD and see if it boots and if you can see video.  Most monitors have a LED that is a different color - usually yellow - when no signal is detected on the cable, and another color - usually green - to indicate there is a signal being detected on the cable to the monitor.

Dave ;)

---

### Post by Kirkland14 on 2010-07-30
thanks Dave.  I will give all this a try and get back.  Thanks again

Kevin

---

### Post by Kirkland14 on 2010-07-30
So upon further investigation and looking on the HP server problem solving page I believe that the power supply is dead.  thanks for the help anyway.

Kevin

---

