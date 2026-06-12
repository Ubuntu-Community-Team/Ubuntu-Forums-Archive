---
title: "Can't install from universe source?"
date: 2011-02-24
forum: New to Ubuntu
---

### Post by llmunro on 2011-02-24
Hi,

I have installed UNR on my EEE1000H today and all is working fine, except that I'm having trouble installing certain applications.  I've now tried installing Keepassx through Synaptic, the software center, and the terminal and can't seem to get it to work.

In the Software Center, it says that KeepassX is available from the "universe" source, but when I try to install it, I get a message about "Failed to Download Repository Information. Check your internet connection." The internet connection is fine.  I also have looked in Synaptic and made sure that "universe" is checked under "Repositories."

What now?

Thanks much.
Lisa

---

### Post by oldos2er on 2011-02-24
Run ```
sudo apt-get update
``` or in Synaptic, click the 'Reload' button.

---

### Post by llmunro on 2011-02-24
Hi,  

I tried sudo apt-get update and all seemed fine until:

W: Failed to fetch [http://us.archive/ubuntu/com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz](http://us.archive/ubuntu/com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz)  Hash Sum misma tch

E: Some index files failed to download, they have been ignored, or old ones used.

I'm guessing this is the reason.  Ideas?


Thanks.
Lisa

---

### Post by oldos2er on 2011-02-25
Not sure about the hash sum mismatch error. You could try using different servers; in a terminal run **gksu software-properties-gtk**, click the Download from: drop-down menu and choose one that's different from the one you're using now. Afterward you will need to run **sudo apt-get update** again. Not sure this will cure your problem though.

---

