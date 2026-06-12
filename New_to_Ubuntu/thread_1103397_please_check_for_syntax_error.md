---
title: "please check for syntax error"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by broadlogic on 2009-03-22
sudo apt-get -y install $(cat /usr/share/remitt/debian/control | grep ^Depends | awk -F'},' '{ print $2; }' | sed -e 's/,/ /g;')

the control file is copied below for referance
-----------------------------------------------------------------------
Source: remitt
Section: misc
Priority: optional
Maintainer: Jeff Buchbinder <jeff@freemedsoftware.org>
Build-Depends: debhelper (>= 4.0.0), po-debconf
Standards-Version: 3.6.0

Package: remitt
Architecture: all
Depends: ${perl:Depends}, debconf, perl, libxml-libxml-perl, libxml-libxslt-perl, libcrypt-ssleay-perl, libwww-perl, libxml-simple-perl, libcgi-session-perl, libconfig-inifiles-perl, libpdf-api2-perl, libwww-mechanize-perl, libio-socket-ssl-perl, libdbd-sqlite3-perl, libcompress-zlib-perl
Description: REMITT Electronic Medical Information Translation and Transmission
 REMITT is a second-generation medical bill generation system, which
 is capable of accepting electronic medical record (EMR) information,
 translating it into the appropriate format, and transmitting it to
 the appropriate location.
 .
 REMITT is similar to FreeB ([http://www.freeb.org/](http://www.freeb.org/)) in that it can
 generate X12 837P and HCFA 1500 documents using an XML-RPC protocol,
 but REMITT relies on sessions, a monolithic XML file, XSLT, and
 other cutting edge technologies to provide vast speed and quality
 improvements.
---------------------------------------------------------------------
it seems to me that awk -F'}, part is incomplete since { is missing.

what exactly is the purpose of this command?

thank you

it is posted on install instructions for freemed software
[http://www.freemedsoftware.org/node/187](http://www.freemedsoftware.org/node/187)

---

### Post by llamabr on 2009-03-22
According to the man page (which I'm forbidden from suggesting that you read):

  Gawk accepts the following options, listed alphabetically.

       -F fs
       --field-separator fs
              Use fs for the input field separator (the value of the FS  pre-
              defined variable).

So awk is using the } as a field seperator.  It knows that that is the symbol that seperates the two fields.  Much like tab or comma delineated spreadsheet files.

Does that command not work?  It should.

---

### Post by broadlogic on 2009-03-23
llamabr
thank you for the explanation. there was no output or activity and hence i was not sure if the code worked.
regards

---

### Post by unutbu on 2009-03-23
Perhaps break the command into pieces to see what each part does
```

cat /usr/share/remitt/debian/control 
```

If you don't see any output, perhaps this file is empty?
```

cat /usr/share/remitt/debian/control | grep ^Depends

cat /usr/share/remitt/debian/control | grep ^Depends | awk -F'},' '{ print $2; }'

cat /usr/share/remitt/debian/control | grep ^Depends | awk -F'},' '{ print $2; }' | sed -e 's/,/ /g;'

sudo apt-get -s install $(cat /usr/share/remitt/debian/control | grep ^Depends | awk -F'},' '{ print $2; }' | sed -e 's/,/ /g;')
```

The last command substitutes the "-s" flag for the "-y" flag. The "-s" flag tells apt-get to simulate the install without actually installing anything, whereas the "-y" flag means say yes to all questions.

---

### Post by broadlogic on 2009-03-26
the code works now. thank you for the explanation and breaking it down for testing.

---

