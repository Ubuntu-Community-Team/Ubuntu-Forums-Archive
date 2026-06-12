---
title: "Issues connecting to an ubuntu samba share using a Vista machine"
date: 2008-10-22
forum: Networking &amp; Wireless
---

### Post by survient on 2008-10-22
Ok, not sure if this is a Vista issue or my ubuntu server's issue, but I'm having issues accessing the server's samba shares using a vista machine. Sometimes it will work just fine, other times it will just sit there and time out. On my other ubuntu machines and XP machines, they connect fine and almost instantly, I've never had issues. I'm just trying to figure out if I need to change something on the server or on the Vista machine. Any help would be appreciated.

---

### Post by cariboo on 2008-10-23
If all the other computers can connect with no problems then it definitely is a Vista problem. The only thing I can suggest is to check and see if there is a specific vista driver for your network card. I had to go to my motherboard manufacturers web site and download the vista drivers for my video, sound and network adapters, to get 64bit Vista to work properly.

Jim

---

### Post by survient on 2008-10-23
I agree it may be something Vista has that causes the issue, but my main question is what and where an adjustment needs to be made to resolve the issue. The drivers for the NIC are up to date, as are the Windows Updates overall. I know Vista authenticates shares differently than XP or samba, at least from what I've read, so I wasn't sure if I had to do something with the server to get it to support Vista's requirements, and what that change would be.

---

### Post by cariboo on 2008-10-23
I honestly don't use Vista enough to be able to answer your question. With the default installation I had nothing but trouble, but since installing MSI's Vista drivers everything just plain works, even my old TV@nywhere Tv tuner. :) I should mention that I'm running an OEM Vista 64Bit Ultimate Edition, and yes it was expensive
.
Jim

---

