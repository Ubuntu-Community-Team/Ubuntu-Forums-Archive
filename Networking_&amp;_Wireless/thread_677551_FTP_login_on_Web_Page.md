---
title: "FTP login on Web Page"
date: 2008-01-24
forum: Networking &amp; Wireless
---

### Post by kyleflan on 2008-01-24
First off, I hope I have the right forum category, if not I sincerely apologize.

I was wondering if there's a way to have an FTP login on one of my personal web pages. I'm using apache to host my own web server and would like to be able to go to the home web page and login to my FTP from there.

I appreciate any help.

-Kyle

---

### Post by chris_nava on 2008-01-25
If you already have an FTP server installed/configured and are just trying to put a link that connects via ftp then it's easy.

Inside the anchor tag use an FTP url instead of an HTTP url.
HTTP URL <a href="http://server/folder/folder/file.txt">link name</a>

FTP URL <a href="ftp://server/folder/folder/file.txt">link name</a>

Clicking on the link you will be prompted to enter a user name and password for FTP access.

Note: That the folder path in the FTP url is relative to your SYSTEM root not the DOCUMENT root that HTTP uses.

Note also: The default action in some browsers (IE and Firefox) is to open the FTP connection IN THE BROWSER.  It's a poorly documented client side configuration option (i don't know it and Googling it has failed me ATM)  to specify an FTP program instead.  There is no way to force such behavior via the web page.

---

### Post by kyleflan on 2008-01-26
chris_nava, thanks for your response. However, I am looking more for a way to put form fields on the page and have users login that way.

-Kyle

---

