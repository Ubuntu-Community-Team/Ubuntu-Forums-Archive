---
title: "virus from azureus?"
date: 2007-09-20
forum: Networking &amp; Wireless
---

### Post by cadamr on 2007-09-20
I'm having a major problem here. I recently tried downloading a torrent with azureus. I'm new to torrents so I don't really know how they work. 

When the download finished, I continued to have high levels network activity. I assumed I was just seeding (I think that's the right term?) so others could download it. But when I removed the torrent and closed azureus, it continued. Almost all the activity is download, not upload activity. I started the Firestarter firewall, and it's continuously blocking connections from the port that azureus was using.  

I've tried deleting the download, deleting the torrent file, uninstalling azureus, deleting the $HOME/.azureus directory, and restarting the computer, but nothing stops the downloads. I don't even know what's being downloaded.

Any and all help will be GREATLY appreciated!!!!

---

### Post by cadamr on 2007-09-20
I really need to fix this, I can't connect to the network without the firewall using 50% of the processor.

---

### Post by cadamr on 2007-09-22
really need help.

---

### Post by misfitpierce on 2007-09-22
Kill the program through the system monitor in system admin
Then start synaptic package manager or delete program through terminal...
sudo apt-get remove azureus
Download Deluge has same features without resource cost of azureus._ Link found in sig Deluge_

---

### Post by tragicglee on 2007-09-23
> **cadamr said:**
> Almost all the activity is download, not upload activity. I started the Firestarter firewall, and it's continuously blocking connections from the port that azureus was using.

I may be wrong, but it sounds like one of the anti-p2ps is probing your ports and trying to get in

---

### Post by cadamr on 2007-09-24
> I may be wrong, but it sounds like one of the anti-p2ps is probing your ports and trying to get in

What do you mean by anti-p2ps? is there anything I can do about it?

misfitpierce: I've already uninstalled azureus, deleted the files in $HOME/.azureus, and restarted multiple times since then.

---

