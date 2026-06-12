---
title: "Missing Dependencies"
date: 2010-12-14
forum: New to Ubuntu
---

### Post by bvpainter on 2010-12-14
To get my HP Deskjet 3050 printer to run I have downloaded the latest hplip-3.10.9.run file and tried to run it , but I get the following error message.

warning: There are 6 missing REQUIRED dependencies.
note: Installation of dependencies requires an active internet connection.
"warning: Missing REQUIRED dependency: python-devel (Python devel - Python development files)
warning: This installer cannot install 'python-devel' for your distro/OS and/or version.
error: Installation cannot continue without this dependency. Please manually install this dependency and re-run this installer.
bernard@bernard ~/Downloads $"

I went to package manager and it appears that the latest version of Python is loaded. How can I install the missing dependency python-devel, as it does not appear in the list of programs available.

Any other advice about installing "hplip-3.10.9.run" would be appreciated.

---

### Post by oldos2er on 2010-12-14
Maybe **python-dev** is what you need.

---

### Post by mc4man on 2010-12-14
I believe there was a very similar or even the same thread recently - after installing python-dev, you'll then get "There are 5 missing.."

Don't see the thread offhand, possibly it listed all.

Otherwise don't take what it reports so literally, devel means -dev
Try searching the main name in synaptic, many times also try adding lib to front of name. It's best not to be too specific when searching  synaptic.
Then look for a likely candidate for the library or it's -dev package if that is what's required.

---

### Post by bvpainter on 2010-12-14
Thanks problem sorted.

---

