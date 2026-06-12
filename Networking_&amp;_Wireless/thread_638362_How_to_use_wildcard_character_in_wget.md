---
title: "How to use wildcard character in wget?"
date: 2007-12-11
forum: Networking &amp; Wireless
---

### Post by jutirain on 2007-12-11
Hi all,

I'm using wget on Ubuntu 7.04

Can I use wildcard like "wget http://opensource.adobe.com/gil/example/*.cpp"?
(I want to get all the .cpp file under directory:[http://opensource.adobe.com/gil/example/](http://opensource.adobe.com/gil/example/))

I try the method in this reference: [http://www.karakas-online.de/gnu-linux-tools-summary/internet-specific-commands.html](http://www.karakas-online.de/gnu-linux-tools-summary/internet-specific-commands.html)
i.e., quote the url with ' '
but output the following error message:
Warning: wildcards not supported in HTTP.
--17:19:37--  [http://opensource.adobe.com/gil/example/*.cpp](http://opensource.adobe.com/gil/example/*.cpp)
           => `*.cpp'
Resolving opensource.adobe.com... 192.150.18.106
Connecting to opensource.adobe.com|192.150.18.106|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
17:19:37 ERROR 404: Not Found.

If I use
wget [http://opensource.adobe.com/gil/example/](http://opensource.adobe.com/gil/example/) -r -l1 -A.cpp

I get the following message:
--17:08:08--  [http://opensource.adobe.com/gil/example/](http://opensource.adobe.com/gil/example/)
           => `opensource.adobe.com/gil/example/index.html'
Resolving opensource.adobe.com... 192.150.18.106
Connecting to opensource.adobe.com|192.150.18.106|:80... connected.
HTTP request sent, awaiting response... 403 Forbidden
17:08:18 ERROR 403: Forbidden.

Removing opensource.adobe.com/gil/example/index.html since it should be rejected.
unlink: No such file or directory

====================
I'm not sure the problem is very relevant to the forum, if not, where may be the appropriate place to post?

Thanks in advance.

---

### Post by Aikon- on 2007-12-11
This won't work because wget has no way of getting a list of files from the server. You need to explicitly pass the files you want wget to download so that it can call them directly.

If the server you are downloading from allows directory indexes (i.e. there is no index.html or similar, and when you browse to the directory it gives you a list of files/folders within that directory), then you can specify wget to act recursively (i.e. "wget -r") and it will parse that file and get the URLs to the files and subfolders from there.

**edit**

Sorry, I didn't see the part where you tried to do it recursively like I said. The server has indexes disabled for the directory, which means it won't give you a file list; this means there is no way for you to just grab all the files (or in your case, all the files of a certain extension) without foreknowledge of what they are named.

If you know what they are called, you could create an input file with the URL to each on its own line and pass that to wget, which would parse it and grab each one in the list.

---

