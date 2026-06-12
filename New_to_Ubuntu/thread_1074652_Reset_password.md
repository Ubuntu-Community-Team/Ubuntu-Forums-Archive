---
title: "Reset password?"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by DBell5 on 2009-02-19
I myself am not quite a noob, albeit new to Ubuntu.
I installed a copy (Hardy) on one daughter's desktop, in hopes of reducing the inevitable crapping-up of the system. It's work well for her (and me!0 for a number of months. Yesterday, she came to me sheepishly, unable to get in, because she'd changed the password (unfortunately, it was MY password, because stupid Dad hadn't created a personal account for her), and couldn't get it right.

Is there any hope, short of a re-install?

Thanks, Dave

---

### Post by mikewhatever on 2009-02-19
You can reset the password using this guide:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by Peter09 on 2009-02-19
If you have`no other admin account then you need to go into recovery mode. (Hit escape at the grub prompt and you will see a list of entries, second one down should say recovery). You may get a menu up once booted, select the recovery terminal mode.

If you are comfortable with terminal mode then you can change her password there. Otherwise type

```
startx
```

and I think (once the desktop comes up) you should be able to change her password in system->admin->users and groups.

I suggest you give yourself an admin account incase this happens again.

---

### Post by DBell5 on 2009-02-19
Thanks, Mike and Peter! These look like just what I needed.

Once I get back in, I'll create a couple of proper accounts!

On another note, in the mean time, I've downloaded a new install disk. Is there an upgrade mode for the install, that avoids deleting any existing accounts and files?

Dave

---

### Post by rhcm123 on 2009-02-19
> **DBell5 said:**
> Thanks, Mike and Peter! These look like just what I needed.

Once I get back in, I'll create a couple of proper accounts!

On another note, in the mean time, I've downloaded a new install disk. Is there an upgrade mode for the install, that avoids deleting any existing accounts and files?

Dave

yes, and you can do it right from in ubuntu (or you can use the disk and "loopmount" it to the computer's cd-rom drive. I did that once and it was a headache... Just go to System -> Administration -> Synaptic package manager, and the upgrade button should be right on top.

If you are on 8.04 and would like to upgrade to 8.10, post again, because that requires 1 tiny extra step.

EDIT: And by yes, i meant yes, there is a way to upgrade that avoids deleting all your files and settings (Although backing up never hurts) :)

---

### Post by DBell5 on 2009-02-19
> **rhcm123 said:**
> yes, and you can do it right from in ubuntu (or you can use the disk and "loopmount" it to the computer's cd-rom drive. I did that once and it was a headache... Just go to System -> Administration -> Synaptic package manager, and the upgrade button should be right on top.

I'll do that, then, as my fancy new work-provided laptop CD/DVD RAM drive doesn't appear to work to burn an ISO image!

> **rhcm123 said:**
> If you are on 8.04 and would like to upgrade to 8.10, post again, because that requires 1 tiny extra step.

Yes, I think I am running 8.04 (will check tonight).
As long as the "one tiny little thing" doesn't resemble that in "Coraline"...

Spasibo, rhcm!

Dave

---

### Post by rhcm123 on 2009-02-19
> **DBell5 said:**
> I'll do that, then, as my fancy new work-provided laptop CD/DVD RAM drive doesn't appear to work to burn an ISO image!



Yes, I think I am running 8.04 (will check tonight).
As long as the "one tiny little thing" doesn't resemble that in "Coraline"...

Spasibo, rhcm!

Dave

Lol at your coraline reference. Now, if you want to upgrade to 8.10 you will have to do the following:

----If not running 8.04:
-Upgrade to 8.04, then read below :)

----If running 8.04:
(You can skip this really long winded explanation if you want. I like to be verbose in my explanations. :) )
You may notice that while running 8.04 there is no option on synaptic to ugrade to the latest release, even though one is out. This is because synaptic by default looks for LTS (long-term service) relases, not regular releases.The difference is package support. All releases eventually go from regular to LTS (e.g. 7.10 regular to 7.10 LTS) after the release is stabalized and package support is finalized. There is no real difference between regular and LTS releases, just repository support and package stability. When a release is ready for LTS, they just make the nessecary changes to the pre-installed packages and rename the ISO "LTS".


**READ HERE FOR THE SIMPLE UPGRADE FROM 8.04 TO 8.10 INSTRUCTIONS:**

However, synaptic/canonical likes to help the end user out (as those regular releases can be unstable on some systems) and will only look for LTS releases. You have to tell it to look for regular releases, by doing the following:

-Go to System -> Administration -> Software Sources
-Click on the "Updates" Tab.
-Go to the bottom where it says "Show new Distribution Releases". Change that to "Normal Releases". (This makes your computer look for not only LTS releases but Normal as well)
-Close the sources panel, open synaptic.
-Hit the refresh button at the bottom.
-The upgrade button should be at the top.


HAVE FUN :) :popcorn:

---

