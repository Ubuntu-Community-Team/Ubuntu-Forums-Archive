---
title: "running a CD intended for windows"
date: 2011-08-26
forum: New to Ubuntu
---

### Post by hookitup on 2011-08-26
hello ppl , i have this CD that contains a book basically, it is intended to run on windows, is there a program that i can use to run it on ubuntu , 11.04 is the version i am using. i tried to make the  "START.exe" executable so i can run it in wine but i only have read access to it scene it is a cd that is copywrite protected. is there a way i can use this CD on ubuntu,, any help is much appreciated.


Thanks

---

### Post by InspiredIndividual on 2011-08-26
[Here]("http://stream-recorder.com/forum/blocked-wine-start-unix-problem-opening-exe-t6560.html") are a few possible workarounds.

Does any of them work for you?

---

### Post by hookitup on 2011-08-27
i believe this is all assuming u have read-write permissions over the file ,,,, im trying to run a CD so i do not have write permission to make it executable.

---

### Post by PhilGil on 2011-08-27
Try copying the contents of the CD to your hard drive and running the executable from there.

In Windows executables are sometimes just used as containers, like zip files. You could try opening it with file roller and see if you can extract the book's contents.

---

### Post by corncob on 2011-08-28
You might open Terminal and type
```
wine
```
(Don't forget to put a space after wine).  Then drag START.exe (or whatever) into the terminal from the file browser.  That way START.exe (or whatever) is an argument of wine and it doesn't matter if its marked as executable or not.

---

### Post by Mark Phelps on 2011-08-28
Wine will only run SOME Windows executables, it is not a miracle cure for running Windows stuff in Ubuntu.

You should look at the contents of the CD on a Windows PC and located the filename of the executable file.  Then, go to the WineHQ site and look through their application compatibility search tool to see its rating.  If it's not listed, or if it has a low rating, or if it's rated Garbage or Bronze, it's not going to work and installing Wine will be a waste of your time.

---

