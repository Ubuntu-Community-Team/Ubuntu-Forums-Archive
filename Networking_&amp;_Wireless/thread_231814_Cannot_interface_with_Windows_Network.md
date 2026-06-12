---
title: "Cannot interface with Windows Network"
date: 2006-08-07
forum: Networking &amp; Wireless
---

### Post by hotch on 2006-08-07
I have installed Ubuntu 6.06 on a Dell laptop with a wireless connection to a D-Link router. Everything works beautifully, including accessing the Internet and handling e-mail.

The one thing I cannot do is to access the rest of my network, two Windows computers, peer to peer, through the router. Years ago, using Corel Linux (now Xandros) and an earlier incarnation of Windows, the network set up automatically, with no problems. Now, with Ubuntu, only frustration follows. A lot of the setup has changed since then, so I probably should not make a comparison.

Using smbfs, which seems to be the Ubuntu default, I can see the network Windows computers in "Network Servers," but cannot access them. I get this warning instead:

"The filename "BOB" indicates that this file is of type "desktop configuration file". The contents of the file indicate that the file is of type "x-directory/smb-share". If you open this file, the file might present a security risk to your system.

"Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "x-directory/smb-share", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file."

The Windows computers do not see the Ubuntu laptop at all.

So I installed Samba to see what would happen. The only change I have made to smb.conf is to change the workgroup name. The rest is default.

Now the Windows computers (or at least one of them) can see the Ubuntu laptop but cannot access it. It asks for a user name and password, and the set used for Ubuntu does not work. 

On the other hand, trying to access the Windows computers from Ubuntu, the result is the same as before. I can see the computers, but cannot access them. For some reason, one of the Windows computers now has an icon on the Ubuntu desktop, but when I try to access through it, I am told "The folder contents could not be displayed." Perservering will give me the same long note as before.

Where do I go from here? I get the feeling that this should be something simple, but it is not that way to me.

---

### Post by meng on 2006-08-07
I had this frustration too, and the answer was to edit the \windows\hosts file. Could this be your problem also? If so look here if you require more guidance.
[http://www.oreilly.com/catalog/samba/chapter/book/ch03_01.html](http://www.oreilly.com/catalog/samba/chapter/book/ch03_01.html)
By the way, the whole book is online so I personally don't recommend buying the books.

---

