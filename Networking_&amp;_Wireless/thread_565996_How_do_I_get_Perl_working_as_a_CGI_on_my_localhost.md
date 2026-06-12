---
title: "How do I get Perl working as a CGI on my localhost?"
date: 2007-10-02
forum: Networking &amp; Wireless
---

### Post by master5o1 on 2007-10-02
<i>Apache/2.2.3 (Ubuntu) mod_mono/1.2.1 PHP/5.2.1 mod_perl/2.0.2 Perl/v5.8.8 Server at 127.0.0.1 Port 80</i>


Why doesn't a perl script work? It just prints the source if outside a cgi-bin folder, and if it's in one it can't find the file. Argh!

---

### Post by spur on 2007-10-02
Did you set up your alias, so that you can use a file other than  the default ( I think '/usr/var/www' for your cgi files.

---

### Post by master5o1 on 2007-10-02
and btw when i made this thread i checked through all the threads that the title search came up with.


Still no luck :(

---

### Post by spur on 2007-10-02
No offence but are you calling it through [http://localhost?](http://localhost?) Perl has to be called in that way to work. 
If you call up  [http://localhost](http://localhost) can you navigate to the file you want to use?
you may need to call http://localhost/<your directory> if it can't find that your alias is not set right.

---

### Post by master5o1 on 2007-10-03
I found a work around that might be better.

Using the /usr/lib/cgi-bin folder which is were apache points localhost/cgi-bin to, I decided to stick them in a folder /usr/lib/cgi-bin/s :)

---

