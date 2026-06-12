---
title: "zip.exe how can download with ubuntu"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by chanaka.rupasinghe on 2010-01-03
I have trying to down load following dictionary. But Can't do it. Pls help me 

Archive:  /home/chanaka/Downloads/madura.exe
[/home/chanaka/Downloads/madura.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/chanaka/Downloads/madura.exe or
          /home/chanaka/Downloads/madura.exe.zip, and cannot find /home/chanaka/Downloads/madura.exe.ZIP, period.

---

### Post by Methuselah on 2010-01-03
Oops...dp

---

### Post by Methuselah on 2010-01-03
This is an executable file intended for windows.
If you must you can try to open it with wine.

sudo apt-get install wine

I don't know if there are better options other than to use windows to open it.

---

### Post by arochester on 2010-01-03
As it says above zip and exe are for Windows. You should be able to download it - but you will probably not be able to install it on a Linux computer.

Where have you tried to download it from?

Do you want a Sinhalese dictionary for Linux? e.g [http://nmlaxaman.blogspot.com/2009/01/dictionary-for-english-sinhala-and.html](http://nmlaxaman.blogspot.com/2009/01/dictionary-for-english-sinhala-and.html)

---

### Post by scrooge_74 on 2010-01-03
Why are you trying to download a .exe file? Don't you know that is bad? Besides it wont run in linux (thank the coders for that).

---

### Post by gdonwallace on 2010-01-03
If you are needing to install a compression program that will read .zip files, I would suggest 7zip.  It reads .zip files and many other formats as well.  You can install 7zip from the Software Center.

As stated above, .exe files are intended for windows machines, and cannot be run on linux unless you have Wine or Crossover for Linux installed.  Both of these "create" a windows environment that will run windows program natively.  Although not all windows programs will run reliably all the time.

good luck.

---

### Post by lol768 on 2010-01-03
The file you are trying to open with the archive manager looks like a windows executable file. You could try WINE, it might be able to run the program.

---

### Post by oldos2er on 2010-01-03
> **arochester said:**
> As it says above zip and exe are for Windows. 

*.exe's are Windows' executables, but zip is a multi-platform (including *nix) compression system.

---

