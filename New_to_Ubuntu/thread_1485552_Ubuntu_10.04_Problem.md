---
title: "Ubuntu 10.04 Problem"
date: 2010-05-17
forum: New to Ubuntu
---

### Post by ryandavis33 on 2010-05-17
When i did a fresh install of Ubuntu 10.04 i got stuck in an infinte loop of logins with (due to my graphics card) i was unable to see anything else but the login screen to fix any problems. My question is...if i just install Ubuntu 10.04 via the Update Manager will that solve my problem?? If not what can i do?  Please tell me if i need to provide more info


Thanks:popcorn:

---

### Post by 4Orbs on 2010-05-17
Just to clarify things: Did the infinite login loop occur after you had installed Ubuntu and then activated the recommended driver?

---

### Post by ryandavis33 on 2010-05-17
I dont remember installing any driver...i just installed Ubuntu and after it rebooted and told me to take out the disc...thats when i was stuck at the login

---

### Post by 4Orbs on 2010-05-17
Did you check the download md5sum before you burned the installation disk? If not you might want to check the disk for errors by putting the disk in the drive and reboot. Then, as soon as you see the two little pictures at the bottom of the screen, hit the space bar to open the bootup options menu. If the gray language choice screen pops up and blocks your view of the menu, hit the esc button. Then use the arrow keys to select "Check Disc for Errors", hit enter and wait for the error check to complete.

---

### Post by blakdogg on 2010-05-17
> **ryandavis33 said:**
> When i did a fresh install of Ubuntu 10.04 i got stuck in an infinte loop of logins with (due to my graphics card) i was unable to see anything else but the login screen to fix any problems. My question is...if i just install Ubuntu 10.04 via the Update Manager will that solve my problem?? If not what can i do?  Please tell me if i need to provide more info


Thanks:popcorn:
I am not sure what you mean by "see". I had a problem where I couldn't login it always returned me to the login screen. It wasn't a password issue, as the wrong password gave me an error. It seems like ubuntu tried to start X, then X logged me back out returning me to the login.

I tried a few options, but in the end I reinstalled and ignored the nvidia drivers. 

I have now run into an issue where X cannot be shutdown, but at least it last two weeks this time.

---

### Post by ryandavis33 on 2010-05-18
What i meant be "see" is that my grpahics card will not display anything but the login screen...if i press another button to go somewhere else like some command line it will show fuzzy stuff

---

