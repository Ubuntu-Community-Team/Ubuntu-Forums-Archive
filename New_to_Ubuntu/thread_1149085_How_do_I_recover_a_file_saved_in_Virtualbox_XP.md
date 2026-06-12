---
title: "How do I recover a file saved in Virtualbox XP?"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by ii Candor ii on 2009-05-04
I have 9.04 JJ installed on a Dell PowerEdge 1800. The graphics are garbled and I've gone through the paces to fix it -- in short this bug is not fixable in my situation (yet).

I'm planning to reinstall, but I REALLY need to get a file first. I have booted 8.10 II and can explore the hard drive. The file was saved inside an XP virtual machine.

My question is, what is the default location of the C:\ drive in a Virtualbox installation -- how can I access the files I saved on the virtual machine?

---

### Post by ii Candor ii on 2009-05-04
Basically I'm just asking where the location of the C:\ drive would be in an XP virtual machine installed via Virtualbox.

---

### Post by y_garti on 2009-05-04
if i understand you've got a file inside a virtual xp that you want to move away?

if that is the case you can mount an operation system live CD(lets say ubuntu) and when the os booted up you can send it to you on the mail (the essayist way) or you can mount you host computer to your vm and copy direcly the file to there

---

### Post by y_garti on 2009-05-04
i don't use virtual-box so i don't know but in vmware he save the file in a file call vmdk so i guess there is something like that in virtual-box
but the best way to extract a file from a vm is to treat it like it was a physical computer (or to mount the drive to the host computer(if its posibole in virtualbox))

---

### Post by ii Candor ii on 2009-05-04
> **y_garti said:**
> if i understand you've got a file inside a virtual xp that you want to move away?

if that is the case you can mount an operation system live CD(lets say ubuntu) and when the os booted up you can send it to you on the mail (the essayist way) or you can mount you host computer to your vm and copy direcly the file to there

That's the idea. But I don't know the file path.

Also, the second idea I would do, but there is also a different but in 9.04 where you can't mount/view anything in "Places" if you have booted up Ubuntu with a disc in the drive. So I can't just live boot 9.04 and run the XP virtual machine. Does that make sense?

If you can tell me the file path for C:\ in the virtual machine that would be great!

---

### Post by y_garti on 2009-05-04
i don't think that i really understand what you need?
1 what is your host computer (ubuntu or xp) ?
2 is it working ?
3 what is you virtual computer (ubuntu or xp) ?
4 is the virtual os working ?
6 what you need is to copy some files from the virtual computer ?

---

### Post by ii Candor ii on 2009-05-04
> **y_garti said:**
> i don't think that i really understand what you need?
1 what is your host computer (ubuntu or xp) ?
2 is it working ?
3 what is you virtual computer (ubuntu or xp) ?
4 is the virtual os working ?
6 what you need is to copy some files from the virtual computer ?
Host computer is Ubuntu 9.04 - will not boot up - only in recovery mode

Virtual computer is XP Home

It's currently booted into Ubuntu 8.10 via Live CD so I'm accessing the 9.04 file system from the 8.10 live boot. Doe that make more sense?

Yes, I need to get a file from the virtual XP Home drive.

---

### Post by ii Candor ii on 2009-05-05
Bump.

---

### Post by Michaelg14 on 2009-05-05
Virtualbox keeps its data files in a hidden directory in the home folder.  The file is .VirtualBox and is probably OK. Your best bet will be to boot from a live CD go to yout home folder on your hard drive the one created with 9.04 select the view menu and check show hidden files.  Copy the .Virtualbox folder to some backup medium.  Restore 9.04, reinstall Virtualbox, replace the .Virtualbox file with the one you have on backup.  It sounds complicated and it is but it works, I have done it.

---

### Post by ii Candor ii on 2009-05-05
> **Michaelg14 said:**
> Virtualbox keeps its data files in a hidden directory in the home folder.  The file is .VirtualBox and is probably OK. Your best bet will be to boot from a live CD go to yout home folder on your hard drive the one created with 9.04 select the view menu and check show hidden files.  Copy the .Virtualbox folder to some backup medium.  Restore 9.04, reinstall Virtualbox, replace the .Virtualbox file with the one you have on backup.  It sounds complicated and it is but it works, I have done it.

Wow. That doesn't sound too terribly complicated. But it does sound like it will take a while to do.

Thank you very much!

---

