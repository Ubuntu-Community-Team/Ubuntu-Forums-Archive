---
title: "Help compiling Code::Blocks in Lucid?"
date: 2011-02-12
forum: New to Ubuntu
---

### Post by lelandnielsen on 2011-02-12
I'm attempting to install Code::Blocks and I'm getting this message:

```

sudo apt-get check
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  codeblocks: Depends: codeblocks-common (= 8.02svn6088) but 10.05-0ubuntu1~lucid2 is installed
              Depends: libcodeblocks0 (= 8.02svn6088) but 10.05-0ubuntu1~lucid2 is installed
  codeblocks-common: Breaks: codeblocks (< 10.05) but 8.02svn6088 is installed
  codeblocks-contrib: Depends: libwxsmithlib0 (= 8.02svn6088) but 10.05-0ubuntu1~lucid2 is installed
E: Unmet dependencies. Try using -f.


```

I'm new to this and have no idea what this means or how to proceed.  Any help is greatly appreciated.  Thanks!

---

### Post by Vaphell on 2011-02-12
i assume you install from a 3rd party repo. Is there a specific reason why default version for lucid (8.something) is not good for you? That one would install with no issues and conflicting dependencies.
I'd uninstall all codeblocks related packages, disable 3rd party repo and install from official repos again.

---

