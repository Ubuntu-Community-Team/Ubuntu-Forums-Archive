---
title: "Combining multiple ISO files"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by zakaluka on 2009-03-25
Hello all,

I am sure this question has been asked before, but I can't find anything for my particular situation.  I have 3 separate DVD iso images (between 500mb and 1.5gb).  All of these are only data, not movies.  What I want to do is combine and burn them onto a single DVD.  

When I searched, all I found was information for DVD movies, which obviously take a lot more work to integrate successfully.

I know I can mount each image separately and copy the contents into a new folder, then generate a new ISO.  However, is there a tool, free or non-free, that makes this easier to do (I have to do a lot of such ISO images, and don't want to go through hours of trial and error to fit everything onto a minimum number of DVDs).  Preferably, one that doesn't take up 2x diskspace in the process.

Thanks for your help,

z.

---

### Post by llamabr on 2009-03-25
I'm sure there's a gui tool for this, but mkisofs is pretty quick and simple.  I usually do a:

```
mkisofs -o the.iso file/
```

and there you have it.

I'd encourage you to read the man page, but everyone here loses their entire mind when I do.  So maybe google it.

---

### Post by zakaluka on 2009-03-25
Hi llamabr,

Thanks for the quick reply.  I used to use linux as my primary OS back in the 90s, so I'm not afraid of man files :).  Although, I've been out of practice for the last 8 years.  Regardless, going over my question again, I see that I wrote it in a very convoluted manner.  So, allow me to rephrase:

**Is there a tool that, given 2+ ISO images, would produce a new ISO image that contains the contents of the original images.  I would like it to do this *without* manual intervention.**

Or, is a bash script the best way to go about this.  It's been at least 6-7 years since I wrote a meaningful bash script, but I could do it with some work.  However, I am all for not re-inventing the wheel, so an existing tool would be much more helpful.

Also, I don't care whether the tool is free, non-free, or commercial.

Regards,

z.

---

### Post by llamabr on 2009-03-25
Hi.  I think I see the problem.  You'd need to make a directory, make mount points, mount each one, back out, and make an iso of that.  It does sound like a pain, particularly if you need to do it over and over.

I'm sure there's a gui to do this.  But I wouldn't know where to start:

```
brock@vader:~$ apt-cache search iso gui
k3b - A sophisticated KDE CD burning application
texlive-latex-extra - TeX Live: LaTeX supplementary packages
cbm - display the current network traffic in colors
gmountiso - This is Gmountiso, a PyGTK GUI to mount your cd images
omins - a collection of LADSPA plugins aimed at modular synthesizers
rubybook - the "Programming Ruby" book
tra - a file-system synchronizer
xcdroast - X based CD-writer software
brock@vader:~$ 
```

---

### Post by zakaluka on 2009-03-25
Hi llamabar,

I got similarly dismal searches when I was trying, both with synaptic and apt-cache.  I only know of 1 tool (MagicISO or UltraISO, not sure which one) on Windows that can do this.  So, obviously an area that could use a tool.

Thanks for all your help in resolving the situation.  I will go with the bash script / manual option for now.

Regards,

z.

---

