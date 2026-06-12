---
title: "Running a perl script using libraries in non-standard locations"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by AmbnCleo on 2009-01-08
Hi there.
I need to run scripts (from browser prompt) using libraries that are in non-standard locations.  
I keep getting the 500 internal server error and when i check the apache server error log it displays..

[error] Can't locate AUC.pm in @INC (@INC contains: lib /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl5.8.8 /usr/share/perl/5.8 /usr/local/lib/site_perl . /etc/apache2)

The AUC.pm file resides in a subdirectory of my root document directory (/home/amber/public_html/cgi-bin/lib.   

As a test I copied the AUC.pm to one of the paths above and the script bypassed that error and moved on to the next 'Can't locate .pm' error.

My question is that is there a way I can add the lib path for this software to work to the @INC somehow?

Very new to this and I am really pulling my hair out now!!!

Thanks in advance

Regards
Amber

---

