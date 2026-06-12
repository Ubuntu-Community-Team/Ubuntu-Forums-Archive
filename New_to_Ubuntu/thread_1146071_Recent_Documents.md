---
title: "Recent Documents"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by rosswmcgee on 2009-05-02
When I try to open a spreadsheet from recent documnents the virus scanner runs and the documents do not open. This is a new developement. To open the Docs I have to enter my file system then it works. That leaves a new doc on the recent docs. I cleared the recent docs and tried it that way, but the same thing happens. How may I correct this?

Ok I removed virus scanner. Now I get this msg in recent documents, Could not open "nyse.xls"

Archive type not supported.

---

### Post by rosswmcgee on 2009-05-02
When I try to open a spreadsheet from recent documents the virus scanner runs and the documents do not open. This is a new development. To open the Docs I have to enter my file system then it works. That leaves a new doc on the recent docs. I cleared the recent docs and tried it that way, but the same thing happens. How may I correct this? In other words recent documents is opening the virus scanner, but not the document. So I removed virus scanner and then tried it
and now I get this message in recent documents. Could not open "nyse.xls" archive not supported.

Archive type not supported.

---

### Post by mikewhatever on 2009-05-02
The spread sheet format in Open Office is .ods. What's xls?

---

### Post by _Purple_ on 2009-05-02
> **mikewhatever said:**
> The spread sheet format in Open Office is .ods. What's xls?

.xls is the extension for Excel Worksheet

---

### Post by eilios on 2009-05-02
Try to manually open it from the directory. Did you move it?

EDIT: I'm not sure if that would work, I'll test under those conditions and see if I get the same error.

EDIT2: Nope, different error. Disregard this post :(

---

### Post by llamabr on 2009-05-02
In terminal, navigate to the place where the files are, and then do a:

```
file *xls
```

and then

```
ooffice nyse.xls
```

and post the output.

---

### Post by rosswmcgee on 2009-05-02
** (soffice:22272): WARNING **: unable to get gail version number
rosswmcgee@rosswmcgee-desktop:~$

---

### Post by rosswmcgee on 2009-05-02
You can save it either way, always has worked before.

---

### Post by rosswmcgee on 2009-05-02
It does work by changing the file to ODS. However this still is a new problem. My other 9.04 computer works fine with an xls  extension.

---

### Post by rosswmcgee on 2009-05-02
I am down to this. The archive manager  in recent documents will not support xls files but will support ods files in just one of my 9.04 operating systems. How to correct this?

---

### Post by rosswmcgee on 2009-05-03
I have 2 9.04 computers, one has stopped recognizing xls files, the other still does. How do I restore this function? Both recognize ods files.

---

### Post by cariboo on 2009-05-03
The archive manager has nothing to do with opening xls files in Open Office. You have a problem with Open Office Calc. The one thing I don't understand is what virus checker are you using, because as far as I know there are no active virus scanners for Ubuntu.

---

### Post by rosswmcgee on 2009-05-03
In the system applications section. Virus Scanner Under system tools.




 So if the Open Office Calc is the problem, what would be the suggested repair?

---

### Post by rosswmcgee on 2009-05-03
I tried re install virus scanner un install open office/re install open office. Back to original problem. When I try recent documents using an xls file, virus scanner opens up. I am sure if virus scanner is removed, it would repeat the msg, archive mgr can not recogonize xls files 

Removed 9.04 stripped down Open Office. Installed Open Office Suite 3.0. Same problem.Other 9.04 computer no problem.

---

### Post by rosswmcgee on 2009-05-06
I chose to do a clean install of 9.04 problem now fixed. I can read xls files in recent documents.

---

