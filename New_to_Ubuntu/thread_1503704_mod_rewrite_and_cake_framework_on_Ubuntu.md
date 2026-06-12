---
title: "mod_rewrite and cake framework on Ubuntu"
date: 2010-06-07
forum: New to Ubuntu
---

### Post by danfangdango on 2010-06-07
Hi, 
I have recently installed the Cake PHP framework on my computer, but I'm having trouble getting the style files needed to have the localhost cake page working properly.

I have read on the installation guide that i need to do the following


[LIST=1]
[*]                     Make sure that an .htaccess override is allowed: in your             httpd.conf, you should have a section that defines a section for             each Directory on your server. Make sure the             AllowOverride is set to All for the             correct Directory. For security and performance reasons, do *not* set AllowOverride to All in <Directory />. Instead, look for the <Directory> block that refers to your actual website directory.
[/LIST]
Now, I've located my httpd.conf in the etc/apache2/ directory, but where there is the httpd.conf, it's copletely blank.

Am I in the wrong place or is it possible that I've done something wrong.

I'll appreciate any help.

Kind regards

---

### Post by madnessjack on 2010-06-07
in the etc/apache2/conf/ directory, there's a file called httpd-vhosts.conf. That's where all my directory scripts are if that helps.

---

