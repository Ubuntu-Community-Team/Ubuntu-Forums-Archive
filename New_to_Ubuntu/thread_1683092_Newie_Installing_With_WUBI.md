---
title: "Newie Installing With WUBI"
date: 2011-02-07
forum: New to Ubuntu
---

### Post by garywayneyoung on 2011-02-07
Hello,

I am a complete newbie to Ubuntu. I successfully installed Ubuntu online  using WUBI from within Windows 7.  I still want to be able to read and write files from my windows system from within Ubuntu.  I see no way to access my windows files from within Ubuntu.  Ideas?

Many thanks in advance.

---

### Post by electroken on 2011-02-07
If you go to the upper left top of the screen you will see (I think this is correct but i am pretty new at this too) a entry called places. Click on that and go down to computer I think and click on that and it will start to show all your drives. if you click on a drive (highlight it) you can get the option to mount the drive and that is what you choose to do, then you will be able to read you windows disk. 
Remember that if you boot up in windows at some point (given that you are dual booting this computer) your linux files and partitions will not be seen by windows so be careful not to overwrite your linux files or format the drive or partition it etc.

---

### Post by beew on 2011-02-07
I don't know about Wubi, but if you have a real dual boot (on a separate partition) or if you install Ubuntu in an external hard drive and boot into it you would have no problem accessing Windows files (Windows however cannot access Linux)  Wubi is basically a Windows program living in a Windows folder, I wouldn't be surprised if it is limited in many ways. IMHO if you truly want to try Ubuntu you would do better either dual booting or make a portable Ubuntu installation in an external hard drive instead of WUBI.

---

### Post by jmszr on 2011-02-07
garywayneyoung,

Here are the relevant passages from the WubiGuide: [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide) :
 
How do I access the Windows drives?

The Windows partition where you installed Wubi is available as /host within Ubuntu (Places > Computer > File System > Host) All the other partitions will be available under Places > Removable Media

How can I access the Wubi files from Windows?
There are a few Windows applications that can mount ext2-based file systems. See for instance:

      [http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)
    
      [http://www.fs-driver.org/](http://www.fs-driver.org/)
    
      [http://ext2read.sf.net](http://ext2read.sf.net) (has ext4 support) 

The relevant Wubi files you need to access are located under C:\ubuntu\disks\ 

Hope that helps.

---

