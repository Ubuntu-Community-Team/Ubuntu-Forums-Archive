---
title: "Absolute Beginner's Guide To Checksums: Help Via A Descriptive Example"
date: 2009-09-27
forum: New to Ubuntu
---

### Post by LewRockwell on 2009-09-27
Absolute Beginner's Guide To Checksums: Help Via A Descriptive Example

Chasing and checking checksums, when you're not using Synaptic or apt-get of course

So this morning we followed a link from here:
[http://lxer.com/module/newswire/view/126005/index.html](http://lxer.com/module/newswire/view/126005/index.html)

To here:
[http://www.linux-magazine.com/Online/Blogs/Productivity-Sauce-Dmitri-s-open-source-blend-of-productive-computing/Installing-Firefox-on-Puppy-Linux](http://www.linux-magazine.com/Online/Blogs/Productivity-Sauce-Dmitri-s-open-source-blend-of-productive-computing/Installing-Firefox-on-Puppy-Linux)

Then we went here to download:
[http://www.mozilla.com/en-US/firefox/personal.html](http://www.mozilla.com/en-US/firefox/personal.html)

Then we finally found this website and parent directory:
[http://mozilla.osuosl.org/pub/](http://mozilla.osuosl.org/pub/)

Then we worked through those directories til we found the md5sums:
[http://mozilla.osuosl.org/pub/mozilla.org/firefox/releases/latest/MD5SUMS](http://mozilla.osuosl.org/pub/mozilla.org/firefox/releases/latest/MD5SUMS)

And now that we actually found the checksum values, there are a whole bunch of them so how do we attempt to confirm ours?

Well, our firefox-x.x.x.tar.bz2 file is on our machine so we'll just open a terminal session in Puppy(pup terminal sessions are root so be careful!)```
md5sum firefox-x.x.x.tar.bz2 (depress enter)
```(Of course you will be substituting other values in place of the x character)

Now we'll use our find function(Find function is found in our Edit drop-down menu in Firefox) and just start typing in the checksum value that you produced in the terminal session(you can also cut and paste).

If it shows up...great! If it doesn't then you'll need to do some checking as to why the downloaded file is not checksuming correctly.


We also wanted to thank all the websites that make their checksum values easy to find!

And hopefully shame the rest into doing the same...Mozilla...Hint, Hint!

.

---

### Post by LewRockwell on 2009-09-27
It should also be noted that the website and example for placing the latest version of Firefox on Puppy doesn't appear to be correct

Also, releasing a tarball into your root directory probably isn't the best idea anyway

After the testing of this procedure on our tech bench, the subject partition was wiped and a fresh install of Puppy was completed

Then we used Puppy's pet install function to install an older version of Firefox and we also installed Dillo while we were at it

As always, your mileage may vary, buyer beware, and buyer be aware

We now return you to your regularily scheduled programming

---

### Post by bodhi.zazen on 2009-09-27
You might be interested in this :

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Although the link is on md5sum, it works for other sums as well (sha1 , sha256 , etc).

---

