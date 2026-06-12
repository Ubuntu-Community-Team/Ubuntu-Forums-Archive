---
title: "Gdesklets won't run"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by adjordan on 2009-05-13
I have just installed 'gdesklets' using Add/Remove Applications; all seemed to work normally without Errors, but when I try to run the Program I get an Error Message 'Failed to execute child process "gdesklets" (No such file or directory)'. This is the first problem I've encountered with Ubuntu 9.04; can anyone help?

---

### Post by stchman on 2009-05-13
> **adjordan said:**
> I have just installed 'gdesklets' using Add/Remove Applications; all seemed to work normally without Errors, but when I try to run the Program I get an Error Message 'Failed to execute child process "gdesklets" (No such file or directory)'. This is the first problem I've encountered with Ubuntu 9.04; can anyone help?

Are you running 64 bit?  If yes the gDesklets does not work properly with 64 bit.  Try screenlets if you want desktop widgets.

---

### Post by adjordan on 2009-05-13
> **stchman said:**
> Are you running 64 bit?  If yes the gDesklets does not work properly with 64 bit.  Try screenlets if you want desktop widgets.

No, 32 Bit. I tried Screenlets but couldn't get that to install at all. Whilst looking for a solution to that problem , I saw a recommendation from someone to use gdesklets instead, and since it is included in the Ubuntu distribution I thought it would be a safe bet, but there you go!

---

### Post by TfcIan on 2009-05-13
Same problem for me and I did several reinstalls to make sure. Also tried installing with that Synaptic installer too. Screenlets works ok for me though.

---

### Post by cbenitez on 2009-05-16
Same here. I'm new to all of this Ubuntu stuff. I have an HP Mini 1030NR and I recently installed UNR 9.04 on my WD 160Gb external USB hard drive. I wanted to have a cool-looking desktop so I installed the gdesklets package and I get the "Failed to execute child process..." error code. I don't know how to go about getting this to work so any help will be beneficial. Any thoughts??

---

### Post by bcoffield on 2009-05-17
Hello.  I tried to install gdesklets today and received the same message as well.  I installed it using synaptic....

---

### Post by Devilotx on 2009-05-20
I fixed it with sudo apt-get install python2.5, but the weather applets do not work anymore, they give a failure message.

need my weather applets!

---

### Post by fleaaccela on 2009-05-30
Same problem here. Installing via Synaptic and getting this message:

Applications > Accessories > Gdesklet

"Failed to execute child process "gdesklets" (No such file or directory)"

usr/bin/gdesklets says: #!/usr/bin/python2.5

But I have python 2.6 - I don't know if I would want to mess with this file as it may interfere with other programs that use it.

I'm pretty sure all the other users above me are having the same problem as I am. This has got to be the reason.

---

### Post by fleaaccela on 2009-05-30
FIXED:

for people who find this post (like i did) and have this error, do the following:

System > Administration > Synaptic Manager

Quick Search, enter "python2.5" (without quotation marks)

check the package, install, done. don't worry, it doesn't seem to change the existing version of python2.6 (i don't think)

now gdesklets should be able to run. i couldn't find a single post that told me to do this and i looked for a while. then again, mabey i was looking in the wrong place. either way, every little bit helps, right? :KS

---

### Post by fontis on 2009-05-30
Thanks alot, that fix really worked!

---

### Post by holic86 on 2009-06-25
Thank you very much sir!

---

### Post by Dobbie03 on 2009-08-01
Cheers.  I was having the same problem.

---

### Post by diham on 2009-08-27
thanks a lot!!!

---

### Post by neogeek on 2009-09-18
Works ... thanks!

---

### Post by nephlim on 2009-12-14
I installed python2.5 then gdesklets and it did the trick.

thanks man

---

