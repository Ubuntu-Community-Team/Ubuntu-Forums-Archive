---
title: "Ubuntu Server 64 bit Help"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by so0ky on 2010-02-14
Hello,

This is my very first post.  I have enjoyed Ubuntu on and off over the years, and honestly the only reason why I don't use Ubuntu on my personal computer is simply because of PC games.  If Ubuntu could run intense graphical games, I would throw Microsoft out the window.

Anyways, onto my question.

I have a rack server simply because I work at a datacenter, and I am trying to broaden my horizons with Linux, specifically Ubuntu Server 64bit.  I successfully configured my server for remote connections because the community articles are VERY helpful.

My question is this.  I am trying to install CS 1.6 server on my box for the experience.  I have saved the hldsupdatetool.bin in the following path:

/hlds/hldsupdatetool.bin      How do I execute the file?  I added +x to the permissions of the file.  Here are the commands I have done:

./
exec
execute

None work.

Yes I am root.

Thank you for your time in reading this and helping a noob out.  :D

---

### Post by oldos2er on 2010-02-14
```
/hlds/hldsupdatetool.bin
```

---

### Post by so0ky on 2010-02-14
Sorry for my ignorance....

However, I get hldsupdatetool.bin no such file or directory.  I have double, triple checked the file name as well as the path as to where I saved it.  I still get that response.

Is this my error, or is there an alternate possibility?

---

### Post by oldos2er on 2010-02-14
I assumed you were running from the root directory. Another possibility is to run **cd /hlds** followed by **./hldsupdatetool.bin**

---

### Post by so0ky on 2010-02-14
I have done as you have suggested, and the computer says there is no such file or directory.  I have triple checked the file name and it is spelled correctly.  The file is indeed fact there, as I see it after doing the ls command in the /hlds directory.

I am starting to think that I need to download something in order for the server to be able to run .bin files.  Does anyone know of a command to accomplish this?

Thank you for your help and time.

---

### Post by so0ky on 2010-02-14
I figured out the issue.

I had to download and install the ia32-lib package so there is the necessary software to run 32 bit applications.

Thanks.

---

### Post by oldos2er on 2010-02-14
Glad you solved it!

---

