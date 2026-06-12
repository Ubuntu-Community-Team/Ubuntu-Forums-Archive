---
title: "access permission problems"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by orbitfish on 2009-01-06
I am trying to get a local copy of my wordpress blog running on an offline machine. I have successfully managed this in windows but am running into permission problems in Ubuntu Gutsy Gibbon 7.10.

Have managed to install xampp lite into GG 7.10 and have moved the wordpress directory to /opt/lampp/htdocs using the terminal and installed the appropriate themes etc.

The problem is that when I try to install through my browser I am told that I am Forbidden: I do not have permission to access /wordpress/wp-admin/install.php on this server.

This is followed by a load of letters and numbers:
Apache/2.2.9 (Unix) DAV/2 mod_ssl/2.2.9 OpenSSL/0.9.8h PHP/5.2.6 mod_apreq2-20051231/2.6.0 mod_perl/2.0.4 Perl/v5.10.0 Server at localhost Port 80

I do not know how to alter the permissions or to run the command through the terminal (if that's possible).

Help much appreciated: from a (struggling) convert:)

---

### Post by northern lights on 2009-01-06
Altering the permissions of /opt (or any other system directory, for that matter) is not a good idea.

Two options:
Run the offline wordpress version from within /home, where you have permissions.
Or download it to /home/wherever/ and subsequently copy to /opt/lampp/htdocs/.

The latter can be done either via opening nautilus (filebrowser) as root, either from the terminal or the Alt+F2 dialog:```
gksu nautilus
```or directly via the commandline:```
sudo cp /home/wherever/ /opt/lampp/htdocs
```

Theoretically, you could also run your browser as root and directly download to /opt/lampp/htdocs/, but running your browser as the superuser is a security risk I'd avoid.

---

### Post by orbitfish on 2009-01-06
Thank you northern lights

As the computer is not going online at anytime in the foreseeable future do you think the security risk will be an issue.

Excuse my ignorance...I was okay with that legacy system but am struggling with Ubuntu at present.

thanks in advance:)

---

### Post by northern lights on 2009-01-06
> **orbitfish said:**
> As the computer is not going online at anytime in the foreseeable future do you think the security risk will be an issue.

If you're not connected to the net (cable unplugged, router/modem off, etc.) you can safely run your browser as root also. I wonder how you're going to download the wordpress then though?!

Anyhow, the above mentioned method(s) should work perfectly fine. Download to /home, copy to /opt as root.

---

### Post by orbitfish on 2009-01-06
Downloaded to home folder then copied as root to /opt and got lampp started no problem; however, when I try to access it through the browser I get the following:

Warning: file_get_contents(lang.tmp) [function.file-get-contents]: failed to open stream: Permission denied in /opt/lampp/htdocs/xampp/index.php on line 2

Warning: Cannot modify header information - headers already sent by (output started at /opt/lampp/htdocs/xampp/index.php:2) in /opt/lampp/htdocs/xampp/index.php on line 4

Unsure what this means but it doesn't look good.

---

