---
title: "Network Manager and Old Keyrings"
date: 2008-05-03
forum: Networking &amp; Wireless
---

### Post by gary vollink on 2008-05-03
Does anybody know where I can tell Network-Manager to use a different keyring?

On Feisty, my network manager stored everything in the keyring, "default", but with Hardy, a new keyring was automatically set up called "login".

I used seahorse/preferences (a/k/a System->Preferences->Encryption and Keyrings) to suggest that "login" should be the Default Keyring.

This didn't work, upon initial login, NM would ask me to unlock the Default keyring (and would only accept the old password for the default keyring).

A few reboots later, I did something that was probably stupid...  I told that same preferences dialog to delete the "Default" keyring.  Here things get strange. Now, I reboot, log-in, and NM asks me for the password for the Default keyring.  I type in the old password for the default keyring, and... it works!?!?)

Maybe something didn't really get deleted.

I can't find any practical examples of where these individual files are stored to actually try to figure out what's really happening.  I really don't want to have to crack open the source code to try to figure out the interactions between network-manager-gnome, ubuntu-keyring, libpam-gnome-keyring and gnome-keyring.

Any tips/pointers, ideas, or "you are crazy because of..." statements would be appreciated.

Ubuntu 8.10 (Hardy Heron) - Toshiba Satellite S105-4074

---

### Post by lariamat on 2008-05-23
I would like to bring up this topic again as I had the same problem on my computer and there seem to be many people who have the same problem. 
I also filed this as a bug one week after the release of hardy but I never got any feedback.
After some more days I gave up as I wasn't able to locate the problem and I don't have the time to go into the source code.

I installed wicd (ugly). It works but I would like to use nm if possible.
In Hardy many problems popped up for me that never before existed in feisty or gutsy.
Maybe someone found a solution and wants to answer this thread.
thank you

---

### Post by gary vollink on 2008-05-23
I have no evidence for certain, but ... I think that when I upgraded, it created "login" by making a copy of my existing "default" keyring, and naming it "login".  Thus - I had two sets of keys that were identical, and both had the same (and wrong) password.

Eventually, after deleting my old "default" keyring, I was able to change the password on the "login" keyring to match my login password, and it started reacting as designed.

Without being sure that this is really what happened, it's just a story that I tell myself so that I can sleep at night.  :-)

---

