---
title: "Installing Open Office 3.3"
date: 2011-01-16
forum: New to Ubuntu
---

### Post by Robing Goodfellow on 2011-01-16
SO, I've looked through the forums, I've read "The Official Ubuntu Book," and I still have one (only one?) glaring question, at least for the moment.

How do I install "unsupported" applications.  I get how to use, and have used, Synaptic and the Ubuntu Software Center.  But what if the program I want is not in there?  Thus far I've had to search the net for a tutorial and cut & paste Terminal code, but had no bloody idea what I was doing.  That's unsatisfactory.  I'm new to Linux, but not to computers and codes.

So for example.  I'd love to check out the new beta (rc9?) of Open Office.  It's available for download, not supported in the USC or Synaptic (nor did I expect it to be).  So if I download a tar.gz or a zip or some other form of download, how the heck do I install it without mucking up my system?

Thanks in advance

---

### Post by fabricator4 on 2011-01-16
> **Robing Goodfellow said:**
> How do I install "unsupported" applications.  I get how to use, and have used, Synaptic and the Ubuntu Software Center.  But what if the program I want is not in there? 

Hi, 3.3 is not in beta anymore, it has passed to "release candidate" status which is the next step.

Download the installation package that you want (the Debian one) and the language pack with the same version number.  Follow the instructions in the installation guide:

[*OpenOffice 3.X installation guide (pdf)*]("http://wiki.services.openoffice.org/w/images/7/7e/Installation_Guide_OOo3.pdf")

Generally speaking, installation instructions should be found in one of two places: Either as a set of instructions on the website pertaining to the software (which is where I found the one above) or possibly as a readme file that you will find when you extract the installation package. Often you'll find the instructions in both places, with the most comprehensive and up-to-date ones on the web site (hopefully).

If you can't find installation instructions or if they are too cryptic to follow you should write to the software author or the maintainer, whichever is more appropriate. 

If given a choice the Debian packages are the most appropriate ones for Ubuntu.

Unfortunately installation instructions are not intended as a learning tool for bash or Linux, so if they seem like another language to you, you'd have to do some research (the man and help pages are always good) to find out what they are telling you to do.

The man pages themselves can be rather cryptic themselves as they are intended only as an overview.  They always give a link to the full manual for that command however, and this will normally give a more complete synopsis and examples.

Chris.

---

### Post by Hagar Delest on 2011-01-17
See also [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by j8a on 2011-03-10
> **Hagar de l'Est said:**
> See also [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)
I also prefer the guide from the link above. I had to remove openoffice.org and all the components (Draw, Write, Calc, Base and Impress) before installing the OO3.3

---

