---
title: "Deleting Duplicate Music Files"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by gamergod131 on 2009-01-30
Hello.

I have recently copied my music library from my ipod classic to my home folder in order to transfer music from on hard drive to another before I wiped the old drive. I used amarok to add music to my ipod on opensuse, but I forgot to delete to old data. Therefore, when I add my music to library, I have multiple copies of the same songs. Is there a program that could scan my music folder and automatically delete the duplicate files?

---

### Post by porchrat on 2009-01-30
You're better off making a bash script to do this.

To do this we need details.  How exactly are the files arranged? and, if the files are all in the same directory what sort of names do the duplicates have that differentiate them from the originals?

EDIT: Unless of course the duplicates all have the same names as the originals, but are present in different directories, in which case this is easy because all you would have to do would be to copy everything into a single directory and those with the same filenames would overwrite.

---

### Post by blazemore on 2009-01-30
Install Songbird. There's an extension that can do just that. It will also look for broken files, or files with missing important tags.

---

### Post by hyper_ch on 2009-01-30
you could, just to be sure, md5 hash all mp3/flac/ogg/... files and then compare the hashes.

---

### Post by blazemore on 2009-01-30
This could work, if I learned enough shell scripting.
For now, I would definately reccomend Songbird with the Exorcist plugin.

---

### Post by gamergod131 on 2009-01-30
> **blazemore said:**
> This could work, if I learned enough shell scripting.
For now, I would definately reccomend Songbird with the Exorcist plugin.

Thanks for the tip and I will try songbird when I get home. I believe the files are all in one directory - /home/(my username)/Music/music.

---

### Post by hyper_ch on 2009-01-30
the script wouldn't be difficcult

find all (music files);

foreach (musicfile) do:
  md5sum
  write md5sum \tPath/filename to textfile
end;

open it in OOo and import it as csv with TAB separation and sort it accordingly or write a script that will check if there are two equal hashes.

---

### Post by DeRose on 2009-11-14
There was some duplicates songs on my library that cause repeated play of same songs, then i make a search on google to [delete songs duplicate]("http://www.duplicate-finder-pro.com/duplicate-mp3-finder.htm") then i found a software though google called duplicate finder that helps me to remove those duplicates, take a look at this tool.

Download Here :  [http://www.duplicate-finder-pro.com](http://www.duplicate-finder-pro.com)

---

### Post by sfxpt on 2009-11-14
> **DeRose said:**
> . . . then i found a software though google called duplicate finder that helps me to remove those duplicates, take a look at this tool.

Download Here :  [http://www.duplicate-finder-pro.com](http://www.duplicate-finder-pro.com)

If you'd prefer something from the OSS as oppose to a proprietary one, check this out:

[http://search.cpan.org/~suntong/File-FindSimilars-2.06/lib/File/FindSimilars.pm#DESCRIPTION](http://search.cpan.org/~suntong/File-FindSimilars-2.06/lib/File/FindSimilars.pm#DESCRIPTION)

the degree of calculation is merely    O(n^2 * m)  which is over thousands times faster than any existing file fingerprinting technology.

---

