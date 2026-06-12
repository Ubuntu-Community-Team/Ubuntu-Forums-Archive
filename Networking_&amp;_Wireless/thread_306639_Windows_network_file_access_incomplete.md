---
title: "Windows network file access incomplete"
date: 2006-11-25
forum: Networking &amp; Wireless
---

### Post by rek on 2006-11-25
Using "Places>Connect To Server", I have no problem connecting to my shared folders on my Windows XP machine. The problem that I have is that the Windows folders don't show up on the file chooser menus for applications such as OpenOffice and Firefox. The folders do show up is gedit. What do I need to do to make my Windows folders appear in those other file choosers? Thanks.

---

### Post by rek on 2006-11-27
I haven't resolved this specific issue yet. But, I was able to get the access that I needed by adding an entry to /etc/fstab for the windows network drive. Now that drive is mounted every time on boot and I have full access to it from every menu.

---

