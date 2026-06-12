---
title: "Since  10.10 upgrade no Windows"
date: 2010-10-22
forum: New to Ubuntu
---

### Post by ex-wirecutter on 2010-10-22
Since upgrading to Ubuntu 10.10 I find my Windows loader no longer works .If I scroll down to Windows XP , I briefly get the Windows startup screen and then after a few seconds the computer shuts down and restarts . Needless to say it all worked fine with Ubuntu 10.04 . I have tried the Windows recovery console and it reports that I have several non-recoverable files plus a missing or corrupt ntdlr amongst other things . I have also tried update-grub and all the other suggestions gleaned from this forum but my Windows OS seems to have gone .  Not a big Windows fan but would like to have it available if required . Apart from that Ubuntu 10.10 seems fine .

---

### Post by thunk77 on 2010-10-22
You probably need the windows disk to fix this

---

### Post by thunk77 on 2010-10-22
edit

---

### Post by thunk77 on 2010-10-22
edit again

---

### Post by ex-wirecutter on 2010-10-22
Thanks , but if you read my post I have already tried that.

---

### Post by ex-wirecutter on 2010-10-22
I know this is supposed to be impossible but just wondered if a non active Windows virus in my Linux partition has somehow invaded my Windows whilst the files were being shunted about during the upgrade mmmm .. no. Can't happen! Maybe it's a coincidental hard drive fault then.

---

### Post by Wild_Wes on 2010-10-22
Do you have them on separate hard drives? I went and bought an external hard drive and it hasn't invaded windows. Sorry, I forgot to say that I am using 10.10 also.

---

### Post by Paul820 on 2010-10-22
[http://www.computerhope.com/issues/ch000465.htm]("http://www.computerhope.com/issues/ch000465.htm")

If it repairs your mbr then you will need to redo grub2 as it will not recognise Ubuntu. Bit of a pain but hopefully you will get it going again.

EDIT: Scroll down until you see 'Recover Grub 2 via LiveCD'
[https://wiki.ubuntu.com/Grub2]("https://wiki.ubuntu.com/Grub2")

EDIT: You windows OS hasn't gone, it's still there.

---

### Post by ArgusVision on 2010-10-22
Do you have another PC with a working Windows install? (I know that sounds oxymoronic...) 
You can Boot to your Ubuntu live cd on the working PC. Copy the ntldr file to a usb drive. Then copy that file to your windows partition on the affected PC. If "ntldr missing" is your only error, that will fix it.

You ***may*** still have to run **fixmbr** like Paul suggested.

---

### Post by ArgusVision on 2010-10-22
As a general rule I don't accept files from people I don't know personally.

With that said, I'm attaching a working ntldr file that you can use if you don't have another PC to grab it off of. It's not actually a .tar file.
After you download it, right click on it and select rename. Remove the .tar extension. Then you can copy it to the windows drive.

You can see I have been a member since 2007, and can check my posts to see that I have never displayed any malicious tendencies.

---

### Post by Quackers on 2010-10-22
Quote
I have tried the Windows recovery console and it reports that I have several non-recoverable files plus a missing or corrupt ntdlr amongst other things . I have also tried update-grub and all the other suggestions gleaned from this forum but my Windows OS seems to have gone 

So you tried bootrec.exe /fixmbr or bootrec.exe /fixboot - sfc /scannow - any of them? 
If you've tried "all the other suggestions gleaned from this forum" where is the output from the boot info script?

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by ex-wirecutter on 2010-10-22
Many thanks for all replies , I am overwhelmed , will try all the suggestions but so far have come up against error messages of one sort or another every time. Will keep bashing away at it then if all else fails I'll ditch Windows which I rarely use but will enjoy the challenge of trying for a while at least. Not sure how to close this thread but please consider it done. Thanks again.

---

### Post by ArgusVision on 2010-10-22
Ok. Wish you the best.

---

### Post by ex-wirecutter on 2010-10-23
and finally... after hours of key bashing and many cups of coffee, reluctantly gave up and reinstalled my backup copy of Windows and Ubuntu Lucid 10.04 ... (side by side), normal service has been resumed .

---

### Post by sadaruwan12 on 2010-10-23
That's very good to hear please mark the thread as solved from the thread tools so we can move on.

Thank you.

---

