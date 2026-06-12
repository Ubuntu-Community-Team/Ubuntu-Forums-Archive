---
title: "Major OOPS!"
date: 2010-02-13
forum: New to Ubuntu
---

### Post by bgamble7 on 2010-02-13
So I deleted my Ubuntu partition because I haven't been using it much lately and I needed the space on my laptop.  Now I have a GRUB error 22 and I can't get the darn thing to boot.

On the advice of one of the IT guys on my ship I have tried to boot to a Win XP disk (the original OS was Vista)  and with that I get a blue screen of death as soon as it tries to boot into windows.  What I do have is the recovery portion of the HD, but no way to access it because GRUB is preventing it.

The major dilemma is that I am on a ship in the middle of the eastern Mediterranean.  I have no  recovery disks, I have no Ubuntu Disk, and I am at the mercy of very slow download speeds.  It appears that I am up the proverbial creek with out a paddle.

Does anyone out there have any sage advice for me?

---

### Post by Shpongle on 2010-02-13
have you got any medium to boot from ? ie cd, usb key, ipod ?

---

### Post by bgamble7 on 2010-02-13
I have all three.

---

### Post by Shpongle on 2010-02-13
then i suggest use a torrent to get an iso , maybe a light weight one like crunchbang or something , and burn it to cd and boot and reinstall an os , or try reinstall grub , and youll have a live cd at least you can use that if you wanna wait till you get back

---

### Post by bgamble7 on 2010-02-13
Only issue with that is that the gubment frowns on torrent stuff.   I might be able to con one of the IT guys into doing it for me though.  

Where does GRUB end up at? Without the HD installed it still gives me the same error when if I don't roger up to booting form the cd.

Are there any small programs out there that are bootable that I can use to remove it?

---

### Post by weichimaster on 2010-02-13
You can try installing lilo as boot manager. This will re-create the Windows MBR.

1) Boot from live Ubuntu cd
2) Type the following in at a terminal:
```

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr  ##replace /dev/sda with the disk you want to reset the mbr of
```

---

### Post by Shpongle on 2010-02-13
these torrents are legal , its allowed under the gpl . also you could just directly download but it would take longer , well i find it does. you can probably fix grub just by editing some config files as it most likely messed up the boot order , but iv no idea where to start with that , maybe some others can help

---

### Post by ajgreeny on 2010-02-13
Download and burn Supergrub live CD as an image, and you can restore your windows MBR with that.  Surely that will not go against any of your rules.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by bgamble7 on 2010-02-14
DillByrne,
     It wasn't the legality of the actual files being downloaded or the act of downloading...Let me clarify a bit.  I am on a US Navy ship at sea in the eastern Mediterranean.  I am at the mercy of really slow download speeds and applications that I can install on the ships system.  The fact that I am even downloading files to move to my laptop might even be a bit questionable in the eyes of those that govern our network.

ajgreeny,
     Super GRUB Live worked like a champ!  I am back up and running.

I am now looking forward to getting off the ship in our next port so I can download a copy of the latest iteration of Ubuntu.  This instance, and the fact that the various windows install disks (4 of them) and the 2 different recovery disc sets that I tried to no avail have left me a bit underwelmed with good ol' M$.  I think I will be giving Linux another shot.

Thanks again for the help.

---

### Post by sandyd on 2010-02-14
> **bgamble7 said:**
> DillByrne,
**     It wasn't the legality of the actual files being downloaded or the act of downloading...Let me clarify a bit.  I am on a US Navy ship at sea in the eastern Mediterranean.  I am at the mercy of really slow download speeds and applications that I can install on the ships system.  The fact that I am even downloading files to move to my laptop might even be a bit questionable in the eyes of those that govern our network.**

ajgreeny,
     Super GRUB Live worked like a champ!  I am back up and running.

I am now looking forward to getting off the ship in our next port so I can download a copy of the latest iteration of Ubuntu.  This instance, and the fact that the various windows install disks (4 of them) and the 2 different recovery disc sets that I tried to no avail have left me a bit underwelmed with good ol' M$.  I think I will be giving Linux another shot.

Thanks again for the help.

why should they be questionable?
the U.S. uses linux in its weapons systems. and probably on the weapons systems of the ship your on too.

---

### Post by falconindy on 2010-02-14
> why should they be questionable?
the U.S. uses linux in its weapons systems. and probably on the weapons systems of the ship your on too.
It's not a matter of the operating system used. I'm quite sure it's an issue of exposing a government laptop to the Internet in such a way that could conceivably pose an issue of leaking information from the ship's internal network (and possibly beyond).

More importantly: You do not question your superiors when in the military.

P.S. the military implications of this thread + the title gave me a good chuckle. Watch out for General Failure.

---

### Post by bgamble7 on 2010-02-14
Way off topic here, but did you happen to hear in the news a few months back about a US warship discharging a few rounds into Poland?

---

### Post by sailthesea on 2010-02-14
Ramage?

---

### Post by bgamble7 on 2010-02-14
I can neither confirm nor deny my being stationed on that ship...  Just sayin.

---

### Post by sailthesea on 2010-02-14
> **bgamble7 said:**
> I can neither confirm nor deny my being stationed on that ship...  Just sayin.

Of course not;)
Have good watch

---

