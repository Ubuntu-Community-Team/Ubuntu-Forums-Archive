---
title: "Deleting using terminal"
date: 2010-01-04
forum: New to Ubuntu
---

### Post by Dynamus on 2010-01-04
How do you delete programs. I downloaded bittorrent but I want to delete it now, so how do I go about doing that?

---

### Post by seandude on 2010-01-04
sudo apt-get autoremove name-of-torrent

---

### Post by themusicalduck on 2010-01-04
> **seandude said:**
> sudo apt-get autoremove name-of-torrent

I think that should just be ```
sudo apt-get remove bittorrent
``` rather than autoremove.

EDIT: I guess I should of tried it since it seems to work both ways! Sorry for correcting you wrongly.

---

### Post by bobin on 2010-01-04
go to synaptic manager. search for the program right click nad remove. Or u can use add/remove

---

### Post by bobin on 2010-01-04
go to synaptic manager. search for the program right click nad remove. Or u can use add/remove

---

### Post by SchizmWolf on 2010-01-04
If it's already installed, what I like to do is sudo apt-get uninstall *nameofprogram* and then apt-get purge *nameofprogram* just to be extra sure.

---

### Post by lotharmat on 2010-01-04
> **SchizmWolf said:**
> If it's already installed, what I like to do is sudo apt-get uninstall *nameofprogram* and then apt-get purge *nameofprogram* just to be extra sure.


you could just use:

```
sudo apt-get --purge remove [packagename]

```
Does it all!

---

