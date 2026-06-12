---
title: "No Pubkey!"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by nicesocks on 2009-02-21
I keep getting this error when running apt-get update: [color=red]```
NO_PUBKEY 28A8205077558DD0
```[/color]

now, i've googled that error, and learned i'm to do the following: ```
# sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
``` and i get the same error; ```
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 28A8205077558DD0
W: GPG error: http://archive.ubuntu.com intrepid Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems
```
typing: ```
sudo gpg --keyserver hkp://subkeys.pgp.net --recv-keys 28A8205077558DD0
``` nets ```
gpg: WARNING: unsafe ownership on configuration file `/home/nicesocks/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
```

what can i do to resolve this?  it means many a program won't work.  and i honestly don't know what i did that toggled this.  >_<

---

### Post by mkvnmtr on 2009-02-21
I don't know what you have done to cause this but I always go to the community docs page for Medibuntu and follow the instructions. I always just google it. They say to first input a command to ad the repository to your sources list and then another command to get the key. Then they ask to download some stuff and I click yes. Then after it is done I get the update. I think you might of done it in the wrong order. Find the page I spoke of and try it their way.

---

### Post by vikramaditya on 2009-02-21
Check this link...
[http://georgia.ubuntuforums.org/showpost.php?p=6649356&postcount=5](http://georgia.ubuntuforums.org/showpost.php?p=6649356&postcount=5)
worked for the folks in that thread (make sure to replace "$KEY" with "28A8205077558DD0")

---

### Post by binbash on 2009-02-22
save this as change.pl : 

```

#!/usr/bin/env perl
# Perl script to fix Launchpad PPA links and import required keys.
# VERSION: 1.2
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
# 1.2:
#    * Added md5sum check for sources.list
#    * Added support for /etc/apt/sources.list.d/*.list
# 1.1:
#    * Added support for key format in edge.launchpad.net server.
#    * Needs IO::Socket::SSL
#
# Do NOT edit unless you know what you're doing!

use strict;
use LWP::Simple qw(get);
use Digest::file qw(digest_file_hex);

my $aptdir = '/etc/apt';
my $sourcelist = $aptdir.'/sources.list';
my $sourceparts = $aptdir.'/sources.list.d';
my $backupext = '.backup';
my $tmpfilename = '/tmp/lp_change.list';
my @lplink = ('http://launchpad.net/~','/+archive/ppa');
my (@allsources, @lpusers);

# Return .list files
@allsources = grep{ -f $_ and /\.list$/ } glob("$sourceparts/*");
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

if (defined(@lpusers)) {
    print("Will retrieve keys for: @lpusers\n");
}
else {
    print("\nNo Launchpad PPA links/users detected, exiting.\n");
}

my $getkey = GetKey->new;
foreach my $u (@lpusers) {
    my $url = $lplink[0].$u.$lplink[1];
    print("Attempting to get Launchpad key for $u: $url\n");
    my $html = get($url);
    $getkey->parse($html);
}


package GetKey;
use base qw(HTML::Parser);
use IO::Socket::SSL;
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

then make it executable (chmod +x filename), then run it via : 

perl change.pl

---

### Post by forger on 2009-02-22
Or follow the proper guide here:
[thread=1056099]**Update your Launchpad PPA repositories and apt keys**[/thread]

---

### Post by nicesocks on 2009-02-27
i've tried everything here.  and i'm still getting this error when i sudo apt-get update:```
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures were invalid: BADSIG 28A8205077558DD0 Launchpad PPA for GNOME Do Core Team
W: GPG error: http://archive.ubuntu.com intrepid Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems
```
i love that it suggests i run apt-get update to correct this, even though that's what i ran to get this error.  cyclical humor is my favorite, i just don't like when machines do it.

---

### Post by Bios Element on 2009-02-27
I had the same bloody bug. I'm afraid I cannot remember exactly how I fixed it however. :( But basically what I did is I googled and found a blog post about it. It had a link to the correct PubKeys which I installed and it works fine now. Hope you figure it out!

---

### Post by forger on 2009-02-28
> **nicesocks said:**
> 
typing: ```
[COLOR="Red"]sudo gpg[/COLOR] --keyserver hkp://subkeys.pgp.net --recv-keys 28A8205077558DD0
``` nets ```
gpg: WARNING: unsafe ownership on configuration file `/home/nicesocks/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
```

what can i do to resolve this?  it means many a program won't work.  and i honestly don't know what i did that toggled this.  >_<


You **SHOULD NOT** use sudo and gpg! Just gpg, without sudo.

As I mentioned above, use this perl script:
[http://ubuntuforums.org/showthread.php?t=1056099](http://ubuntuforums.org/showthread.php?t=1056099)

---

### Post by ankon_sarkhel on 2009-02-28
me a total noob in this forum. Do not know how 2 post anew thread. Someone help me pls

---

### Post by forger on 2009-02-28
> **ankon_sarkhel said:**
> me a total noob in this forum. Do not know how 2 post anew thread. Someone help me pls

[http://ubuntuforums.org/forumdisplay.php?f=326](http://ubuntuforums.org/forumdisplay.php?f=326) see "New Thread"

---

