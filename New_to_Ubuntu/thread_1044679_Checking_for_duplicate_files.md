---
title: "Checking for duplicate files"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by iains on 2009-01-19
I found a script for finding duplicate files on the archive (Dec 30th 2007)

[I][COLOR="DarkRed"]"I've improved my duplicate file finding "one liner" (just about) so that it is 1000's of times faster..


# Check sizes first and only checksum files of the same size
find . ! -empty -type f -printf "%s '%p'\n" | sort -n | uniq -D -W 1 | \
cut -d" " -f2- | \
xargs md5sum | sort | \
uniq -w32 -d --all-repeated=separate | \
cut -c35-
"
[/COLOR][/I]
I put it on my machine and it worked. But wanting to check it out in detail I went through step by step. Unless I'm mistaken the step ' uniq -D -w 1' only checks the first char of file size for duplicates and therefore doesn't save much.

The uniq command does not have an option to check the  n fields only n characters. 

If you add 9 spaces into the printf format :  "%s          '%p'\n" and then use 'uniq -D -w10' it will check for up to 10digits of file size.

When I changed this it cut down the search time for a lot of photos from 3m 40s to 1m 10s.

Will somebody please tell me if I've got it wrong.

---

### Post by mister_pink on 2009-01-19
I don't see how it should make any difference, maybe if you post what you mean I might have more of an idea. If you "un-one-liner" it (ie make it into a full script) you could have it check the sizes completely by just cutting that column.

The problem is that I think it now just compares the first 9 characters which are all spaces, and then the first one again. You need it to have some way of aligning the right hand side of the numbers.

Edit: Just realised what you were getting at, and yes, I think it will work actually.

---

### Post by iains on 2009-01-20
My post may have been a bit confusing since the spaces(shown below as '-') in 
[COLOR="Red"]find . ! -empty -type f -printf "%s----------'%p'\n"[/COLOR] got truncated. 

It was the [COLOR="Red"]uniq -D -w 1[/COLOR] which seems to regard any entries with the same first digit as duplicates.

By adding 10 spaces after the file size and then checking the first 10 it will only further process files of the same size.

---

