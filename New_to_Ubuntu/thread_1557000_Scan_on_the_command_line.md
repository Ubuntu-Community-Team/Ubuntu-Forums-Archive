---
title: "Scan on the command line"
date: 2010-08-20
forum: New to Ubuntu
---

### Post by WitchCraft on 2010-08-20
How can i scan on the command line ?

The problem I have a USB connected multifunctional device (HP MFC 1312 Color laser printer, scanner).

Both the printer and scanner work fine, but the probem is I connected them to the network via cups and saned.

Now cups works fine, so does saned, but the Xsane windows client is simply crap. I have no problem with it, but the rest of the family, which is windows-centerd, is having problems with it...

Their problem: it's 'difficult' to use and Xsane on windows can't save a file to a location with a whitespace or a non-ascii charachter in the pathname...

Is there any way to scan via command line ?
With option to resolution, filename, format, file output location, etc.

So that I can write them a little application myself, where they can select format, resolution, OCR yes/no and save location.

Or is there any way I can get an application like OmniPage to connect to sane ?

---

### Post by Bachstelze on 2010-08-20
The scanimage tool can be used to scan.  It outputs the image in PNM format on standard output, so you will probably need to convert it to another format, using either a library for your language or an external tool like imagemagick.

---

### Post by ronnielsen1 on 2010-08-20
I haven't had any problem with Xsane. You might try reinstalling.

> Is there any way to scan via command line ?
With option to resolution, filename, format, file output location, etc.

[http://www.sane-project.org/lj98/doc003.html](http://www.sane-project.org/lj98/doc003.html)

---

### Post by WitchCraft on 2010-08-20
Solved:

[http://stackoverflow.com/questions/476084/c-twain-interaction](http://stackoverflow.com/questions/476084/c-twain-interaction)
[http://en.wikipedia.org/wiki/TWAIN](http://en.wikipedia.org/wiki/TWAIN)


[http://www.cyberciti.biz/faq/linux-scan-image-commands/](http://www.cyberciti.biz/faq/linux-scan-image-commands/)
[http://www.ellert.se/twain-sane/faq.html](http://www.ellert.se/twain-sane/faq.html)
[http://linux.about.com/library/cmd/blcmdl1_scanadf.htm](http://linux.about.com/library/cmd/blcmdl1_scanadf.htm)




> **ronnielsen1 said:**
> 
I haven't had any problem with Xsane. 
You might try reinstalling.

Xsane is not the problem. 
The problem is Xsane**[COLOR="Red"]-win32[/COLOR]**...

---

### Post by WitchCraft on 2010-08-20
Eeeek, TWAIN doesn't work on Windows 7.

But this one finally solved the problem:
[http://sourceforge.net/projects/sharpsane/files/](http://sourceforge.net/projects/sharpsane/files/)

It's a C# library for the sane network protocol.
I'm writing my own scanner software now.
Haha, guess what, it's very undocumented, doesn't even provide an example, but after fixing one bug, it works, and now I get correct images.

---

### Post by momcat1 on 2010-08-24
OK, I'm interested. Are you working with a Twain scanner? More details, please?

---

