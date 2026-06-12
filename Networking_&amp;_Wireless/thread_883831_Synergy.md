---
title: "Synergy"
date: 2008-08-08
forum: Networking &amp; Wireless
---

### Post by semicomatose on 2008-08-08
I'm converting my other XP machine to Ubuntu Hardy, and the first thing on my list is to get Synergy working, with the Ubuntu box as the server and this XP machine as client. It worked great between XP and XP, but I can't get the connection with Ubuntu.
I installed Synergy through synaptic package manager, and wrote this synergy.conf file for the server:
```
section: screens
Catharis:
hev:
end
section: options
keystroke(f10) = switchToScreen(Catharsis)
keystroke(f9) = switchToScreen(hev)
end
```

I tried adding the links section, and I tried changing the text format. The server load great, declaring that it's loaded my synergy.conf fine, but the XP client won't connect to my Ubuntu "Catharsis". My F10 hotkey declares that I'm switching to Catharsis just fine, but F9 does nothing.

Both these machines use Static internal IPs of 192.168.1.101 and 192.168.1.102 , but I don't think that would make a difference.

Suggestions?

-semi

---

### Post by ubuntuguru on 2008-08-08
does it work when your not using the hotkeys???

---

### Post by semicomatose on 2008-08-08
No. No luck removing the hotkeys and using links instead. I'm all out of ideas here, and I really need some suggestions.

-semi

---

### Post by semicomatose on 2008-08-08
Update: I can use Ubuntu as a client, while my XP machine is the server. That's kinda nice, but *still no luck with using Ubuntu as the server!!!*

-semi

---

### Post by ubuntuguru on 2008-08-11
are you using the same versions of synergy on both computers???

---

### Post by balaram on 2008-08-11
I'm using synergy on three dual booted (Ubuntu-Windows) computers using LINKS not hotkeys.
On HOST computer do the following.
Go to System-Preferences-Sessions, click the ADD button, "Add Startup Program" window will then popup, in name box type: Synergy Host, in command box type: synergys -c followed by the location of your synergy.conf file, mine looks like this:
synergys -c /home/username/.quicksynergy/synergy.conf,
there is also an optional comment box where I typed "start synergy host at startup," for that is what should now occur. Reboot your system and hopefully things will now work. On my systems it takes synergy about 10 seconds after boot to kick in.

---

