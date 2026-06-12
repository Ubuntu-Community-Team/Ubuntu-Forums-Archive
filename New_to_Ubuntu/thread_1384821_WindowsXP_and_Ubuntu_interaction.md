---
title: "WindowsXP and Ubuntu interaction"
date: 2010-01-18
forum: New to Ubuntu
---

### Post by oingk on 2010-01-18
Hi, I dual boot Ubuntu and Windows XP (each on a different partition) and I have a couple of questions: 

1) From information I find it seems that Windows XP is not the safest OS in regards to its vulnerability for being "compromised". So could I just save all my documents on my Linux and just run Windows for the few programs that don't work with Linux? Or would a "compromisation" of my WinXP possibly mean a compromisation of my Linux? I mean if one can (program or human) can manage to access windows, could they also move into the other partition where Linux resides? 

2) Is there a program that can help me communicate my two partitions, eg for sending documents from windows to linux, so far as this would be a safe thing to do (I mean would such a thing be safe to do)?

---

### Post by warfacegod on 2010-01-18
> **oingk said:**
> Hi, I dual boot Ubuntu and Windows XP (each on a different partition) and I have a couple of questions: 

1) From information I find it seems that Windows XP is not the safest OS in regards to its vulnerability for being "compromised". So could I just save all my documents on my Linux and just run Windows for the few programs that don't work with Linux? Or would a "compromisation" of my WinXP possibly mean a compromisation of my Linux? I mean if one can (program or human) can manage to access windows, could they also move into the other partition where Linux resides? 

2) Is there a program that can help me communicate my two partitions, eg for sending documents from windows to linux, so far as this would be a safe thing to do (I mean would such a thing be safe to do)?

I would say the chances are slim that you will Have Windows hacked if you are careful using it. Windows can't read an ext partition. So the cahnces of Window being hacked and then your Linux install through it almost nil. Also, because Windows can't read Linux filesystems, if you created a document in Windows you would then need to boot into Linux to move it to your folder.

What Windows programs are you using that don't work in Linux?

---

### Post by blackened on 2010-01-18
1) While it's theoretically possible that your Linux installation could be compromised from your Windows installation, it is highly unlikely. Windows, without third party software, can neither read nor write to any of the standard Linux filesystem types (ext2, ext3, ext4, ReiserFS, XFS, JFS, etc.). Especially in the case of ReiserFS, the Windows software rfstool just allows read-only access. While this doesn't eliminate the possibility of your installation being compromised, it does add just another level of difficulty to the process. But, as always, where there's a will there's a way.

2) You have two main options:

a) Use a network-based solution like dropbox or UbuntuOne to synchronize your files between installations, or

b) Create a partition using a filesystem that both operating systems can read out of the box (FAT32 being the simplest).

---

### Post by oingk on 2010-01-18
thanks,
ok so is there a way from Linux to grub a document from the windows partition?

programs I use that I don't think can be run in linux include some silly programs like ChaosPro (that lets use generate fractals, very good, is there an alternative for linux?) and one called Fractal Time that is very old and I think can only be run on MSDOS.

---

### Post by oingk on 2010-01-18
> **blackened said:**
> 1) While it's theoretically possible that your Linux installation could be compromised from your Windows installation, it is highly unlikely. Windows, without third party software, can neither read nor write to any of the standard Linux filesystem types (ext2, ext3, ext4, ReiserFS, XFS, JFS, etc.). Especially in the case of ReiserFS, the Windows software rfstool just allows read-only access. While this doesn't eliminate the possibility of your installation being compromised, it does add just another level of difficulty to the process. But, as always, where there's a will there's a way.

2) You have two main options:

a) Use a network-based solution like dropbox or UbuntuOne to synchronize your files between installations, or

b) Create a partition using a filesystem that both operating systems can read out of the box (FAT32 being the simplest).



1) I didn't understand everything you said, but what I think you said is that its quite difficult for this to happen. (I'm not using any specific 3rd party software that I know of).

2) hmm. ok I'll search around for this. thanks

---

### Post by warfacegod on 2010-01-18
I love fractals! There are fractal generators for linux, yes. Try Xaos. Doesn't seems very advanced to me but I know almost nothing about using fractal software.

Try DOSBox and see if Fractal Time will run with it.

---

### Post by oingk on 2010-01-18
warfacegod, thanks both your suggestions are good

---

### Post by adam814 on 2010-01-18
Maybe I'm missing something here, but why not mount your Windows volume in Linux?  That way you could use your Windows partition (mostly) like any other folder on your Linux install.

To do that you would just go to System > Administration > NTFS Configuration Tool and set it up in the GUI.

---

### Post by oingk on 2010-01-18
adam, thanks I didn't know this was possible.

I will consider that too.

---

### Post by blackened on 2010-01-18
> **adam814 said:**
> Maybe I'm missing something here, but why not mount your Windows volume in Linux?  That way you could use your Windows partition (mostly) like any other folder on your Linux install.

To do that you would just go to System > Administration > NTFS Configuration Tool and set it up in the GUI.

While this is completely worthwhile from the Linux>Windows standpoint, it won't help you if you need to access something on your Linux install from within Windows. Hence my suggestion for a common partition that both can read. Granted you could always use ext2fs to access files on the Linux side of things, but from what I've read ext2fs's ext4 (the default filesystem under 9.04+) support is still in its early stages and still only supports aspects common between ext4 and ext2.

---

### Post by PenguinInside on 2010-01-19
> **adam814 said:**
> Maybe I'm missing something here, but why not mount your Windows volume in Linux?  That way you could use your Windows partition (mostly) like any other folder on your Linux install.

To do that you would just go to System > Administration > NTFS Configuration Tool and set it up in the GUI.

Did you install some special package that puts "NTFS Configuration Tool" in the Administration menu? I haven't had that in any of my default Karmic installs.

---

### Post by adam814 on 2010-01-19
> **PenguinInside said:**
> Did you install some special package that puts "NTFS Configuration Tool" in the Administration menu? I haven't had that in any of my default Karmic installs.

Now that you mention it it might not be installed by default as I upgraded from Jaunty and I might have installed it then.  The package is "ntfs-config".

---

