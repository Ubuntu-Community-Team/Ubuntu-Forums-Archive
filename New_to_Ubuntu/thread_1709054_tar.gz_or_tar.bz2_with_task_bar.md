---
title: "tar.gz or tar.bz2 with task bar"
date: 2011-03-17
forum: New to Ubuntu
---

### Post by lance bermudez on 2011-03-17
How do I get a task bar for the commmand line for the tar.gz or tar.bz2 when compressing files? I want a task like wget has for download and like you get when you tar.gz or tar.bz2 with a gui.

---

### Post by user1397 on 2011-03-17
> **lance bermudez said:**
> How do I get a task bar for the commmand line for the tar.gz or tar.bz2 when compressing files? I want a task like wget has for download and like you get when you tar.gz or tar.bz2 with a gui.

[http://www.neohide.com/tar-gz-a-quick-and-easy-compression-and-extraction-command-line](http://www.neohide.com/tar-gz-a-quick-and-easy-compression-and-extraction-command-line)

---

### Post by _0R10N on 2011-03-17
I did a little research and I'm still looking for a switch that shows a progress bar. The link above doesn't do the trick, it only shows the files being packaged/compressed.

---

### Post by user1397 on 2011-03-17
> **_0R10N said:**
> I did a little research and I'm still looking for a switch that shows a progress bar. The link above doesn't do the trick, it only shows the files being packaged/compressed.

ah, progress bar, i was confused with the OP as he stated task bar not progress bar. yea i don't know how to do that sorry :(

---

### Post by lance bermudez on 2011-03-19
[http://sourceforge.net/projects/clpbar/](http://sourceforge.net/projects/clpbar/)

I fond the above program call bar it shows a prograss bar how ever I cant seem to get it to work for the command
tar -zcf /home/dir/dir.tar.gz /home/dir/
copy /home/dir /otherdir/dir

I have attached the man bar so that you can help me. I tryed to read the man bar but could not make heads or tails of it. the man bar file is 34.4 kb so i had to zip it so that i could upload it.

---

### Post by lance bermudez on 2011-03-19
best I have been able to do is this
tar -zcvvvvf chant.tar.gz chant/ | zenity --progress --text="zipping" --percentage=1 --auto-kill

have no idea as to how to get "--test=zipping" to show a % as the progress bar moves

---

### Post by lance bermudez on 2011-03-19
tar -zcvvvvf file.tar.gz chant/ | tee | bar

---

### Post by lance bermudez on 2011-03-20
tar -zcvvvvf file.tar.gz chant/ | tee | bar -s 328m

get bar now but no move of bar stays at 0% however the # still run at bottom. any one know what I'm doing wrong?

---

