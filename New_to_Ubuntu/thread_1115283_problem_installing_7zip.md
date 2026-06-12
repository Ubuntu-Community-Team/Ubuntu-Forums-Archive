---
title: "problem installing 7zip"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by funkdified on 2009-04-03
i recently used add/remove to install 7zip.. but the shortcut does not appear in my app list anywhere... also, usr/bin has 7z and 7za now... but neither appear to be executables.. any idea?

---

### Post by LeWench on 2009-04-03
You can just remove the package, and reinstall it again.

---

### Post by kanikilu on 2009-04-03
7zip does not get added to the applications menu. I think all you need to do is install the **p7zip-full** package, and then the archive manager (file-roller) will be able to handle 7z archives. Although, you can of course use the CLI version, **man 7z**.

---

### Post by funkdified on 2009-04-03
nope. no luck.. could this be a symptom of something?

---

### Post by funkdified on 2009-04-03
ah.. thanks for the info.. i tried opening a .rar file with the archive manage, but no luck.. says unsupported format... how can i tell if 7zip has installed correctly?

UPDATE:

Looked in synaptic and found

non-free rar module for p7zip
p7zip is the Unix port of 7-Zip, a file archiver that archives with
very high compression ratios.

p7zip-rar provides a module for p7zip-full to make 7z able to
extract RAR files.

--------------
I had not installed this "non-free" module.. maybe that was the problem.. Is there a RAR archiver that is totally free and does not require registration

---

### Post by funkdified on 2009-04-03
hmm. i installed RAR shareware which is now allowing me to open the .rar archive.. anyone else had trouble with the rar function in 7zip?

---

### Post by kanikilu on 2009-04-03
RAR is a proprietary format, so it's not included by default. Check out your options here:

[http://tombuntu.com/index.php/2008/02/15/open-rar-archives-in-ubuntu/](http://tombuntu.com/index.php/2008/02/15/open-rar-archives-in-ubuntu/)

---

### Post by jmszr on 2009-04-03
funkified,

      This does not answer your question, but as an alternative I run ALZip 6.7: [http://www.altools.com/Downloads.aspx](http://www.altools.com/Downloads.aspx) through Wine and have had no problems with it.
I gave up looking for 7zip awhile ago.

---

### Post by oldos2er on 2009-04-03
> **funkdified said:**
> i recently used add/remove to install 7zip.. but the shortcut does not appear in my app list anywhere... also, usr/bin has 7z and 7za now... but neither appear to be executables.. any idea?

 7zip is CLI, so there's no menu entry for it.

---

### Post by stchman on 2009-04-03
> **funkdified said:**
> i recently used add/remove to install 7zip.. but the shortcut does not appear in my app list anywhere... also, usr/bin has 7z and 7za now... but neither appear to be executables.. any idea?

The GUI application file roller has .7z capability after you install the following packages:

```

sudo apt-get -y install rar unrar p7zip p7zip-full

```

This also installs rar capability.

---

