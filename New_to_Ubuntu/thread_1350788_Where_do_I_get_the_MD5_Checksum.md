---
title: "Where do I get the MD5 Checksum?"
date: 2009-12-09
forum: New to Ubuntu
---

### Post by kevinwmiller on 2009-12-09
To see if an iso's been downloaded correctly.

---

### Post by sisco311 on 2009-12-09
[http://releases.ubuntu.com/]("http://releases.ubuntu.com/")

---

### Post by kevinwmiller on 2009-12-09
Um, I mean the software to check a burned iso?  I didn't see it there, just past releases.

My apologies, maybe I'm stating it wrong.

---

### Post by techstop on 2009-12-09
> **kevinwmiller said:**
> Um, I mean the software to check a burned iso?  I didn't see it there, just past releases.

My apologies, maybe I'm stating it wrong.

It was only two clicks away;

[http://releases.ubuntu.com/9.10/MD5SUMS](http://releases.ubuntu.com/9.10/MD5SUMS)

If you've downloaded the file in linux, you can run the following command;

```
md5sum download.iso
```

...where download.iso is the name of the file you've downloaded. 

If you're using Windows instead, a program like hashcalc can be used.

---

### Post by sisco311 on 2009-12-09
[uhelp]community/HowToMD5SUM[/uhelp]

---

### Post by CaptainMark on 2009-12-09
its pre installed on ubuntu run in the terminal ```
md5sum /path_to_file
```

---

### Post by kevinwmiller on 2009-12-09
So, md5sum PCBSD7.1.1-x86-DVD.iso 

?

I ran it, it said that there was no such file or directory.

---

### Post by techstop on 2009-12-09
> **kevinwmiller said:**
> So, md5sum PCBSD7.1.1-x86-DVD.iso 

?

I ran it, it said that there was no such file or directory.

You can either specify the full path, or run the command from the directory that contains the file you want to calculate the hash on. See also;

```
man md5sum
```

---

### Post by kevinwmiller on 2009-12-09
Sounds good, but I'm not very experienced with the command line yet, so I wouldn't know how to specify everything.  It's in my download folder.

---

### Post by sisco311 on 2009-12-09
> **kevinwmiller said:**
> Sounds good, but I'm not very experienced with the command line yet, so I wouldn't know how to specify everything.  It's in my download folder.

Just type md5sum, type a space and drag the iso image in the terminal window then press Enter.

---

### Post by kevinwmiller on 2009-12-09
Oh, excellent.  It worked.  Thanks Sisco.  You rock!

---

### Post by fancypiper on 2009-12-09
[Mark Your Thread as [SOLVED] After Getting Your Answer](http://ubuntuforums.org/showpost.php?p=4527051&postcount=6)

---

### Post by kevinwmiller on 2009-12-09
And the Checksum has to match perfectly?  According to that method, NONE of my downloaded iso images downloaded correctly.

How is that?  Also, would surfing the web during download contribute to the download of an iso being corrupted?

---

### Post by fancypiper on 2009-12-09
Yes, it has to match exactly.  Surfing shouldn't affect the download.

If you download via bittorrent, you are more likely to get a good download.

---

### Post by kevinwmiller on 2009-12-09
I can do bit torrent, but would they list a Checksum?

I'll mark the thread solved here in a minute, I just want to make sure I understand all of this correctly. :)

---

### Post by sisco311 on 2009-12-09
> **kevinwmiller said:**
> I can do bit torrent, but would they list a Checksum?

I'll mark the thread solved here in a minute, I just want to make sure I understand all of this correctly. :)

The checksum will be the same, since you download the same iso file.

Also you should be able to [fix a corrupted iso images with invalid md5 checksum using Bittorrent]("http://www.zyxware.com/articles/591/fix-corrupted-iso-images-with-invalid-md5-checksum-using-bittorrent")

---

### Post by fancypiper on 2009-12-09
Bittorrent does the checksum and re-downloads corrupted packets as it downloads, but the checksums should be the same either way.

---

