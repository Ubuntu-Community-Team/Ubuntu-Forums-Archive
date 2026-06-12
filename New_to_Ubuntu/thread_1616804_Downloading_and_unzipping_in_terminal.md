---
title: "Downloading and unzipping in terminal"
date: 2010-11-08
forum: New to Ubuntu
---

### Post by scrooks on 2010-11-08
I am attempting to download and  unzip a .tar.gz and a .zip file from a web server (Webmin & CWIS in particular). I noted some similar posts on the topic of retrieving files from the web in terminal, but have been unable to reconstruct the process successfully. 

I attempted to do this outside the terminal via the archive and unzipped it, but whereas I can see the files, and coming from a Windows .exe environment, I am lost as to actually executing the program. I tried 'tar xvzf webmin* but received this message:

tar: webmin: Cannot read: Is a directory
tar: At beginning of tape, quitting now
tar: Error is not recoverable: exiting now

gzip: stdin: unexpected end of file
tar: Child returned status 2
tar: Exiting with failure status due to previous errors

I also tried 'wget [http://web](http://web) address.'  There are two files on the server, how would I specify one and then subsequently unzip it. I can view the packages that I retrieved from the address, but coming from a windows .exe environment, I am a bit lost as to how to actually execute the files itself. 

Any help would be greatly appreciated.

---

### Post by SuaSwe on 2010-11-08
So to clarify, you have successfully downloaded the .tar.gz file?

From the looks, when attempting to unzip the archive, at least one of the files starting with "webmin" in the folder you are in is a directory, which cannot be unzipped causing the process to fail. You want to make sure that you are in the directory where the .tar.gz file is residing, and specify only it/them, not any other files.

You also need a hyphen before xvzf:

```

tar -xvzf webmin.tar.gz

```

:)

---

### Post by scrooks on 2010-11-08
That worked, thank you!

---

### Post by SuaSwe on 2010-11-08
Awesome! If you could, mark the thread as Solved using Thread Tools toward the top-right. :)

---

