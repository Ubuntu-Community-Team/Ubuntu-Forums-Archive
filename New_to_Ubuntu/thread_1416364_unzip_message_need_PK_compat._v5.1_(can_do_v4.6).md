---
title: "unzip message need PK compat. v5.1 (can do v4.6)"
date: 2010-02-26
forum: New to Ubuntu
---

### Post by topviet on 2010-02-26
I cannot unzip certain zip files. I got this message:
"unzip message need PK compat. v5.1 (can do v4.6)"

What that mean? What should I do to unzip the file?

Thanks.

---

### Post by mikeyphi on 2010-02-26
> **topviet said:**
> I cannot unzip certain zip files. I got this message:
"unzip message need PK compat. v5.1 (can do v4.6)"

What that mean? What should I do to unzip the file?

Thanks.

Welcome!!

Looks like it doesn't like the version you have.

Open System/Admin/Synaptic Package Manager
(you will be asked for your password)

Select Search and type in 'unzip'

Highlight the unzip package and look under Package/Properties for the version number.

Please report back - also report the name of any other specific software you are using to try to unzip.

---

### Post by topviet on 2010-02-26
> **mikeyphi said:**
> Welcome!!

Looks like it doesn't like the version you have.

Open System/Admin/Synaptic Package Manager
(you will be asked for your password)

Select Search and type in 'unzip'

Highlight the unzip package and look under Package/Properties for the version number.

Please report back - also report the name of any other specific software you are using to try to unzip.

Unzip version 6.0-1 on Ubuntu 9.10. I tried to unzip my zip file zipped by SecureZip for Windows on Windows XP. I can open my other zip files that zipped by older version of Pkzip.

---

### Post by mikeyphi on 2010-02-26
So - it looks like the problem is you're trying to open a secureZip file and Ubuntu unzip can't do it - although it does support encryption.

SecureZip Express is what you need - it was free but has been withdrawn!

You might have to get back into windows to sort the encryption.

---

### Post by topviet on 2010-02-27
I found a solution: After installed p7zip-full, I can extract my zip file zipped by SecureZIP Express 12.0.

---

### Post by Hossbeast on 2011-05-12
p7zip-full gives you the program "7z"

$ sudo apt-get install 7z

then,

$ 7z e /path/to/file   # extracts everything in the archive

---

