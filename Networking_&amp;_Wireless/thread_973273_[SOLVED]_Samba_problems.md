---
title: "[SOLVED] Samba problems?"
date: 2008-11-06
forum: Networking &amp; Wireless
---

### Post by AlanR8 on 2008-11-06
Evening all

My "server" runs Hardy and my two laptops run Intrepid therefore KDE 4.1.*. I use SMB4K to browse the network and mount drives. All is well in this area.

Here's the stinger. I can copy files and folders between the Intrepid machines, but if I try to copy a FOLDER to the Hardy server I get a "Permission Denied" error. Oddly, if I open the folder I can copy the individual files to the Hardy server.

I installed the Samba Server Configuration software on my two Intrepid machines, (system-config-samba) and to the Hardy box but under Hardy the program won't open. I suspect the problem is down to samba users that the above program has resolved on the Intrepid machines.

How do I resolve it on the Hardy box?

---

### Post by AlanR8 on 2008-11-07
Sorted the problem but no clearer as to why it happened. 

The fix was to install Intrepid on the "server" and all is now back to normal. I suspect it was a samba user issue.

If any of you networking experts can shed some light on this matter I'd be grateful.

---

