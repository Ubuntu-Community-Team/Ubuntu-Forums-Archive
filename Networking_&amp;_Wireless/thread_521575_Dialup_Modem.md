---
title: "Dialup Modem"
date: 2007-08-09
forum: Networking &amp; Wireless
---

### Post by corncob on 2007-08-09
I have DSL at home so Ubuntu is always on line -- no problems.  Its my friend who has dial up that can't connect.  She has a U.S. Robotics Performance Pro Modem that is supposed to be Linux compatible.   I've read previous posts and it seems to be configured properly but where is the CONNECT button?  I can't figure out how to get it to dial.  Ray

---

### Post by kevinlyfellow on 2007-08-09
It's under the normal System -> Adminstration -> Network and there is an option for a modem connection.  Have her install gnome-ppp, it's much better.

---

### Post by Bartender on 2007-08-10
If you installed Edgy or Feisty the best thing you can do is ignore the "Network" utility.  It doesn't work for dial-up.  Take a look at 
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)
for the generic dial-up help.
This might help you get going
[http://ubuntuforums.org/showthread.php?t=480717](http://ubuntuforums.org/showthread.php?t=480717)
Since that thread is a work-in-progress, read it all the way thru before you start trying anything.

If the PCI hardware modem is functional it should be detected when you type in the first wvdial command described in post #3.

Also, get gnome-ppp installed (directions for using another PC are in the thread) and ask it to auto-detect the modem.  It'll take a few minutes of poking around in gnome-ppp to find that function.  If I remember, it's under "Modem">New or Edit or something like that.

If it works please post back.  The full-hardware USR PCI modem oughta work but have read several posts from folks who said it didn't.  Very curious to hear your results.

EDIT:  If you get the modem to cooperate, and get the dialer software configured properly, you still will have problems if she's on AOL, Juno, PeoplePC, etc.  Any ISP that uses proprietary software to connect.

---

### Post by corncob on 2007-08-11
Thanks for all the good info.  I downloaded GNOME ppp and installed it.  I had to change the device to /dev/ttyS2 but it did dial up and go on line.  Funny thing though -- when I switched user to my friend's account in order to configure it there, it could no longer open the modem, as ttyS2 or any of the other choices.  I had thought something might be wrong with her account as you see 3 "Ubuntus" when she logs on (while I only see one) but that was no big deal.  Going back to my own screen, the modem again worked.  I was thinking of deleting her account and then reinstating it but I'll work on that another day.    Ray

---

### Post by kevinlyfellow on 2007-08-11
> **corncob said:**
> Thanks for all the good info.  I downloaded GNOME ppp and installed it.  I had to change the device to /dev/ttyS2 but it did dial up and go on line.  Funny thing though -- when I switched user to my friend's account in order to configure it there, it could no longer open the modem, as ttyS2 or any of the other choices.  I had thought something might be wrong with her account as you see 3 "Ubuntus" when she logs on (while I only see one) but that was no big deal.  Going back to my own screen, the modem again worked.  I was thinking of deleting her account and then reinstating it but I'll work on that another day.    Ray

This may be easier to fix than you think ;-)  Go to System -> Administration -> Users and Groups and go to the user properties and check off "Connect to Internet Using a Modem" under the user privileges tab.

---

### Post by nowshining on 2007-08-11
a note on the gnome-ppp highly agree it is easier and also going into setup and selecting detect detected my usb dialup-modem.. :) and also is agreeable easier to use and such..lolz...

---

### Post by corncob on 2007-08-13
Its all working now.  The modem had been enabled in her user profile but rebooting the computer  fixed the problem and she's dialing up fine now.  She still sees 3 "Ubuntu"s when she logs on but as long as that's not part of a larger problem, I won't worry about it.       Ray

---

### Post by kevinlyfellow on 2007-08-13
> **corncob said:**
> Its all working now.  The modem had been enabled in her user profile but rebooting the computer  fixed the problem and she's dialing up fine now.  She still sees 3 "Ubuntu"s when she logs on but as long as that's not part of a larger problem, I won't worry about it.       Ray

I'm not sure what you mean by the "3 Ubuntus" .  Do you mean three splash screens when logging in?

---

