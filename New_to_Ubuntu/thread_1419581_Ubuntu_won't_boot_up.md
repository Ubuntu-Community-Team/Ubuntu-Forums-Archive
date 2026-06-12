---
title: "Ubuntu won't boot up"
date: 2010-03-02
forum: New to Ubuntu
---

### Post by asharpham on 2010-03-02
I've obviously lost a file or have one or more corrupted files as I can no longer boot up into Ubuntu. I can run Ubuntu from the CD and then look at the drive which appears to be okay. But I have no idea what files are either missing or corrupted. I can see the file structure and view all the files inside folders, including hidden files, but don't know where to start looking for what's wrong.

Any ideas?

Alan.

---

### Post by NightwishFan on 2010-03-02
When booting, hold in shift until you get a menu. Choose rescue mode, which if it does not boot, will show you error messages. You could also check your installed ubuntu's logs under /var/log/

Perhaps copy syslog and kern.log and add them as attachments here.

---

### Post by asharpham on 2010-03-02
I haven't tried the shift thing yet but here are the 2 files you mentioned. Actually no they're not. The Attachment Manager says both are invalid files. Perhaps the files types are not acceptable.

---

### Post by blazemore on 2010-03-02
What actually happens when you try to boot up normally? Do you get an error message?

---

### Post by asharpham on 2010-03-02
I've now tried shift while booting but nothing happened. I just got the cursor blinking at the top left of a blank screen which is what I get if I don't do anything.

The only thing that works at the moment is the Ubuntu installation CD.

---

### Post by blazemore on 2010-03-02
> **asharpham said:**
> I've now tried shift while booting but nothing happened. I just got the cursor blinking at the top left of a blank screen which is what I get if I don't do anything.

The only thing that works at the moment is the Ubuntu installation CD.

While your cursor's blinking, if you hit Ctrl + Alt + F1 do you get a login prompt?

---

### Post by asharpham on 2010-03-03
No, nothing happens. The cursor just keeps blinking. In fact the only thing that gets rid of it is hitting the off switch on the computer. And I don't have to hold it down, just touch it once and the computer turns off.

---

### Post by Ozymandias_117 on 2010-03-03
It sounds like something is wrong with your MBR. Follow the steps [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") to reinstall grub.

---

### Post by asharpham on 2010-03-03
Thanks for that. It worked and I now have my gateway back. I can open Windows but I still get errors when I try to open Ubuntu. But one good thing is that I have found what appears to be a full backup of Ubuntu. I thought I had backed it up but couldn't find where. It was sitting on my Windows drive.

It appears to be only a couple of weeks old so my next question is, would you suggest that I format the USB stick and reinstall Ubuntu, then restore the backup?

The name of the file is [2010-02-21_14.26.28.802000.alan-laptop.ful]("file:///C:/2010-02-21_14.26.28.802000.alan-laptop.ful/") and there are several .inc files with similar names. I presume these are incremental updates to the backup.

Alan.

---

