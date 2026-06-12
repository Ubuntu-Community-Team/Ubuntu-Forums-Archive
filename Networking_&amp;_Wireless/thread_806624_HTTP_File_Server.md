---
title: "HTTP File Server"
date: 2008-05-25
forum: Networking &amp; Wireless
---

### Post by Blinkiz on 2008-05-25
I want to expand my headless fileserver with the ability to share files by HTTP. It should be possible to upload files as well.

Please advice about a setup that can act as a **HTTP File Server**.
It should NOT be a GUI based solution. A plus is if the http can have SSL. If the suggestion is apache or similar, please provide more information about suggested scripts to get a complete solution.

---

### Post by superprash2003 on 2008-05-25
apache is good.. There are many php upload scripts on the internet.. here's one [www.tizag.com/phpT/fileupload.php](www.tizag.com/phpT/fileupload.php) and here's another [http://php.about.com/od/advancedphp/ss/php_file_upload.htm](http://php.about.com/od/advancedphp/ss/php_file_upload.htm)

---

### Post by Blinkiz on 2008-05-25
Thanks superprash2003. Nice two links but a bit too much programming. Well, maybe I have to dig into PHP scripting for this.

Everybody else, please provide more suggestions! Maybe complete PHP upload scripts?

---

### Post by lswb on 2008-05-25
If you only need to serve static files (no cgi or other dynamic services) take a look at the webfsd package. It is available in the standard repositories using synaptic or apt. Low overhead and can be configured to run in userspace with a non-standard http port number if desired. Works well for me for sharing files on local network.

If you are looking for ways to share files between linux hosts on a local network, also take a look at sshfs. Not a http solution but really useful and only requires installation of ssh server package on the host.

---

### Post by Blinkiz on 2008-05-26
webfsd seems to be great. It seems like a good product for me. But it does not support upload of files. sshfs is not for me. Needs to be http so I can use whatever browser/computer I like to get files.

**Please provide more upload/download scripts that can be used with lighttpd or Apache.**

---

