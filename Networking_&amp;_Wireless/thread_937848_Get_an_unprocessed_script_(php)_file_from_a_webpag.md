---
title: "Get an unprocessed script (php) file from a webpage"
date: 2008-10-04
forum: Networking &amp; Wireless
---

### Post by liviubero on 2008-10-04
Hello,
 I have a (silly) question:
 I want to have a copy of a script file like a php file or asp one which is on a web server.
 What I mean:
 Every time when I call some web page like [www.somename.org/index.php]("http://www.somename.org/index.php") I get the processed index.php file as a html content. But I don't want to have it preprocessed - I want the original php script.
 With ```
wget www.somename.org/index.php
``` I get only a html version of that file.
 So I don't want a content like
 [COLOR=DarkSlateBlue]hello[/COLOR]
 But one like [COLOR=DarkSlateBlue]<?="hello";?>[/COLOR]
I know that when sending a http get request to a web server, the server will let the php motor process the script and then will send me the processed content. Is there any way to have that script not processed (else then through ftp) - although this would contradict the meaning of a php-supporting web server?
Something like a scanner of a remote folder...

 Thanks,
 Liviu

---

