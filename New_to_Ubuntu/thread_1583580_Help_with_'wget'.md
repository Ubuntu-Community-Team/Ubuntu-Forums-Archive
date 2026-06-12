---
title: "Help with 'wget'"
date: 2010-09-28
forum: New to Ubuntu
---

### Post by egalvan on 2010-09-28
I've been using wget to download lists of individual files...
for example...

```
wget -c -i files-to_wget
```

file_to_wget
```
http://www.archive.org/download/OTRR_Certified_X_Minus_One/OTRR_Certified_X_Minus_One_Ver1_CD_1of3.zip
http://www.archive.org/download/OTRR_Certified_X_Minus_One/OTRR_Certified_X_Minus_One_Ver1_CD_2of3.zip
http://www.archive.org/download/OTRR_Certified_X_Minus_One/OTRR_Certified_X_Minus_One_Ver1_CD_3of3.zip

http://ia310812.us.archive.org/3/items/OTRR_Certified_Redbook_Dramas/OTRR_Certified_Redbook_Dramas_Ver1_CD_1of1.zip
```


this works well, but now I want to automate the downloading...

this is an example url... (there are approx 100 such in the file)
[http://ia350638.us.archive.org/2/items/OTRR_Certified_Dragnet/](http://ia350638.us.archive.org/2/items/OTRR_Certified_Dragnet/)

see the screencap below to visualize...

I want to:
download all files EXCEPT the '**/..**'
is this done with the ** -np, --no-parent  ** option?


automatically resume interrupted downloads
this seems to be the **  -c,  --continue  ** option. right?


do not get files already downloaded
is this done with ** -nc, --no-clobber ** option?


is the **--random-wait ** option recommended?
I've read that it make the session "friendly"
I don't know what that means.

how does the ** -P,  --directory-prefix=PREFIX **
option work? does it save files to a specified directory?


========== up-date=========
changed this ...
```
 wget --continue --no-parent --input-file=files_complete_to_wget
```

to this ... (added code in red)

```
$ wget [COLOR="Red"]-r -l 2 --random-wait [/COLOR] --continue --no-parent --input-file=files_complete_to_wget
```

but now receive this error

```
$ wget -r -l 2 --random-wait  --continue --no-parent --input-file=files_complete_to_wget
--01:42:32--  http://ia350638.us.archive.org/2/items/OTRR_Certified_Dragnet/
           => `ia350638.us.archive.org/2/items/OTRR_Certified_Dragnet/index.html'
Resolving ia350638.us.archive.org... 207.241.231.21
Connecting to ia350638.us.archive.org|207.241.231.21|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [ <=>                                                                                                      ] 2,070         --.--K/s             

01:42:33 (108.31 MB/s) - `ia350638.us.archive.org/2/items/OTRR_Certified_Dragnet/index.html' saved [2070]

Loading robots.txt; please ignore errors.
--01:42:33--  http://ia350638.us.archive.org/robots.txt
           => `ia350638.us.archive.org/robots.txt'
Connecting to ia350638.us.archive.org|207.241.231.21|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 26 [text/plain]

100%[=========================================================================================================>] 26            --.--K/s             

01:42:33 (3.08 KB/s) - **`ia350638.us.archive.org/robots.txt' saved **[26/26]

FINISHED --01:42:33--
Downloaded: 2,096 bytes in 2 files
```

I still seem to be missing something...

screenshot of url I want to capture files from.

---

### Post by TeoBigusGeekus on 2010-09-28
Maybe [this]("http://www.linuxjournal.com/content/downloading-entire-web-site-wget") could help you.

---

### Post by egalvan on 2010-09-28
> **TeoBigusGeekus said:**
> Maybe [this]("http://www.linuxjournal.com/content/downloading-entire-web-site-wget") could help you.

I had already found that exact site (and some ten others with similar info) with Google.

I've been testing many combinations that were shown, but still have not hit on the one needed to actually download the files.

Which is why I am asking for help with this specific example,
so I can get a working 'wget' options line.

Specifically,
I have about 100 url's, each showing five (or more) files, along with a 'parent' link.

I want to download all the files on that page, and ignore the parent.

My latest edit to post #1 shows the furthest I have gotten..
a download of the **`ia350638.us.archive.org/robots.txt' ** file...


The screencap in post #1 shows an example url.

---

### Post by egalvan on 2010-09-28
downloaded and am reading the wget documentation...

I tried wget with 'globbing'...
but both examples return "file not found"


examples... (shortened to improve legibility)

/2/items/OTRR_Certified_Dragnet/OTRR_Certified_Dragnet_[COLOR="Red"]*[/COLOR]

/2/items/OTRR_Certified_Dragnet/OTRR_Certified_Dragnet_Ver2.1_CD_[COLOR="Red"]?[/COLOR]of9.zip

---

### Post by gmargo on 2010-09-28
For recursive downloading, **wget** respects the "Robot Exclusion Standard" (see third paragraph of wget's man page), which means it pays attention to the **robots.txt** file, which disallows all:
```

$ cat robots.txt 
User-agent: *
Disallow: /

```

---

### Post by gmargo on 2010-09-28
Here's a shell script that will grab the archive.org directory and generate a list of links to the individual files.  You should be able to write another script that takes this output and runs the wget command.

```

#!/bin/sh
# vim: ts=8 sts=4 sw=4 et :

#--------------------------------------------------------------------------
# gmargo 2010-09-28
#--------------------------------------------------------------------------
# Given an archive.org directory URL, such as
#     http://ia331315.us.archive.org/3/items/artofcaricaturin006061mbp/
# generate a list of URLs of links in the directory.
#--------------------------------------------------------------------------

URL=$1
if [ "x$URL" = "x" ]; then
    echo "Usage: $0 url"
    exit 1
fi

TMP=/tmp/dir.$$.html
rm -f $TMP
wget -q -O $TMP "$URL"
if [ $? -ne 0 ]; then
    echo "wget $URL failed"
    exit 2
fi

grep '^<a href' < $TMP | perl -ne 's/<a href="([^"]+)".*/$1/;print' | perl -ne "s#^#$URL/#;print"

rm -f $TMP


```And here's the output of the script on your example URL:
```

$ ./list_links.sh http://ia350638.us.archive.org/2/items/OTRR_Certified_Dragnet/
http://ia350638.us.archive.org/2/items/OTRR_Certified_Dragnet//OTRR_Certified_Dragnet.jpg
http://ia350638.us.archive.org/2/items/OTRR_Certified_Dragnet//OTRR_Certified_Dragnet_Ver2.1_CD_1of9.zip
http://ia350638.us.archive.org/2/items/OTRR_Certified_Dragnet//OTRR_Certified_Dragnet_Ver2.1_CD_2of9.zip
http://ia350638.us.archive.org/2/items/OTRR_Certified_Dragnet//OTRR_Certified_Dragnet_Ver2.1_CD_3of9.zip
http://ia350638.us.archive.org/2/items/OTRR_Certified_Dragnet//OTRR_Certified_Dragnet_Ver2.1_CD_4of9.zip
http://ia350638.us.archive.org/2/items/OTRR_Certified_Dragnet//OTRR_Certified_Dragnet_Ver2.1_CD_5of9.zip
http://ia350638.us.archive.org/2/items/OTRR_Certified_Dragnet//OTRR_Certified_Dragnet_Ver2.1_CD_6of9.zip
http://ia350638.us.archive.org/2/items/OTRR_Certified_Dragnet//OTRR_Certified_Dragnet_Ver2.1_CD_7of9.zip
http://ia350638.us.archive.org/2/items/OTRR_Certified_Dragnet//OTRR_Certified_Dragnet_Ver2.1_CD_8of9.zip
http://ia350638.us.archive.org/2/items/OTRR_Certified_Dragnet//OTRR_Certified_Dragnet_Ver2.1_CD_9of9.zip
http://ia350638.us.archive.org/2/items/OTRR_Certified_Dragnet//OTRR_Certified_Dragnet_files.xml
http://ia350638.us.archive.org/2/items/OTRR_Certified_Dragnet//OTRR_Certified_Dragnet_meta.xml
http://ia350638.us.archive.org/2/items/OTRR_Certified_Dragnet//OTRR_Certified_Dragnet_reviews.xml

```

---

### Post by egalvan on 2010-09-28
> **gmargo said:**
> Here's a shell script that will grab the archive.org directory and generate a list of links to the individual files.

Almost exactly what I was needing.
It just needs to take the url's from a file named "url-to-get"
and output (append) the links to a file named "files-to-wget".


>  You should be able to write another script that takes this output and runs the wget command.

No, just generating the file as above (files-to-wget),
then feed this to wget with the '-i' option.

The only thing left would be to have wget generate the directories the way it does when using the '-r' option.

Thank you!

---

### Post by sarali on 2010-09-28
very helpful!

---

