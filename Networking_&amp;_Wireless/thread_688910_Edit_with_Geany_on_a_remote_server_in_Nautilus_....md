---
title: "Edit with Geany on a remote server in Nautilus ..."
date: 2008-02-05
forum: Networking &amp; Wireless
---

### Post by yhugo on 2008-02-05
hello everybody,

how i can edit with Geany on a remote server in Nautilus (SSH connexion) ... ?

With gEdit it's working well but with geany the files never open ... only a blank page.

Thanx for your help

have a nice day

ciao

---

### Post by simon_w on 2008-05-13
Hi there,

I have the same problem, but only intermittently.  Sometimes I can open remote files (via sftp) directly from Nautilus into Geany, and sometimes I cannot, and I have yet to work out why.  It's beginning to drive me a bit nuts.

Geany is selected as the default application in the nautilus files properties dialog, on the 'Open With' tab, yet double clicking launches GEdit, and using 'Open with other Application' and selecting Geany launches Geany, but does not open the file.

Any advice or suggestions would be extremely welcome.  I'm assuming it's some kind of problem with Nautilus, and not with Geany?

Note:  local files work fine.

Thanks!

Simon
:)

---

### Post by simon_w on 2008-05-28
the problem seems to be with gvfs, which I know nothing about whatsoever.  Sometimes, (under circumstances and for reasons which I cannot determine and appear totally random from my level of understanding, ) when I connect via ssh/sftp in nautilus the remote filesystem is mounted under $HOME/.gvfs, and sometimes it isn't.  In the latter case, I can browse the filesystem in Nautilus, and open files in GEdit, but not in certain other programs, such as Geany.

Mounting the remote fs manually using sshfs never seems to fail though, and it's a tolerable work-around for me.  Hope it can help you too.

Simon
:)

---

