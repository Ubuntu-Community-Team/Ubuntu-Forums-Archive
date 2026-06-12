---
title: "change/increase filename numbers?"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by slughappy1 on 2010-04-29
I have a bunch of files that have wrong numbers. I had a pdf that I used pdftk burst on. It naturally made a single pdf file for every page. That is sort of the problem. It named them all in order, but some of pages were missing in the original pdf that I want to add. So I would like to increase the numbers of certain files by a certain amount. For example, I want to leave the files named pg_0001-36 alone. Then I would like to increase every filename after that by 20 or so pages. So the next file, instead of having the filename pg_0037, would have the filename pg_0050. I would also need all the files after pg_0037 to increase by the same amount.

---

### Post by iMisspell on 2010-04-29
If you post the full file name (of one of the files), i (or someone else) could make you a quick little bash script to rename them for you.

---

### Post by gmargo on 2010-04-29
Try this perl script on for size.  I called it 'rename_incr.pl'.
```

#!/usr/bin/perl -w
use strict;
use warnings;
#--------------------------------------------------------------------------
# http://ubuntuforums.org/showthread.php?t=1465018
# Subject: change/increase filename numbers?
#--------------------------------------------------------------------------

sub Usage
{
    print STDERR "Usage: $0 increment file1 [file2 ...]\n";
    exit 1;
}
Usage() unless @ARGV >= 2;
my ($incr, @files) = @ARGV;
Usage() unless $incr =~ /^\d+$/;

foreach my $oldfile (@files)
{
    next if $oldfile !~ /^(.*?)(\d+)$/;
    my ($start, $num) = ($1,int($2));
    $num += $incr;
    my $zerolen = length($oldfile) - length($start) - length("$num");
    $zerolen = 0 if $zerolen < 0;
    my $newfile = $start . ("0" x $zerolen) . $num;
    #print "oldfile=$oldfile   newfile=$newfile\n";

    next if $oldfile eq $newfile;

    if (! -f $oldfile)
    {
        print "$oldfile => $newfile skipped, source does not exist\n";
        next;
    }
    if (-f $newfile)
    {
        print "$oldfile => $newfile skipped, destination already exists\n";
        next;
    }
    if (! rename($oldfile,$newfile))
    {
        print "$oldfile => $newfile rename failed\n";
        next;
    }

    #print "$oldfile => $newfile renamed\n";
}

exit 0;



```

---

### Post by kaibob on 2010-04-29
If this is something that will only be done once or seldom, you can use the following one-liner. You have to change the pages to be renumbered (47..37) and the increment (13 in this case). You have to be careful about overwriting existing files, and be sure to test this on copies just for safety. 

```
for i in {47..37} ; do j=$((i+13)) ; mv pg_00${i} pg_00${j} ; done
```

BTW, I assume that the files have a pdf extension, and, if that's the case, this needs to be added to the above command.

---

### Post by slughappy1 on 2010-04-30
Thanks for all who responded. I ended up using GPRename. It worked, but was a little slow. Much faster that one at a time though :-)

---

