---
title: "Syncing Ipod with Banshee music player"
date: 2010-02-10
forum: New to Ubuntu
---

### Post by kolo-01 on 2010-02-10
Hi,
I am trying to sync my 4th gen Ipod with banshee and have the ipod supprt extension in preferences is enabled, but the ipod does not appear in the left sidebar as it says it should in the tutorials. The ipod appears in the main navigation directory, is there anything more that i need to do to enable banshee to recognise the ipod?
any help would be appreciated.

---

### Post by blazemore on 2010-02-11
I'm ashamed to say this, but this is confirmed as not working in Karmic, which in my opinion is disgraceful.

The easiest way is probably to upgrade to the latest beta release of Banshee.

The instructions to do this are as follows:

On the top panel, click System -> Administration -> Software Sources

Enter your password when prompted, then click OK

Go to Other Software (May be called 3rd party software, I can't remember)

Add a new entry with the following content:
> ppa:banshee-team/banshee-unstable

Press Close, then Reload, and wait for the package repository to update.

Make sure Banshee is properly closed (right-click the system tray icon if it's there, and choose Exit)

Then go to Update Manager (System -> Administration -> Update Manager) and update your system in the usual way.

If everything goes well, the system should pull down a Banshee update from the Banshee developers' repository, which, I am told, fixes this ridiculous bug.

---

### Post by kolo-01 on 2010-02-12
thanks that ppa works well

---

### Post by blazemore on 2010-02-13
> **kolo-01 said:**
> thanks that ppa works well

No problem glad I could help. I hear this is due to HAL being deprecated but Banshee still uses it. Next version of Banshee should be in Lucid, so won't have this problem.

---

