---
title: "how to download files.it wont let me"
date: 2011-04-19
forum: New to Ubuntu
---

### Post by flagrl on 2011-04-19
i finally figured out how to get the internet working a couple weeks ago. well someone else did for me. but im back for one more question. i want to download stuff off the internet but it wont let me its saying i dont have a zipfile to do it but i cant download it cause i dont a have zip file. how can i download files

---

### Post by mynameisnotbob on 2011-04-19
what is the exact error message?

---

### Post by flagrl on 2011-04-19
it says:

Archive:  /tmp/BlubsterSetup-1.exe
[/tmp/BlubsterSetup-1.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /tmp/BlubsterSetup-1.exe or
          /tmp/BlubsterSetup-1.exe.zip, and cannot find /tmp/BlubsterSetup-1.exe.ZIP, period.

---

### Post by mynameisnotbob on 2011-04-19
It's not an archive. It's a Windows program. Instead, do the following.
First, enter this exact code in Terminal:
```
sudo apt-get install wine
```, press enter,
and enter your password when it asks. Don't worry that there's no letters showing up, just keep typing and press enter when you are done.
Next, redownload the program, except press "Save File" instead of "Open". Then click on Places, go to Downloads. Find the file (called 'BlubsterSetup-1.exe in your case). Then right click and click Open with Wine Windows Program Loader. Proceed from there. Tell me if it gives you an error.

---

### Post by flagrl on 2011-04-19
it comes up with


The file '/home/cerissa/Downloads/BlubsterSetup(2).exe' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

---

### Post by mynameisnotbob on 2011-04-19
ohh sorry forgot that part.
in terminal put this:
chmod +x ~/Downloads/BlubsterSetup(2).exe
then try again
post if it still returns an error.

---

### Post by flagrl on 2011-04-19
i got this 

bash: syntax error near unexpected token `('

---

### Post by nrabett on 2011-04-19
An easier way of making Wine execute the file: Find the .exe file in the Donloads folder (use "Places" to find this folder). Right-click on the .exe-file, choose Properties -> Permissions and check the box "Allow to execute file as a program". After that, double-click on the file.

---

### Post by flagrl on 2011-04-19
thank you its working now thank you so much

---

### Post by mynameisnotbob on 2011-04-19
yeah :oops: sorry I'm a bit of a terminal geek.

---

