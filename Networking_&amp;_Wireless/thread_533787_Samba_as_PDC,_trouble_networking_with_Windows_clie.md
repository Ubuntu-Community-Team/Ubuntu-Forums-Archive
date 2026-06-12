---
title: "Samba as PDC, trouble networking with Windows client"
date: 2007-08-24
forum: Networking &amp; Wireless
---

### Post by lemot66 on 2007-08-24
Hi all,

I recently followed several great tutorials for establishing my Ubuntu machine as the PDC.  I have connected a WinXP box as the client - pushing files to the shared directory on the PDC works great.  

However the problem I have is when I try to do the reverse - access shared folders from the client via smb://winxpcomputername calls.  The thing is, out of 10 windows folders that are shared (each have the exact same shared permission settings which I configured and are not read-only), only half of them work.  And the weird part is...it's inconsistent!  One minute folders A, B, and F are accessible, and the next minute B, C, and F are the only ones accessible....  

When one of the directories at random is "inaccessible", I get a dialog "Authentication Required".  So I try my username/password of my current unix account...click ok, and I keep getting the same dialog box.  Obviously the client isn't authenticating the unix user.  I took a look at winbind based on suggestions from several of you in the forums, but it seems as though that's not the answer I'm looking for, since Samba is acting as my PDC, and the Windows user seems to authenticate fine on the unix box.  

I'm not sure what the reason is for this, or how to fix it.  Can anyone out there help me please?

Oh, and I apologize if my description was unclear at any point.

Thanks!
Tom

---

