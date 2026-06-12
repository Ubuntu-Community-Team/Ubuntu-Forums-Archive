---
title: "firefox gone?"
date: 2010-12-09
forum: New to Ubuntu
---

### Post by a77ssii on 2010-12-09
Haven't used my Dell Mini running 8.04 in about 8 or 9 months, I always use my full size with Karmic so powered up and it immediately wanted to update and the update failed.  I now have lost Firefox in my applications menu and also on my panel.  It is still in user/lib and will run if I go through help/connect to ubuntu but for the life of me I can't figure out how to get it back into applications and onto my panel.  Any ideas as to what happened and how to restore it?

---

### Post by houseworkshy on 2010-12-09
I can't un-post so am putting this here instead, long time no reply so needs a bump anyway.  
You could try reinstalling it via synaptic or the termainal.  Perhaps it would be a good idea to "sudo apt-get purge firefox " first OR via synaptic "compleatly remove" to get rid of what may be invalid settings.
Better yet wait for someone who has Hardy on their system to reply as they can test things out before giving advise, I used, and loved it, it for a year or two but switched so am now several updates out of date on Hardy knowlage.

---

### Post by a77ssii on 2010-12-10
Thanks.  I've tried a reinstall via terminal, all packages installed and nothing added.  Still no Firefox.  I'll just keep plugging away myself or hopefully someone will pop up with a solid answer.  The only reason Hardy is still on the Mini is because of warranty, when it's out I'm headed to Karmic for it.  I have Lucid on a desktop and have had incessant issues with it but my laptop with Karmic is about bulletproof.

---

### Post by BugBuster on 2010-12-10
Try resetting your panel and menu preferences by doing so
```

rm -r ~/.gconf/apps/panel
rm -r ~/.gnome2
rm -r ~/.config

```
Then logout and login again.

Note: This will reset your panel/menu preferences and give you an environment like a first time login. So if you have made any changes you will have to do them again.

---

### Post by corncob on 2010-12-10
> **a77ssii said:**
> Haven't used my Dell Mini running 8.04 in about 8 or 9 months, I always use my full size with Karmic so powered up and it immediately wanted to update and the update failed.  I now have lost Firefox in my applications menu and also on my panel.  It is still in user/lib and will run if I go through help/connect to ubuntu but for the life of me I can't figure out how to get it back into applications and onto my panel.  Any ideas as to what happened and how to restore it?

Can you make a launcher for it?  Right click the panel, choose 'add to panel', then 'custom application launcher'.  The command on my firefox launcher is 'firefox %u' (I don't know what the %u does -- seems to work the same without it).  Or, for the desktop, right click the desktop and select 'create launcher'.

---

### Post by a77ssii on 2010-12-11
Tried the launcher initially, I've done it for a number of different things and it fails for Firefox.  I did BugBusters suggestion and while I still don't have Firefox in my applications it is working now without having to back it in through help.  Problem solved to a working point and since I don't rely on the Mini it's no big deal.  Thanks.

---

