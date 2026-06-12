---
title: "[SOLVED] Copy many files from internet?"
date: 2007-08-15
forum: Networking &amp; Wireless
---

### Post by captainwitherspoon on 2007-08-15
Hi, I'm looking for a quick way to copy 30 lectures from the internet. 
Here is the address for lecture 24.
[http://ocw.mit.edu/ans7870/8/8.01/f99/videolectures/wl99lec24-300k.rm](http://ocw.mit.edu/ans7870/8/8.01/f99/videolectures/wl99lec24-300k.rm)
Is there a command I can use to download them all at once? Somehow change lec24 to lec* and copy to specified folder.. I'll probably have to do this many times so it'd be great to have a solution.

---

### Post by 1/0 on 2007-08-15
Just install the downthemall add-on for firefox. It'll do the trick.

---

### Post by captainwitherspoon on 2007-08-15
Tried it, The problem is I can't get to a mnu that has all of the files on one page. I'm sure the files are all named the same except the lec#. There's no terminal command to copy files from the internet?

---

### Post by kevdog on 2007-08-15
The wget command is what you want to use, but would require you know the name of all the urls, unless you can download the http page, use a combination of grep/sed to fish out the urls you want, and then pass this list to wget so it could fetch the urls.

---

### Post by noob12 on 2007-08-15
Actually you can tell wget to go recursive, stop at one level, pull only things where the URLs match a pattern.  That'll probably do it for you.  Do **man wget**.

---

### Post by captainwitherspoon on 2007-08-15
Thanks for the replies. I can see that that 'man' command is going to come in handy. 
I am now able to download the files individually but I can't yet set it up to download them all with a single command. 

Here is the section of the manual that seems to apply to my situation. 

  ```
You want to download all the GIFs from a directory on an HTTP
           server.  You tried wget http://www.server.com/dir/*.gif, but that
           didn’t work because HTTP retrieval does not support globbing.  In
           that case, use:

                   wget -r -l1 --no-parent -A.gif http://www.server.com/dir/
```

Here is the address of the files I'm after
```
http://ocw.mit.edu/ans7870/8/8.01/f99/videolectures/wl99lec24-300k.rm
```

Here is what I typed and what happened. 
```

z@xZx:~$ wget -r -l1 --no-parent -A "wl99lec*-300k.rm" http://ocw.mit.edu/ans7870/8/8.01/f99/videolectures/
--19:38:57--  http://ocw.mit.edu/ans7870/8/8.01/f99/videolectures/
           => `ocw.mit.edu/ans7870/8/8.01/f99/videolectures/index.html'
Resolving ocw.mit.edu... 204.2.128.184
Connecting to ocw.mit.edu|204.2.128.184|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
19:38:58 ERROR 404: Not Found.

Removing ocw.mit.edu/ans7870/8/8.01/f99/videolectures/index.html since it should be rejected.
unlink: No such file or directory

FINISHED --19:38:58--
Downloaded: 0 bytes in 0 files
z@xZx:~$ 

```

I also tried it without the / at the end of videolectures which kept it from adding the index directory but still didn't download the files. hrmmm

Any more ideas?

---

### Post by noob12 on 2007-08-15
I thought you said they were all linked from one page.  If so point to that page.

Otherwise you have to do something like this; crude but effective. You should test the single wget first on one lecture.

```

# This assumes you are using bash or a bourne-like shell
for i in 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30; do 
   echo "Fetching lecture $i ...";
   wget -nH "http://ocw.mit.edu/ans7870/8/8.01/f99/videolectures/wl99lec$i-300k.rm";
done

```

---

### Post by stinger30au on 2007-08-15
you need to install downthemall first in firefox
then install flashgot

flashgot is like flashget and you can tell it to select all the files in one hit

enjoy

---

### Post by noob12 on 2007-08-15
We went through that.  He's got no page with all of the links on them.

---

### Post by captainwitherspoon on 2007-08-16
Ok Here's the page where the lectures are. 
```
http://ocw.mit.edu/OcwWeb/Physics/8-01Physics-IFall1999/VideoLectures/index.htm
```
I'm not exactly sure how it works but it seems that when you click a link it redirects to a different place which sends it to the file which is why download themall doesn't work. They have a help file that tells how to download the files individually, you have to change the first  part of the address to the link given above. This means you can't see them all in a webbrowser. If you type everything but the file into the address bar it doesn't display a page. It's realaudio. If I try to play them normally in realplayer they are extremely choppy, unwatchable.

---

### Post by 1/0 on 2007-08-16
I don't know about the quality of the clips but I'm able to download the files with downthemall. I just choose videos in the filter and start. No need for flashgot or anything. Try it out.

---

### Post by captainwitherspoon on 2007-08-16
Did you try playing it? Pretty sure you just got a link, not the whole video file...

---

### Post by noob12 on 2007-08-16
I guess I wasn't clear that you can just cut and paste the little script I provided in posting #7 into your shell window.  Or is that not working?

---

### Post by captainwitherspoon on 2007-08-16
I'm sorry, for some reason I completely missed that post, thanks, it seems to be working perfectly.

---

### Post by captainwitherspoon on 2007-08-16
I see how that works, the "for i" part sets values for i and &i is where those vaules are plugged in, that's a great solution, that will also come in handy... Linux is awesome once you get the hang of it..

---

### Post by captainwitherspoon on 2007-08-31
Hey, this isn't very important but it'd be sort of nice. I found a list of courses where the file names aren't as uniform. I was wondering if there's another quick way to get all of these files

```
http://ocw.mit.edu/ans7870/8/8.03/f04/video/ocw-8.03-lec-mit-09sep2004-0001-220k.rm
http://ocw.mit.edu/ans7870/8/8.03/f04/video/ocw-8.03-lec-mit-14sep2004-0002-220k.rm
http://ocw.mit.edu/ans7870/8/8.03/f04/video/ocw-8.03-lec-mit-16sep2004-0003-220k.rm
http://ocw.mit.edu/ans7870/8/8.03/f04/video/ocw-8.03-lec-mit-21sep2004-0004-220k.rm
http://ocw.mit.edu/ans7870/8/8.03/f04/video/ocw-8.03-lec-mit-23sep2004-0005-220k.rm
http://ocw.mit.edu/ans7870/8/8.03/f04/video/ocw-8.03-lec-mit-28sep2004-0006-220k.rm
http://ocw.mit.edu/ans7870/8/8.03/f04/video/ocw-8.03-lec-mit-30sep2004-0007-220k.rm
http://ocw.mit.edu/ans7870/8/8.03/f04/video/ocw-8.03-lec-mit-05oct2004-0008-220k.rm
http://ocw.mit.edu/ans7870/8/8.03/f04/video/ocw-8.03-lec-mit-07oct2004-0009-220k.rm
http://ocw.mit.edu/ans7870/8/8.03/f04/video/ocw-8.03-lec-mit-12oct2004-0010-220k.rm
http://ocw.mit.edu/ans7870/8/8.03/f04/video/ocw-8.03-lec-mit-19oct2004-0011-220k.rm
http://ocw.mit.edu/ans7870/8/8.03/f04/video/ocw-8.03-lec-mit-21oct2004-0012-220k.rm
http://ocw.mit.edu/ans7870/8/8.03/f04/video/ocw-8.03-lec-mit-26oct2004-0013-220k.rm
http://ocw.mit.edu/ans7870/8/8.03/f04/video/ocw-8.03-lec-mit-28oct2004-0014-220k.rm
http://ocw.mit.edu/ans7870/8/8.03/f04/video/ocw-8.03-lec-mit-02nov2004-0015-220k.rm
http://ocw.mit.edu/ans7870/8/8.03/f04/video/ocw-8.03-lec-mit-04nov2004-0016-220k.rm
http://ocw.mit.edu/ans7870/8/8.03/f04/video/ocw-8.03-lec-mit-09nov2004-0017-220k.rm
http://ocw.mit.edu/ans7870/8/8.03/f04/video/ocw-8.03-lec-mit-16nov2004-0018-220k.rm
http://ocw.mit.edu/ans7870/8/8.03/f04/video/ocw-8.03-lec-mit-18nov2004-0019-220k.rm
http://ocw.mit.edu/ans7870/8/8.03/f04/video/ocw-8.03-lec-mit-23nov2004-0020-220k.rm
http://ocw.mit.edu/ans7870/8/8.03/f04/video/ocw-8.03-lec-mit-25nov2004-0021-220k.rm
http://ocw.mit.edu/ans7870/8/8.03/f04/video/ocw-8.03-lec-mit-01dec2004-0022-220k.rm
http://ocw.mit.edu/ans7870/8/8.03/f04/video/ocw-8.03-lec-mit-03dec2004-0023-220k.rm
```

As you can see, they added dates into the file name along with lecture number so that program given above doesn't work. I

---

