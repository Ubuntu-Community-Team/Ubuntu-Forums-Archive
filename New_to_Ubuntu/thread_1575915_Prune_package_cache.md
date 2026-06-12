---
title: "Prune package cache"
date: 2010-09-16
forum: New to Ubuntu
---

### Post by BugBuster on 2010-09-16
Basically what I do is copy packages periodically from /var/cache/apt/archives using rsync client to another location so as not to lose them accidentally.

With time this results in multiple versions of the same package being accumulated in the backup folder.

Is there a way to prune this backup and keep only one(latest) version of a package?

---

### Post by andrewthomas on 2010-09-16
```
sudo apt-get autoclean
```

---

### Post by BugBuster on 2010-09-16
> **andrewthomas said:**
> ```
sudo apt-get autoclean
```

This does not always work as expected.
Also what "apt-get autoclean" is meant to do is delete packages that are not downloadable i.e not listed in the the package lists found in /var/lib/apt/lists

However sometimes there are multiple versions of a package that can be downloaded e.g. "now" "lucid-updates" "lucid-security" etc. and hence apt-get autoclean keeps all three versions.

What I want is a script/tool to keep only the latest and delete the older(in terms of version).

---

### Post by CharlesA on 2010-09-16
I'd be interested in this as well, since I do the same thing (and cannot get apt-cacher-ng working).

You could probably do a shell script to do that, but I'm not sure how that would work.

I'll poke around. :)

---

### Post by CharlesA on 2010-09-17
Hey there,

I wrote up a script that'll remove any packages that are duplicates and are older then the current ones. Just make sure that the current ones have a more recent date, else it'll delete the current ones and leave the old ones.

Here it is:

```
#!/bin/bash

###
### cache.sh
### Removes old debs from a package cache based on the date of the file
### Created by CharlesA
### Tested 9/17/2010
### Updated 9/17/2010
###

UNDER="_"
WILD="*"

# Enter the full path here: /path/to/package/cache/
read -p "Enter Full Path to Package Cache: " DEB
# List all debs in package cache
ls ${DEB}*.deb > ~/deb
# Find non-unique lines
cat ~/deb | cut -d _ -f 1 | uniq -d > ~/unique && rm ~/deb
if [ -s ~/unique ]; then
# Find filenames and display duplicates
read -p "Display all duplicate files? (Y/N)" FILES
# If Yes --> Display all duplicate files; If No --> Only display the oldest files.
if [[ $FILES == Y || $FILES ==  y ]]; then
while read DIR
do
# This displays all duplicate files with oldest on top
ls -r --time=atime $DIR$UNDER$WILD | tee -a ~/time && rm ~/time
done < ~/unique
read -p "Are the oldest files above the newer ones? (Y/N)" OLD
# If Yes --> Proceed to ask to delete; If No --> Exit
if [[ $OLD == Y || $OLD ==  y ]]; then
while read DIR
do
# This displays the oldest file that has a duplicate filename
ls -r --time=atime $DIR$UNDER$WILD | head -n 1 >>  ~/time
done < ~/unique
read -p "Delete found files? (Y/N)" CONFIRM
# If Yes --> Delete files; If No --> Exit
if [[ $CONFIRM == Y || $CONFIRM ==  y ]]; then
# Delete old versions
while read DEL
do
rm $DEL
done < ~/time
rm ~/time
rm ~/unique
echo "Done!"
else
echo "You have selected not to delete the listed files, exiting."; exit
fi
else
echo "Check ~/time to compare files, exiting."; exit
fi
# Display only oldest files.
else
while read DIR
do
# This displays the oldest file that has a duplicate filename
ls -r --time=atime $DIR$UNDER$WILD | head -n 1 | tee -a ~/time
done < ~/unique
read -p "Are these correct? (Y/N)" CORRECT
# If Yes --> Delete files; If No --> Exit
if [[ $CORRECT == Y || $CORRECT ==  y ]]; then
read -p "Delete found files? (Y/N)" CONFIRM
# If Yes --> Delete Files; If No --> Exit
if [[ $CONFIRM == Y || $CONFIRM ==  y ]]; then
# Delete old versions
while read DEL
do
rm $DEL
done < ~/time
rm ~/time
rm ~/unique
echo "Done!"
else
echo You have selected not to delete the listed files, exiting.; exit
fi
else
echo "Check ~/time to compare files, exiting."; exit
fi
fi
else
echo "No Duplicates Detected."; rm ~/unique; exit
fi

```

***Note: If you are removing *.deb from the default cache directory, you will probably have to run the script with sudo or as root.***

It's not 100% perfect, which is why it will ask if you want to review the duplicate files it finds, in case one of them is listed incorrectly. :)

---

### Post by BugBuster on 2010-09-20
Thanks CharlesA!!

I'll surely give this a try and report my observations.
God Bless!!

---

### Post by CharlesA on 2010-09-20
I tried to use atime instead of just sorting by modification time, but if you copied the files without keeping the time stamps, the creation and modification times were be off. I'm not 100% sure is going off the atime is the best way to do it, but it worked when I tried it.

---

### Post by BugBuster on 2010-09-20
Well CharlesA..

I tried your script and it does the job pretty well. Thanks once again.

Here are a few primary observations:
1) I notice that the script uses directory listings to find duplicates and hence using "ls" instead of "ls -r --time=atime" in line 36 should give better results(this happens in my case) as the file names are almost identical except the version number.
So using ls -l , package_0.6-5_amd64.deb will be listed earlier than package_0.6-6_amd64.deb for most cases.

2)The script generates a few temporary text files to store intermediate results. Is there a way we can store these in memory? Else we could store these in the package cache directory.
This is because just in case the directory where the user runs this script contains the same file names as used in the script then it could result in data loss(sounds slightly paranoid..but u never know!)

---

### Post by CharlesA on 2010-09-20
I don't know how it could read them into memory from something such as ls, since it would have to be read line by line to by used by the removal part.

As for listing all the files: you could edit it to add the -l switch. :)

---

### Post by CharlesA on 2010-09-20
Well, using **ls -v** works, except if the file name looks like this:

```
92K 2010-09-20 08:56 [COLOR="Red"]python-packagekit_0.5.7-0ubuntu[COLOR="Blue"]2.1_all.deb[/COLOR][/COLOR]
92K 2010-09-20 08:56 [COLOR="Red"]python-packagekit_0.5.7-0ubuntu[COLOR="Blue"]2_all.deb[/COLOR][/COLOR]

```

Note the blue part. :(

If they were listed as "2.0" it would work fine.

I've also changed where it stores the temp files to /tmp/ instead of the home directory, so that shouldn't cause any files to be overwritten. I'll finish testing it to make sure it works before posting.

---

### Post by CharlesA on 2010-09-20
Ok, here's the updated script. I switched from using atime to just using the modified time and put the temp files in /tmp/

**Known Issues:**

Since it goes by the date modified, be sure you use [COLOR="Red"]rsync -t[/COLOR] or [COLOR="Red"]cp -p[/COLOR] to preserve timestamps.

If you don't do that, the time stamps on the old files will be changed and the script won't find the correct files. You can fix that be using [COLOR="Red"]touch -m[/COLOR] on the newer file.

```
#!/bin/bash

###
### cache.sh
### Removes old debs from a package cache based on the date of the file
### Created by CharlesA
### Tested 9/20/2010
### Updated 9/20/2010
###

TMP=/tmp/
UNDER="_"
WILD="*"

# Enter the full path here: /path/to/package/cache/
read -p "Enter Full Path to Package Cache: " CACHE
# List all debs in package cache
ls ${CACHE}*.deb > ${TMP}cache
# Find non-unique lines
cat ${TMP}cache | cut -d _ -f 1 | uniq -d > ${TMP}unique && rm ${TMP}cache
if [ -s ${TMP}unique ]; then
# Find filenames and display duplicates
read -p "Display all duplicate files? (Y/N)" DUPES
# If Yes --> Display all duplicate files; If No --> Only display the oldest files.
if [[ $DUPES == Y || $DUPES ==  y ]]; then
while read DIR
do
# This displays all duplicate files with oldest on top
ls -oghtr $DIR$UNDER$WILD | cut -d " " -f 3- | tee -a ${TMP}time && rm ${TMP}time
done < ${TMP}unique
read -p "Are the oldest files above the newer ones? (Y/N)" OLD
# If Yes --> Proceed to ask to delete; If No --> Exit
if [[ $OLD == Y || $OLD ==  y ]]; then
while read DIR
do
# This displays the oldest file that has a duplicate filename
ls -r --time=atime $DIR$UNDER$WILD | head -n 1 >>  ${TMP}time
done < ${TMP}unique
read -p "Delete found files? (Y/N)" CONFIRM
# If Yes --> Delete files; If No --> Exit
if [[ $CONFIRM == Y || $CONFIRM ==  y ]]; then
# Delete old versions
while read DEL
do
rm $DEL
done < ${TMP}time
rm ${TMP}time
rm ${TMP}unique
echo "Done!"
else
echo "You have selected not to delete the listed files, exiting."; exit
fi
else
echo "Check ${TMP}time to compare files, exiting."; exit
fi
# Display only oldest files.
else
while read DIR
do
# This displays the oldest file that has a duplicate filename
ls -r --time=atime $DIR$UNDER$WILD | head -n 1 | tee -a ${TMP}time
done < ${TMP}unique
read -p "Are these correct? (Y/N)" CORRECT
# If Yes --> Delete files; If No --> Exit
if [[ $CORRECT == Y || $CORRECT ==  y ]]; then
read -p "Delete found files? (Y/N)" CONFIRM
# If Yes --> Delete Files; If No --> Exit
if [[ $CONFIRM == Y || $CONFIRM ==  y ]]; then
# Delete old versions
while read DEL
do
rm $DEL
done < ${TMP}time
rm ${TMP}time
rm ${TMP}unique
echo "Done!"
else
echo You have selected not to delete the listed files, exiting.; exit
fi
else
echo "Check ${TMP}/time to compare files, exiting."; exit
fi
fi
else
echo "No Duplicates Detected."; rm ${TMP}unique; exit
fi

```

Let me know if you find any bugs. :)

---

### Post by BugBuster on 2010-10-22
Hey CharlesA..I have found a perfect(well..at least in my test cases) solution for this issue!!

The secret is in the the 'dpkg-scanpackages' perl script in /usr/bin. This script has all the logic to select only the latest packages and generate a Packages.gz file for setting up a local repo.

I just extended the logic of this script to **delete** the packages that this script identifies as obsolete(older than the latest available in the cache).

Here is the original file that comes with Debian testing..
> 
#!/usr/bin/perl
#
# dpkg-scanpackages
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.

use warnings;
use strict;

use IO::Handle;
use IO::File;
use Getopt::Long qw(:config posix_default bundling no_ignorecase);

use Dpkg;
use Dpkg::Gettext;
use Dpkg::ErrorHandling;
use Dpkg::Control;
use Dpkg::Version;
use Dpkg::Checksums;
use Dpkg::Compression::FileHandle;
use Dpkg::IPC;

textdomain("dpkg-dev");

# Do not pollute STDOUT with info messages
report_options(info_fh => \*STDERR);

my (@samemaint, @changedmaint);
my @spuriousover;
my %packages;
my %overridden;

my %options = (help            => sub { usage(); exit 0; },
           version         => \&version,
           type            => undef,
           udeb            => \&set_type_udeb,
           arch            => undef,
           multiversion    => 0,
           'extra-override'=> undef,
               medium          => undef,
          );

my $result = GetOptions(\%options,
                        'help|h|?', 'version', 'type|t=s', 'udeb|u!',
                        'arch|a=s', 'multiversion|m!', 'extra-override|e=s',
                        'medium|M=s');

sub version {
    printf _g("Debian %s version %s.\n"), $progname, $version;
    exit;
}

sub usage {
    printf _g(
"Usage: %s [<option> ...] <binarypath> [<overridefile> [<pathprefix>]] > Packages

Options:
  -t, --type <type>        scan for <type> packages (default is 'deb').
  -u, --udeb               scan for udebs (obsolete alias for -tudeb).
  -a, --arch <arch>        architecture to scan for.
  -m, --multiversion       allow multiple versions of a single package.
  -e, --extra-override <file>
                           use extra override file.
  -M, --medium <medium>    add X-Medium field for dselect multicd access method
  -h, --help               show this help message.
      --version            show the version.
"), $progname;
}

sub set_type_udeb()
{
    warning(_g("-u, --udeb option is deprecated (see README.feature-removal-schedule)"));
    $options{type} = 'udeb';
}

sub load_override
{
    my $override = shift;
    my $comp_file = Dpkg::Compression::FileHandle->new(filename => $override);

    while (<$comp_file>) {
    s/\#.*//;
    s/\s+$//;
    next unless $_;

    my ($p, $priority, $section, $maintainer) = split(/\s+/, $_, 4);

    if (not defined($packages{$p})) {
        push(@spuriousover, $p);
        next;
    }

    for my $package (@{$packages{$p}}) {
        if ($maintainer) {
        if ($maintainer =~ m/(.+?)\s*=\>\s*(.+)/) {
            my $oldmaint = $1;
            my $newmaint = $2;
            my $debmaint = $$package{Maintainer};
            if (!grep($debmaint eq $_, split(m:\s*//\s*:, $oldmaint))) {
            push(@changedmaint,
                 sprintf(_g("  %s (package says %s, not %s)"),
                         $p, $$package{Maintainer}, $oldmaint));
            } else {
            $$package{Maintainer} = $newmaint;
            }
        } elsif ($$package{Maintainer} eq $maintainer) {
            push(@samemaint, "  $p ($maintainer)");
        } else {
            warning(_g("Unconditional maintainer override for %s"), $p);
            $$package{Maintainer} = $maintainer;
        }
        }
        $$package{Priority} = $priority;
        $$package{Section} = $section;
    }
    $overridden{$p} = 1;
    }

    close($comp_file);
}

sub load_override_extra
{
    my $extra_override = shift;
    my $comp_file = Dpkg::Compression::FileHandle->new(filename => $extra_override);

    while (<$comp_file>) {
    s/\#.*//;
    s/\s+$//;
    next unless $_;

    my ($p, $field, $value) = split(/\s+/, $_, 3);

    next unless defined($packages{$p});

    for my $package (@{$packages{$p}}) {
        $$package{$field} = $value;
    }
    }

    close($comp_file);
}

usage() and exit 1 if not $result;

if (not @ARGV >= 1 && @ARGV <= 3) {
    usageerr(_g("1 to 3 args expected"));
}

my $type = defined($options{type}) ? $options{type} : 'deb';
my $arch = $options{arch};

my @find_args;
if ($options{arch}) {
     @find_args = ('(', '-name', "*_all.$type", '-o',
            '-name', "*_${arch}.$type", ')');
}
else {
     @find_args = ('-name', "*.$type");
}

my ($binarydir, $override, $pathprefix) = @ARGV;

-d $binarydir or error(_g("Binary dir %s not found"), $binarydir);
defined($override) and (-e $override or
    error(_g("Override file %s not found"), $override));

$pathprefix = '' if not defined $pathprefix;

my $find_h = new IO::Handle;
open($find_h, '-|', 'find', '-L', "$binarydir/", @find_args, '-print')
     or syserr(_g("Couldn't open %s for reading"), $binarydir);
FILE:
    while (<$find_h>) {
    chomp;
    my $fn = $_;
    my $output;
    my $pid = spawn('exec' => [ "dpkg-deb", "-I", $fn, "control" ],
            'to_pipe' => \$output);
    my $fields = Dpkg::Control->new(type => CTRL_INDEX_PKG);
    $fields->parse($output, $fn)
        or error(_g("couldn't parse control information from %s."), $fn);
    wait_child($pid, no_check => 1);
    if ($?) {
        warning(_g("\`dpkg-deb -I %s control' exited with %d, skipping package"),
                $fn, $?);
        next;
    }
    
    defined($fields->{'Package'})
        or error(_g("No Package field in control file of %s"), $fn);
    my $p = $fields->{'Package'};
    
    if (defined($packages{$p}) and not $options{multiversion}) {
        foreach (@{$packages{$p}}) {
        if (version_compare_relation($fields->{'Version'}, REL_GT,
                         $_->{'Version'}))
                {
            warning(_g("Package %s (filename %s) is repeat but newer version;"),
                    $p, $fn);
            warning(_g("used that one and ignored data from %s!"),
                    $_->{Filename});
            $packages{$p} = [];
        } else {
            warning(_g("Package %s (filename %s) is repeat;"), $p, $fn);
            warning(_g("ignored that one and using data from %s!"),
                    $_->{Filename});
            next FILE;
        }
        }
    }
    warning(_g("Package %s (filename %s) has Filename field!"), $p, $fn)
        if defined($fields->{'Filename'});
    
    $fields->{'Filename'} = "$pathprefix$fn";
    
        my $sums = Dpkg::Checksums->new();
    $sums->add_from_file($fn);
        foreach my $alg (checksums_get_list()) {
            if ($alg eq "md5") {
            $fields->{'MD5sum'} = $sums->get_checksum($fn, $alg);
            } else {
                $fields->{$alg} = $sums->get_checksum($fn, $alg);
            }
        }
    $fields->{'Size'} = $sums->get_size($fn);
        $fields->{'X-Medium'} = $options{medium} if defined $options{medium};
    
    push @{$packages{$p}}, $fields;
    }
close($find_h);

load_override($override) if defined $override;
load_override_extra($options{'extra-override'}) if defined $options{'extra-override'};

my @missingover=();

my $records_written = 0;
for my $p (sort keys %packages) {
    if (defined($override) and not defined($overridden{$p})) {
        push(@missingover,$p);
    }
    for my $package (@{$packages{$p}}) {
     print(STDOUT "$package\n") or syserr(_g("Failed when writing stdout"));
         $records_written++;
    }
}
close(STDOUT) or syserr(_g("Couldn't close stdout"));

if (@changedmaint) {
    warning(_g("Packages in override file with incorrect old maintainer value:"));
    warning($_) foreach (@changedmaint);
}
if (@samemaint) {
    warning(_g("Packages specifying same maintainer as override file:"));
    warning($_) foreach (@samemaint);
}
if (@missingover) {
    warning(_g("Packages in archive but missing from override file:"));
    warning("  %s", join(' ', @missingover));
}
if (@spuriousover) {
    warning(_g("Packages in override file but not in archive:"));
    warning("  %s", join(' ', @spuriousover));
}

info(_g("Wrote %s entries to output Packages file."), $records_written);


And here is the patched version...
> #!/usr/bin/perl
#
# dpkg-scanpackages
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.

use warnings;
use strict;

use IO::Handle;
use IO::File;
use Getopt::Long qw(:config posix_default bundling no_ignorecase);

use Dpkg;
use Dpkg::Gettext;
use Dpkg::ErrorHandling;
use Dpkg::Control;
use Dpkg::Version;
use Dpkg::Checksums;
use Dpkg::Compression::FileHandle;
use Dpkg::IPC;

textdomain("dpkg-dev");

# Do not pollute STDOUT with info messages
report_options(info_fh => \*STDERR);

my (@samemaint, @changedmaint);
my @spuriousover;
my %packages;
my %overridden;

my %options = (help            => sub { usage(); exit 0; },
           version         => \&version,
           type            => undef,
           udeb            => \&set_type_udeb,
           arch            => undef,
           multiversion    => 0,
           'extra-override'=> undef,
               medium          => undef,
          );

my $result = GetOptions(\%options,
                        'help|h|?', 'version', 'type|t=s', 'udeb|u!',
                        'arch|a=s', 'multiversion|m!', 'extra-override|e=s',
                        'medium|M=s');

sub version {
    printf _g("Debian %s version %s.\n"), $progname, $version;
    exit;
}

sub usage {
    printf _g(
"Usage: %s [<option> ...] <binarypath> [<overridefile> [<pathprefix>]] > Packages

Options:
  -t, --type <type>        scan for <type> packages (default is 'deb').
  -u, --udeb               scan for udebs (obsolete alias for -tudeb).
  -a, --arch <arch>        architecture to scan for.
  -m, --multiversion       allow multiple versions of a single package.
  -e, --extra-override <file>
                           use extra override file.
  -M, --medium <medium>    add X-Medium field for dselect multicd access method
  -h, --help               show this help message.
      --version            show the version.
"), $progname;
}

sub set_type_udeb()
{
    warning(_g("-u, --udeb option is deprecated (see README.feature-removal-schedule)"));
    $options{type} = 'udeb';
}

sub load_override
{
    my $override = shift;
    my $comp_file = Dpkg::Compression::FileHandle->new(filename => $override);

    while (<$comp_file>) {
    s/\#.*//;
    s/\s+$//;
    next unless $_;

    my ($p, $priority, $section, $maintainer) = split(/\s+/, $_, 4);

    if (not defined($packages{$p})) {
        push(@spuriousover, $p);
        next;
    }

    for my $package (@{$packages{$p}}) {
        if ($maintainer) {
        if ($maintainer =~ m/(.+?)\s*=\>\s*(.+)/) {
            my $oldmaint = $1;
            my $newmaint = $2;
            my $debmaint = $$package{Maintainer};
            if (!grep($debmaint eq $_, split(m:\s*//\s*:, $oldmaint))) {
            push(@changedmaint,
                 sprintf(_g("  %s (package says %s, not %s)"),
                         $p, $$package{Maintainer}, $oldmaint));
            } else {
            $$package{Maintainer} = $newmaint;
            }
        } elsif ($$package{Maintainer} eq $maintainer) {
            push(@samemaint, "  $p ($maintainer)");
        } else {
            warning(_g("Unconditional maintainer override for %s"), $p);
            $$package{Maintainer} = $maintainer;
        }
        }
        $$package{Priority} = $priority;
        $$package{Section} = $section;
    }
    $overridden{$p} = 1;
    }

    close($comp_file);
}

sub load_override_extra
{
    my $extra_override = shift;
    my $comp_file = Dpkg::Compression::FileHandle->new(filename => $extra_override);

    while (<$comp_file>) {
    s/\#.*//;
    s/\s+$//;
    next unless $_;

    my ($p, $field, $value) = split(/\s+/, $_, 3);

    next unless defined($packages{$p});

    for my $package (@{$packages{$p}}) {
        $$package{$field} = $value;
    }
    }

    close($comp_file);
}

usage() and exit 1 if not $result;

if (not @ARGV >= 1 && @ARGV <= 3) {
    usageerr(_g("1 to 3 args expected"));
}

my $type = defined($options{type}) ? $options{type} : 'deb';
my $arch = $options{arch};

my @find_args;
if ($options{arch}) {
     @find_args = ('(', '-name', "*_all.$type", '-o',
            '-name', "*_${arch}.$type", ')');
}
else {
     @find_args = ('-name', "*.$type");
}

my ($binarydir, $override, $pathprefix) = @ARGV;

-d $binarydir or error(_g("Binary dir %s not found"), $binarydir);
defined($override) and (-e $override or
    error(_g("Override file %s not found"), $override));

$pathprefix = '' if not defined $pathprefix;

my $find_h = new IO::Handle;
open($find_h, '-|', 'find', '-L', "$binarydir/", @find_args, '-print')
     or syserr(_g("Couldn't open %s for reading"), $binarydir);
FILE:
    while (<$find_h>) {
    chomp;
    my $fn = $_;
    my $output;
    my $pid = spawn('exec' => [ "dpkg-deb", "-I", $fn, "control" ],
            'to_pipe' => \$output);
    my $fields = Dpkg::Control->new(type => CTRL_INDEX_PKG);
    $fields->parse($output, $fn)
        or error(_g("couldn't parse control information from %s."), $fn);
    wait_child($pid, no_check => 1);
    if ($?) {
        warning(_g("\`dpkg-deb -I %s control' exited with %d, skipping package"),
                $fn, $?);
        next;
    }
    
    defined($fields->{'Package'})
        or error(_g("No Package field in control file of %s"), $fn);
    my $p = $fields->{'Package'};
    
    if (defined($packages{$p}) and not $options{multiversion}) {
        foreach (@{$packages{$p}}) {
        if (version_compare_relation($fields->{'Version'}, REL_GT,
                         $_->{'Version'}))
                {
            warning(_g("Package %s (filename %s) is repeat but newer version;"),
                    $p, $fn);
            warning(_g("used that one and ignored data from %s!"),
                    $_->{Filename});
            warning(_g("Moving the older version of package %s to /tmp !!!"),$_->{Filename});
            system "mv $_->{Filename} /tmp";
             $packages{$p} = [];
        } else {
            warning(_g("Package %s (filename %s) is repeat;"), $p, $fn);
            warning(_g("ignored that one and using data from %s!"),
                    $_->{Filename});
            warning(_g("Moving the older version of package %s to /tmp !!!"),$fn);
            system "mv $fn /tmp";
            next FILE;
        }
        }
    }
    warning(_g("Package %s (filename %s) has Filename field!"), $p, $fn)
        if defined($fields->{'Filename'});
    
    $fields->{'Filename'} = "$pathprefix$fn";
    
        my $sums = Dpkg::Checksums->new();
    $sums->add_from_file($fn);
        foreach my $alg (checksums_get_list()) {
            if ($alg eq "md5") {
            $fields->{'MD5sum'} = $sums->get_checksum($fn, $alg);
            } else {
                $fields->{$alg} = $sums->get_checksum($fn, $alg);
            }
        }
    $fields->{'Size'} = $sums->get_size($fn);
        $fields->{'X-Medium'} = $options{medium} if defined $options{medium};
    
    push @{$packages{$p}}, $fields;
    }
close($find_h);

load_override($override) if defined $override;
load_override_extra($options{'extra-override'}) if defined $options{'extra-override'};

my @missingover=();

my $records_written = 0;
for my $p (sort keys %packages) {
    if (defined($override) and not defined($overridden{$p})) {
        push(@missingover,$p);
    }
    for my $package (@{$packages{$p}}) {
     print(STDOUT "$package\n") or syserr(_g("Failed when writing stdout"));
         $records_written++;
    }
}
close(STDOUT) or syserr(_g("Couldn't close stdout"));

if (@changedmaint) {
    warning(_g("Packages in override file with incorrect old maintainer value:"));
    warning($_) foreach (@changedmaint);
}
if (@samemaint) {
    warning(_g("Packages specifying same maintainer as override file:"));
    warning($_) foreach (@samemaint);
}
if (@missingover) {
    warning(_g("Packages in archive but missing from override file:"));
    warning("  %s", join(' ', @missingover));
}
if (@spuriousover) {
    warning(_g("Packages in override file but not in archive:"));
    warning("  %s", join(' ', @spuriousover));
}

info(_g("Wrote %s entries to output Packages file."), $records_written);


Please compare these two files with a program such as "meld" to see the changes.

And yes...try this script on several test cases before any real world use and at your own risk;)!!

---

### Post by CharlesA on 2010-10-22
So that'll purge the packages in /var/cache/apt/archives or in any folder?

Looks like a way better solution then my bad bash script. :)

---

### Post by BugBuster on 2010-10-22
> **CharlesA said:**
> So that'll purge the packages in /var/cache/apt/archives or in any folder?

Looks like a way better solution then my bad bash script. :)


Yes, it will prune packages in any directory you have write permissions...just cd to the directory containing the .deb packages and run this script as you would run dpkg-scanpackages but without the '-m' option as '-m' is meant to include all versions for a given package.

Like so...
```

$dpkg-prunepackages . /dev/null | gzip -9c > Packages.gz

```

(Note : I copied the original dpkg-scanpackages to /usr/local/bin, edited the file and named it as dpkg-prunepackages and hence the name in the example. Also this script is from Debian but one should be able to adapt these changes to the Ubuntu script without much effort.)

---

### Post by CharlesA on 2010-10-22
Awesome. Thanks! :)

---

### Post by BugBuster on 2010-10-23
> Awesome. Thanks!

Thanks to you as well! And do post your experience with the script when you try it.

And by the way your bash script wasn't bad at all. It is what got us started after all!!!:)

---

### Post by fourscore on 2010-10-23
Why don't u use aptoncd  instead to take the backups of packages in the apt-archive. This  way you can have the latest versions.

---

### Post by chinmaykamat on 2010-12-11
Cool script BugBuster. Tested it and it works very well :)

---

### Post by BugBuster on 2011-01-10
And here's the updated(improved) version of the same script. I have integrated the delete function as a "-p" option which will delete the old packages.

Check out "dpkg-prunepackages --help" for more info!

```

#!/usr/bin/perl
#
# dpkg-scanpackages
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.

use warnings;
use strict;

use IO::Handle;
use IO::File;
use Getopt::Long qw(:config posix_default bundling no_ignorecase);

use Dpkg;
use Dpkg::Gettext;
use Dpkg::ErrorHandling;
use Dpkg::Control;
use Dpkg::Version;
use Dpkg::Checksums;
use Dpkg::Compression::FileHandle;
use Dpkg::IPC;

textdomain("dpkg-dev");

# Do not pollute STDOUT with info messages
report_options(info_fh => \*STDERR);

my (@samemaint, @changedmaint);
my @spuriousover;
my %packages;
my %overridden;

my %options = (help            => sub { usage(); exit 0; },
	       version         => \&version,
	       type            => undef,
	       udeb            => \&set_type_udeb,
	       arch            => undef,
	       multiversion    => 0,
	       purge           => 0,			 	
	       'extra-override'=> undef,
               medium          => undef,
	      );

my $result = GetOptions(\%options,
                        'help|h|?', 'version', 'type|t=s', 'udeb|u!',
                        'arch|a=s', 'multiversion|m!', 'extra-override|e=s',
                        'medium|M=s','purge|p!');

sub version {
    printf _g("Debian %s version %s.\n"), $progname, $version;
    exit;
}

sub usage {
    printf _g(
"Usage: %s [<option> ...] <binarypath> [<overridefile> [<pathprefix>]] > Packages

Options:
  -t, --type <type>        scan for <type> packages (default is 'deb').
  -u, --udeb               scan for udebs (obsolete alias for -tudeb).
  -a, --arch <arch>        architecture to scan for.
  -m, --multiversion       allow multiple versions of a single package.
  -p, --purge		   purge older and keep only latest version of a single package(works only when -m is not specified)
  -e, --extra-override <file>
                           use extra override file.
  -M, --medium <medium>    add X-Medium field for dselect multicd access method
  -h, --help               show this help message.
      --version            show the version.
"), $progname;
}

sub set_type_udeb()
{
    warning(_g("-u, --udeb option is deprecated (see README.feature-removal-schedule)"));
    $options{type} = 'udeb';
}

sub load_override
{
    my $override = shift;
    my $comp_file = Dpkg::Compression::FileHandle->new(filename => $override);

    while (<$comp_file>) {
	s/\#.*//;
	s/\s+$//;
	next unless $_;

	my ($p, $priority, $section, $maintainer) = split(/\s+/, $_, 4);

	if (not defined($packages{$p})) {
	    push(@spuriousover, $p);
	    next;
	}

	for my $package (@{$packages{$p}}) {
	    if ($maintainer) {
		if ($maintainer =~ m/(.+?)\s*=\>\s*(.+)/) {
		    my $oldmaint = $1;
		    my $newmaint = $2;
		    my $debmaint = $$package{Maintainer};
		    if (!grep($debmaint eq $_, split(m:\s*//\s*:, $oldmaint))) {
			push(@changedmaint,
			     sprintf(_g("  %s (package says %s, not %s)"),
			             $p, $$package{Maintainer}, $oldmaint));
		    } else {
			$$package{Maintainer} = $newmaint;
		    }
		} elsif ($$package{Maintainer} eq $maintainer) {
		    push(@samemaint, "  $p ($maintainer)");
		} else {
		    warning(_g("Unconditional maintainer override for %s"), $p);
		    $$package{Maintainer} = $maintainer;
		}
	    }
	    $$package{Priority} = $priority;
	    $$package{Section} = $section;
	}
	$overridden{$p} = 1;
    }

    close($comp_file);
}

sub load_override_extra
{
    my $extra_override = shift;
    my $comp_file = Dpkg::Compression::FileHandle->new(filename => $extra_override);

    while (<$comp_file>) {
	s/\#.*//;
	s/\s+$//;
	next unless $_;

	my ($p, $field, $value) = split(/\s+/, $_, 3);

	next unless defined($packages{$p});

	for my $package (@{$packages{$p}}) {
	    $$package{$field} = $value;
	}
    }

    close($comp_file);
}

usage() and exit 1 if not $result;

if (not @ARGV >= 1 && @ARGV <= 3) {
    usageerr(_g("1 to 3 args expected"));
}

my $type = defined($options{type}) ? $options{type} : 'deb';
my $arch = $options{arch};

my @find_args;
if ($options{arch}) {
     @find_args = ('(', '-name', "*_all.$type", '-o',
			'-name', "*_${arch}.$type", ')');
}
else {
     @find_args = ('-name', "*.$type");
}

my ($binarydir, $override, $pathprefix) = @ARGV;

-d $binarydir or error(_g("Binary dir %s not found"), $binarydir);
defined($override) and (-e $override or
    error(_g("Override file %s not found"), $override));

$pathprefix = '' if not defined $pathprefix;

my $find_h = new IO::Handle;
open($find_h, '-|', 'find', '-L', "$binarydir/", @find_args, '-print')
     or syserr(_g("Couldn't open %s for reading"), $binarydir);
FILE:
    while (<$find_h>) {
	chomp;
	my $fn = $_;
	my $output;
	my $pid = spawn('exec' => [ "dpkg-deb", "-I", $fn, "control" ],
			'to_pipe' => \$output);
	my $fields = Dpkg::Control->new(type => CTRL_INDEX_PKG);
	$fields->parse($output, $fn)
	    or error(_g("couldn't parse control information from %s."), $fn);
	wait_child($pid, no_check => 1);
	if ($?) {
	    warning(_g("\`dpkg-deb -I %s control' exited with %d, skipping package"),
	            $fn, $?);
	    next;
	}
	
	defined($fields->{'Package'})
	    or error(_g("No Package field in control file of %s"), $fn);
	my $p = $fields->{'Package'};
	
	if (defined($packages{$p}) and not $options{multiversion}) {
	    foreach (@{$packages{$p}}) {
		if (version_compare_relation($fields->{'Version'}, REL_GT,
					     $_->{'Version'}))
                {
		    warning(_g("Package %s (filename %s) is repeat but newer version;"),
		            $p, $fn);
		    warning(_g("used that one and ignored data from %s!"),
		            $_->{Filename});
		  if ($options{purge})
		   {
		    warning(_g("DELETING OLDER PACKAGE %s!!!"),$_->{Filename});
		    system "rm $_->{Filename}";
		   }
 		    $packages{$p} = [];
		} else {
		    warning(_g("Package %s (filename %s) is repeat;"), $p, $fn);
		    warning(_g("ignored that one and using data from %s!"),
		            $_->{Filename});
		  if ($options{purge})
		   {
		    warning(_g("DELETING OLDER PACKAGE %s!!!"),$fn);
		    system "rm $fn";
		   }
		    next FILE;
		}
	    }
	}
	warning(_g("Package %s (filename %s) has Filename field!"), $p, $fn)
	    if defined($fields->{'Filename'});
	
	$fields->{'Filename'} = "$pathprefix$fn";
	
        my $sums = Dpkg::Checksums->new();
	$sums->add_from_file($fn);
        foreach my $alg (checksums_get_list()) {
            if ($alg eq "md5") {
	        $fields->{'MD5sum'} = $sums->get_checksum($fn, $alg);
            } else {
                $fields->{$alg} = $sums->get_checksum($fn, $alg);
            }
        }
	$fields->{'Size'} = $sums->get_size($fn);
        $fields->{'X-Medium'} = $options{medium} if defined $options{medium};
	
	push @{$packages{$p}}, $fields;
    }
close($find_h);

load_override($override) if defined $override;
load_override_extra($options{'extra-override'}) if defined $options{'extra-override'};

my @missingover=();

my $records_written = 0;
for my $p (sort keys %packages) {
    if (defined($override) and not defined($overridden{$p})) {
        push(@missingover,$p);
    }
    for my $package (@{$packages{$p}}) {
	 print(STDOUT "$package\n") or syserr(_g("Failed when writing stdout"));
         $records_written++;
    }
}
close(STDOUT) or syserr(_g("Couldn't close stdout"));

if (@changedmaint) {
    warning(_g("Packages in override file with incorrect old maintainer value:"));
    warning($_) foreach (@changedmaint);
}
if (@samemaint) {
    warning(_g("Packages specifying same maintainer as override file:"));
    warning($_) foreach (@samemaint);
}
if (@missingover) {
    warning(_g("Packages in archive but missing from override file:"));
    warning("  %s", join(' ', @missingover));
}
if (@spuriousover) {
    warning(_g("Packages in override file but not in archive:"));
    warning("  %s", join(' ', @spuriousover));
}

info(_g("Wrote %s entries to output Packages file."), $records_written);

```

---

