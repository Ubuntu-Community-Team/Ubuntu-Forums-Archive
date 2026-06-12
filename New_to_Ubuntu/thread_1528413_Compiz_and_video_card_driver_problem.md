---
title: "Compiz and video card driver problem"
date: 2010-07-10
forum: New to Ubuntu
---

### Post by jemp on 2010-07-10
Hi Guys,

I was trying to get Compiz to work but I could not, it turns out then I need to install video card driver. When I went to System->administrator->hardware drivers I get the following error message:

'E:Malformed line 55 in source list /etc/apt/sources.list (dist parse), E:The list of sources could not be read.'

Please help if you know what the problem is!

Thanks,
Jemp

---

### Post by AAOFan on 2010-07-10
Lets start out with the first question.

What type of video card do you have?

---

### Post by staf0048 on 2010-07-10
You may also want to paste your sources.list file.  Seems like there's something wrong on line 55 from the error.  If you paste it, I'm sure someone will be able to help you figure out why it's not reading it correctly.

Also, if you don't know what type of video card you have, go to a terminal and type ```
lspci
``` and just copy and paste the results here.  We should be able to get it all sorted out for you.

---

