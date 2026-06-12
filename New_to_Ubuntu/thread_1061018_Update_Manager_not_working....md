---
title: "Update Manager not working..."
date: 2009-02-05
forum: New to Ubuntu
---

### Post by DonaldJ on 2009-02-05
Update manager finds 150 updates, but fails to work properly...

Click install, the downloads window is blank, modem light flashing indicating it might be downloading, but it remains that way for all night...  I must cut the power to the tower to break the freeze-up...

I tried to download another update manager, but a pop-up reads that there is a conflict that must be dealt with in synaptic manager...

---

### Post by ptn107 on 2009-02-05
Try updating from the command line.  Applications -> Accessories -> Terminal.  Type:

```
sudo apt-get update && sudo apt-get dist-upgrade -y
```

Post any errors.

If it mentions anything about 'Could not get lock', delete the file it's complaining about (it's usually /var/cache/apt/archives/lock).

Conflicts with packages can be solved during the upgrade process by appending '-f' (fix) to the command as in:

```
sudo apt-get -f dist-upgrade -y
```

---

### Post by DonaldJ on 2009-02-05
I tried that..  it didn't help..  Thanks...  

I'm reinstalling Ubuntu...

---

### Post by DonaldJ on 2009-02-08
I suspect what happened to make it so the update manager fail, was that I installed a few peripheral add-on softwares, and ran a cleaner without having rebooted...

I think novices should stay away from cleaners till they can go through the found list, and know they aren't deleting critical segments of the operating system..  like how in Windows, CMDiskCleaner saw everything that wasn't basic operating system as junk.. Clicking delete to all that CMDC found with its registry cleaner would slam the Windows OS nearly back to new install...
Point being, you must know what you're dong to run CMDC, just as you must know what you're doing to run Linux cleaners...  

The key to running Ubuntu and any Linux, is trust... It seems with Linux you can trust the people behind it all, because they are as honest as it gets...
Try to relax with it..  There aren't any evils hiding in it..  It's just real computer operating system, without any of the evils...

---

