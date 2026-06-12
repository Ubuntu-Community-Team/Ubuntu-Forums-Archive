---
title: "Display .ARW (Sony) raw image thumbnails in nautlius"
date: 2009-09-02
forum: New to Ubuntu
---

### Post by humphreybc on 2009-09-02
Hi there,

I was wondering if it's possible to display .ARW file thumbnails in nautilus? I have gnome-raw-thumbnailer already installed, and I suspect this would work with Canon/Nikon .RAW files - but because I use a Sony A100 DSLR I work with .ARW files.

gThumb can't open these files, but F-Spot Viewer can so I can see the files when I double click on them, but I cannot see a preview of them.

Is there a way?

Thanks

---

### Post by illpig on 2009-11-05
*push*
pls community help us.

the only thing i found:
[http://www.rawtherapee.com/?mitem=3](http://www.rawtherapee.com/?mitem=3) downloaded -> extracted -> copied the .ARW into the new program-folder and i could see a thumbnail.
as you can see below. strange, isn`t it?

---

### Post by vispillo on 2010-01-09
This is a little late, and you may have found a different (and probably better) way of doing this, but I came across the same problem the other day and managed to get automatically generated thumbnails for Sony ARW files.

Requirements:
[LIST]
[*]dcraw
[*]exifautotran (package: libjpeg-tools)
[*]imagemagick
[/LIST]

Then you create a little script that takes two arguments - the path to the original ARW file and an output file name for the thumbnail. You could write this in any language you're familiar with - a simple shell script should suffice. However, I'm happiest using perl, so here's what I came up with (hacky, I know, but it works):

```
#!/usr/bin/perl -w

# strip the leading file:// protocol information
# this script will only work locally
my (undef,$infile)  = split(/file:\/\//,$ARGV[0]);
my $outfile = $ARGV[1];
# location of a temporary file to work on.
my $tmpfile = `mktemp`;
# decode location url (whitespaces,umlauts,etc)
$infile =~ s/\%([A-Fa-f0-9]{2})/pack('C', hex($1))/seg;
# extract the embedded thumbnail (640x480 jpg)
system("dcraw -e -c \"$infile\" > \"$tmpfile\"");
# rotate it
system("exifautotran \"$tmpfile\"");
# convert to a conveniently sized .png
system("convert \"jpg:$tmpfile\" -resize 128x128 png:$outfile");
# delete temporary file
unlink($tmpfile);
```

Save that script in a convenient location (I use ~/bin) and make it executable (e.g chmod +x ~/bin/arw-thumbnailer).

Then all you need to do is to tell Gnome to associate that script with Sony raw files (adjust the path to match your setup):

```
gconftool-2 -s /desktop/gnome/thumbnailers/image@x-sony-arw/command -t string "/path/to/arw-thumbnailer %u %o"
gconftool-2 -s /desktop/gnome/thumbnailers/image@x-sony-arw/enable -t boolean true
```

Like I said, there's probably a much more elegant solution to this, but this seems to work fairly well for the moment.

---

### Post by vasdjs on 2010-06-13
Hi, thread may be getting old, but I too have a sony camera A200 and work with ARW files. I have found that Digicam is great for displaying ARW's and can do slide shows too. My difficulty is now saving the ARW's as JPG's so that i can pass them on to others who don't use the ARW format. Any ideas? Ta

---

