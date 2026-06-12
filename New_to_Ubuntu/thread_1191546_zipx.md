---
title: "zipx?"
date: 2009-06-19
forum: New to Ubuntu
---

### Post by vividia on 2009-06-19
I came across a compression format I'm unfamiliar with.  I can't extract it.  Is there a codec for this for Ubuntu?  I still run Intrepid.

---

### Post by Michael.Godawski on 2009-06-19
hi,
as far as I know it is a new format made for Win7. Windows-only so to speak.

---

### Post by andrew.46 on 2009-06-19
Hi vividia,

> **vividia said:**
> I came across a compression format I'm unfamiliar with.  I can't extract it.  Is there a codec for this for Ubuntu?  I still run Intrepid.

Unfortunately I have not come across any of these archives so I cannot test one but I believe that this is a newer compression format produced by Winzip in May 2009. Some details can be seen here: [Additional Compression Methods Specification]("http://www.winzip.com/comp_info.htm"). A quote:

> 
This document describes the file format that WinZip uses to create PPMd compressed, WavPack compressed and Jpeg compressed Zip files. The PPMd compression format was introduced in WinZip 10.0 Beta, released in August 2005. The WavPack compression format was introduced in WinZip 11.0 Beta, released in October 2006. The compressed Jpeg format was introduced in WinZip 12.0, released in September 2008. In WinZip 12.1, released in May of 2009, the Zipx file was introduced. The Zipx file is a Zip file that uses any of the aforementioned compression methods or the LZMA or bzip2 compression methods as documented in the Zip file appnote.txt specification.


Interesting to see if these can be accessed with Linux tools...

Andrew

---

### Post by vividia on 2009-06-24
> **andrew.46 said:**
> 

Interesting to see if these can be accessed with Linux tools...

Andrew

Guess I'll wait and see what happens.  Thanks for the info guys!

- Viv

---

### Post by jonobr on 2009-06-24
man.......... Just as I was getting used to Zip... This comes along......
Im getting old LOL

This was a useful thread. THanks all.........

---

### Post by martin.devlin on 2010-03-08
I was able to extract from a .zipx file by using wine and the Windows Zipx ZipX 1.61 Build 120 which I downloaded from here:
[http://www.brothersoft.com/zipx-download-81271.html](http://www.brothersoft.com/zipx-download-81271.html)

1. Download the zipx-setup.exe file
2. Using a terminal execute the windows installer using wine:
  wine zipx-setup.exe
3. Select OK for all the default options in the installer wizard.

I'm using wine version wine-1.1.38 on Ubuntu 9.04 

It works no problem - wine is a life saver! Though, does anyone know of a native program that can handle zipx?

- M

---

### Post by vividia on 2010-04-16
sweet!  I tried out what you did and it worked.

Thanks!

---

### Post by cknight on 2011-01-20
Didn't work for me, but I downloaded the trial version of winzip, used this via wine and it worked just fine.

---

### Post by Dr. Awesome on 2011-08-13
Same as Ck. Instead of "zipx-setup.exe" I had to use "jZipV1l.exe" so I don't know if it's just a completely different file I downloaded, but when I opened jZip it didn't have an option for zipx, just zip.

---

### Post by callmemahavir on 2012-04-17
It is a new compression format only supported by WinZip.

But you can find lot of information on this site...

[http://website.informer.com/visit?domain=zipxfile.com](http://website.informer.com/visit?domain=zipxfile.com)

As the site says latest version of 7zip also supports the format.

---

### Post by oldos2er on 2012-04-17
Closed, necromancy.

---

