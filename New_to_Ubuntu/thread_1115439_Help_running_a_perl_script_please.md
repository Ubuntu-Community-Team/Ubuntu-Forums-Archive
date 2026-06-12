---
title: "Help running a perl script please"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by skunkrecords on 2009-04-03
I would like to run a program that allows me to convert fonts to vector points. The program can be downloaded at [http://typeface.neocracy.org/download.html](http://typeface.neocracy.org/download.html) (the link on the bottom).
I'm not too sure how to install or use. I think the readme assumed I was a little smarter :(

Or if someone could interpret the synopsis.. 
**SYNOPSIS**
    use TypefaceJS;

    my $typeface = TypefaceJS::new->( input_filename => "truetype_font.ttf",
    unicode_range_names => ['Basic Latin', 'Latin-1 Supplement'], );

    $typeface->write_file( output_filename => 'font.typeface.js' );

THanks guy!

---

### Post by hyperyoda on 2009-04-03
> **skunkrecords said:**
> I would like to run a program that allows me to convert fonts to vector points. The program can be downloaded at [http://typeface.neocracy.org/download.html](http://typeface.neocracy.org/download.html) (the link on the bottom).
I'm not too sure how to install or use. I think the readme assumed I was a little smarter :(

Or if someone could interpret the synopsis.. 
**SYNOPSIS**
    use TypefaceJS;

    my $typeface = TypefaceJS::new->( input_filename => "truetype_font.ttf",
    unicode_range_names => ['Basic Latin', 'Latin-1 Supplement'], );

    $typeface->write_file( output_filename => 'font.typeface.js' );

THanks guy!


Hi,

Here is what I did:

```

debian:/tmp/1# wget http://typeface.neocracy.org/TypefaceJS-0.10.tar.gz
--2009-04-03 08:09:52--  http://typeface.neocracy.org/TypefaceJS-0.10.tar.gz
Resolving typeface.neocracy.org... 64.74.153.128
Connecting to typeface.neocracy.org|64.74.153.128|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 11191 (11K) [application/x-tar]
Saving to: `TypefaceJS-0.10.tar.gz'

100%[======================================>] 11,191      --.-K/s   in 0.1s

2009-04-03 08:09:52 (76.7 KB/s) - `TypefaceJS-0.10.tar.gz' saved [11191/11191]

debian:/tmp/1# tar zxvf TypefaceJS-0.10.tar.gz
TypefaceJS-0.10/
TypefaceJS-0.10/MANIFEST
TypefaceJS-0.10/Makefile.PL
TypefaceJS-0.10/lib/
TypefaceJS-0.10/lib/TypefaceJS.pm
TypefaceJS-0.10/scripts/
TypefaceJS-0.10/README
TypefaceJS-0.10/LICENSE
TypefaceJS-0.10/t/
TypefaceJS-0.10/t/001_load.t
TypefaceJS-0.10/Changes
debian:/tmp/1# cd TypefaceJS-0.10
debian:/tmp/1/TypefaceJS-0.10# ls
Changes  lib  LICENSE  Makefile.PL  MANIFEST  README  scripts  t
debian:/tmp/1/TypefaceJS-0.10# more Makefile.PL


use ExtUtils::MakeMaker;
# See lib/ExtUtils/MakeMaker.pm for details of how to influence
# the contents of the Makefile that is written.
WriteMakefile(
    NAME         => 'TypefaceJS',
    VERSION_FROM => 'lib/TypefaceJS.pm', # finds \$VERSION
    AUTHOR       => 'David Chester (davidchester@gmx.net)',
    ABSTRACT     => 'Generate fonts for use with typeface.js (http://typeface.neocracy.org)',
    PREREQ_PM    => {
                     'Test::Simple' => 0.44,
                    },
);
debian:/tmp/1/TypefaceJS-0.10# make
make: *** No targets specified and no makefile found.  Stop.
debian:/tmp/1/TypefaceJS-0.10# make Makefile.PL
make: Nothing to be done for `Makefile.PL'.
debian:/tmp/1/TypefaceJS-0.10# perl Makefile.PL
Checking if your kit is complete...
Looks good
WARNING: Setting VERSION via file 'lib/TypefaceJS.pm' failed
 at /usr/share/perl/5.10/ExtUtils/MakeMaker.pm line 517
Writing Makefile for TypefaceJS
debian:/tmp/1/TypefaceJS-0.10# ls
Changes  lib  LICENSE  Makefile  Makefile.PL  MANIFEST  README  scripts  t
debian:/tmp/1/TypefaceJS-0.10# make
cp lib/TypefaceJS.pm blib/lib/TypefaceJS.pm
Manifying blib/man3/TypefaceJS.3pm
debian:/tmp/1/TypefaceJS-0.10# ls
blib     lib      Makefile     MANIFEST    README   t
Changes  LICENSE  Makefile.PL  pm_to_blib  scripts

```

---

### Post by skunkrecords on 2009-04-05
Ok, so I followed your steps, then I created test.pm under the lib folder and put the code from the readme in there
```

use TypefaceJS;

    my $typeface = TypefaceJS::new->( input_filename => "truetype_font.ttf",
    unicode_range_names => ['Basic Latin', 'Latin-1 Supplement'], );

    $typeface->write_file( output_filename => 'font.typeface.js' );
```

I get this error:
```
michael@michael-desktop:~/Desktop/TypefaceJS-0.10/lib$ perl test.pm
Can't locate Font/FreeType.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at TypefaceJS.pm line 79.
BEGIN failed--compilation aborted at TypefaceJS.pm line 79.
Compilation failed in require at test.pm line 1.
BEGIN failed--compilation aborted at test.pm line 1.

```

I'm guessing I need to fix "Can't locate Font/FreeType.pm"? 
Help please? Thanks!

---

### Post by skunkrecords on 2009-04-07
bump

---

