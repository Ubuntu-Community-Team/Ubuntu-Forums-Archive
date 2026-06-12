---
title: "konkueror browser"
date: 2010-09-09
forum: New to Ubuntu
---

### Post by Karlof on 2010-09-09
Hi forum    What does protocol not supported on konkueror  browser mean    how do I put it right    Thanks karlof

---

### Post by undecim on 2010-09-09
That can happen if you are following a link with a protocal that konqueror doesn't support. I haven't used konq in a long time, so I have no idea what protocols it supports. However, if you look at the very leftmost part of the web address when you get that error, you might see something like

http://
https://
ftp://
sftp://
ftps://

etc... these are protocol specifications for URIs. The first two, http and https will definitly be supported by konq. The other 3 may or may not be (like I said, I haven't used konq in a while). If you try to visit a URI with a protocol that konqueror doesn't know, you will get that error.

Sometimes, webmasters will make a typo in their links and you will have "htpt" instead of "http" take a look at what protocol you're trying to use and see if it looks like a typo.

---

### Post by Karlof on 2010-09-09
Thanks for the explanation undecim I think there was a 
blip it seems okay now thanks

karlof

---

