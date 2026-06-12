---
title: "Delete"
date: 2010-08-28
forum: New to Ubuntu
---

### Post by Apostolique on 2010-08-28
It seems like some pictures in my Camera can't be moved or deleted. I can copy them fine. I made sure I had the required permissions.

Anything I may be missing?

---

### Post by -kg- on 2010-08-28
What type of camera, and what type of media are the pictures on?  Are they on, say, an SD card, or is it your camera's internal memory?

If it is internal memory, you may have to use the camera's menu to delete them.  Otherwise, you might try using "gksu <software title>" to give you the required permission to delete them.

I've never had a problem like this before with my camera, though.  It saves to an MMC card (older camera), and once I've transferred the photos over, I'm able to erase it normally.  This should be the case with all removable media except perhaps those formatted to one of the ext formats.  That's been my experience, anyway.

"gksu nautilus" should give you a Nautilus that will give you sufficient permissions to do this or, like I said, use your camera's menu system to delete them.

---

### Post by Apostolique on 2010-08-29
I never had any problem before. Everything used to work without problem. 
The files are inside the camera on an xD (not SD) card.

---

### Post by mapes12 on 2010-08-29
> gksudo nautilus" should give you a Nautilus that will give you sufficient permissions to do this Make sure you hold down the shift key at the same time as delete otherwise roots trash bin will fill up without any GUI notification.

On my camera I have to use the cameras delete function. Plugging it into my PC I can see and delete the files but they stay on the camera for some reason.

---

### Post by -kg- on 2010-08-30
Is the card removable?  You might want to consider a card reader that's capable of reading multiple different types of cards.

I have one that [looks similar to this]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=3743056&CatId=942"), and as you'll notice, they're fairly inexpensive.  That's what I use to deal with the MMC card in my camera, rather than connecting the whole camera to the computer and having to deal with it.

I know there are some cameras with non-removable (and non-expandable) internal memory, though, which you must deal with the camera directly.  I have one of those, as well, though I don't use it any more.

---

