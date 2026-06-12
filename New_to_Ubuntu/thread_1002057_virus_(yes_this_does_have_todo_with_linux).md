---
title: "virus (yes this does have todo with linux)"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by metzy85 on 2008-12-04
Ok so i am repairing a virus on a computer for a friend and i have the 120gb hard drive in a enclosure and i tried to open it it windows with no avail either from the virus stopping me or dumb windows permissions. So i installed Linux and am able to open the drive but can not find any virus scanners for it. Any ideas about any of this? Or another way for me todo this?

---

### Post by Mothinator on 2008-12-04
Have you tried [clamAV]("http://www.clamav.net/")?

It is available in the Ubuntu repositories:
```
sudo apt-get install clamav
```

---

### Post by Michael.Godawski on 2008-12-04
If you are looking for virus scanners which work in linux try these:


[LIST]
[*] [http://www.avast.com/eng/avast-for-linux-workstation.html](http://www.avast.com/eng/avast-for-linux-workstation.html)
[*] [http://www.clamav.net/](http://www.clamav.net/)
[/LIST]

---

### Post by mbsullivan on 2008-12-04
> i tried to open it it windows with no avail either from the virus stopping me or dumb windows permissions. So i installed Linux and am able to open the drive but can not find any virus scanners for it.

So... does the infected disc boot to Windows, or Linux? Is it a Windows virus you're targeting, or a Linux one?

The way I read it, it sounds like you're trying to scan a Windows drive from Linux, no?

Anyway, this should be possible (as others have suggested) with ClamAV. The basic procedure would be:

(1) Install ClamAV
(2) Mount the offending harddrive (say, to /mnt/disk)
(3) Scan the disk:

```
clamscan -ri  --log=~/win_virus_log.log /mnt/disk/
```

This will scan all folders on the disk (-r for recursive), printing infected files to the terminal (-i) and logging the results to ~/win_virus_log.log.

Mike

---

### Post by ibuclaw on 2008-12-04
Took about twenty minutes digging round, but found these to add to Michael's small list:

[F-Prot AntiVirus]("http://www.f-prot.com/download/")

[McAfee AntiVirus & other]("https://secure.nai.com/apps/downloads/free_evaluations/default.asp?region=us&segment=enterprise")

[AVG AntiVirus]("http://free.avg.com/download?prd=afl#tba1")

[NIXory AntiSpyware]("http://nixory.sourceforge.net/")

[Avira Antivir]("http://www.free-av.com/en/download/download_servers.php")

[Avira Linux LiveCD/Rescue System]("http://www.free-av.com/en/tools/12/avira_antivir_rescue_system.html")

Though I wouldn't recommend downloading and installing them at random (unless you are in a LiveCD environment).

[EDIT]
If you install WINE, you could try/find out if any Windows-based Software will work too.

Regards
Iain

---

### Post by metzy85 on 2008-12-07
ok this has really helped. But i am not extremely cultured in ubuntu and linux in general. i download the DEB of the installer and install them by double click but where do i go to open the program itself i see no shortcuts or when i search the file system i see nothing i have tried both the avg and the avast ones?

---

### Post by newbee70 on 2008-12-07
> **metzy85 said:**
> ok this has really helped. But i am not extremely cultured in ubuntu and linux in general. i download the DEB of the installer and install them by double click but where do i go to open the program itself i see no shortcuts or when i search the file system i see nothing i have tried both the avg and the avast ones?

clamav should be in Applications/ system tools.

---

### Post by metzy85 on 2008-12-07
That CLam av is a weird program in my opinion i dont get how to update it or how to scan a entire hard drive.

---

### Post by dracayr on 2008-12-07
As you got the virus problem before you downloaded clamav, you probably won't need to update it. To scan a disk, execute ```
clamscan -ri  --log=~/win_virus_log.log /mnt/disk/
```, as mbsullivan already said

dracayr

---

### Post by sleepingdragon on 2008-12-07
Avast! or F-Prot would be my personal choices, though I find F-Prot to be faster. Both offer excellent scanning abilities. 

Mount the Win drive to something like /media/windows and call the following for F-Prot.

fpscan -t --adware --applications /media/windows

This will report only suspicious files, but also scans for adware and applications that may prove to be security risks.  There are plenty more option available in F-Prot, depending on how intensively you wish to scan - heuristics are also optional.

---

