---
title: "Updating Flash for YouTube vids"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by chud67 on 2009-04-03
Ok, as of just recently I can't watch YouTube vids anymore on my HP Mini 1000 MIE because when I go to YouTube it says I need to update my Flash player.

So from YouTube's site I clicked the link and downloaded the .deb file for Ubuntu.
Then from a root terminal I ran: **sudo dpkg -i install_flash_player_10_linux.deb**
However I got an error: **package architecture (i386) does not match system (lpia)**
I guess this is because the Mini uses the Atom processor, not a regular proc like most Ubuntu boxes.

Anyone else update their Flash yet? I can't be the only person with an HP Mini who watches YouTube videos...

---

### Post by kansasnoob on 2009-04-03
Try simply going to terminal and running:

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by chud67 on 2009-04-03
Ok, I got Flash to work by doing a:  

```
sudo dpkg -i --force-architecture install_flash_player_10_linux.deb
``` 

 I am now watching YouTube videos again.  :p 

Kansasnoob, thanks for the suggestion, but I didn't see your post before I found the force-architecture trick.

---

