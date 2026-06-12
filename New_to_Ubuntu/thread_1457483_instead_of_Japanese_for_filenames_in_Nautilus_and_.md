---
title: "??? instead of Japanese for filenames in Nautilus and Terminal"
date: 2010-04-18
forum: New to Ubuntu
---

### Post by lwvmobile on 2010-04-18
Hi guys, just installed 9.10, after deciding to revisit Ubuntu again from a long hiatus.

I have a lot of files which have Japanese language file names, and I remember in the past that the names would show up instead of the ??? question marks or the unicode garbage, but all I get is ??? instead of the actual file names, which makes it about impossible to navigate these folders.

I have already tried going to Administration>Language Support and installing Japanese as an additional language, including Translations, Input Methods, and Extra Fonts but still seeing just ??? instead of the actual Japanese.

Also thought I would browse the Synaptic Package Manager looking for Japanese, assuming I just needed to find a Japanese font, but there was a ton of packages there, didn't want to waste a lot of time trying them out.

Any ideas why I get ??? instead of the actual kana and kanji?

I seem to remember in older version of Ubuntu that I didn't have to do anything after install, it just showed up when I browsed those folders.

---

### Post by Jon Monreal on 2010-04-18
Are these files on an NTFS or FAT32 partition?

It's working for me on XFS, but I've heard of problems with some character sets on NTFS partitions.

If not, we can look into other possibilities.

---

### Post by Paqman on 2010-04-18
Where are the files located, and how are you accessing them?

If you're mounting the location the files are stored in through an entry in your /etc/fstab file, then make sure you've specified utf8 in your mount options.

---

