---
title: "ScribeFire bad login/pass combination"
date: 2009-04-02
forum: New to Ubuntu
---

### Post by simontaylor on 2009-04-02
I am posting here because there has been no response - and no help - at either ScribeFire or Wordpress: 

ScribeFire 3.2.3
Mozilla 3.0.8
Wordpress 2.7.1
Ubuntu 8.10

Last week, for no apparent reason, ScribeFire, a Mozilla add-on, stopped accepting my password and username for a Wordpress blog. I know the username and password to be correct. I know xmlrpc.php to be checked inside Wordpress. I don't know what might have caused this breakdown in communications. 

The only change I initiated before ScribeFire stopped working was to secure my LAN using WAP-PSK - I don't know if this could've contributed or caused the problem.

I understand this may seem trivial, but I really would appreciate help.

Thank you,

Simon Taylor

---

### Post by Cypher on 2009-04-02
You have, of course, added your WP blog again into Scribefire and checked to see if the newly created account will work?

If you can access all Internet sites with your change to WPA-PSK, then that's not likely an issue. Scribefire (operating within Firefox) shouldn't even care.

---

### Post by simontaylor on 2009-04-02
I've uninstalled ScribeFire several times, re-adding the WP blog with the same result. I've also deactivated all WP plug-ins to see if there's a clash. 
And reactivated them one by one. 
Thanks for the word on WPA-PSK.
Still, it remains a mystery as to why SF suddenly crashed.

Simon

---

### Post by simontaylor on 2009-04-02
This suggestion has come my way:

It is likely an issue with your .htaccess file. Add this to it and see if your file
can be accessed via the browser.

<Files xmlrpc.php>
SecFilterInheritance Off
</Files>

I can't recall how to get to my .htaccess file

...

?

---

### Post by mikemunsil on 2009-07-22
That fix did not work for me.

You might have to set the options in your FTP software to view hidden files. Once downloaded, you may have to do the same (view hidden) to see the file.

---

### Post by simontaylor on 2009-07-22
The other fix that has worked on the numerous occasions now that Scribefire has returned a bad login/password combo message is to reload at the other end, i.e. WP, the xmlrpc.php file has a tendency to become corrupted... how, why, I don't know. 

Best,
Simon Taylor

---

