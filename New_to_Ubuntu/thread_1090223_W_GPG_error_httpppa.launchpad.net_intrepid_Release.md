---
title: "W: GPG error: http://ppa.launchpad.net intrepid Release"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by longtom on 2009-03-08
That is what I get when I update synaptic:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B81A3FBA47394CE

What does the author want to tell me.

Please help.

longtom

---

### Post by binbash on 2009-03-08
[http://www.ubuntu-inside.me/2009/02/howto-fix-signaturekeyserver-problems.html](http://www.ubuntu-inside.me/2009/02/howto-fix-signaturekeyserver-problems.html)

---

### Post by longtom on 2009-03-08
> **binbash said:**
> [http://www.ubuntu-inside.me/2009/02/howto-fix-signaturekeyserver-problems.html](http://www.ubuntu-inside.me/2009/02/howto-fix-signaturekeyserver-problems.html)

Thanks - but I can't do rapidshare.

Any other way?

longtom

---

### Post by Ms_Angel_D on 2009-03-08
The file from that tutorial is this

```
#!/usr/bin/env perl
# Perl script to fix Launchpad PPA links and import required keys.
# VERSION: 1.3
#
# Requires: HTML::Parser IO::Socket::SSL
# sudo apt-get install libhtml-parser-perl libio-socket-ssl-perl
#
# Copyright (c) 2009 Savvas Radevic <vicedar@gmail.com>
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.
#
# UPDATES:
# 1.4:
#    * Fixed wrong check between @lpusers and $ENV{'http_proxy'}
# 1.3:
#    * Enlists errors (contacting the Launchpad site)
#    * Adds suggestions for proxy if errors found
#    * Using glob("$sourceparts/*.list") instead of regex \.list$ check
#    * Using LWP::UserAgent instead of LWP::Simple
#    * Using environment *_proxy fields
# 1.2:
#    * Added md5sum check for sources.list
#    * Added support for /etc/apt/sources.list.d/*.list
# 1.1:
#    * Added support for key format in edge.launchpad.net server.
#    * Needs IO::Socket::SSL
#
# Do NOT edit unless you know what you're doing!

use strict;
require LWP::UserAgent;
use IO::Socket::SSL;
use Digest::file qw(digest_file_hex);
my $get = LWP::UserAgent->new(
    timeout => 60, #Timeout after 60 seconds
    env_proxy => 1, #Acquire proxy settings
);

my $aptdir = '/etc/apt';
my $sourcelist = $aptdir.'/sources.list';
my $sourceparts = $aptdir.'/sources.list.d';
my $backupext = '.backup';
my $tmpfilename = '/tmp/lp_change.list';
my @lplink = ('http://launchpad.net/~','/+archive/ppa');
my (@allsources, @lpusers);

# Return .list files
@allsources = grep{ -f $_ } glob("$sourceparts/*.list");
# Add main source
if (-f $sourcelist) { push(@allsources, $sourcelist); }
print("Found apt source list files:\n  ".join("\n  ",@allsources)."\n");

foreach my $filename (@allsources) {
    my @new = ();
    print("\nChecking file $filename\n");
    open(S, $filename) or die $!;
    foreach my $l (<S>) {
        if ($l =~ m!^deb(?:-src)?\s+http://ppa.launchpad.net/(\S+)/ubuntu!i) {
            my $r = $1;
            if ($r !~ m!/ppa$!i) {
                $r =~ s!$!/ppa!i;
                $l =~ s!^(deb(?:-src)?\s+http://ppa.launchpad.net/)\S+(/ubuntu)!${1}${r}${2}!i;
                print("Detected/Fixed: $l");
            }
            else {
                print("Detected/Correct: $l");
            }
            $r =~ s!/ppa$!!i;
            # Look if user $r is already on @lpusers - if not, add
            my %lookup = map { $_ => undef } @lpusers;
            if (not exists $lookup{$r}) { push(@lpusers, $r); }
        }
        push(@new, $l);
    }

    close(S);
    open(W, ">$tmpfilename") or die $!;
    print W @new;
    close(W);
    if (digest_file_hex($tmpfilename, "MD5") != digest_file_hex($filename, "MD5")) {
        print("Detected differences between $tmpfilename and $filename\n");
        print("Moving temporary file as $filename\n");
        print("INFO: Enter your administrator password if asked\n\n");
        my @s = ('sudo', 'cp', '-f', $filename, $filename.$backupext);
        system(@s) == 0 or die("system @s failed: $?\n");
        my @s = ('sudo', 'mv', $tmpfilename, $filename);
        system(@s) == 0 or die("system @s failed: $?\n");
    }
    else {
        print("No change for $filename\n");
    }
}
print("\n");

if (defined($ENV{'http_proxy'})) {
    print("Detected http proxy: $ENV{http_proxy}\n");
}

if (defined(@lpusers)) {
    print("Will retrieve keys for: @lpusers\n");
}
else {
    print("\nNo Launchpad PPA links/users detected, exiting.\n");
}

my $i; # Error counter
my $getkey = GetKey->new;
foreach my $u (@lpusers) {
    my $url = $lplink[0].$u.$lplink[1];
    print("Attempting to get Launchpad key for $u: $url\n");
    my $htmlreply = $get->get($url);
    if ($htmlreply->is_success) {
        $getkey->parse($htmlreply->decoded_content);
    }
    else {
        my ($geterror) = $htmlreply->status_line;
        print "ERROR: $geterror\n";
        $i++;
    }
}

if (defined($i)) {
    print "$i errors detected while checking the Launchpad site.\n";
    print "Are you behind a proxy? Read these links:
    - http://www.gnu.org/software/wget/manual/html_node/Proxies.html
    - http://web.archive.org/www.fedoraforum.org/forum/printthread.php?t=742\n";
}

print "\nAll done.\n";


package GetKey;
use base qw(HTML::Parser);
my ($div_tag, $code_tag);
sub start {
    my ($self, $tag, $attr, $attrlist, $origtext) = @_;
    # If HTML tag is "a" (or "A")
    if ($tag =~ /^div$/i and $attr->{id} and $attr->{id} eq 'signing-key') {
        $div_tag = 1;
    }
    elsif ($tag =~ /^code$/i and $div_tag) {
        $code_tag = 1;
    }
}
sub text {
    my ($self, $plaintext) = @_;
    # If we're in the anchor tag, and text is "http" or "ftp"
    if ($div_tag and $code_tag) {
        #New LP uses 1024R/247D1CFF instead of D2BB86E0EBD0F0A43D4DB3A760D11217247D1CFF format
        if ($plaintext =~ m!/([\w\d]+)!i) { $plaintext = $1; }
        print("Found key: $plaintext\n");
        &importkey($plaintext);
    }
}
sub end {
    my ($self, $tag, $origtext) = @_;
    if ($tag =~ /^div$/i) { $div_tag = 0; }
    elsif ($tag =~ /^code$/i) { $code_tag = 0; }
}
sub importkey {
    my ($key) = @_;
    print("Adding $key to your username's gpg\n");
    my @a = ('gpg', '--keyserver', 'keyserver.ubuntu.com', '--recv-keys', $key);
    system(@a) == 0 or print("system @a failed: $?\n");
    
    print("Adding key to apt\n");
    my $b = "gpg --export --armor $key | sudo apt-key add -";
    print("INFO: Enter your administrator password if asked\n\n");
    my $command = `$b`;
    print("$command\n");
}
```

Just copy it to a text document and save it as change.pl

---

### Post by longtom on 2009-03-08
Wonderful,

but in the meantime I found [this](http://ubuntuforums.org/showthread.php?t=1056099) which appeared to do the trick.

longtom

---

