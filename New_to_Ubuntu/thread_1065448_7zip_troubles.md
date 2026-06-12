---
title: "7zip troubles"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by Sheneron on 2009-02-09
I have been trying to extract a .rar file and have been having a lot of trouble.  I used 7 zip in windows and liked it alot but I haven't been able to get it to work in ubuntu.

First off when I right click and click extract here it says it doesn't support that file type.

So then I try it using the terminal.  I say:  7z x file.rar
and it says: 

7-Zip  4.58 beta  Copyright (c) 1999-2008 Igor Pavlov  2008-05-05
p7zip Version 4.58 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,2 CPUs)

Processing archive: WOLFRAM.RESEARCH.MATHEMATICA.V6.0.1.LINUX.X86.X64-EDGEISO.rar

Extracting  WOLFRAM.RESEARCH.MATHEMATICA.V6.0.1.LINUX.X86.X64-EDGEISO/emlin601.cue     Unsupported Method
Extracting  WOLFRAM.RESEARCH.MATHEMATICA.V6.0.1.LINUX.X86.X64-EDGEISO/emlin601.bin     Unsupported Method
Extracting  WOLFRAM.RESEARCH.MATHEMATICA.V6.0.1.LINUX.X86.X64-EDGEISO/edgeiso.nfo     Unsupported Method
Extracting  WOLFRAM.RESEARCH.MATHEMATICA.V6.0.1.LINUX.X86.X64-EDGEISO

Sub items Errors: 3



Anyone know what is happening?  Thanks in advance.

---

### Post by spcwingo on 2009-02-09
You don't have unrar installed.  To install it just copy/paste this in the terminal:

```
sudo apt-get install unrar
```

Then try it again.

---

### Post by Sheneron on 2009-02-09
Well crap, that was easy.  Thanks a bunch.

---

