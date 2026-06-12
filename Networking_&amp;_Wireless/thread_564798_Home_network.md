---
title: "Home network"
date: 2007-10-01
forum: Networking &amp; Wireless
---

### Post by billgoldberg on 2007-10-01
When I try to access my vista workgroup from ubuntu, i get the following error:

> 
**The folder contents could not be displayed.**

Sorry, couldn't display all the contents of
"Windows Network: desktop"


Ddrichardson said:
> 
If you can see the Vista share but cannot access it, try this from Windows:

1. Start/Run secpol.msc
2. Open Local Policies/Security Options, find "Network Security: LAN Manager"
3. Change it to "Send LM & NTLM - use NTLMv2 session security if negotiated."


When I enter secpol.msc I get an error saying it couldn't find the file.

Oh, and vista home premium doesn't see the ubuntu pc at all. Anyone can help there?

Thanks

---

### Post by ddrichardson on 2007-10-01
If you can see the Vista share but cannot access it, try this from Windows:

1. Start/Run secpol.msc
2. Open Local Policies/Security Options, find "Network Security: LAN Manager"
3. Change it to "Send LM & NTLM - use NTLMv2 session security if negotiated."

---

### Post by billgoldberg on 2007-10-01
Edited the original post to make things more specific and bump the question up.

---

### Post by billgoldberg on 2007-10-02
No one?

---

### Post by dei on 2007-10-02
Try to reach the secpol.msy from your start-menu first..(cant say where you find it in vista, never used it)  if this fails, it could be you have not a high-enought-edition of vista (perhaps try with ultimate?). If this is the case you can try to find the corresponding registry-key (Only the administration-frontend is not available in home-editions, the backend in the registry exists anyway). Perhaps you can try to log registry changes while changing the setting in a ultimate-edition and then making the same change to your vista-box.

if you can't get to a solution like this, why not switch this machine to ubuntu too. ;-)

---

### Post by billgoldberg on 2007-10-02
I've giving up and just going to install an home ftp server. Seems easier.

Switching the main to ubuntu isn't an option (yet, when 7.10 stable comes out, i'm going to do some marketing with the rest of the family).

---

### Post by ddrichardson on 2007-10-20
There appears to be a solution [here.]("http://ubuntuforums.org/showthread.php?t=578627")

---

