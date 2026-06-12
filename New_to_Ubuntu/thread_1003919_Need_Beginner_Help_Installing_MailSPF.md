---
title: "Need Beginner Help Installing Mail::SPF"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by cleanden on 2008-12-06
I'm hoping someone can help me decipher what's going on and point me in the right direction.

From a command line I ran:

sudo perl -MCPAN -e shell
install Bundle:CPAN
reload cpan
force install Mail::SPF

but it comes back with:
```
Running install for module 'Mail::SPF'
Running Build for J/JM/JMEHNLE/mail-spf/Mail-SPF-V2.006.tar.gz
 Has already been unwrapped into directory /root/.cpan/build/Mail-SPF-V2.006-SPFDm4o
---- Unsatisfied dependencies detected during ----
---- JMEHNLE/mail-spf/Mail-SPF-v2.006.tar.gz ----
    Net::DNS::Resolver::Programmable [build requires]
Shall I follow them and prepend them to the queue
of modules we are processing right now? [yes]yes
Running Build test
 Delayed until after prerequisites
Running Build install
 Delayed until after prerequisites
Running install for module 'Net::DNS::Resolver::Programmable'
Running Build for J/JM/JMEHNLE/net-dns-resolver-programmable/Net-DNS-Resolver-Programmable-v0.003.tar.gz
 Has already been uwrapped into directory /root/.cpan/build/Net-DNS-Resolver-Programmable-v0.003-JnNODs
 Has already been made
Running Build test
 * ERROR: Configuration was initially created with Module::Build version '0.280801',
 but we are now using version '0.3'.  Please re-run the Build.PL or Makefile.PL script,
 or use --allow_mb_mismatch 1 to skip this version check.
 JMEHNLE/net-dns-resolver-programmable/Net-DNS-Resolver-Programmable-v0.003.tar.gz
 ./Build test -- NOT OK
//hint// to see the cpan-testers results for installing this module, try:
 reports JMEHNLE/net-dns-resolver-programmable/Net-DNS-Resolver-Programmable-v0.003.tar.gz
Running Build install
J/JM/JMEHNLE/net-dns-resolver-programmable/Net-DNS-Resolver-Programmable-v0.003.tar.gz is just needed temporarily during building or testing.  DO you want to install it permanently? (Y/n) [yes] yes
 * ERROR: Configuration was initially created with Module::Build version '0.280801',
 but we are now using version '0.3'.  Please re-run the Build.PL or Makefile.PL script,
 or use --allow_mb_mismatch 1 to skip this version check.
 JMEHNLE/net-dns-resolver-programmable/Net-DNS-Resolver-Programmable-v0.003.tar.gz
 ./Build install -- NOT OK
Running Build for J/JM/JMEHNLE/mail-spf/Mail-SPF-v2.006.tar.gz
 Has already been unwrapped into directory /root/.cpan/build/Mail-SPF-V2.006-SFDm4o
Warning: Prerequisite 'Net::DNS::Resolver::Programmable => v0.002.1' for 'JMEHNLE/mail-spf/Mail-SPF-v2.006.tar.gz' failed when processing 'JMEHNLE/net-dns-resolver-programmable/Net-DNS-Resolver-Programmable-v0.003.tar.gz' with 'make test => FAILED but failure ignored because 'force' in effect'. Continuing, but chances to succeed are limited.
 Has already been made
Running Build test
 * ERROR Configuration was initially created with Module::Build version '0.280801',
 but we are now using '0.3'.  Please re-run the Build.PL or Makefile.PL script,
 or use --allow_mb_mismatch 1 to skip this version check.
JMEHNLE/mail-spf/Mail-SPF-v2.006.tar.gz
 ./Build test -- NOT OK
//hint// to see the cpan-testers results for installing this module, try:
 reports JMEHNLE/mail-spf/Mail-SPF-v2.006.tar.gz
Running Build install
 * ERROR Configuration was initially created with Module::Build version '0.280801',
  but we are now using '0.3'.  Please re-run the Build.PL or Makefile.PL script,
 or use --allow_mb_mismatch 1 to skip this version check.
 JMEHNLE/mail-spf/Mail-SPF-v2.006.tar.gz
 ./Build install -- NOT OK
Failed during this command:
JMEHNLE/net-dns-resolver-programmable/Net-DNS-Resolver-Programmable-v0.003.tar.gz: make_test FAILED but failure ignored because 'force' in effect
 JMEHNLE/mail-spf/Mail-SPF-v2.006.tar.gz    : make_test FAILED but failure ignored because 'force' in effect
```


Thanks,
Alex

---

### Post by jgoguen on 2008-12-07
Ubuntu has a package for Mail::SPF already built.  Just run this command:
```
sudo aptitude install libmail-spf-perl
```
Enter your password when asked, and it'll install Mail::SPF and any other packages it depends on.

---

### Post by cleanden on 2008-12-07
jgoguen,
Thank you!  That did exactly what I needed, and now I have the ability to run aptitude and search for what I need.

If you don't mind, I have several other packages I need to install (I'm trying to get ASSP going on this system) and aptitude hasn't helped me find any of them.  I did find ClamAV but it didn't verify against ASSP's script.

Can you suggest any other ways I can search for and install the following:

File::Scan::ClamAV
Mail::DKIM::Verifier
IO::Socket::SSL
DBD::ADO
DBD::Mimer
DBD::ODBC
DBD::mysql::informationschema
DBD::mysql
Image::Magick
Image::OCR::Tesseract
Image::OCR

Thanks again,
Alex

---

### Post by jgoguen on 2008-12-08
In general, you can search for Perl library packages by starting with 'lib', converting the name to all lower-case, and replacing '::' with '-', and ending with '-perl'.  So to search for Mail::DKIM::Verifier, you would search aptitude for 'libmail-dkim-verifier-perl'.  Now not all of these are available as packages, so for some of them you'll need to install from CPAN.  You can [file a bug]("https://bugs.edge.launchpad.net/ubuntu/+filebug") to request that these modules be packaged.  Not saying it will happen right away, but it lets the developers know that there's people who want those modules.

For the modules that aren't in the repository, you can try taking off the subclasses and installing that package.  That may or may not give you the module you need, but it'll at least cut down on what needs to be installed from CPAN.  For example, Mail::DKIM::Verifier isn't in the repositories, so try installing Mail::DKIM (libmail-dkim-perl) and see if that gives you Mail::DKIM::Verifier.  Remove /root/.cpan/ before trying to install anything from CPAN again, that may get rid of the error you had about the configuration being created with a different version of Module::Build.

---

### Post by jgoguen on 2008-12-08
In general, you can search for Perl library packages by starting with 'lib', converting the name to all lower-case, and replacing '::' with '-', and ending with '-perl'.  So to search for Mail::DKIM::Verifier, you would search aptitude for 'libmail-dkim-verifier-perl'.  Now not all of these are available as packages, so for some of them you'll need to install from CPAN.  You can [file a bug](https://bugs.edge.launchpad.net/ubuntu/+filebug) to request that these modules be packaged.  Not saying it will happen right away, but it lets the developers know that there's people who want those modules.

For the modules that aren't in the repository, you can try taking off the subclasses and installing that package.  That may or may not give you the module you need, but it'll at least cut down on what needs to be installed from CPAN.  For example, Mail::DKIM::Verifier isn't in the repositories, so try installing Mail::DKIM (libmail-dkim-perl) and see if that gives you Mail::DKIM::Verifier.  Remove /root/.cpan/ before trying to install anything from CPAN again, that may get rid of the error you had about the configuration being created with a different version of Module::Build.

---

### Post by cleanden on 2008-12-08
Thanks for a great followup - you helped me find all but a few missing packages:


File::Scan::ClamAV
DBD::ADO
DBD::Mimer
DBD::ODBC
DBD::mysql::informationschema
Image::OCR::Tesseract
Image::OCR

I'll see what I can elsewhere for these.

Thanks again,
Alex

---

