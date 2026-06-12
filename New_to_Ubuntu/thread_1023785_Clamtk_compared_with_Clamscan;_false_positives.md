---
title: "Clamtk compared with Clamscan; false positives"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by JBA2337 on 2008-12-28
Like several other people that I have read about, I have been having problems with Clamtk and false positive viruses. Clamtk always finds at least 5 or 6 "possible viruses"; I checked them all out on the [www.virustotal.com](www.virustotal.com) web site and they all turn out not to be viruses.

However, if I run Clamscan from a terminal prompt, I have no problems at all. My computer tested out completely clean of viruses if I use Clamscan.

At a terminal prompt, type:
cd /    <ENTER>
clamscan --verbose --recursive --log=/home/clamscan.txt   <ENTER>

The clamscan.txt file gives me a record of the results, and if I do a FIND for the word "VIRUS", nothing is found.

In addition, Clamtk took about 16 hours to scan my Ubuntu 8.10 installation, about 5.6 GB; while Clamscan did the same thing in 55 minutes!

I hope this information will be helpful to some of you who are having problems with Clamtk.

JBA2337

---

### Post by Dr Small on 2008-12-28
But why scan at all?
In the 2 years + 1 month that I have been on linux, I ran AVG at the beginning and found it to be a waste of resources.

---

### Post by albinootje on 2008-12-28
> **JBA2337 said:**
>  In addition, Clamtk took about 16 hours to scan my Ubuntu 8.10 installation, about 5.6 GB; while Clamscan did the same thing in 55 minutes!

Please report it :
[http://clamtk.sourceforge.net/faq.html](http://clamtk.sourceforge.net/faq.html)

See the "There is a problem or bug with ..." section.

---

### Post by albinootje on 2008-12-28
> **Dr Small said:**
> But why scan at all?
In the 2 years + 1 month that I have been on linux, I ran AVG at the beginning and found it to be a waste of resources.

The OP might have friends, relatives or colleagues which use .. that other not so well-known OS from Redmond,WA,USA.

---

### Post by Dr Small on 2008-12-28
> **albinootje said:**
> The OP might have friends, relatives or colleagues which use .. that other not so well-known OS from Redmond,WA,USA.
Oh, yeah. I forgot about that OS.

---

