---
title: "Cron or post-boot script?"
date: 2009-07-19
forum: New to Ubuntu
---

### Post by blues2use on 2009-07-19
I am having a problem with my wireless laptop not being able to automount a local network share and display it on the desktop.

Apparently, the wireless network must be up **_-before-_** the drive can be mounted. I have received a suggestion to write a crontab entry that will run the command "sudo mount -a" shortly after the laptop has booted and the wireless network is running. 

Sounds like a good idea but I have no clue as to what to put into crontab to accomplish this task. I know how to use "crontab -e" to make the edits. I just need some suggestions on what the entry might look like. I don't mind editing it to get it to do what's needed.

The other suggestion is to write a separate bash script that is called from cron shortly after the wireless network is up and running and I don't know how to do that either. I am scouring the net trying to find examples. I'm hoping someone has already done this and can give me a hand.

**_Thanks_**

---

### Post by oOarthurOo on 2009-07-19
Network manager is responsible for the wireless control. I don't know of anyway to make NM load before mounting drives. 

I'd experiment with uninstalling network manager and using WPA-supplicant to manage the wireless network. There's a how-to on the debian forums I wrote. Should work well for Ubuntu as well. It brings up the wireless much sooner, so it may help resolve your problem.

---

### Post by blues2use on 2009-07-19
> **oOarthurOo said:**
> Network manager is responsible for the wireless control. I don't know of anyway to make NM load before mounting drives. 

I'd experiment with uninstalling network manager and using WPA-supplicant to manage the wireless network. There's a how-to on the debian forums I wrote. Should work well for Ubuntu as well. It brings up the wireless much sooner, so it may help resolve your problem.

Do you have the forum location or title of the how to handy? I'm searching the debian forums for it right now...

**Thanks**

---

### Post by blues2use on 2009-07-19
> **blues2use said:**
> Do you have the forum location or title of the how to handy? I'm searching the debian forums for it right now...

**Thanks**

btw - I'm not using network manager. It has been removed.

I'm using wicd.

wpa-supplicant and wpagui are installed...

**Thanks**

---

