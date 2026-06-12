---
title: "programs better than wget?"
date: 2007-01-30
forum: Networking &amp; Wireless
---

### Post by heloOO on 2007-01-30
I have a text file that contains 1000 working http addresses (e.g http .../xx.txt). I use wget and it reads the text file, download every .txt one by one. However this is quite linear, are there ways to download multiple files ( read and download from a few http add at one go) ?

---

### Post by kebes on 2007-01-30
The commandline program "curl" supports syntax for downloading a sequence of files. However they are still downloaded serially, so if it's download time you're trying to avoid, this doesn't help.

I guess another option would be to write a script that grabs 5-10 of the addresses at a time, and launches a bunch of instances of "wget". In a script you can launch a program into the background using "&", so something like:

wget [http://wherever/file1.txt](http://wherever/file1.txt) &
wget [http://wherever/file2.txt](http://wherever/file2.txt) &
wget [http://wherever/file3.txt](http://wherever/file3.txt) &

Would start three instances of "wget" in a row, with all of them being sent into the background, so that the next one starts without waiting for the last one to finish. Of course you'll have to be careful not to launch an unlimited number of instances, which would seize your net connection!


Still I'm not sure if this will improve download times versus a serial transfer. It depends where the bottleneck in downloading is.

---

### Post by apoth on 2007-01-30
The most crude way would be to split the file into X pieces and run wget, or whatever reads the URLs in and calls wget, X times. A more advanced way would be to write a threaded program.

I don't know if there are any *nix command line tools or options on wget to solve the problem, but other than that I'm sure some scripting language could provide a small, elegant solution - bash maybe or python?

---

### Post by revertex on 2007-01-30
```
curl --create-dirs -L -O http://site.com/[xx-xx].txt
```

where [xx-xx] is a numeric range.

for this kind of job curl is way better.

---

