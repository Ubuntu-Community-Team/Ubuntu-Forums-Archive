---
title: "Samba security in a coffee shop"
date: 2010-07-25
forum: New to Ubuntu
---

### Post by julian.irwin on 2010-07-25
I recently set up samba to let me share the contents of the home folders on my netbook and desktop over my home network. I am sitting in a coffee shop with my netbook now and the though occured to me: can anyone sitting around me with their laptop get into my home folder? The thought of it makes me nervous even though I always here that linux doesn't require any anti-virus software or a firewall. Is there a way for me to at least password protect my home folder?
Thanks

---

### Post by AlphaLexman on 2010-07-25
I think sharing your 'home' directory (~/) is risky. Use the 'Public' directory for it's full intent. Allow share access to the 'Public' directory, if you want to share photos or music, just create symbolic links in the Public dir.

---

