---
title: "tar Error"
date: 2010-03-01
forum: New to Ubuntu
---

### Post by sangdogg on 2010-03-01
Hello guys, I just have downloaded ACE 5.7 and tried to put it into the directory "ACE"
so I got the files by ```
wget [http://download.dre.vanderbilt.edu/previous_versions/ACE-5.7.0.tar.gz](http://download.dre.vanderbilt.edu/previous_versions/ACE-5.7.0.tar.gz)

```
 
and then tried to do ```
tar xvzf ACE-5.7.0.tar.gz
```
 
but then I get No such file and directory..
 
so I did "ls" if the file is there..
 
 
here is log.
 
 
 
 
 
 
 
trinity@beethovenvirus:~$ wget [http://download.dre.vanderbily.edu/previous_versio](http://download.dre.vanderbily.edu/previous_versio)
ons/ACE-5.7.0.tar.gz -
--22:32:54-- [http://download.dre.vanderbily.edu/previous_versions/ACE-5.7.0.tar](http://download.dre.vanderbily.edu/previous_versions/ACE-5.7.0.tar).
.gz 
=> `ACE-5.7.0.tar.gz'R
Resolving download.dre.vanderbily.edu... 208.69.32.132C
Connecting to download.dre.vanderbily.edu|208.69.32.132|:80... connected.H
HTTP request sent, awaiting response... 302 FoundL
Location: [http://guide.opendns.com/?url=download.dre.vanderbily.edu%2Fprevious_ve](http://guide.opendns.com/?url=download.dre.vanderbily.edu%2Fprevious_ve)
ersions%2FACE-5.7.0.tar.gz [following]-
--22:32:59-- [http://guide.opendns.com/?url=download.dre.vanderbily.edu%2Fpreviou](http://guide.opendns.com/?url=download.dre.vanderbily.edu%2Fpreviou)
us_versions%2FACE-5.7.0.tar.gz 
=> `index.html?url=download.dre.vanderbily.edu%2Fprevious_versions%2FA
ACE-5.7.0.tar.gz'R
Resolving guide.opendns.com... 208.69.32.136C
Connecting to guide.opendns.com|208.69.32.136|:80... connected.H
HTTP request sent, awaiting response... 200 OKL
Length: unspecified [text/html]
 
[ <=> ] 2,354 --.--K/s 
2
22:33:04 (160.35 MB/s) - `index.html?url=download.dre.vanderbily.edu%2Fprevious_v
versions%2FACE-5.7.0.tar.gz' saved [2354]
t
trinity@beethovenvirus:~$ tar xvzf ACE-5.7.0.tar.gzt
tar: ACE-5.7.0.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
trinity@beethovenvirus:~$ ls
index.html?url=download.dre.vanderbily.edu%2Fprevious_versions%2FACE-5.7.0.tar.g
z
trinity@beethovenvirus:~$

---

### Post by cariboo on 2010-03-02
I just untarred the file using file-roller. Just double click the file if it's on your desk top and choose where you want to unarchive it, click extract, and your done.

It also looks like you have a spelling error in your output.

---

### Post by victor.zamanian on 2010-03-02
It's kind of weird that it would say 
tar: ACE-5.7.0.tar.**gz**: Cannot open: No such file or directory

... when you in fact wrote:
trinity@beethovenvirus:~$ tar xvzf ACE-5.7.0.tar.**gzt**

Are you sure it didn't say the following?
tar: ACE-5.7.0.tar.**gzt**: Cannot open: No such file or directory

Another thing that's very odd is that `ls' is giving you the name
*index.html?url=download.dre.vanderbily.edu%2Fprevi ous_versions%2FACE-5.7.0.tar.gz*---which means that's the name of the file that was saved---when `wget' should have saved the file to ACE-5.7.0.tar.gz. Strangeness.

---

