---
title: "Public Key missing"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by dunbrokin on 2009-02-19
When I reload my packages in software sources I get this message....I would appreciate knowing what it means and how I can cure it (if it is important)


W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 28A8205077558DD0

Thanks.

---

### Post by blackgr on 2009-02-19
[http://ubuntuforums.org/showpost.php?p=6700382&postcount=66](http://ubuntuforums.org/showpost.php?p=6700382&postcount=66)

Execute the script kai after that do

sudo apt-get update and the errors will disappear

---

### Post by jerome1232 on 2009-02-19
You need to goto the ppa's overview pages and save their public key to a file then add it using the software sources tool.

For example if you have the Open Office ppa you would get the key from their overview page here [https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa)


Here's some instructions on how to do that.
[https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories](https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories)

All the keys are is a system for guaranteeing your getting your downloads from the source that you think your getting them from.

---

### Post by dunbrokin on 2009-02-19
> **blackgr said:**
> [http://ubuntuforums.org/showpost.php?p=6700382&postcount=66](http://ubuntuforums.org/showpost.php?p=6700382&postcount=66)

Execute the script kai after that do

sudo apt-get update and the errors will disappear

Sorry, what script kai?

---

### Post by dunbrokin on 2009-02-19
> **jerome1232 said:**
> 

For example if you have the Open Office ppa you would get the key from their overview page here [https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa)



How do I know which keys I am missing...i.e. which programs these errors relate to?

---

### Post by binbash on 2009-02-19
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

and run it at terminal : 

perl change.pl

---

### Post by jerome1232 on 2009-02-19
> **dunbrokin said:**
> How do I know which keys I am missing...i.e. which programs these errors relate to?

Well which ppa's did you add? Show us your sources.list

```
cat /etc/apt/sources.list | grep ppa
```

---

### Post by dunbrokin on 2009-02-19
> **jerome1232 said:**
> Well which ppa's did you add? Show us your sources.list



# deb [http://ppa.launchpad.net/googlegadgets/ubuntu](http://ppa.launchpad.net/googlegadgets/ubuntu) hardy main
# deb-src [http://ppa.launchpad.net/googlegadgets/ubuntu](http://ppa.launchpad.net/googlegadgets/ubuntu) hardy main
# deb [http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu) hardy main
# deb [http://ppa.launchpad.net/do-core/ubuntu](http://ppa.launchpad.net/do-core/ubuntu) hardy main
# deb-src [http://ppa.launchpad.net/do-core/ubuntu](http://ppa.launchpad.net/do-core/ubuntu) hardy main
deb [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) intrepid main
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) intrepid main
deb [http://ppa.launchpad.net/do-core/ppa/ubuntu](http://ppa.launchpad.net/do-core/ppa/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/do-core/ppa/ubuntu](http://ppa.launchpad.net/do-core/ppa/ubuntu) intrepid main

---

### Post by dunbrokin on 2009-02-19
pj@PJKING:~/Documents/scripts$ perl change.pl
Can't locate IO/Socket/SSL.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at change.pl line 110.
BEGIN failed--compilation aborted at change.pl line 110.
pj@PJKING:~/Documents/scripts$

---

### Post by dunbrokin on 2009-02-19
> **blackgr said:**
> [http://ubuntuforums.org/showpost.php?p=6700382&postcount=66](http://ubuntuforums.org/showpost.php?p=6700382&postcount=66)

Execute the script kai after that do

sudo apt-get update and the errors will disappear

Hmm did not seem to work...

pj@PJKING:~$ sudo apt-get update
[sudo] password for pj: 
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid/main Translation-en_NZ
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid/restricted Translation-en_NZ
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid Release.gpg                          
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid/main Translation-en_NZ               
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid/restricted Translation-en_NZ         
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]                           
Ign [http://dl.google.com](http://dl.google.com) stable/non-free Translation-en_NZ                     
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid/universe Translation-en_NZ           
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid/multiverse Translation-en_NZ         
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates Release.gpg                  
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates/main Translation-en_NZ       
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates/restricted Translation-en_NZ 
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates/universe Translation-en_NZ   
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_NZ 
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-security Release.gpg                 
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg                          
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_NZ            
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-security/main Translation-en_NZ      
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg [307B]                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_NZ                   
Ign [http://download.skype.com](http://download.skype.com) stable Release.gpg                               
Get:3 [http://dl.google.com](http://dl.google.com) stable Release [1300B]                              
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-security/restricted Translation-en_NZ
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-security/universe Translation-en_NZ  
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-security/multiverse Translation-en_NZ
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid Release                              
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates Release                      
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release.gpg                         
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Translation-en_NZ              
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release                              
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg [307B]                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_NZ                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_NZ                   
Get:5 [http://dl.google.com](http://dl.google.com) stable/non-free Packages [954B]                     
Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg [307B]                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_NZ                   
Get:7 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [27.6kB]                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-security Release                     
Ign [http://download.skype.com](http://download.skype.com) stable/non-free Translation-en_NZ                
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Translation-en_NZ          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release                             
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid/restricted Sources         
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid/main Sources               
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid/main Packages              
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid/restricted Packages        
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid/multiverse Sources         
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid/universe Sources           
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid/universe Packages          
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid/multiverse Packages        
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages                     
Get:8 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [27.6kB]                       
Get:9 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [27.6kB]            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates/main Packages                
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates/restricted Packages          
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates/restricted Sources           
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates/main Sources                 
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates/multiverse Sources           
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates/universe Sources             
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates/universe Packages            
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates/multiverse Packages          
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-security/main Packages               
Ign [http://download.skype.com](http://download.skype.com) stable Release                                   
Get:10 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [27.6kB]                      
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources                      
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                          
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-security/restricted Packages 
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-security/restricted Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-security/main Sources      
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-security/multiverse Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-security/universe Sources  
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-security/universe Packages 
Hit [http://download.skype.com](http://download.skype.com) stable/non-free Packages               
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-security/multiverse Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Sources
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Sources
Fetched 3368B in 3s (978B/s)
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 28A8205077558DD0
W: You may want to run apt-get update to correct these problems

---

### Post by jerome1232 on 2009-02-19
Okay useing google you can find the overview pages easily enough.

[https://launchpad.net/~googlegadgets/+archive/ppa](https://launchpad.net/~googlegadgets/+archive/ppa)
That one was commented out so you don't need to add it's key

[https://launchpad.net/~fta/+archive/ppa](https://launchpad.net/~fta/+archive/ppa)
also commented out so no need to add it's key


[https://launchpad.net/~do-core/+archive/ppa](https://launchpad.net/~do-core/+archive/ppa)

[https://launchpad.net/~tualatrix/+archive/ppa](https://launchpad.net/~tualatrix/+archive/ppa)

[https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa)

[https://launchpad.net/~kubuntu-members/+archive/ppa](https://launchpad.net/~kubuntu-members/+archive/ppa)


Those are all the ppa's you have so just make sure you have a key for each and your good.

---

### Post by dunbrokin on 2009-02-19
Thanks a million Jerome, that worked a treat.....:D

---

### Post by forger on 2009-02-20
[thread=1056099]**Update your Launchpad PPA repositories and apt keys**[/thread]

---

### Post by dunbrokin on 2009-02-20
> **forger said:**
> [thread=1056099]**Update your Launchpad PPA repositories and apt keys**[/thread]


Thanks for that..

---

