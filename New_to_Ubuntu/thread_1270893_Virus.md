---
title: "Virus"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by pcconrad on 2009-09-20
Hello
I scan KlamAV my framework and found virus and i can't remove them.
/lib/linux-restricted-modules/26.24-24-generic/fglrx/libfglrx_ip.a.aGCC4
/lib/linux-restricted-modules/26.24-24-generic/fglrx/libfglrx_ip.a.aGCC4
/usr/share/wine/gecko/wine_gecko-1.0.0-x86.cab
/usr/share/wine/gecko/wine_gecko-1.0.0-x86.cab
/usr/src/linux-2.6.30/arch/x86/boot/compressed/vmlinux.bin
/usr/src/linux-2.6.30/arch/x86/boot/compressed/vmlinux.bin
/usr/src/linux-2.6.30/arch/x86/boot/compressed/vmlinux.bin.all
/usr/src/linux-2.6.30/arch/x86/boot/compressed/vmlinux.bin.all
/usr/src/linux-2.6.30/arch/x86/boot/compressed/vmlinux.bin.gz
/usr/src/linux-2.6.30/arch/x86/boot/compressed/vmlinux.bin.gz
What can i do?? And upgrade system always on and whant upgradr antyvirus.

---

### Post by NoaHall on 2009-09-20
Those aren't viruses, and you aren't infected. Stop trying to remove them, you'll destroy Linux.

---

### Post by Liolikas on 2009-09-20
Reinstall video drivers download them from trustable source like ubuntu.com...at.com etc. if still virus in /lib... so 100% fake.

If in this way cleaned first so post more.

---

### Post by FreewheelinFrank on 2009-09-20
> **NoaHall said:**
> Those aren't viruses, and you aren't infected. Stop trying to remove them, you'll destroy Linux.

^This.

Only scan /home.

Do *not* scan as root. (sudo)

---

### Post by pcconrad on 2009-09-20
I remove video drivers and when start system i have info some server X is runing on youur screen choose other now i doing scan

---

### Post by Liolikas on 2009-09-20
Remove not interesting reinstall may confirm something.
You see that AV calls your video drivers virus. Mistake of some kind or you downloaded your video drivers from: uzukukh0rz.ddn.tk

---

### Post by NoaHall on 2009-09-20
I told you NOT to remove them. Nice job, you've ruined your Linux. 
Do NOT mess with the vital files. They were not infected, the reason why they came up is because the files are either too big to scan, or because they are what Windows considers unsafe.. This is what clamav does. There's no risk from viruses on Linux.

---

### Post by Liolikas on 2009-09-20
> **NoaHall said:**
> I told you NOT to remove them. Nice job, you've ruined your Linux. 
Do NOT mess with the vital files. They were not infected, the reason why they came up is because the files are either too big to scan, or because they are what Windows considers unsafe.. This is what clamav does. There's no risk from viruses on Linux.
Calm down man. He removed he will reinstall. No problem. 

There is no risk from viruses on Linux, but it is in this way because Linux users and most important Linux devs take very serious countermeasures to all possible treats not just "that green shield near clock means I am safe". Not because other reasons.

---

### Post by pcconrad on 2009-09-20
finsh scan but still have that:
/usr/src/linux-2.6.30/arch/x86/boot/compressed/vmlinux.bin
/usr/src/linux-2.6.30/arch/x86/boot/compressed/vmlinux.bin
/usr/src/linux-2.6.30/arch/x86/boot/compressed/vmlinux.bin.all
/usr/src/linux-2.6.30/arch/x86/boot/compressed/vmlinux.bin.all
/usr/src/linux-2.6.30/arch/x86/boot/compressed/vmlinux.bin.gz
/usr/src/linux-2.6.30/arch/x86/boot/compressed/vmlinux.bin.gz

---

### Post by NoaHall on 2009-09-20
Listen to what I am saying!

THEY ARE NOT INFECTED!

Stop scanning outside of your /home/ !
Do you want to destroy your system!??!?

---

### Post by YoungTechie on 2009-09-20
I don't even use linux and even I can tell those are system files.

---

### Post by Sidewinder1 on 2009-09-20
Talk about advice falling on deaf ears...
{Sigh...}
I'll try; No real need to scan anything in linux; if you must, scan /home, external hard disk drives and ntfs or fat32 partitions. Don't delete system files!

---

### Post by sunchiqua on 2009-09-20
Just curious .. why Linux needs an anti-virus ( clam ) if it works against itself ? I mean, how can an anti-virus tell you that the kernel image ( more over, which comes from trusted sources ) is a virus ? :-s

---

### Post by NoaHall on 2009-09-20
It's probably not saying that to him, it's probably saying that it can't scan them because they are too big/wrong format/no permission.

---

