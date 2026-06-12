---
title: "Sounds at login... weird ones"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by nash black on 2010-04-30
Hi

I upgraded to Ubuntu 9 a few weeks ago. I noticed some weird sounds at the login screen, but decided to wait to upgrade to 10.04 and see if that would take care of it... It didn't

After upgrading to 10.04, i still get the bongo drum style music while logging in (wasn't that supposed to go away?) and a weird sound (might be a glitch or a messed up sound file) when the login icons load and when I click on one(or maybe right after I enter the password... I can't remember)

I disabled the bongo music in the sound menu, but I cannot figure out where the other sound is coming from or how to change/ delete it... It would also be nice to get a login sound to replace the bongos.

How can I do these things?

Thanks,
Nash

---

### Post by swoll1980 on 2010-04-30
> **nash black said:**
> Hi

I upgraded to Ubuntu 9 a few weeks ago. I noticed some weird sounds at the login screen, but decided to wait to upgrade to 10.04 and see if that would take care of it... It didn't

After upgrading to 10.04, i still get the bongo drum style music while logging in (wasn't that supposed to go away?) and a weird sound (might be a glitch or a messed up sound file) when the login icons load and when I click on one(or maybe right after I enter the password... I can't remember)

I disabled the bongo music in the sound menu, but I cannot figure out where the other sound is coming from or how to change/ delete it... It would also be nice to get a login sound to replace the bongos.

How can I do these things?

Thanks,
Nash

You have to edit the config file for GDM it's in etc somewhere. /etc/gdm/Presession/Default I think.

---

### Post by nash black on 2010-05-01
Here are the contents of that file:



#!/bin/sh
#
# Note that any setup should come before the sessreg command as
# that must be 'exec'ed for the pid to be correct (sessreg uses the parent
# pid)
#
# Note that output goes into the .xsession-errors file for easy debugging
#
PATH="/usr/bin:$PATH"

#if [ -x '/usr/bin/xsplash' ];
#then
#        /usr/bin/xsplash --daemon
#fi

/sbin/initctl -q emit desktop-session-start DISPLAY_MANAGER=gdm



I'm not sure what exactly I would change to get rid of the sounds...

Is this correct?

---

