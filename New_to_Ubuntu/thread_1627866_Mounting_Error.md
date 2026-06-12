---
title: "Mounting Error"
date: 2010-11-21
forum: New to Ubuntu
---

### Post by schwaigern on 2010-11-21
Greetings Community,

I am having troubles trying to mount an .iso file. I have tried it through the terminal, Furius and Gmount. All have come up with the same error:

An error occured
 wrong fs type, bad option, bad superblock on /dev/loop0,       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Since I'm new to Ubuntu, I haven't a clue what that means...


Thank you,
schwaiger

---

### Post by lmarmisa on 2010-11-21
Maybe you could post the commands your are using.

Anyway, you could try this command:

```

sudo mount yourfile.iso /mnt -t iso9660 -o loop

```

---

### Post by schwaigern on 2010-11-21
> **lmarmisa said:**
> Maybe you could post the commands your are using.

Anyway, you could try this command:

```

sudo mount yourfile.iso /mnt -t iso9660 -o loop

```
I tried that and got the same error code:

mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

My mistake, thought there was only one kind of command for everything.

I used:

sudo mkdir /media/isoimage
sudo modprobe loop
sudo mount YOURFILE.iso /media/iso/ -t iso9660 -o loop


schwaigern

---

### Post by lmarmisa on 2010-11-21
Maybe your iso file is not correct.

Did you download this file?. Is the md5 of the file available in order to check its integrity?.

---

### Post by apollothethird on 2010-11-21
> **schwaigern said:**
> I tried that and got the same error code:

mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

My mistake, thought there was only one kind of command for everything.

I used:

sudo mkdir /media/isoimage
sudo modprobe loop
sudo mount YOURFILE.iso /media/iso/ -t iso9660 -o loop


schwaigern

You're getting that error because you have a corrupted ISO file.  You'll have to go to your source and get another copy.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by schwaigern on 2010-11-21
Yes, I downloaded the file. What is an md5 file? I'm pretty sure the integrity is okay because the download displayed the same amount of memory as the files that i downloaded have.

I also tried this:
$ su -
# mkdir -p /mnt/disk
# mount -o loop disk1.iso /mnt/disk
# cd /mnt/disk
# ls -l

It didn't give me an error, but it still didn't mount the file...

---

### Post by schwaigern on 2010-11-21
Alright. I'll try downloading it again, although I'd hate to because my internet is extremely slow at the moment.

Thank you for your help.

---

### Post by lmarmisa on 2010-11-21
[MD5]("http://en.wikipedia.org/wiki/MD5") is a method used for checking the integrity of a file. Sometimes the files are corrupted during the download process.

---

### Post by lmarmisa on 2010-11-21
Do not overwrite your file if you download it again. So you will be able to check if both files are identical.

Could you post the URL of the ISO file?.

---

### Post by schwaigern on 2010-11-21
I believe this is correct. I do not remember where I got the ISO from, but I know where to get on that is intact. I just hope it works then.

Thank you all for your help!

schwaigern

---

### Post by apollothethird on 2010-11-21
> **schwaigern said:**
> Alright. I'll try downloading it again, although I'd hate to because my internet is extremely slow at the moment.

Thank you for your help.

If the file is extremely huge, you can quickly download a small ISO such as this 11 meg Linux boot sample ( [http://distro.ibiblio.org/pub/linux/distributions/tinycorelinux/3.x/release/tinycore_3.2.iso](http://distro.ibiblio.org/pub/linux/distributions/tinycorelinux/3.x/release/tinycore_3.2.iso) ) and test mounting it.  This is a quick method of verifying your iso mounting command is working.

It might save you some download time in duplicating a tedious download where the ISO file isn't the culprit.

You should also look for a integrety check file (such as the md5.txt file suggested by  Inmarmisa.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by lmarmisa on 2010-11-22
Good idea, apollothethird. +1

Only a comment. If you check the link

[http://distro.ibiblio.org/pub/linux/distributions/tinycorelinux/3.x/release/](http://distro.ibiblio.org/pub/linux/distributions/tinycorelinux/3.x/release/)

you can find not only the file tinycore_3.2.iso but also the file tinycore_3.2.iso.md5.txt with the md5 fingerprint of the file.

You can calculate the md5 of a file running this command:

```

md5sum yourfile

```

---

