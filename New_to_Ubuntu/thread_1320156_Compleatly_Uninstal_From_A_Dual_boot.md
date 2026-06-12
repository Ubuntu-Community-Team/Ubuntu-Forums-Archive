---
title: "Compleatly Uninstal From A Dual boot?"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by R3fr4cti0n on 2009-11-09
how do Remove Ubuntu From a laptop  dual booting vista and ubuntu 9.10 i know how to delete the partion but the GRUB thing i do not understand
thanks

---

### Post by wilee-nilee on 2009-11-09
Be very careful grub is the master boot program if you just remove ubuntu you will have to reinstall the MBR pointing to vista. If you don't get an answer here I would go to a MS forum or call MS tech to get the mbr set back to a Vista boot.

---

### Post by DGortze380 on 2009-11-09
> **R3fr4cti0n said:**
> how do Remove Ubuntu From a laptop  dual booting vista and ubuntu 9.10 i know how to delete the partion but the GRUB thing i do not understand
thanks

Delete the Ubuntu partition
Partition your new free space
Boot a Windows Install CD
Enter a Recovery Console and run fixmbr

---

### Post by nitrousjames on 2009-11-09
I have the same problem, i delete the partition with ubuntu using the partition manager in windows and also the grub thing, next wen i restart it says grub missing and i have to reinstall ubuntu ...  would appreciate the solution although iam never taking off ubuntu from my pc :D  loving ubuntu :D

---

### Post by JBAlaska on 2009-11-09
1. Put the Windows Vista or Windows 7 installation disc in the disc drive, and then start the computer.
2. Press a key when you are prompted.
3. Select a language, a time, a currency, a keyboard or an input method, and then click Next.
4. Click Repair your computer.
5. Click the operating system that you want to repair, and then click Next.
6. In the System Recovery Options dialog box, click Command Prompt.
7. Type Bootrec.exe /FixMbr and then press ENTER.
8. Reboot without the CD and Grub should be gone.

---

### Post by wilee-nilee on 2009-11-09
> **DGortze380 said:**
> Delete the Ubuntu partition
Partition your new free space
Boot a Windows Install CD
Enter a Recovery Console and run fixmbr

Yes that is the answer, and if you don't have a Vista disc if you can prove to MS that you are the owner and have a license you can get the disc from them for 30$. I suspect that this laptop has a recovery partition and came with no disc.

---

### Post by cariboo on 2009-11-09
If you are running Vista you can get a recovery iso [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/"). This is helpful if you doin't have an install disk.

---

### Post by snuggs on 2009-11-09
> **JBAlaska said:**
> 1. Put the Windows Vista or Windows 7 installation disc in the disc drive, and then start the computer.
2. Press a key when you are prompted.
3. Select a language, a time, a currency, a keyboard or an input method, and then click Next.
4. Click Repair your computer.
5. Click the operating system that you want to repair, and then click Next.
6. In the System Recovery Options dialog box, click Command Prompt.
7. Type Bootrec.exe /FixMbr and then press ENTER.
8. Reboot without the CD and Grub should be gone.

i really don't want to be a pain, just a beginner trying to learn and loving ubuntu, but i'm also getting a handle on the installing/dual booting/etc, by doing this - is there any way to damage the computer by doing so? i know things wear out, but i just don't want my "learning experience" to be a painful one. should i tread carefully when working on this? or can i always wipe the hard drive and reinstall everything from scratch?

---

### Post by DGortze380 on 2009-11-09
> **snuggs said:**
> or can i always wipe the hard drive and reinstall everything from scratch?

That's a little excessive, but you could.

---

### Post by yanceypd on 2009-11-09
If you can get the utility cariboo907 suggested, you can remove partions from Vista in cumputer manager for storage devices. Just get the Master boot record fixed in Vista first.

---

