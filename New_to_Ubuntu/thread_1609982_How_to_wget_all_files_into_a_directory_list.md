---
title: "How to wget all files into a directory list ?"
date: 2010-10-31
forum: New to Ubuntu
---

### Post by honeybear on 2010-10-31
When I try to download all files into a directory list, then wget returns no downloads ... 
Someone knows how to make it detect that it is not a html but has though to get those files

for example I put a picture here of an example directory list

---

### Post by bioterror on 2010-10-31
> **honeybear said:**
> When I try to download all files into a directory list, then wget returns no downloads ... 
Someone knows how to make it detect that it is not a html but has though to get those files

for example I put a picture here of an example directory list

wget -r
wget -m

[http://en.wikipedia.org/wiki/Wget#Basic_usage]("http://en.wikipedia.org/wiki/Wget#Basic_usage")
More information about wget you get when you say "man wget"

---

### Post by honeybear on 2010-10-31
> **bioterror said:**
> wget -r
wget -m

[http://en.wikipedia.org/wiki/Wget#Basic_usage]("http://en.wikipedia.org/wiki/Wget#Basic_usage")
More information about wget you get when you say "man wget"

wget -r is not good example since it downlaods all into subdirectories ...

I try wget -m ...

edit : 
same result. Not working; it gets all the subrepertoriy


someone has any ideas how it is possible then?

---

### Post by owenll on 2010-10-31
> man wget will give you a host of options.

---

### Post by honeybear on 2010-10-31
> **owenll said:**
> will give you a host of options.
(I know & read well man wget)

well, but I do not believe that it is possible with wget ... however you know. :(

---

### Post by honeybear on 2010-11-02
OK 

I give you some hints of solution since visibly anyone really knows how to hack over the wget program, or to use it well

```
elinks  FTPSERVERLINK,WITHOUTHTMLCODE  | grep -o 'http:[^"]*' | xargs wget -k 
```

to which I believe that it is possible with wget

---

### Post by kwacka on 2010-11-02
Try 
```
wget --level <depth>
or 
wget -l <depth>
```

the <depth> is the level to which wget will retrieve directories/sub-directories recursively. Default is 5.

---

### Post by honeybear on 2010-11-02
> **kwacka said:**
> Try 
```
wget --level <depth>
or 
wget -l <depth>
```

the <depth> is the level to which wget will retrieve directories/sub-directories recursively. Default is 5.

thanks I am working on this wget -l ... 

wget should be capable of giving this output .. somehow ... I believe it is possible still. Thanks man... I try several combinations

```
 elinks "http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/"  | grep -o 'http:[^"]*'
http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/?C=N;O=D
http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/?C=M;O=A
http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/?C=S;O=A
http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/?C=D;O=A
http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/
http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/README
http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.langpack.xpi
http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.linux-i686.checksums
http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.linux-i686.complete.mar
http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.linux-i686.tar.bz2
http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.linux-i686.tests.zip
http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.linux-i686.txt
http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.linux-x86_64.checksums
http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.linux-x86_64.complete.mar
http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.linux-x86_64.tar.bz2
http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.linux-x86_64.tests.zip
http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.linux-x86_64.txt
http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.mac64.checksums
http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.mac64.complete.mar
http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.mac64.dmg
http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.mac64.tests.zip
http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.mac64.txt
http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.win32.checksums
http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.win32.complete.mar
http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.win32.installer.exe
http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.win32.tests.zip
http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.win32.txt
http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.win32.zip
http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.win64-x86_64.checksums
http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.win64-x86_64.complete.mar
http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.win64-x86_64.installer.exe
http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.win64-x86_64.tests.zip
http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.win64-x86_64.txt
http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.win64-x86_64.zip


```


not so good for the moment ...:using wget 
> 
 wget -k  -l 0 "http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/" -O index.html ; cat index.html   |   grep -o 'http:[^"]*'
--2010-11-02 20:33:14--  [http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/)
Resolving ftp.mozilla.org... 63.245.208.138
Connecting to ftp.mozilla.org|63.245.208.138|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 7928 (7.7K) [text/html]
Saving to: &#8220;index.html&#8221;

100%[===============================================================================================================>] 7,928       37.8K/s   in 0.2s    

2010-11-02 20:33:15 (37.8 KB/s) - &#8220;index.html&#8221; saved [7928/7928]

Converting index.html... 0-65
Converted 1 files in 0.001 seconds.
[http://ftp.mozilla.org/icons/blank.gif](http://ftp.mozilla.org/icons/blank.gif)
[http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/?C=N;O=D](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/?C=N;O=D)
[http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/?C=M;O=A](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/?C=M;O=A)
[http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/?C=S;O=A](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/?C=S;O=A)
[http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/?C=D;O=A](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/?C=D;O=A)
[http://ftp.mozilla.org/icons/back.gif](http://ftp.mozilla.org/icons/back.gif)
[http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/)
[http://ftp.mozilla.org/icons/hand.right.gif](http://ftp.mozilla.org/icons/hand.right.gif)
[http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/README](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/README)
[http://ftp.mozilla.org/icons/unknown.gif](http://ftp.mozilla.org/icons/unknown.gif)
[http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.langpack.xpi](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.langpack.xpi)
[http://ftp.mozilla.org/icons/unknown.gif](http://ftp.mozilla.org/icons/unknown.gif)
[http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.linux-i686.checksums](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.linux-i686.checksums)
[http://ftp.mozilla.org/icons/unknown.gif](http://ftp.mozilla.org/icons/unknown.gif)
[http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.linux-i686.complete.mar](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.linux-i686.complete.mar)
[http://ftp.mozilla.org/icons/unknown.gif](http://ftp.mozilla.org/icons/unknown.gif)
[http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.linux-i686.tar.bz2](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.linux-i686.tar.bz2)
[http://ftp.mozilla.org/icons/compressed.gif](http://ftp.mozilla.org/icons/compressed.gif)
[http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.linux-i686.tests.zip](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.linux-i686.tests.zip)
[http://ftp.mozilla.org/icons/text.gif](http://ftp.mozilla.org/icons/text.gif)
[http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.linux-i686.txt](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.linux-i686.txt)
[http://ftp.mozilla.org/icons/unknown.gif](http://ftp.mozilla.org/icons/unknown.gif)
[http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.linux-x86_64.checksums](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.linux-x86_64.checksums)
[http://ftp.mozilla.org/icons/unknown.gif](http://ftp.mozilla.org/icons/unknown.gif)
[http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.linux-x86_64.complete.mar](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.linux-x86_64.complete.mar)
[http://ftp.mozilla.org/icons/unknown.gif](http://ftp.mozilla.org/icons/unknown.gif)
[http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.linux-x86_64.tar.bz2](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.linux-x86_64.tar.bz2)
[http://ftp.mozilla.org/icons/compressed.gif](http://ftp.mozilla.org/icons/compressed.gif)
[http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.linux-x86_64.tests.zip](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.linux-x86_64.tests.zip)
[http://ftp.mozilla.org/icons/text.gif](http://ftp.mozilla.org/icons/text.gif)
[http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.linux-x86_64.txt](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.linux-x86_64.txt)
[http://ftp.mozilla.org/icons/unknown.gif](http://ftp.mozilla.org/icons/unknown.gif)
[http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.mac64.checksums](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.mac64.checksums)
[http://ftp.mozilla.org/icons/unknown.gif](http://ftp.mozilla.org/icons/unknown.gif)
[http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.mac64.complete.mar](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.mac64.complete.mar)
[http://ftp.mozilla.org/icons/unknown.gif](http://ftp.mozilla.org/icons/unknown.gif)
[http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.mac64.dmg](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.mac64.dmg)
[http://ftp.mozilla.org/icons/compressed.gif](http://ftp.mozilla.org/icons/compressed.gif)
[http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.mac64.tests.zip](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.mac64.tests.zip)
[http://ftp.mozilla.org/icons/text.gif](http://ftp.mozilla.org/icons/text.gif)
[http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.mac64.txt](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b8pre.en-US.mac64.txt)
[http://ftp.mozilla.org/icons/unknown.gif](http://ftp.mozilla.org/icons/unknown.gif)



---

