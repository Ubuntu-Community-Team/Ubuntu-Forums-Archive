---
title: "A stupid question about SSH"
date: 2009-05-30
forum: New to Ubuntu
---

### Post by diablo75 on 2009-05-30
I'm going to be accessing my computer a lot by remote via SSH in the near future.  Lets say I have a text-based browser open in my SSH session, and use it to download a torrent file.  Can I start a second SSH session without killing the first and use it to start a torrent client while leaving the first session up so I can continue browsing, or will I have to close that program, start the client and wait for the torrent download to complete before I can kill it and return to browsing?

---

### Post by lykwydchykyn on 2009-05-31
You can start as many SSH sessions to the same box as you need to.  I think you can configure a limit in the server's config file for security reasons, but I don't think there's a limit by default.

---

### Post by diablo75 on 2009-05-31
> **lykwydchykyn said:**
> You can start as many SSH sessions to the same box as you need to.  I think you can configure a limit in the server's config file for security reasons, but I don't think there's a limit by default.

Sweet, thanks!

---

### Post by 3rdalbum on 2009-05-31
You could also use the "screen" utility to open multiple instance of Bash through the one SSH connection, and switch between them like you would switch between virtual desktops.

---

### Post by asmoore82 on 2009-05-31
If leaving yourself logged in on the remote box is not a problem, you could try this:
[http://ubuntuforums.org/showthread.php?p=7346427#post7346427](http://ubuntuforums.org/showthread.php?p=7346427#post7346427)

---

### Post by The Cog on 2009-05-31
> **3rdalbum said:**
> You could also use the "screen" utility to open multiple instance of Bash through the one SSH connection, and switch between them like you would switch between virtual desktops.

Aonther great thing about screen is that if the SSH connection gets broken, the screen programs just carry on instead of getting killed. You can disconnect and come back later to pick up to check on progress with **screen -r**.

---

