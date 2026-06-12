---
title: "Filtering many wireshark packet capture files w/ shell &amp; perl"
date: 2007-11-30
forum: Networking &amp; Wireless
---

### Post by jsa13 on 2007-11-30
Server and apps folks often think that networkers have some magic insight that only our "crystal ball" packet capture software can reveal.  So they send you out to diagnose the problem and  provid NO info w/ which to create a packet filter - so now you must capture it ALL.  This is the equivalent to drinking from a fire hose.  If you are smart (or experienced) enough to not capture it all to one gigantic file, you can filter these files later and then merge them into one meaningful dataset later.

NOTE: I am not a perl expert. I suck w/ perl.  If you can do it better/faster/cheaper please post a reply and educate me (honestly, I'd appreciate it).

#! /usr/bin/perl

@cap_files = `ls  /export/pktcap/*.cap`;
chomp(@cap_files);

foreach (@cap_files) {
	$cap_file = `echo -n "$_" | awk '{sub("^.*\/","");print}'`;
	chomp ($cap_file);
	`mergecap -aw- $_ | tcpdump -nqpr- -w /export/pktcap/dst/$cap_file dst 192.168.0.78`;
	print "\Filtered results in /export/pktcap/dst/$cap_file \n"
}

You can also use tools like tshark, installed with wireshark-common to get statistics and then generate graphs.  Do `dpkg -L wireshark-common | grep 'bin/'` for a list.

/usr/bin/dumpcap
/usr/bin/capinfos
/usr/bin/editcap
/usr/bin/mergecap

I have some other examples if anyone is interested.... later.

Jason

---

### Post by tr333 on 2007-12-01
I'm not sure of how to do it differently, but there are a few things you could improve in this script.

1. remove the `ls` shell execution and replace it with glob().
2. remove the awk substitution and replace it with a perl subsitution (faster).

```

#! /usr/bin/perl -w

use strict;
use warnings;

my $cap_dir = '/export/pktcap';
my $new_cap_dir = "$cap_dir/dst";

# remove the need for the list containing all the file names
foreach ( glob('/export/pktcap/*.cap') ) {
    chomp;
    # using the '#' character instead of '/' in the substitution, thus removing the need for escaping the '/' character
    # this will assign the value of $_ to $cap_file and then do the substitution on $cap_file
    (my $cap_file = $_) =~ s#^.*/##;
    my $new_cap_file = "$new_cap_dir/$cap_file";
    `mergecap -aw- $_ | tcpdump -nqpr- -w $new_cap_file dst 192.168.0.78`;
    print "\Filtered results in $new_cap_file \n"
}

```

You could also do this with a sh/bash script, which IMHO looks a bit cleaner:

```

#!/bin/sh

CAP_DIR="/export/pktcap/"
NEW_CAP_DIR="$CAP_DIR/dst"

for CAP_FILE in `ls $CAP_DIR/*.cap`; do
    # get the filename from the full path
    CAP_FILE=`basename $CAP_FILE`
    NEW_CAP_FILE="$NEW_CAP_DIR/$CAP_FILE"
    mergecap -aw- $_ | tcpdump -nqpr- -w $NEW_CAP_FILE dst 192.168.0.78
    echo "Filtered Results in $NEW_CAP_FILE"
done

```

If you're doing this on a large number of files (>100) then the Perl script might run a bit faster.
If there's any Perl stuff you don't understand there, look it up at perldoc.perl.org (or post here :)).

NOTE:  I haven't tested any of this code, so just post a reply if there's any problems with it.

---

### Post by jsa13 on 2007-12-03
Cool!  I knew there was a 'pure' way to do it for both perl and shell.  Thanks for showing me both.  I've more stats to gather, so I'll try each.  The '#' character instead of '/' is esp. nice.

Thank you very much tr333.  I am now at suck-1 w/ perl ;)

---

### Post by tr333 on 2007-12-03
> **jsa13 said:**
> The '#' character instead of '/' is esp. nice.

I think it's also possible to use other characters in place of the '/' for both matching (m/var/) and substituting (s/var1/var2/).  Read the regex docs on perldoc.perl.org (or use the perldoc command on your computer) to get more info on this.

---

