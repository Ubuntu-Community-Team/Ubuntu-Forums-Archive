---
title: "Update Manager Icon"
date: 2010-12-10
forum: New to Ubuntu
---

### Post by marl30 on 2010-12-10
I noticed that since I reinstalled Ubuntu a few days ago I haven't seen that little orange update icon appear on the top panel. It would usually popup whenever I ran sudo apt-get update or refreshed Synaptic. I would like to know what settings I need to enable to make it show up? Or what package/s I need to install to get it back. For those who are not sure what I'm talking about, see the orange icon in this link: [http://alternativeto.net/software/ubuntu-update-manager/?profile=linux&platform=linux](http://alternativeto.net/software/ubuntu-update-manager/?profile=linux&platform=linux)

---

### Post by cariboo on 2010-12-10
It depends on how you have setup update-manager, on how often it notifies you of updates. I'm running Natty, and normally update 3-4 times a day, so I never see the update manager notification.

---

### Post by philinux on 2010-12-10
[QUOTE=marl30;10223689]I noticed that since I reinstalled Ubuntu a few days ago I haven't seen that little orange update icon appear on the top panel. It would usually popup whenever I ran sudo apt-get update or refreshed Synaptic. I would like to know what settings I need to enable to make it show up? Or what package/s I need to install to get it back. For those who are not sure what I'm talking about, see the orange icon in this link: [url]

The orange icon is long gone. Update manager will just appear when there are updates in the bottom task panel.

---

### Post by marl30 on 2010-12-10
> **philinux said:**
> [QUOTE=marl30;10223689]I noticed that since I reinstalled Ubuntu a few days ago I haven't seen that little orange update icon appear on the top panel. It would usually popup whenever I ran sudo apt-get update or refreshed Synaptic. I would like to know what settings I need to enable to make it show up? Or what package/s I need to install to get it back. For those who are not sure what I'm talking about, see the orange icon in this link: [url]

The orange icon is long gone. Update manager will just appear when there are updates in the bottom task panel.

Wow, and I thought it was a cool idea. But one I can live without, as it's not really that much of an issue anyhow. Thanks for the replies.

---

### Post by ajgreeny on 2010-12-10
I'm not sure about natty, but in previous versions you can stop the update manager opening automatically, and revert back to the notifier icon using **gconf-editor->apps->update-notifier** and removing the selection from the autolaunch box.

See screenshot.

Apologies if such things have disappeared from natty, but it's worth a look-see.

---

### Post by marl30 on 2010-12-10
> **ajgreeny said:**
> I'm not sure about natty, but in previous versions you can stop the update manager opening automatically, and revert back to the notifier icon using **gconf-editor->apps->update-notifier** and removing the selection from the autolaunch box.

See screenshot.

Apologies if such things have disappeared from natty, but it's worth a look-see.

Thanks, this did the trick alright. :)

---

