---
title: "only half my music will play"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by card_ace on 2009-02-25
i have about 20 gigs of mp3 and wma music(more mp3, maybe 3% is wma), and 12.7 gigs of it will show up in rythmbox.  i downloaded ubuntu restricted extras and several gstreamer codecs to get this far, and on the "import errors" section of my music player, it says i can't play ASF files or find the MIME documentations or something along those lines.  i can't remember exactly.  i don't have an internet connection, so can someone give me the name of whatever i need so i can find it in keryx?

---

### Post by llamabr on 2009-02-25
asf is a ms proprietary format.

What are you using to play them?  A quick search turns up this:

avifile-player - video player for AVI/ASF/WMF files

Maybe give it a try?

---

### Post by card_ace on 2009-02-25
thanks, i downloaded it and i'll install it later today when i get home and let you know

---

### Post by stim on 2009-02-25
Not in relation to your question, but to your signature:
Don't feel bad about having dial up. The Computer and Information Sciences DEPARTMENT CHAIR at my University, has dial-up.  Always wondered why it took so darn long for him to get back to my e-mail questions on the weekends/nights......

---

### Post by card_ace on 2009-02-25
i'm just a country boy out here in the middle of nowhere, and the internet companies excuses for not being able to get us high speed is that the woods around me are blocking the signal.  glad to know i'm not alone

---

### Post by card_ace on 2009-02-26
alright checked again last night.  i installed that update and it still didn't work.  The import error that i'm getting is that i'm missing the GStreamer plugin to decode ASF files.  should i just download all the GStreamer stuff i can find?

---

### Post by Therion on 2009-02-26
Having the all Gstreamer codecs won't hurt but I think there's a **gstreamer-asf** package...  Or at least there used to be.  

If not, download the **gstreamer-plugins-ugly** package.  That should get you the codec you need.

---

### Post by card_ace on 2009-02-28
thanks that worked.  i used the gtstreamer plugins ugly and everything worked fine.  thanks for the help

---

