---
title: "Frozen Bubble Crashes on load"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by beastrace91 on 2009-02-15
When I try to load frozen-bubble it crashes out, in terminal I get this: ```
[SDL Init] SDL::Surface::new failed. Unsupported image format at /usr/lib/perl5/SDL/Surface.pm line 53.

```

Any ideas what I can do to fix this? I love this little game :)

~Jeff

---

### Post by RomeReactor on 2009-02-15
Hi. Did you install it from the repositories, or from their website?

---

### Post by ibuclaw on 2009-02-15
Did you run
```
sudo apt-get install frozen-bubble
```
?

Regards
Iain

---

### Post by beastrace91 on 2009-02-16
I installed it from repositories. I always install from there if I can. Any ideas?

~Jeff

---

### Post by unutbu on 2009-02-16
Please post the output to this command:
```
apt-cache depends frozen-bubble | awk '/Depends:/{print $2}' | sort | uniq | xargs apt-cache policy
```
It will show us what versions of the frozen-bubble dependencies are installed.

---

### Post by beastrace91 on 2009-02-16
The result:

```
jeff@jeff-ubuntu:~$ apt-cache depends frozen-bubble | awk '/Depends:/{print $2}' | sort | uniq | xargs apt-cache policy
fb-music-high:
  Installed: 0.1.2
  Candidate: 0.1.2
  Version table:
 *** 0.1.2 0
        500 http://us.archive.ubuntu.com intrepid/universe Packages
        100 /var/lib/dpkg/status
fb-music-low:
  Installed: (none)
  Candidate: 2.2.0-1ubuntu1~intrepid1
  Version table:
     2.2.0-1ubuntu1~intrepid1 0
        500 http://us.archive.ubuntu.com intrepid-backports/universe Packages
     2.1.0-2ubuntu3 0
        500 http://us.archive.ubuntu.com intrepid/universe Packages
frozen-bubble-data:
  Installed: 2.2.0-1ubuntu1~intrepid1
  Candidate: 2.2.0-1ubuntu1~intrepid1
  Version table:
 *** 2.2.0-1ubuntu1~intrepid1 0
        500 http://us.archive.ubuntu.com intrepid-backports/universe Packages
        100 /var/lib/dpkg/status
     2.1.0-2ubuntu3 0
        500 http://us.archive.ubuntu.com intrepid/universe Packages
libc6:
  Installed: 2.8~20080505-0ubuntu9
  Candidate: 2.8~20080505-0ubuntu9
  Version table:
 *** 2.8~20080505-0ubuntu9 0
        500 http://us.archive.ubuntu.com intrepid-updates/main Packages
        100 /var/lib/dpkg/status
     2.8~20080505-0ubuntu7 0
        500 http://us.archive.ubuntu.com intrepid/main Packages
libglib2.0-0:
  Installed: 2.18.2-0ubuntu2
  Candidate: 2.18.2-0ubuntu2
  Version table:
 *** 2.18.2-0ubuntu2 0
        500 http://us.archive.ubuntu.com intrepid-updates/main Packages
        100 /var/lib/dpkg/status
     2.18.2-0ubuntu1 0
        500 http://us.archive.ubuntu.com intrepid/main Packages
libpango1.0-0:
  Installed: 1.22.2-0ubuntu1
  Candidate: 1.22.2-0ubuntu1
  Version table:
 *** 1.22.2-0ubuntu1 0
        500 http://us.archive.ubuntu.com intrepid-updates/main Packages
        100 /var/lib/dpkg/status
     1.22.1-0ubuntu1 0
        500 http://us.archive.ubuntu.com intrepid/main Packages
libsdl1.2debian:
  Installed: 1.2.13-2ubuntu1
  Candidate: 1.2.13-2ubuntu1
  Version table:
 *** 1.2.13-2ubuntu1 0
        500 http://us.archive.ubuntu.com intrepid/main Packages
        100 /var/lib/dpkg/status
libsdl-mixer1.2:
  Installed: 1.2.8-4
  Candidate: 1.2.8-4
  Version table:
 *** 1.2.8-4 0
        500 http://us.archive.ubuntu.com intrepid/main Packages
        100 /var/lib/dpkg/status
libsdl-pango1:
  Installed: 0.1.2-4
  Candidate: 0.1.2-4
  Version table:
 *** 0.1.2-4 0
        500 http://us.archive.ubuntu.com intrepid/main Packages
        100 /var/lib/dpkg/status
libsdl-perl:
  Installed: 1.20.3dfsg-3
  Candidate: 1.20.3dfsg-3
  Version table:
 *** 1.20.3dfsg-3 0
        500 http://us.archive.ubuntu.com intrepid/universe Packages
        100 /var/lib/dpkg/status
perl:
  Installed: 5.10.0-11.1ubuntu2.2
  Candidate: 5.10.0-11.1ubuntu2.2
  Version table:
 *** 5.10.0-11.1ubuntu2.2 0
        500 http://us.archive.ubuntu.com intrepid-updates/main Packages
        500 http://security.ubuntu.com intrepid-security/main Packages
        100 /var/lib/dpkg/status
     5.10.0-11.1ubuntu2 0
        500 http://us.archive.ubuntu.com intrepid/main Packages
W: Unable to locate package <perlapi-5.10.0>

```

I see it is missing one at the end there when I try to apt-get that file I get the following: ```
jeff@jeff-ubuntu:~$ sudo apt-get install perlapi-5.10.0
[sudo] password for jeff: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package perlapi-5.10.0 is a virtual package provided by:
  perl-base 5.10.0-11.1ubuntu2.2
You should explicitly select one to install.
E: Package perlapi-5.10.0 has no installation candidate

```

How can I tell it the right one to get? Do you think this is causing the issue?

Thanks,
~Jeff

---

### Post by unutbu on 2009-02-16
I think the solution is to 
```

sudo apt-get purge frozen-bubble-data

```
Then go to System>Admin>Software Sources and turn off intrepid-backports.

Then type
```

sudo apt-get update
sudo apt-get install frozen-bubble-data

```
Tell us if that helps.

Explanation: I've installed frozen-bubble on an Intrepid machine, and compared my packages with yours. Here are the differences:
```

frozen-bubble-data
Yours: 2.2.0-1ubuntu1~intrepid1 intrepid-backports/universe
Mine: 2.1.0-2ubuntu3            intrepid/universe

libc6:
Yours: 2.8~20080505-0ubuntu9 intrepid-updates/main
Mine:  2.8~20080505-0ubuntu7 intrepid/main

libglib2.0-0:
Yours: 2.18.2-0ubuntu2 intrepid-updates/main
Mine: 2.18.2-0ubuntu1  intrepid/main

libpango1.0-0:
Yours: 1.22.2-0ubuntu1 intrepid-updates/main
Mine:  1.22.1-0ubuntu1 intrepid/main
```

I get the same error "W: Unable to locate package <perlapi-5.10.0>",
and since frozen-bubble runs fine for me, I think this error is irrelevant.

Your error refers to an "Unsupported image format". If you look at the code at 
/usr/lib/perl5/SDL/Surface.pm line 53, you'll see it is trying to load some image.

So which package is providing a file with an unsupported image format?
Of the four packages above, the obvious suspect is frozen-bubble-data.

I went to [http://packages.ubuntu.com/intrepid-backports/all/frozen-bubble-data/filelist](http://packages.ubuntu.com/intrepid-backports/all/frozen-bubble-data/filelist)
and compared the list of files in the intrepid-backports version of frozen-bubble-data to
the list of files provided by my version of frozen-bubble-data. 

The intrepid-backports version contains /usr/share/games/frozen-bubble/data/plasma.raw
while the intrepid/universe version does not. I'm guessing it is the raw file format which is unsupported.

---

### Post by beastrace91 on 2009-02-16
Removing and then regetting those files yeilds the same error message upon trying to load the game. I am open to any other ideas.

~Jeff

---

### Post by unutbu on 2009-02-16
Did you turn off intrepid-backports?
Did you check that you now have version 2.1.0-2ubuntu3 of frozen-bubble-data installed?
```

apt-cache policy frozen-bubble-data
```
If so, I'm stumped.

---

### Post by beastrace91 on 2009-02-17
```
jeff@jeff-ubuntu:~$ apt-cache policy frozen-bubble-data
frozen-bubble-data:
  Installed: 2.2.0-1ubuntu1~intrepid1
  Candidate: 2.2.0-1ubuntu1~intrepid1
  Version table:
 *** 2.2.0-1ubuntu1~intrepid1 0
        500 http://us.archive.ubuntu.com intrepid-backports/universe Packages
        100 /var/lib/dpkg/status
     2.1.0-2ubuntu3 0
        500 http://us.archive.ubuntu.com intrepid/universe Packages
```

I think I have the right one...
~Jeff

---

### Post by unutbu on 2009-02-17
Actually, I'm suggesting the opposite. :)  2.2.0-1ubuntu1~intrepid1 is the wrong version.  Remove this package, turn off intrepid backports, and then install version 2.1.0-2ubuntu3.

---

### Post by beastrace91 on 2009-02-17
Which repository is the "backports"? Don't want to comment out the wrong one.

~Jeff

---

### Post by unutbu on 2009-02-17
Click System>Admin>Software Sources.
Click the Updates tab
Disable the box that says "Unsupported updates (intrepid-backports).
Click close. I believe the app will then run "sudo apt-get update" for you, but if you want to be very sure, open a terminal and type
```

sudo apt-get update

```
manually. Remove frozen-bubble-data if you havent' already, and then reinstall the package. Since intrepid-backports is disabled, your machine should find and install the regular version. (2.1.0-2ubuntu3).

---

### Post by beastrace91 on 2009-02-18
Same error message after removing the data, disabling the backports and then redownloading it :(

~Jeff

---

### Post by unutbu on 2009-02-18
Okay, let's approach this from another direction then. 

Posted at [http://paste.ubuntu.com/119781/](http://paste.ubuntu.com/119781/) is a slightly edited version of /usr/lib/perl5/SDL/Surface.pm, the file which is aborting with the "Unsupported image format" error.

Some debugging code has been added which should give us some feedback on what files are being loaded. 

So how about try the following: 

```

cd /usr/lib/perl5/SDL
sudo mv Surface.pm Surface.pm-orig   # backup the original
sudo wget http://paste.ubuntu.com/119781/plain/ -O /usr/lib/perl5/SDL/Surface.pm
```

The wget command downloads my version of Surface.pm and saves it as /usr/lib/perl5/SDL/Surface.pm on your machine.

Then run frozen-bubble from the terminal:

```
frozen-bubble   

```
You might see lots of output, depending on how far the program gets before it crashes.
Most of it is irrelevant, but the last few lines will be telling. Please post the last 10 lines or so here. The last image it tries to load before crashing may give us a clue as to where the problem lies.

Once we figure out how to fix your problem, you can restore your original Surface.pm file by typing
```

cd /usr/lib/perl5/SDL
sudo mv Surface.pm-orig Surface.pm
```

---

### Post by beastrace91 on 2009-02-18
Output with your new file: ```
jeff@jeff-ubuntu:/usr/lib/perl5/SDL$ frozen-bubble
Constant subroutine main::NULL redefined at /usr/games/frozen-bubble line 57
	main::BEGIN() called at /usr/lib/perl5/SDL.pm line 57
	eval {...} called at /usr/lib/perl5/SDL.pm line 57
Constant subroutine FBLE::NULL redefined at /usr/share/perl5/FBLE.pm line 35
        [[ Frozen-Bubble-2.1.0 ]]

  http://www.frozen-bubble.org/

  Copyright (c) 2000-2006 The Frozen-Bubble Team.
 
    Artwork: Alexis Younes
             Amaury Amblard-Ladurantie
    Soundtrack: Matthias Le Bidan
    Design & Programming: Guillaume Cottenceau
    Level Editor: Kim and David Joham

  Originally sponsored by Mandriva <http://www.mandriva.com/>

  This program is free software; you can redistribute it and/or modify
  it under the terms of the GNU General Public License version 2, as
  published by the Free Software Foundation.

[SDL Init] Loading /usr/share/games/frozen-bubble/gfx/pinguins/window_icon_penguin.png... at /usr/lib/perl5/SDL/Surface.pm line 30.
SDL::Surface::new failed. Unsupported image format at /usr/lib/perl5/SDL/Surface.pm line 56.
```

Also thanks for all your help thus far :)
~Jeff

---

### Post by wolfen69 on 2009-02-18
do
```
cat /usr/lib/perl5/SDL/Surface.pm
```
and post output here.

here is mine:
```
# 
#	Surface.pm
#
#	A package for manipulating SDL_Surface *
#
#	Copyright (C) 2003 David J. Goehrig

package SDL::Surface;

use strict;
use SDL;

require SDL::Rect;
require SDL::Color;
require SDL::Palette;

use SDL::Event;

sub new {
	my $proto = shift;	
	my $class = ref($proto) || $proto;
	my %options = @_;
	my $self;

	verify (%options, qw/ -name -n -flags -fl -width -w -height -h -depth -d
				-pitch -p -Rmask -r -Gmask -g -Bmask -b -Amask -a
				-from -f /) if $SDL::DEBUG;
	
	if ( $options{-name} ne "" && exists $SDL::{IMGLoad} ) {		
	   $self = \SDL::IMGLoad($options{-name});	
	} else {
		my $f = $options{-flags}  	|| $options{-fl} 	|| SDL_ANYFORMAT();
		my $w = $options{-width} 	|| $options{-w}		|| 1;
		my $h = $options{-height} 	|| $options{-h}		|| 1;	
		my $d = $options{-depth} 	|| $options{-d}		|| 8;
		my $p = $options{-pitch} 	|| $options{-p}		|| $w*$d;              
		my $r = $options{-Rmask} 	|| $options{-r}	
			||  ( SDL::BigEndian() ? 0xff000000 : 0x000000ff );
		my $g = $options{-Gmask} 	|| $options{-g}
			||  ( SDL::BigEndian() ? 0x00ff0000 : 0x0000ff00 );
		my $b = $options{-Bmask} 	|| $options{-b}
			||  ( SDL::BigEndian() ? 0x0000ff00 : 0x00ff0000 );
		my $a = $options{-Amask} 	|| $options{-a}
			||  ( SDL::BigEndian() ? 0x000000ff : 0xff000000 );

		if ( $options{-from}|| $options{-f} ) { 
			my $src = $options{-from}|| $options{-f};
			$self = \SDL::CreateRGBSurfaceFrom($src,$w,$h,$d,$p,$r,$g,$b,$a);
		} else {
			$self = \SDL::CreateRGBSurface($f,$w,$h,$d,$r,$g,$b,$a);
		}
	}
	die "SDL::Surface::new failed. ", SDL::GetError()
		unless ( $$self);
	bless $self,$class;
	**[COLOR="Red"]return $self;[/COLOR]**
}

sub DESTROY {		
	SDL::FreeSurface(${$_[0]});
}

sub flags {
	SDL::SurfaceFlags(${$_[0]});
}

sub palette {
	SDL::SurfacePalette(${$_[0]});
}

sub bpp {
	SDL::SurfaceBitsPerPixel(${$_[0]});
}

sub bytes_per_pixel {
	SDL::SurfaceBytesPerPixel(${$_[0]});
}

sub Rshift {
	SDL::SurfaceRshift(${$_[0]});
}

sub Gshift {
	SDL::SurfaceGshift(${$_[0]});
}

sub Bshift {
	SDL::SurfaceBshift(${$_[0]});
}

sub Ashift {
	SDL::SurfaceAshift(${$_[0]});
}

sub Rmask {
	SDL::SurfaceRmask(${$_[0]});
}

sub Gmask {
	SDL::SurfaceGmask(${$_[0]});
}

sub Bmask {
	SDL::SurfaceBmask(${$_[0]});
}

sub Amask {
	SDL::SurfaceAmask(${$_[0]});
}

sub color_key {
	SDL::SurfaceColorKey(${$_[0]});
}

sub alpha {
	SDL::SurfaceAlpha(${$_[0]});
}

sub width {
	SDL::SurfaceW(${$_[0]});
}

sub height {
	SDL::SurfaceH(${$_[0]});
}

sub pitch {
	SDL::SurfacePitch(${$_[0]});
}

sub pixels {
	SDL::SurfacePixels(${$_[0]});
}

sub pixel {
	die "SDL::Surface::pixel requires a SDL::Color"
		if $_[3] && $SDL::DEBUG && !$_[3]->isa("SDL::Color");
	$_[3] ?
		new SDL::Color -color => SDL::SurfacePixel(${$_[0]},$_[1],$_[2],${$_[3]}) :
		new SDL::Color -color => SDL::SurfacePixel(${$_[0]},$_[1],$_[2]);
}

sub fill {
	die "SDL::Surface::fill requires a SDL::Rect object"
		unless !$SDL::DEBUG || $_[1] == 0 || $_[1]->isa('SDL::Rect');
	die "SDL::Surface::fill requires a SDL::Color object"
		unless !$SDL::DEBUG || $_[2]->isa('SDL::Color');
	if ($_[1] == 0 ) {
		SDL::FillRect(${$_[0]},0,${$_[2]});
	} else {
		SDL::FillRect(${$_[0]},${$_[1]},${$_[2]});
	}
}

sub lockp {
	SDL::MUSTLOCK(${$_[0]});
}

sub lock {
	SDL::SurfaceLock(${$_[0]});
}

sub unlock {
	SDL::SurfaceUnlock(${$_[0]});
}

sub update {
	my $self = shift;;
	if ($SDL::DEBUG) {
		for (@_) { 
			die "SDL::Surface::update requires SDL::Rect objects"
				unless $_->isa('SDL::Rect');
		}
	}
	SDL::UpdateRects($$self, map { ${$_} } @_ );
}

sub flip {
	SDL::Flip(${$_[0]});
}

sub blit {
	if ($SDL::DEBUG) {
		die "SDL::Surface::blit requires SDL::Rect objects"
			unless ($_[1] == 0 || $_[1]->isa('SDL::Rect'))
			&& ($_[1] == 0 || $_[3]->isa('SDL::Rect'));
		die "SDL::Surface::blit requires SDL::Surface objects"
			unless $_[2]->isa('SDL::Surface'); 
	}
	SDL::BlitSurface(map { $_ != 0 ? ${$_} : $_ } @_);
}

sub set_colors {
	my $self = shift;
	my $start = shift;
	for (@_) {
		die "SDL::Surface::set_colors requires SDL::Color objects"
			unless !$SDL::DEBUG || $_->isa('SDL::Color');
	}
	return SDL::SetColors($$self, $start, map { ${$_} } @_);
}

sub set_color_key {
	die "SDL::Surface::set_color_key requires a SDL::Color object"
		unless !$SDL::DEBUG || $_[2]->isa('SDL::Color');
	SDL::SetColorKey(${$_[0]},$_[1],${$_[2]});
}

sub set_alpha {
	SDL::SetAlpha(${$_[0]},$_[1],$_[2]);
}

sub display_format {
	my $self = shift;
	my $tmp = SDL::DisplayFormat($$self);
	SDL::FreeSurface ($$self);
	$$self = $tmp;
	$self;
}

sub rgb {
	my $self = shift;
	my $tmp = SDL::ConvertRGB($$self);
	SDL::FreeSurface($$self);
	$$self = $tmp;
	$self;
}

sub rgba {
	my $self = shift;
	my $tmp = SDL::ConvertRGBA($$self);
	SDL::FreeSurface($$self);
	$$self = $tmp;
	$self;
}

sub print {
	my ($self,$x,$y,@text) = @_;
	SDL::PutString( $$self, $x, $y, join('',@text));
}

sub save_bmp {
	SDL::SaveBMP( ${$_[0]},$_[1]);
}

sub video_info {
	shift;
	SDL::VideoInfo();
}

1;

__END__;

=pod 

=head1 NAME

SDL::Surface - a SDL perl extension

=head1 SYNOPSIS

  use SDL::Surface;
  $image = new SDL::Surface(-name=>"yomama.jpg");

=head1 DESCRIPTION

The L<SDL::Surface> module encapsulates the SDL_Surface* structure, and
many of its ancillatory functions.  It has a similar interface to the L<SDL::Surface>
class. Where it differs:

=over 4

=item *

All methods require SDL::* objects.  If $SDL::DEBUG is false, no type checks will be made.

=item *

C<SDL::Surface::set_color_key> takes a flag and an SDL::Color object only.

=back

=head1 AUTHOR

David J. Goehrig

=head1 SEE ALSO

L<perl> L<SDL::Rect> L<SDL::Color> L<SDL::Surface>

=cut

```

compare line 56 with yours. i've highlighted line 56 in red.

---

### Post by ibuclaw on 2009-02-18
Or maybe:
```
file /usr/share/games/frozen-bubble/gfx/pinguins/window_icon_penguin.png
```

To ensure that the file isn't corrupted ?
[PHP]
$ file window_icon_penguin.png
window_icon_penguin.png: PNG image data, 48 x 48, 8-bit/color RGB, non-interlaced
[/PHP]
[EDIT]
@wolfen69. That is what mine looks like. and **cpan install SDL::Surface** tells me its the most uptodate version.

Regards
Iain

---

### Post by beastrace91 on 2009-02-18
Here is the output: ```
jeff@jeff-ubuntu:~$ cat /usr/lib/perl5/SDL/Surface.pm
# 
#	Surface.pm
#
#	A package for manipulating SDL_Surface *
#
#	Copyright (C) 2003 David J. Goehrig

package SDL::Surface;

use strict;
use SDL;

require SDL::Rect;
require SDL::Color;
require SDL::Palette;

use SDL::Event;

sub new {
	my $proto = shift;	
	my $class = ref($proto) || $proto;
	my %options = @_;
	my $self;

	verify (%options, qw/ -name -n -flags -fl -width -w -height -h -depth -d
				-pitch -p -Rmask -r -Gmask -g -Bmask -b -Amask -a
				-from -f /) if $SDL::DEBUG;

	if ( $options{-name} ne "" && exists $SDL::{IMGLoad} ) {		
	    warn "Loading $options{-name}...";
	    $self = \SDL::IMGLoad($options{-name});	
	} else {
		my $f = $options{-flags}  	|| $options{-fl} 	|| SDL_ANYFORMAT();
		my $w = $options{-width} 	|| $options{-w}		|| 1;
		my $h = $options{-height} 	|| $options{-h}		|| 1;	
		my $d = $options{-depth} 	|| $options{-d}		|| 8;
		my $p = $options{-pitch} 	|| $options{-p}		|| $w*$d;              
		my $r = $options{-Rmask} 	|| $options{-r}	
			||  ( SDL::BigEndian() ? 0xff000000 : 0x000000ff );
		my $g = $options{-Gmask} 	|| $options{-g}
			||  ( SDL::BigEndian() ? 0x00ff0000 : 0x0000ff00 );
		my $b = $options{-Bmask} 	|| $options{-b}
			||  ( SDL::BigEndian() ? 0x0000ff00 : 0x00ff0000 );
		my $a = $options{-Amask} 	|| $options{-a}
			||  ( SDL::BigEndian() ? 0x000000ff : 0xff000000 );

		if ( $options{-from}|| $options{-f} ) { 
			my $src = $options{-from}|| $options{-f};
			warn "Loading $src...";
			$self = \SDL::CreateRGBSurfaceFrom($src,$w,$h,$d,$p,$r,$g,$b,$a);
		} else {
			warn "Loading ($f,$w,$h,$d,$r,$g,$b,$a)...";
			$self = \SDL::CreateRGBSurface($f,$w,$h,$d,$r,$g,$b,$a);
		}
	}
	die "SDL::Surface::new failed. ", SDL::GetError()
		unless ( $$self);
	bless $self,$class;
	return $self;
}

sub DESTROY {		
	SDL::FreeSurface(${$_[0]});
}

sub flags {
	SDL::SurfaceFlags(${$_[0]});
}

sub palette {
	SDL::SurfacePalette(${$_[0]});
}

sub bpp {
	SDL::SurfaceBitsPerPixel(${$_[0]});
}

sub bytes_per_pixel {
	SDL::SurfaceBytesPerPixel(${$_[0]});
}

sub Rshift {
	SDL::SurfaceRshift(${$_[0]});
}

sub Gshift {
	SDL::SurfaceGshift(${$_[0]});
}

sub Bshift {
	SDL::SurfaceBshift(${$_[0]});
}

sub Ashift {
	SDL::SurfaceAshift(${$_[0]});
}

sub Rmask {
	SDL::SurfaceRmask(${$_[0]});
}

sub Gmask {
	SDL::SurfaceGmask(${$_[0]});
}

sub Bmask {
	SDL::SurfaceBmask(${$_[0]});
}

sub Amask {
	SDL::SurfaceAmask(${$_[0]});
}

sub color_key {
	SDL::SurfaceColorKey(${$_[0]});
}

sub alpha {
	SDL::SurfaceAlpha(${$_[0]});
}

sub width {
	SDL::SurfaceW(${$_[0]});
}

sub height {
	SDL::SurfaceH(${$_[0]});
}

sub pitch {
	SDL::SurfacePitch(${$_[0]});
}

sub pixels {
	SDL::SurfacePixels(${$_[0]});
}

sub pixel {
	die "SDL::Surface::pixel requires a SDL::Color"
		if $_[3] && $SDL::DEBUG && !$_[3]->isa("SDL::Color");
	$_[3] ?
		new SDL::Color -color => SDL::SurfacePixel(${$_[0]},$_[1],$_[2],${$_[3]}) :
		new SDL::Color -color => SDL::SurfacePixel(${$_[0]},$_[1],$_[2]);
}

sub fill {
	die "SDL::Surface::fill requires a SDL::Rect object"
		unless !$SDL::DEBUG || $_[1] == 0 || $_[1]->isa('SDL::Rect');
	die "SDL::Surface::fill requires a SDL::Color object"
		unless !$SDL::DEBUG || $_[2]->isa('SDL::Color');
	if ($_[1] == 0 ) {
		SDL::FillRect(${$_[0]},0,${$_[2]});
	} else {
		SDL::FillRect(${$_[0]},${$_[1]},${$_[2]});
	}
}

sub lockp {
	SDL::MUSTLOCK(${$_[0]});
}

sub lock {
	SDL::SurfaceLock(${$_[0]});
}

sub unlock {
	SDL::SurfaceUnlock(${$_[0]});
}

sub update {
	my $self = shift;;
	if ($SDL::DEBUG) {
		for (@_) { 
			die "SDL::Surface::update requires SDL::Rect objects"
				unless $_->isa('SDL::Rect');
		}
	}
	SDL::UpdateRects($$self, map { ${$_} } @_ );
}

sub flip {
	SDL::Flip(${$_[0]});
}

sub blit {
	if ($SDL::DEBUG) {
		die "SDL::Surface::blit requires SDL::Rect objects"
			unless ($_[1] == 0 || $_[1]->isa('SDL::Rect'))
			&& ($_[1] == 0 || $_[3]->isa('SDL::Rect'));
		die "SDL::Surface::blit requires SDL::Surface objects"
			unless $_[2]->isa('SDL::Surface'); 
	}
	SDL::BlitSurface(map { $_ != 0 ? ${$_} : $_ } @_);
}

sub set_colors {
	my $self = shift;
	my $start = shift;
	for (@_) {
		die "SDL::Surface::set_colors requires SDL::Color objects"
			unless !$SDL::DEBUG || $_->isa('SDL::Color');
	}
	return SDL::SetColors($$self, $start, map { ${$_} } @_);
}

sub set_color_key {
	die "SDL::Surface::set_color_key requires a SDL::Color object"
		unless !$SDL::DEBUG || $_[2]->isa('SDL::Color');
	SDL::SetColorKey(${$_[0]},$_[1],${$_[2]});
}

sub set_alpha {
	SDL::SetAlpha(${$_[0]},$_[1],$_[2]);
}

sub display_format {
	my $self = shift;
	my $tmp = SDL::DisplayFormat($$self);
	SDL::FreeSurface ($$self);
	$$self = $tmp;
	$self;
}

sub rgb {
	my $self = shift;
	my $tmp = SDL::ConvertRGB($$self);
	SDL::FreeSurface($$self);
	$$self = $tmp;
	$self;
}

sub rgba {
	my $self = shift;
	my $tmp = SDL::ConvertRGBA($$self);
	SDL::FreeSurface($$self);
	$$self = $tmp;
	$self;
}

sub print {
	my ($self,$x,$y,@text) = @_;
	SDL::PutString( $$self, $x, $y, join('',@text));
}

sub save_bmp {
	SDL::SaveBMP( ${$_[0]},$_[1]);
}

sub video_info {
	shift;
	SDL::VideoInfo();
}

1;

__END__;

=pod 

=head1 NAME

SDL::Surface - a SDL perl extension

=head1 SYNOPSIS

  use SDL::Surface;
  $image = new SDL::Surface(-name=>"yomama.jpg");

=head1 DESCRIPTION

The L<SDL::Surface> module encapsulates the SDL_Surface* structure, and
many of its ancillatory functions.  It has a similar interface to the L<SDL::Surface>
class. Where it differs:

=over 4

=item *

All methods require SDL::* objects.  If $SDL::DEBUG is false, no type checks will be made.

=item *

C<SDL::Surface::set_color_key> takes a flag and an SDL::Color object only.

=back

=head1 AUTHOR

David J. Goehrig

=head1 SEE ALSO

L<perl> L<SDL::Rect> L<SDL::Color> L<SDL::Surface>

=cut
```

~Jeff

---

### Post by youbuntu on 2009-12-04
What a faff about for such a rubbish game - the developers of the game should fix this!!!!.

---

### Post by beastrace91 on 2009-12-04
Does this issue still exist? If so WOW this thread is from back when I was still running Ibex :o

~Jeff

---

