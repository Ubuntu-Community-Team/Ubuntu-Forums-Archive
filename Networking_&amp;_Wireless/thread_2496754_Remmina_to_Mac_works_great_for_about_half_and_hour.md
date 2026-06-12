---
title: "Remmina to Mac works great for about half and hour and then it needs restarting."
date: 2024-04-11
forum: Networking &amp; Wireless
---

### Post by scottbomb on 2024-04-11
I've been using Remmina to access a Mac via VNC on my home LAN. It works great for a while but eventually, it goes into a state where clicking on something either does nothing or it brings brings into focus a different application or maybe even one that's not running at all. Clicking Firefox tabs just gives the tabs a blue hue but doesn't switch between them anymore. My workaround is to close Remmina, wait a few minutes, reconnect, and I'm working again for about another half hour. I monitored its memory usage with top -p <process_number> and it stays pretty stable so it doesn't look like a memory leak. Even if I just let it sit there and do nothing, it will still eventually start acting wonky if I grab the mouse and try to do something.

Any ideas on what I can look at?

[ I've tried other clients like vncviewer, xtightvncviewer, tigervnc. They all connect but won't scale the remote screen to the window size so all I see is the top-left corner of the mac's desktop. Specifying "-geometry 1440x810" doesn't do anything either. ]

---

### Post by scottbomb on 2024-04-11
virt-viewer seems to be working good. Faster than Remmina and it scales with the window size, like Remmina does. If this keeps working reliable, I can just remove Remmina and use this.

---

### Post by scottbomb on 2024-04-11
OK virt-viewer for the win. It's been working flawlessly since I first tried it. Uninstalling other vnc clients and will look to see if Remmina already has a bug report and I'll create one if not.

---

