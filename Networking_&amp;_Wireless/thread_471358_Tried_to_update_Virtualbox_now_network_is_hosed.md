---
title: "Tried to update Virtualbox now network is hosed"
date: 2007-06-11
forum: Networking &amp; Wireless
---

### Post by Gary.M on 2007-06-11
I made an attempt to update Virtualbox to the latest version (1.4) by doing this:

Kubuntu Feisty


Uninstall Virtualbox
Used add-remove package updater to include the Virtualbox repository
Selected the new version 1.4 of Virtualbox
Checked the list of additional associated files and saw that all required were already installed. One may have been updatable, and I selected update. Also added the recommended files. One of this was associated with ethernet bridging. This may have been my undoing?
Applied

Restarted Kubuntu

No network manager at startup!!

If I open settings and try to manage the network settings (admin mode) my wireless connection won't accept the changes (says the default gateway is invalid) and I cannot save the config.

I am a newbie to Linux. I browsed around and found a file logging X-session errors, and have attached a portion that if it is of use to any of you gurus out there. (much of what is shown is repeated in the rest of the file)

What do I do from here?

Thanks in advance...

---

### Post by ebe326 on 2007-06-12
I haven't used kubuntu in a while so I'm trying to remember correctly. On the gateway issue, make sure your wireless connection is showing in the dropdown menu on the gateway screen. I think you can either type in your gateway (typically, this would be your router or modem ip address) or just delete the default 0.0.0.0 and apply your changes. 

david

---

### Post by Gary.M on 2007-06-12
Thanks for the reply. I did that already, but it still insisted that it couldn't accept the config I wanted to enter. As its a newish install and I've been experimenting I've flattened it now and done a new install again, configured a little better based on what I've learned. And I'm taking backup images of the install as I go to enable me to roll back if I hit trouble again.

---

