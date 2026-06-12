---
title: "Sound alert in Evolution."
date: 2009-02-07
forum: New to Ubuntu
---

### Post by groeswenphil on 2009-02-07
Hi,
Just a small query. How can you create a sound alert in Evolution E mail? Currently it just gives a nasty beep from the motherboard.

I've found this on the help file.

You must select the Enable sound server startup
option, and the Sounds for events option before you can
access the Sound Events tabbed section.

But how do you do that?

Phil

---

### Post by DJ_Peng on 2009-02-08
Make sure you have evolution-plugins installed and in Evo go to *Edit > Plugins*. On the left hand side of that window select the **Mail Notification** plugin and enable it, then on the Configuration tab check the box for *Play new sound when new messages arrive*. Select the *Play sound file* radio button and then locate the file you want to have played. I don't remember if you have to restart Evo for it to work but the next time you start the mail client you should get an audio alert when new messages arrive.

Thanks for reminding me that I needed to tell Evo where my new message alert sound was after I relocated the file a few weeks ago. No wonder my system was so darned quiet when I got new mail. :)

---

