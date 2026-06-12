---
title: "Printing from the command line"
date: 2011-01-21
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2011-01-21
Hi All,

I'm running 10.10 and have a Samsung ML-1640.

The strangest thing happens when I try to print from the command line.
If I type:

```
lpr filename
```

in the terminal the file will print provided it is a gedit file with no extension.  If the file is a gedit file with the .txt extension and I type for example:

```
lpr filename.txt
```

My printer will blink and makes noises like it is printing but no paper will be pulled through.

If I try to print an open office document (with or without the extension) or a word document that I got in an email the same thing happens.  The printer blinks, makes noises, acts like it is printing but no paper is pulled through so no hard copy is produced.

When I check the printer job list all the jobs show as completed.
I **can** print the files by opening their application and choosing print.

Does anyone have an idea of what is going wrong and how to fix it?

---

### Post by lykeion on 2011-01-21
Hi, since I have the exact same printer I tested to print a text file (with and without .txt extension) with lpr but I couldn't reproduce your problem. Printing an OpenOffice document (.odt) with lpr does not work, but why would you want to do that?

I suggest you look through this page (and especially about the error log): [https://wiki.ubuntu.com/DebuggingPrintingProblems](https://wiki.ubuntu.com/DebuggingPrintingProblems)

---

### Post by GrouchyGaijin on 2011-01-21
> **lykeion said:**
> Hi, since I have the exact same printer I tested to print a text file (with and without .txt extension) with lpr but I couldn't reproduce your problem. Printing an OpenOffice document (.odt) with lpr does not work, but why would you want to do that?

I suggest you look through this page (and especially about the error log): [https://wiki.ubuntu.com/DebuggingPrintingProblems](https://wiki.ubuntu.com/DebuggingPrintingProblems)

It would be quicker to print something from the command line than having to open the program and then print.  I'll look through that link again.

---

### Post by lykeion on 2011-01-21
You can print text files and pdf:s with lpr. Formatted files like .odt will not work, but why not just call oowriter from the commandline to print .odt-files:
```
oowriter -p yourfile.odt
```

---

### Post by GrouchyGaijin on 2011-01-21
> **lykeion said:**
> ... but why not just call oowriter from the commandline to print .odt-files:
```
oowriter -p yourfile.odt
```

Because I didn't know how.  Thank you!

---

