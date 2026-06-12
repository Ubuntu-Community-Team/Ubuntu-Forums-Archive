---
title: "No network manager after upgrade to 8.10"
date: 2008-10-29
forum: Networking &amp; Wireless
---

### Post by kartoffsky on 2008-10-29
I don't see "network" under system-> administration. I do see 'network tools,' but that turns out to be something else. I can add "network monitor" to top panel & see that I'm connected to my home network (thanks to "[How To: Manual Network Configuration without the need for Network Manager"]("http://ubuntuforums.org/showthread.php?t=571188") tutorial ) but want to try the bluetooth connection and would like to have the choice to connect to other networks without editing configuration files or, worse yet, having to try and explain that process to my girlfriend over the phone. Is it possible that I somehow disabled network manager? Is it hidden somewhere other than system->administration? Is its disappearance somehow related to the fact that now if I go to any of the specific destinations on the 'places' menu (for example places->desktop) it fires up Rhythmbox 0.11.6 instead of opening the folder in question?)? Thanks in advance for your help

---

### Post by java8964 on 2008-10-31
I have the same problem. After I upgrade to 8.10, I can't find network under system->Asminstration any more. Any idea? How I can get it back?

Thanks

---

### Post by java8964 on 2008-10-31
Is the command "nm-applet" will start the dialog as that? I tried to manually start it on command line and get the following error:

/etc/dbus-1/system.d$ sudo nm-applet --sm-disable

** (nm-applet:15371): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3


(nm-applet:15371): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

Is that the reason why I can't see the network in system->administration? If so, any idea how to fix the above error?

---

### Post by cariboo on 2008-10-31
There isn't a System-->Administration-->Network setting in Intrepid.

Jim

---

### Post by saberz on 2008-10-31
I had experienced the same thing, and I did the old faithful. I restarted, upon restart the Token Key Ring manager came up saying it had found my router and asked for the security key. Did you try rebooting? Or set up the SSID manually under one of the system admin/prep network options?

I'd be more detailed but im at work and can't remember what it is exactly.

---

### Post by Obfuscator on 2008-10-31
Check [http://ubuntuforums.org/showthread.php?t=963335&page=3]("http://ubuntuforums.org/showthread.php?t=963335&page=3"). Just drop /etc/network/interfaces, and cycle NetworkManager.

---

### Post by km4hr on 2008-11-01
Solution found! Install PCLinuxOS. It does everything right, at least for the workstation user. I really prefer Gnome over KDE. That's why I keep trying Ubuntu. But I can't ignore the quality of PCLinuxOS. Everything just works.

Every time Ubuntu comes out with a new version I give a try because of all the hoopla I read everywhere. But once again 8.10 is same old disapoinment.

The strongest thing about Ubuntu is the marketing department. The technical and quality control departments are out to lunch.

---

### Post by Nirangor on 2008-11-05
Well, I have a similar problem with the fresh install (not upgrade) of the 8.10. Network Manager doesn't show up upon system start.
Trying to manually start it gives me the following:

sudo /usr/bin/nm-applet

** (nm-applet:11001): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3


(nm-applet:11001): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

It seems I'm not the only one with a similar problem, but nevertheless... any ideas?

---

### Post by zee on 2008-11-07
You should try first to kill the already running instance of nm-applet with a nice "killall nm-applet".

I upgraded today to 8.10 and I have the same problem with nm-applet with no real solutions in sight.

---

### Post by puppy on 2008-11-07
Guys this appears to be a new problem - I upgraded to Intrepid on launch day and the strange network manager behaviour only started last night after some kernel updates. Something's been broken... there's another open thread with more details on the first page of the wireless and networking forum page.

---

### Post by puppy on 2008-11-07
I've found the culprit! Last night my system updated the following file:

linux-backports-modules-2.6.27-7-generic 2.6.27-7.5

and then when i started up this morning, no wireless

I shall file a bug report...

---

### Post by puppy on 2008-11-07
Bug #295232 has been filed - if you are having new problems with your wireless interface dissapearing since yesterday please add your comments to this bug report so that it can be escalated for a fix - thx!

---

### Post by jimv on 2008-11-07
> **km4hr said:**
> Solution found! Install PCLinuxOS. It does everything right, at least for the workstation user. I really prefer Gnome over KDE. That's why I keep trying Ubuntu. But I can't ignore the quality of PCLinuxOS. Everything just works.

Every time Ubuntu comes out with a new version I give a try because of all the hoopla I read everywhere. But once again 8.10 is same old disapoinment.

The strongest thing about Ubuntu is the marketing department. The technical and quality control departments are out to lunch.

Must have odd hardware or something.  I've been running Ubuntu on this laptop since Feisty, and I've not had many issues.

---

### Post by puppy on 2008-11-07
Hmm, I was determined not to respond to that 'solution' from km4hr. Personally, I run across bridges as fast as my little hooves can take me, and never, ever look underneath them :rolleyes:

---

### Post by IanW on 2008-11-07
Anyone still searching for a "Network Config" menu item will now find it in System/Preferences, NOT System/Admin.

---

### Post by rdwtux on 2008-11-08
I have this same problem after upgrading. 

I was able to get the nm-applet to come up and then connect to my wireless network but it wasn't clean.  I had to kill 'nm-applet' and NetworkManager processes and then re-run nm-applet.

---

### Post by cmcesq on 2009-04-03
I am having thiss exact same problem: no Network Manager at System-> Administration.  When I attempt to run NM-applet I get the exact same error msg:

** (nm-applet:11001): WARNING **: <WARN> applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken. Return: 3

(nm-applet:11001): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

Doesn't look like anyone ever came up with an answer to this, it there one?

---

### Post by EldiS82 on 2009-04-23
Same problem here...
Fresh install of Ubuntu 8.10, and there is no Network Manager, just Network Tools.

Still waiting for solution...

---

