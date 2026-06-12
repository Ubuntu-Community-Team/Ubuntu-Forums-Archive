---
title: "How do I join the video group in Ubuntu 11.04?"
date: 2011-08-12
forum: New to Ubuntu
---

### Post by StopMakingBabies on 2011-08-12
I have Ubuntu 11.04 and I'm trying to use webcam studio but it says I need to join the "video group" but I have no idea what that is. Can someone help me on how to join it?

---

### Post by nothingspecial on 2011-08-12
Hi, type this

```
sudo usermod -a -G video $USER
```

don't miss the -a or you will stuff things up royally.

---

### Post by The Cog on 2011-08-12
FYI, that's the quick and easy way of starting the System->Users and Groups application, click Manage Groups, highlight the video group and click Properties, then check the checkbox against your own name.

This (like the post above) adds you to the user group called video, which then gives you rights to do video related things.

It also shows why it's quicker and easier for people giving help to give you a command line than to write a long description of how to do it in the GUI.

---

### Post by StopMakingBabies on 2011-08-12
> **The Cog said:**
> FYI, that's the quick and easy way of starting the System->Users and Groups application, click Manage Groups, highlight the video group and click Properties, then check the checkbox against your own name.

This (like the post above) adds you to the user group called video, which then gives you rights to do video related things.

It also shows why it's quicker and easier for people giving help to give you a command line than to write a long description of how to do it in the GUI.I did do that, but whenever I open it it still says I'm not part of the group.

---

### Post by The Cog on 2011-08-13
Double-check with the command **id** which lists all the groups you belong to. Or, can you see your name checked against the video group in Users and Groups GUI?

Ah - you need to log out and back in again to pick up the new group membership.

---

