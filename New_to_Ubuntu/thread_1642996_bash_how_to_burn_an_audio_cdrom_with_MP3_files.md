---
title: "bash: how to burn an audio cdrom with MP3 files?"
date: 2010-12-11
forum: New to Ubuntu
---

### Post by honeybear on 2010-12-11
under bash ?

---

### Post by TeoBigusGeekus on 2010-12-11
```
growisofs -Z /dev/scd0 -R -J /path/to/files/
```
Change scd0 to what applies to your system (scd1,sr0,sr1, etc.)

---

### Post by honeybear on 2010-12-11
> **TeoBigusGeekus said:**
> ```
growisofs -Z /dev/scd0 -R -J /path/to/files/
```
Change scd0 to what applies to your system (scd1,sr0,sr1, etc.)

but this will copy teh mp3 onto the cdrom, but not burn as audio format , right?


> 

# Copy then burn single audio tracks TAO:
cdda2wav -D 0,4,0 -B /tmp/prefix-of-music-files
The files will be written out as /tmp/prefix-of-music-files_01.inf /tmp/prefix-of-music-files_01.wav /tmp/prefix-of-music-files_02.inf ...

    * Linux 2.6 kernel: cdrecord -v speed=2 dev=ATA:1,0,0 -audio /tmp/prefix-of-music-files*.wav
    * Linux 2.4 kernel: cdrecord -v speed=2 dev=0,4,0 -audio /tmp/prefix-of-music-files*.wav

# Burn audio tracks DAO:
Copy to hard drive:
cdda2wav -D 0,4,0 -g -O wav -S 1 -v30 -P 0 -n 75 -B /tmp/CD/track-01.wav /tmp/CD/track-02.wav ...
Burn CD:

    * Linux 2.6 kernel: cdrecord dev=ATA:1,0,0 fs=4096k -v -useinfo speed=1 -dao -eject -pad -audio "/tmp/CD/track-01.wav" ...
    * Linux 2.4 kernel: cdrecord dev=0,4,0 fs=4096k -v -useinfo speed=1 -dao -eject -pad -audio "/tmp/CD/track-01.wav" ...



---

### Post by TeoBigusGeekus on 2010-12-11
Yes, you're right. I didn't read the title correctly.
See [this]("https://wiki.archlinux.org/index.php/Gapless_Audio_CD_Creation_from_MP3s") from Archwiki.

---

### Post by honeybear on 2010-12-11
> **TeoBigusGeekus said:**
> Yes, you're right. I didn't read the title correctly.
See [this]("https://wiki.archlinux.org/index.php/Gapless_Audio_CD_Creation_from_MP3s") from Archwiki.

```
 cdrecord -v -eject dev=/dev/sr0 -eject -pad -audio *.wav
```
shall work

but I do not know if it can burn and stop if not space and leave audio cdrom working

+ 

I am wondering if the command mp3 to wav is necessary before 

```

	for i in *.mp3; do 
		echo "Processing $i"	
		THEWAVFILE="`basename "$i" .mp3`".wav
		if [ ! -f "$THEWAVFILE" ] ; then 
			lame --decode "$i" "`basename "$i" .mp3`".wav
		fi
	done

```

---

