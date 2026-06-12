---
title: "Gedit can't open file, but nano/cat can."
date: 2009-11-25
forum: New to Ubuntu
---

### Post by Remagen on 2009-11-25
Hey there, I dumped some TCP stream data into a file, most of it is unprintable ascii.  

When I try to open it in gedit, I get this:
gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

Doing the same in nano, the first page (of 20mb+ of data) is:
HTTP/1.1 200 OK
Cache-Control: private
Content-Length: 2803
Content-Type: text/html
Expires: Sun, 13 Sep 2009 18:41:47 GMT
Server: Microsoft-IIS/7.0
P3P: CP="NON DSP COR DEVa PSAa IVAo CONo OUR IND UNI PUR NAV DEM LOC", policyre$
Set-Cookie: BTA=GUID=17A97C2F6647473DB61D09BDCE30B42E; expires=Thu, 09-Sep-2010$
Set-Cookie: BTASES=SID=1445B80743F147B3AEC98B188604DA20; path=/
X-Powered-By: ASP.NET
Date: Mon, 14 Sep 2009 18:41:46 GMT
Connection: close

<script language=Javascript src="/ads_v2/script/btwrite.js"></script>
<SCRIPT LANGUAGE=Javascript>function BTAdClick(szURL){window.open(szURL);};var $
</SCRIPT><NOSCRIPT><A HREF="http://servedby.advertising.com/click/site=00007667$
Date: Mon, 14 Sep 2009 18:40:00 GMT
Server: Apache-Coyote/1.1
Pragma: no-cache

So, obviously the data is there, but how can I get gedit to read it?

---

### Post by blazemore on 2009-11-25
> **Remagen said:**
> most of it is unprintable ascii. 
Gedit won't read anything except text files I don't think
In the meantime you may use ghex2. 
It can edit any kind of files

---

### Post by blazemore on 2009-11-25
try ```
string -n 1 filename.ext > filename.readable.ext && gedit filename.readable.ext
```

---

### Post by pi.boy.travis on 2009-11-25
gedit is designed for text files only, any CLI editor will prove much more versatile then one with a GUI, except for emacs. . .

---

### Post by freecity on 2010-11-19
I have exactly the same problem. 
ghex2 could not open it neither, but I managed to open it in Windows by wordpad.
For anyone would like to try, my text file can be downloaded from the following link:
[https://www.yousendit.com/download/dklyUWVuT2I1R094dnc9PQ](https://www.yousendit.com/download/dklyUWVuT2I1R094dnc9PQ)

It is an output from the Hadoop. Basically each line is a word and its number occurs in some huge text files.
thanks

---

### Post by davec64 on 2010-11-19
> **pi.boy.travis said:**
> gedit is designed for text files only, any CLI editor will prove much more versatile then one with a GUI, except for emacs. . .

Light touch paper and stand well back!!  :popcorn:

---

### Post by freecity on 2010-11-19
> **freecity said:**
> I have exactly the same problem. 
ghex2 could not open it neither, but I managed to open it in Windows by wordpad.
For anyone would like to try, my text file can be downloaded from the following link:
[https://www.yousendit.com/download/dklyUWVuT2I1R094dnc9PQ](https://www.yousendit.com/download/dklyUWVuT2I1R094dnc9PQ)

It is an output from the Hadoop. Basically each line is a word and its number occurs in some huge text files.
thanks

solved with Gvim.
Should I replaced gedit? It seems a quite weak editor.

---

