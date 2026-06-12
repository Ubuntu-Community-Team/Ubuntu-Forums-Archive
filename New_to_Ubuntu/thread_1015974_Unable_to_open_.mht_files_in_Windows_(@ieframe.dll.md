---
title: "Unable to open .mht files in Windows (@ieframe.dll)"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by Harry_Iyer on 2008-12-19
Hello Everyone!

I am quite new to using Ubuntu/Linux and hence I dual boot with Windows XP.
Ubuntuforums.org has been of great help to me right from getting my installation done right to sorting some of the basic beginner issues (disabling IPv6, Compiz, root password etc.) Now though, I have a completely new problem and I have tried searching everywhere but to no avail.

I use Firefox in both XP & Ubuntu with the unMHT add-on to save webpages in web archive format. The trouble is, all types of files that I download or save using Firefox in either XP or Ubuntu pose no problem but, all the files that I have ever saved in .mht format using FF in Ubuntu are unreadable in Windows (both FF & IE7) but NOT vice-versa.

I can't quite figure out why, but in Windows, all the .mht files are being shown as the type ***_[COLOR="Red"]@ieframe.dll,-913[/COLOR]_*** and size = 0 bytes

Here are some screenshots of the problem :

[IMG]http://www.picscrazy.com/view/IEerror[/IMG]

[IMG]http://www.picscrazy.com/view/ieframe[/IMG]

[IMG]http://www.picscrazy.com/view/unMHTerror[/IMG]

Please help me. Thanks in advance.

_

---

### Post by Harry_Iyer on 2009-01-01
*bump*

---

### Post by Dedoimedo on 2009-01-01
Hi,

Try install IE in Linux:
[http://www.dedoimedo.com/computers/ie_linux.html](http://www.dedoimedo.com/computers/ie_linux.html)

And see if this helps you overcome your problem...

Cheers,
Dedoimedo

---

### Post by getnripped on 2009-02-11
I installed that as well but sadly it did not fix a problem i have with viewing .mht files. Is there a way to view them w/fire fox?

---

### Post by Harry_Iyer on 2009-02-12
I think I found the root of the problem to be the file names.

You see, using Firefox in Ubuntu, only those files that I save as .mht give such an error which have the following characters in their file names

\ / * < > : ? " |

The above characters are still not allowed in either
file or folder names in You-Know-Who.

What puzzles me is that this problem only exists with the .mht files. Other files such as .jpg or .mp3 retain their file names (with the above characters truncated) and work properly.

Is there some sort of way to ensure that while saving the files (or file names) in Ubuntu, they can't include the above characters?

There has to be a thread in this forum about file name conflicts. Could someone point me to it?

_

---

