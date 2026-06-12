---
title: "Where has 'Shared Folders' in 'System' menu gone?"
date: 2008-06-12
forum: Networking &amp; Wireless
---

### Post by ChildOfMana on 2008-06-12
I used to run Ubuntu 7.04 on this machine and I was sharing folders (via NFS) with a client machine.

I did this by going to System > Administration > Shared Folders, selecting my /home folder and selecting NFS as the "share with" option.

I've not long installed Hardy and now I can't seem to find the Shared Folders option anywhere. Where has it gone? Is there something I'm missing? Is there another way to share folders with a client machine (also running Hardy)?

I've got nfs-kernel-server and nfs-common packages installed.

Thanks.

---

### Post by ChildOfMana on 2008-06-12
Okay so I managed to find an alternative way to accomplish the same task by following the instructions here [http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

Just out of sheer curiosity though I'd like to know why Shared Folders was removed (or if it was moved - where to).

Can anyone shed any light?

---

### Post by lavinog on 2008-06-15
looking for the same answer

---

### Post by lswb on 2008-06-15
I can't really shed any light as to why it was removed, but the command name that runs it is "shares-admin" and you could probably add it back to the menu from System/Preferences/Main Menu/New Item.

I notice that the help browser on Hardy says that this should be at System/Administration/Shared Folders, but there are plenty of other places where the help browser is not in sync with what is actually there.

---

### Post by lavinog on 2008-06-15
It seems that it was removed because it was integrated into nautilus.
Right click on a folder and there should be a "sharing options" option. It will then install samba for you. Unfortunately there seems to be a bug with the install script and it forgets to add the user to the samba user list.
[https://bugs.launchpad.net/ubuntu/+source/nautilus-share/+bug/212098]("https://bugs.launchpad.net/ubuntu/+source/nautilus-share/+bug/212098")I don't know how effective this bug report is since it really doesn't seem to address the issue I am having, because I get the message, but relogging in doesn't fix it.

---

### Post by lavinog on 2008-06-15
Ok I figured out my problem...
Edit: I needed to relogin, but it still didn't work because I tried to share it as su earlier and trying to share it as a regular user was causing another error because it was the same share name.

---

### Post by ChildOfMana on 2008-06-15
Yeah I tried the right-click option but it was only for Samba. I'm hooking up two Ubuntu machines via NFS and the old "Shared Folders" option gave you the option of sharing either via Samba or NFS. The right-click option only gives you the option to share via Samba. Strange.

Still, figured it out in the end. Although it was a lot of messing about - would have been easier (but maybe not as fun) to do it via a GUI.

---

### Post by Guilden_NL on 2008-09-09
I agree with ChildOfMana, the decision to remove it from the menu is short sighted.  Yes, there are a lot of people with mixed Windows/Linux networks and they use Samba.  I have that config for obvious reasons.  However, 98% of my home network is Unix/Linux so NFS is what I prefer to use.  I had to search through the forums to find this thread and the resulting How To that was listed here.

I am not familiar enough with Ubuntu to know where to place this back in for a feature request. Will put it on my list and when I figure out how to submit the feature requests, will include this as well.

BTW, thanks ChildOfMana for the link, it didn't come up in my search for some reason.  I sometimes have to drop out to Google and narrow it to the Ubuntu domain to get good search results.

---

### Post by matriculated on 2008-09-09
I guess the decision to move it to Nautilus was to make it easier for people moving from Windows (as that's how it's done on XP: right click folder, click on sharing tab). I believe the System menu also allowed you to choose Samba or Netatalk for Apple users. I wish there was a way to inform users of these changes when doing an upgrade.

---

