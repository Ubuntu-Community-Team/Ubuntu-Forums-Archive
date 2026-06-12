---
title: "Merge multiple .pnm files to one .pdf"
date: 2010-06-14
forum: New to Ubuntu
---

### Post by Nullomore on 2010-06-14
Hello! I'm just starting out on ubuntu and I'm having some trouble merging multiple pnm files into one multi-page pdf.

I first scanned the pages using xsane. Then, I edited the files with gimp and saved. When I tried to go back to xsane and save all the edited pnm's as one pdf, the xsane window just turned gray for a long time.

Am I somehow messing it up when I edit the images with gimp?

I searched the forums for help, and I found out about netpbm through this thread ([http://http://ubuntuforums.org/showthread.php?t=692522]("http://http://ubuntuforums.org/showthread.php?t=692522")2). Is there a way to use netpbm to do what I need? I read some stuff on netpbm, but it was all way over my head.

I appreciate any help I can get!

---

### Post by kaibob on 2010-06-15
> **Nullomore said:**
> Hello! I'm just starting out on ubuntu and I'm having some trouble merging multiple pnm files into one multi-page pdf.

You can convert multiple PNM files into one PDF file with graphicsmagick, a small command-line utility that's in the repositories. First copy all the PNM files into an empty directory. Then, open a terminal window, change to the directory that contains the PNM files, and enter:

```
gm convert *.pnm output.pdf
```

If the PNM files are damaged in some way, graphicsmagick will let you know. 

You can also do this with Imagemagick, but certain versions of Imagemagick will fail when converting multiple files of another format to one PDF file.

---

### Post by Nullomore on 2010-06-15
graphicsmagick worked perfectly! Thanks so much!

Just out of curiosity, any idea why xsane won't make the pdf after editing the pictures?

---

### Post by Veloteuton63 on 2012-05-04
> **kaibob said:**
> You can convert multiple PNM files into one PDF file with graphicsmagick, a small command-line utility that's in the repositories. First copy all the PNM files into an empty directory. Then, open a terminal window, change to the directory that contains the PNM files, and enter:

```
gm convert *.pnm output.pdf
```

If the PNM files are damaged in some way, graphicsmagick will let you know. 

You can also do this with Imagemagick, but certain versions of Imagemagick will fail when converting multiple files of another format to one PDF file.

GREAT! I was about to do it all by hand - wonderfully easy and fast - Thanks for the hint:popcorn:

---

### Post by overdrank on 2012-05-04
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

