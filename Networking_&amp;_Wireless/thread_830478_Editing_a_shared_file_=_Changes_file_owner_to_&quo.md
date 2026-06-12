---
title: "Editing a shared file = Changes file owner to &quot;nobody&quot;???"
date: 2008-06-15
forum: Networking &amp; Wireless
---

### Post by ddixonr on 2008-06-15
Why does editing a shared file change the owner to "nobody"?

Details:

1. I created html files on my web server (desktop).
2. Rather than spend all my time confined to the desktop, I opted to share the necessary files/folders so that I can work from the laptop throughout the house.
3. After editing each file from the shared www folder, the files & folders appear with locks (looking at them from the desktop). The owner says "nobody."

Now, I can ONLY edit those locked files from the laptop. I know that I can change the owner with the chown command, but I'd have to do it after every edit (which can be several times a day).

---

### Post by SpaceTeddy on 2008-06-16
please post your smb.conf. I have the suspection that you either used the guest account and a public share, or you used a force user.
Either way, this should be easy.

hope we can figure it out :)

---

