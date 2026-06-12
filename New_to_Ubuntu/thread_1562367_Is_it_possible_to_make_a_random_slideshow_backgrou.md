---
title: "Is it possible to make a random slideshow background using a .xml file"
date: 2010-08-27
forum: New to Ubuntu
---

### Post by trikster_x on 2010-08-27
I have made a slideshow in 10.04 using the preinstalled slideshow's  .xml file as a template, and that was fairly simple.  I am not familiar with the .xml programming language and was wondering if there was a way to pull a random background from a set directory or a predefined list of images that I can modify on the fly.  I understand that there are probably a myriad of programs that can do this.  However, the computer I want to use this on is going to play double duty as a digital picture frame and a media center in my living room and I would prefer to make it as difficult as possible to change what can be displayed on the main screen.  Obviously an easy to use GUI would completely defeat that.  Mainly I want to know if it is a big task to call files randomly in the xml language.  If not, what would be the most efficient method for this task?  

I'll be doing more research on the internet and if I find a working solution before anyone throws a nice guide or their own template on this thread, I'll post my xml template for anyone interested in this method to use.

---

### Post by dv3500ea on 2010-08-27
XML is a data format not a programming language.

You can create a script using bash|perl|ruby|python|... to do this by calling the command 'gconftool-2' command.

I wrote a script ages ago using perl (because I get bored of my wallpaper easily :) ). You can use this if you want.

```

#!/usr/bin/perl -w
#This program is public domain.
#command line options:
#
#		random-wallpaper.pl
#	starts the wallpaper switcher
#		random-wallpaper.pl go 1
#	allows cycling of wallpaper
#		random-wallpaper.pl go 1
#	stops the cycling of wallpaper
#		random-wallpaper.pl switch
#	switches to a random wallpaper
#		random-wallpaper.pl frequency t
#	sets the time between different wallpapers to t seconds
#		random-wallpaper.pl selection
#	opens the folder of random wallpapers
#
#To install this file, copy it to /usr/bin (or another folder in your $PATH):
#	sudo cp random-wallpaper.pl /usr/bin/random-wallpaper.pl
#Make it executable:
#	sudo chmod +x /usr/bin/random-wallpaper.pl
#Edit the random wallpapers:
#	random-wallpaper.pl selection
#You may want to add 'random-wallpaper.pl' to your startup.
use strict;

my $FREQ = 20;
my $GO = 1;

unless (-e "$ENV{HOME}/.random_wallpaper/") {
	mkdir "$ENV{HOME}/.random_wallpaper/" || die $!
}

srand(time());
my @potential = glob("$ENV{HOME}/.random_wallpaper/*");

sub rand_wallpaper {
	my $i = int(rand() * @potential);
	system("gconftool-2 --type string --set /desktop/gnome/background/picture_filename '$potential[$i]'");
	print "$potential[$i]\n";
}

sub get_config {
	open (my $in, '<', "$ENV{HOME}/.random_wallpaper.conf") || die $!;
	my $txt = '';
	while (<$in>) {
		$txt .= $_;
	}
	my @list = split(/\n/, $txt);
	my %opts;
	foreach (@list) {
		$_ =~ m/(.*) (.*)/;
		$opts{$1} = $2;
	}
	return %opts;
}

sub set_config {
	open (my $out, '>', "$ENV{HOME}/.random_wallpaper.conf") || die $!;
	my %opts = @_;
	foreach (keys(%opts)) {
		print $out "$_ $opts{$_}\n";
	}
	close $out;
}

sub use_config {
	my %conf = get_config();
	$FREQ = $conf{'FREQ'}+0;
	$GO = $conf{'GO'}+0;
	@potential = glob("$ENV{HOME}/.random_wallpaper/*");
}

if (@ARGV) {
	if ($ARGV[0] eq 'frequency') {
		my %opts = get_config();
		$opts{'FREQ'} = $ARGV[1];
		set_config(%opts);
	}
	if ($ARGV[0] eq 'go') {
		my %opts = get_config();
		$opts{'GO'} = $ARGV[1];
		set_config(%opts);
	}
	if ($ARGV[0] eq 'selection') {
		system("xdg-open $ENV{HOME}/.random_wallpaper/");
	}
	if ($ARGV[0] eq 'switch') {
		rand_wallpaper();
	}
        exit;
}

if (@potential) {
	while (1) {
		use_config();
		print "GO=$GO\nFREQ=$FREQ\n";
		if ($GO) {
			rand_wallpaper();
		}
		sleep($FREQ);
	}
} else {
	warn "No files\n";
}



```

---

### Post by trikster_x on 2010-08-27
Thanks for the suggestion.  Doing some digging I found out very quickly that doing what I wanted with an xml file is possible but a bit too complex for me.  I did however manage to make a bash script that I can set to run on login that will choose a random jpg from a given directory and apply it as the wall paper.  The script was amazingly simple once I found the bash command to change backgrounds:

```
#! /bin/bash
while :
 do
   files=(/usr/share/backgrounds/*/*.jpg)        # create an array of the files in a given directory.  Wild cards can be used here to look for files in subdirectories of any given directory.
   N=${#files[@]}          # Number of members in the array
   ((N=RANDOM%N))
   randomfile=${files[$N]}



   gconftool-2 --type string --set /desktop/gnome/background/picture_filename $randomfile  # set the file to use as a background and update background

   sleep 10 # chooses the next image every 10 seconds.  Simply change the number to change duration.
 done
```

The whole script is set in a loop that has no exit so the images will keep cycling infinitely.  I tried to work in the link command to keep the background selection in the appearances menu from getting too cluttered, but the background wouldn't update while the command was present.  If anyone has any suggestions for adding a link command, let me know and I'll try it.

---

### Post by jarv on 2010-12-26
Similar script, added a couple for loops to specify directories and extensions (will follow directories recursively)


```

#!/bin/bash

extensions="jpg gif png"
directories=" 
             /some/dir
             /another/dir  
             /usr/share/pixmaps/backgrounds/gnome/
            "

for extension in $extensions
do
    for directory in $directories
    do
        files=`find $directory -name "*.$extension"`
        for file in $files
        do
            file_array=( "${file_array[@]}" $file )
        done

    done
done
cnt=${#file_array[@]}
((rnd=RANDOM%cnt))
rndpic=${file_array[$rnd]}
gconftool-2 --type string --set /desktop/gnome/background/picture_filename $rndpic

```

---

### Post by kgarbutt on 2010-12-26
If all you want to do is show different photos on your desktop, you can use gphotoframe. GNOME Photo Frame is a photo frame gadget for the GNOME Desktop. It shows pictures on the desktop from multiple sources such as local folders, F-Spot databases, Flickr and more.

You can download a deb file here:

[http://code.google.com/p/gphotoframe/downloads/list](http://code.google.com/p/gphotoframe/downloads/list)

---

