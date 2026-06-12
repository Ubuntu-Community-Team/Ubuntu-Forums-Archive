---
title: "help with Gnome 3 in ubuntu 10.10"
date: 2011-05-02
forum: New to Ubuntu
---

### Post by migrate from windows on 2011-05-02
Hi
I wanted to get a feel of gnome 3 in ubuntu 10.10, I installled gnome -3 session from the synaptic manager. Im not able to login with gnome 3... the desktop background appears ...a few flickers and then ...some random text in console...then back to login screen......anybody can help???

---

### Post by Dimarchi on 2011-05-02
As far as I know, there is no way to install Gnome 3 under 10.10 using the official Ubuntu repositories. Even under 11.04 it is iffy at best...it will not work without breaking stuff, not to mention it is not there in the official repositories. It will work in 11.10 and it will be available for installation from the official repositories. This is how it is according to my knowledge of the current situation regarding Gnome 3.

---

### Post by migrate from windows on 2011-05-02
It is available in the official maverick/universe repo!!!!!

---

### Post by Dimarchi on 2011-05-04
Ah, yes...parts of Gnome 3 are there, but not the full desktop. By official I refer to the small Ubuntu logo next to the package.

I seem to remember trying it, once.

Are you able to log in with something other than Gnome 3?

---

### Post by migrate from windows on 2011-05-04
yes... able to login with ubuntu desktop.

---

### Post by ivanovnegro on 2011-05-04
As far as I know Gnome 3 is only available from a PPA, for both, Ubuntu 10.10 and 11.04.

---

### Post by Dimarchi on 2011-05-06
Gnome 3 PPA is known to break 11.04 with no downgrade option available according to the PPA page...not sure about 10.10 - it may have a better success rate since it is closer to Gnome than 11.04 is. Or break 10.10, too. I have no idea.

Still, I would wager that a virtual machine running a distro with a working Gnome 3 is the best option, but that does not help with migrate from windows's problem. There is clearly a conflict of some kind that prevents migrate from even trying what little of Gnome 3 there is in 10.10 universe repos. That may be specific to the computer setup or something else, but the description of what happens does not provide enough information. Is that console text truly random, or error messages?

---

### Post by migrate from windows on 2011-05-12
The console text happens just a split second to make sense of it. But I could read the last line like checking battery state....something. The same thing happens when i try to enable compiz...may be 'mutter WM' is just another compiz for my hardware.

---

### Post by Dimarchi on 2011-05-13
Ok...that is normal stuff that is present there but usually hidden by GUI when starting up. Hmmm...the reason for why gnome3-session does not work can probably be found in the logs - but which log or logs I have no clue. For now, this is the best advice I can give: search the logs for gnome3-session related stuff. See where it fails...gnome3 and/or mutter are good canditates to look for, I suppose.

---

