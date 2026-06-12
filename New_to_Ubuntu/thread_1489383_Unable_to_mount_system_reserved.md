---
title: "Unable to mount system reserved"
date: 2010-05-21
forum: New to Ubuntu
---

### Post by racie on 2010-05-21
Hello.  I'm running a dual-boot of Windows 7 and Ubuntu 10.04.  After an unexpected hang with my sleep mode in Windows 7, I am unable to view my Windows files from Ubuntu.  When I click "system reserved," I get a message that says, "Unable to mount System Reserved. Error creating moint point: No such file or directory."  I am really confused.  Why can't it mount?

---

### Post by Peter09 on 2010-05-21
I think when Windows fails as you describe it can leave the file system in a state where it is unwise for Ubuntu to mount it as it may cause corruption - so thats why its refusing to mount it. (I think this is correct)
 
Try rebooting into windows and shutting down properly.

---

### Post by racie on 2010-05-21
Thank you for your response.  I've tried this and it still doesn't work.  Perhaps there are some disk errors that I need to scan in Winodws.

---

### Post by racie on 2010-05-23
Strange... today I had time to run a defragmenter in Windows, but System Reserved still cannot mount.  I also tried plugging in my flip video camera in Ubuntu and I get an error saying that it can't mount also.  Are these issues related?  Any suggestions?

---

### Post by mbzn on 2010-05-23
My guess is that the camera was plugged in "when windows failed". A clean shut down used to resolve this in earlier versions of windows. do a disk check(not a defrag) and see what happens

---

### Post by racie on 2010-05-23
> **mbzn said:**
> My guess is that the camera was plugged in "when windows failed". A clean shut down used to resolve this in earlier versions of windows. do a disk check(not a defrag) and see what happens

A disk defrag of Windows???  I already did that, but I still cannot access Windows from Ubuntu (mount error).  Plus, I don't know how to do it in Ubuntu, nor do I think it needs it.

---

### Post by mbzn on 2010-05-23
in windows 7 you can go to the (sort of folder icon at the botom) my computer. go computer>local disk (C:). Right click that and say propeties then the tools tab and you should see a button "Check now"

See the Attachment...

---

### Post by racie on 2010-05-23
Oh, haha.  I need to learn to read.  Sorry about that.  :P  I'll post back with the results.

*edit*  It claims that no problems were found.

---

### Post by racie on 2010-05-24
Anyone have any ideas?

---

### Post by John Bean on 2010-05-24
Are you sure "System Reserved" is your W7 partition? Odd sort of name for a Windows partition.

---

### Post by racie on 2010-05-24
Yes.  It has been working perfectly up until several days ago.

---

### Post by John Bean on 2010-05-24
> **racie said:**
> Yes.  It has been working perfectly up until several days ago.

Ok. well I can't see how it can be a problem with Windows anyway since the error you quoted complains of being unable to create a mount point. Normally auto-mounted disks you click on in Nautilus will be mounted in a directory created "on the fly" in  /media, so the failure implies that /media has become inaccessible to FUSE for folder creation for whatever reason. Has anything been changed recently?

---

### Post by racie on 2010-05-24
Nothing's changed recently, other than usual issues with Windows.  I was assuming this problem was related to Windows because I installed Ubuntu through Wubi, so it is not on a dedicated partition.

---

### Post by John Bean on 2010-05-25
> **racie said:**
> Nothing's changed recently, other than usual issues with Windows.  I was assuming this problem was related to Windows because I installed Ubuntu through Wubi, so it is not on a dedicated partition.

Ah, I see. Perhaps you could have mentioned that a little sooner ;-)

I have zero experience of wubi installs I'm afraid so perhaps it is a Windows thing.

---

### Post by baddog144 on 2010-05-25
Only thing I could suggest would be running chkdsk on the drive... I don't have any idea why it wouldn't be working, and System Reserved is a funny name for a Windows partition, but if it works for you... *shrug*

---

### Post by racie on 2010-05-29
Well, the problem seems to have spontaneously resolved itself.  This has been quite strange.

---

### Post by GiladGressel on 2010-06-01
Bump

I am having the exact same problem.  There was zero problems with windows, I did NOT do a Wubi install.

I have dual booting Windows 7 and Lucid.

Running on an asus 1201n.

I was able to acces my windows 7 hd before , but now it cannot mount.  Neither can my flash drive either.

The only thing I did recently was install kde-  and then purge it. 

Any ideas?  I'd like to be able to mount my drives....

thanks!
-gilad

---

### Post by barrmulio on 2010-07-31
just a quick note if it helps someone - i installed via wubi, and it didn't create the automount folder '/media'
so go to terminal, type in:
sudo mkdir /media
sudo chmod 777 /media (not sure if 777 is the best combination, but it's working now)

---

### Post by soldier1st on 2010-08-03
why would you want to mount or open the system reserved partition? it contains the boot files and such for Windows 7 to start and other than that it has no use so why try?

---

