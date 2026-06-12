---
title: "PDF Split and Merge"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by hifly1231 on 2008-12-27
I'm a Linux newbie coming from Windows XP.  I've installed pdftk on my Ubuntu Intrepid Ibex.  pdftk_burst is working fine, but pdftk_cat will not work.  Now I'm trying to install PDF Split & Merge (pdfsam) on my Ubuntu.  I've downloaded the zipped file to my desktop, but now I have absolutely no idea what to do.  Can someone help me, step by step?  Thanks!!!

---

### Post by hyper_ch on 2008-12-28
I use this, it's java based but works fine:

[http://www.cabaret-solutions.com/en/downloads/linux](http://www.cabaret-solutions.com/en/downloads/linux)

---

### Post by mbeach on 2008-12-28
this link may provide some insight:
[http://ubuntuforums.org/archive/index.php/t-546763.html](http://ubuntuforums.org/archive/index.php/t-546763.html)

but I think you may just want to run the following at the command line (Applications -> Accessories -> Terminal)
```
sudo apt-get install pdfsam
```

or goto Synaptics package manager and install there.
See:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
for a decent overview of installing programs in Ubuntu.  Usuallly for common programs, you don't need to download the zip, extract, install etc - there are tools built in to do all that for you.

---

### Post by nanonils on 2009-01-19
> **mbeach said:**
> this link may provide some insight:
[http://ubuntuforums.org/archive/index.php/t-546763.html](http://ubuntuforums.org/archive/index.php/t-546763.html)

but I think you may just want to run the following at the command line (Applications -> Accessories -> Terminal)
```
sudo apt-get install pdfsam
```

or goto Synaptics package manager and install there.
See:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
for a decent overview of installing programs in Ubuntu.  Usuallly for common programs, you don't need to download the zip, extract, install etc - there are tools built in to do all that for you.

That doesn't work (as detailed in your link): pdfsam is not in the normal repositories (including medibuntu). What 3rd party repository did you enable for this to install? 

I am also a past Windows user and too inexperienced to install this .jar file that's in the PDFsam zip. PDFsam seems to be easier to use than PDFtk, especially with long file names since you can simply click them. Also, PDFtk doesn't render half the fonts and  right when I merge my documents. Both the kerning and tracking is totally screwed up ([http://en.wikipedia.org/wiki/Kerning](http://en.wikipedia.org/wiki/Kerning)). First I thought this is a Windows font problem but I created these documents under Ubuntu with all the fonts installed. I have read this is a problem with ghostscript. 

Thanks for clarifying!

---

### Post by nanonils on 2009-01-19
Getting there... .jar was associated with the Archive Manger. Instead one has to associate it (or just "open with" for single use) with OpenJDK Java Runtime. PDFsam works like a charm. Best it's easy to change the order of documents without cumbersome retyping as in pdftk. I haven't tried my past documents yet that rendered incorrectly but the file size of pdfsam is different from when I use pdftk so there is a difference, it's not just a graphical user interface for pdftk.

---

