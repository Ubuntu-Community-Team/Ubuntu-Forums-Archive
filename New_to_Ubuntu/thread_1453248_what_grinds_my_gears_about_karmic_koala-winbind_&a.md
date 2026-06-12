---
title: "what grinds my gears about karmic koala-winbind &amp; samba"
date: 2010-04-13
forum: New to Ubuntu
---

### Post by bradmayne04 on 2010-04-13
I can't hold back any longer!  Karmic has really got me going.  Here's what has brought me to utter despair.  Some involves Ubuntu and some is just from the toxic oasis that is my life.  I came home from prison on March 3 2010 to find out that my mom broke my last laptop.  As soon as you turn it on tou hear the worlds loudest beeping noise.  So, she feels bad and gets me another laptop (an e machine but beggars can't be choosers the broken lappy is a toshiba satellite) so we get it home and i install ubu 9.10 64 bit.  Everything is okay for the most part after install (had to get broadcom wi-fi driver off install disk) so I then began to giet a little more involved.  I began to configure Samba.  I could not get samba running until i downloaded and installed winbind.  With that everything began to fall into place as far as samba is concerned.  However, my internet browsing speed is now very slow.  I have read up about the name resolve order and all that.  Now, when I delete winbind and restart firefox it's back to "normal" browsing speed.  I know we've been over this now 
on other threads.  When I went to prison the distro that was out was "Feisty Fawn".  Now feisty worked well right out of the box.  (show's how long i was in prison huh?)  can anyone tell me a simple and i stress simple workaround?  I've been posting a lot on this since march 10th or so and would really love to hear an answer at this point.  Oh and to answer this ahead of time i'm trying to connect to a windows machine.  It's a vista.  If i use winbind (which I need to get samba working properly) it's only a matter of time before web browsing is at a stand still.  When i remove winbind and restart firefox all is well for browsing again!  I've heard something about fstab and automount but i'm unsure of what that is and how to do it.  (i've forgotten a lot)LOL please help!
.

---

### Post by jvc26 on 2010-04-30
I would try as a first step moving up to Lucid, which has just come out and is a Long-Term-Support (LTS) release. I had issues with Samba PDCs and Win 7 in Karmic which were resolved by the Lucid upgrade. I can't promise anything, but that may give you a reasonably quick answer!

J

---

