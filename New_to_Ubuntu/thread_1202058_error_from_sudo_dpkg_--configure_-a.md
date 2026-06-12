---
title: "error from sudo dpkg --configure -a"
date: 2009-07-01
forum: New to Ubuntu
---

### Post by Topazio785 on 2009-07-01
I received the following error.
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

So I ran the dpkg --configure - a command and here is the result.

dpkg: parse error, in file `/var/lib/dpkg/updates/0000' near line 1:
 field name `<?xml' must be followed by colon

I'd appreciate it if someone could let me know what the next steps would be.

Thank You!:p

---

### Post by Miljet on 2009-07-01
This is probably not the correct way to recover from this error, but I have discovered a way to fix it. Make note of the path and filename in the error notice. Using the terminal, navigate to the correct directory. In your case it would be:
```
cd /var/lib/dpkg/updates 
```

Use ls to make sure that the corrupt file is listed. This step will also insure that you are in the right directory. Then remove the corrupt file using:
```
 sudo rm filename
```
substituting the correct filename. It looks like yours is '0000'.
Then run ```
sudo dpkg --configure -a
``` again. 

Finally try to run Update Manager again to reinstall the package.

---

### Post by Topazio785 on 2009-07-03
I removed the 0000 file and still get this message

field name `<?xml' must be followed by colon

any ideas on how to fix this?

---

### Post by Michael.Godawski on 2009-07-03
hi,

just a thought. Have you tried to edit the file and add the missing colon, like stated in the error message?

I am not on a Linux machine right now, so I can't check what the files look like.
Perhaps like a xml file: [Sample]("http://www.alistapart.com/d/usingxml/xml_uses_a.html").

---

