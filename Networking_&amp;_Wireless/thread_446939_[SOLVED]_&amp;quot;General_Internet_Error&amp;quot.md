---
title: "[SOLVED] &amp;quot;General Internet Error&amp;quot; opening files over LAN"
date: 2007-05-17
forum: Networking &amp; Wireless
---

### Post by HomerSimpson748 on 2007-05-17
I've run into a problem opening shared files over our LAN that are created/owned by other users. It happens when I use Gnome to "connect to server" and when I browse the server using smb:// in Nautilus. OpenOffice gives a "General Internet Error". (The appropriate read/write permissions are in place on the server.)

I can copy said files locally, then back to the server, replacing the originals (making me the owner) and open/modify without a problem. 

Mounting the server using smbmount (as opposed to Gnome/connect to server or smb:// browse)  makes the error go away, but said files open as read only. We're presently running Feisty w/ OO2.2.

Can someone help me keep my sanity today?

---

### Post by tomt on 2007-05-20
I get the same problem. I think it is only with open office documents. The only work around I have found is copying the document over the network.

This is not really ideal!

---

### Post by morelinux01 on 2008-01-30
> **tomt said:**
> I get the same problem. I think it is only with open office documents. The only work around I have found is copying the document over the network.

This is not really ideal!

did you solved it?

---

### Post by quesyducky on 2008-02-27
I think it has something to do with the username/pw. When I try and open remote files like this, I get a popup dialogue asking for a name/pw, with waht i believe to be my correct login (tduke@server.edu), then another pops up, with a blank name (that i cannot change) asking for a pw. So, because I get the error the first time, and then am prompted with a different dialogue, i think that somewhere in Oo or nautilus it has the wrong username stored/used. for example, nautilus needs the '@server.edu', Oo doesnt (I am not fully convinced of that, as it is an M$ server, only one would work).

So, I am going to scout nautilus and Oo for any login info stored.

(my first forum post! hope it was readable!)

Also, are there any word processors that are able to open remote files with ease? Abiword? that would isolate the problem and porvide a temp fix, just 'open with Abi" files that dont need all the Oo features.

---

### Post by HomerSimpson748 on 2008-03-13
Turns out it was a problem with owner/permissions on the server. Ooops!

---

