---
title: "ubuntu one - how do you make a file visible to the world?"
date: 2011-09-05
forum: New to Ubuntu
---

### Post by anewguy on 2011-09-05
Title pretty much says it all.  I have a PDF file that I uploaded to Ubuntu One via signing in to Ubuntu One and selecting upload file.  I checked the box for publish the file as I thought that was the public sharing option.  After the file uploads, I can view it while I'm logged in to Ubuntu One, but any attempt to address it via the URL provided by Ubuntu One from the browser without being logged into Ubuntu One fails with page not found (404).

Can anyone tell me how to transfer a file from my PC to Ubuntu One and have that file be viewable by the "public"?

Thanks in advance!

Dave ;)

---

### Post by AlphaLexman on 2011-09-05
```
chmod +o+r /path/to/filename.pdf
```
Should work.

---

### Post by anewguy on 2011-09-05
Do files on Ubuntu One maintain their rights from the machine they were posted from?  I would have thought the Ubuntu One servers have their own permissions that we can't override.

---

### Post by anewguy on 2011-09-05
Finally got it to work:

- logged on to my Ubuntu One account
- selected upload file, browsed for file, left "Publish" unchecked and clicked upload
- when file finished uploading, then I click on "Publish File"

Now it gave a URL that is indeed public.

Dave ;)

---

