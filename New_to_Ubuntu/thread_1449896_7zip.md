---
title: "7zip"
date: 2010-04-08
forum: New to Ubuntu
---

### Post by h8uthemost on 2010-04-08
Hey guys,

When I try to create an archive with 7zip the files will zip up just fine. But when I try to zip up those same files with 7z but set a password for the archive I get this error:

Error:
Incorrect command line

I only get this when trying to set a password. Has anyone else came across this? Is there anything I can do to fix this? I'm using Ubuntu 9.04 and the version of p7zip that I'm using is also 9.04.

Thank you for any help.

---

### Post by undecim on 2010-04-08
what command are you using?

---

### Post by h8uthemost on 2010-04-08
All I'm doing is right-clicking on the folder and hitting Create Archive. Then that little window pops up and under Other Options I type in my password.

---

### Post by undecim on 2010-04-08
Maybe a bug with fileroller? What is the name of the folder?

---

### Post by h8uthemost on 2010-04-08
I forgot to mention it's all folders. I've tried a lot of them all with different names.

Does your version of p7z let you zip with a password? What version are you using? Previously I was using the version that was in Synaptics, which was 4.something. But I never tried password zipping with that version. I just started trying when I updated to 9.04.

And I'm appreciating the replies. Thank you.

---

### Post by undecim on 2010-04-08
> **h8uthemost said:**
> I forgot to mention it's all folders. I've tried a lot of them all with different names.

Does your version of p7z let you zip with a password? What version are you using? Previously I was using the version that was in Synaptics, which was 4.something. But I never tried password zipping with that version. I just started trying when I updated to 9.04.

And I'm appreciating the replies. Thank you.

I think the problem is in fileroller, which is the graphical frontend for making archives. Fileroller calls 7z to compress the files.

I have p7zip-full installed. My versions for both packages are```
undecim@caffeine ^_^ ~$ aptitude show p7zip-full | grep Version
Version: 9.04~dfsg.1-1
undecim@caffeine ^_^ ~$ aptitude show file-roller | grep Version
Version: 2.28.1-0ubuntu1
```

---

### Post by h8uthemost on 2010-04-08
Ok that did it. I just completely removed p7zip 9.04 and installed p7zip Full 4.58. And I just successfully zipped up a folder while passwording it, and unzipping it.

Guess I should have tried that before making this thread. :p I appreciate your help undecim.

EDIT: By the way, what's the difference between the regular p7z and the full? Synaptics says full includes 7za(don't know what that is). But that extension is included as an option when I got to create and archive.

EDIT AGAIN: Looks like 7za isn't an extension.

---

### Post by undecim on 2010-04-08
7za I think is a command line utility...

It's looking to me like a bug in p7zip, but no p7zip-full. I'm poking around with p7zip... I'm reproducing the error you explained, and I'll submit a bug report.

---

### Post by h8uthemost on 2010-04-08
Ah. So it wasn't just me then. Well I'm glad you gave me the idea to go with full. I like the idea that p7z lets you encrypt the file list when you zip with a password. So I'm glad to get this straightened out.

Thanks again.

---

### Post by undecim on 2010-04-08
Yeah, this is definitely a bug with p7zip.

the 7zr (from p7zip) command is used when you don't have 7z (p7zip-full), and the -p (password) option causes an error on 7zr, even though it should act the same as 7z when dealing only with 7zip files.

---

