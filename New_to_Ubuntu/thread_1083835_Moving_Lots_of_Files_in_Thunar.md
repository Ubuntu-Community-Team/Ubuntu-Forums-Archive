---
title: "Moving Lots of Files in Thunar"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by SillySod on 2009-03-01
Hello - I have a couple of directories with a massive number of files in (over 100,000) which are still images extracted from a video file using a little command line whizz which I have since forgotten.

I've found that it was taking Thunar in excess of 10 minutes to load the folder contents, so I decided to split them up and put 10,000 files each in a separate directory.

When I move the files, it seems to confuse Thunar and the contents of the source and destination directories are never re-loaded, although the move seems to work fairly quickly.  The only way to stop this is to use the System Monitor to shut down Thunar and start again.

Is there a way round this?

Also, I wonder if there is a way of "compacting" the size of a directory which has had a large number of files but now contains fewer files.  The directory size is reported as 27MB even after all the files have been moved.

Many thanks.

---

### Post by vanadium on 2009-03-01
It is safer to go command line for that number of files. To "compress" the directory, you can only delete and recreate the dir. I don't think ext3 has automated features for that.

---

