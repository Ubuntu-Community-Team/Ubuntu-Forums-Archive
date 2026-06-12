---
title: "Dynamic Host List"
date: 2008-07-24
forum: Networking &amp; Wireless
---

### Post by Windsurfer619 on 2008-07-24
Hi, I was wondering if anyone knows a good way I could add/remove entries from the host list either with a script, or (preferably) automatically when I connect to an access point.

---

### Post by Windsurfer619 on 2008-08-25
Well, no one answered, so I made a simple GTK perl script to do it for me:

```
#!/usr/bin/perl
# by Adam
use warnings;
use strict;

use Gtk2 '-init';
use Glib qw/TRUE FALSE/;

my $main = Gtk2::Window->new('toplevel');
$main->set_position('center');
$main ->set_title('Change Hosts');
$main ->signal_connect(delete_event => \&delete_event);
$main ->set_border_width(15); #this is like CSS' padding, not border

my $box1 = Gtk2::VBox->new(FALSE, 0); #I don't know what these arguments do
$main->add($box1);

my $button1 = Gtk2::Button->new("I'm home");
$button1->signal_connect(clicked => \&host_local);
$box1 -> pack_start($button1, TRUE, TRUE, 0); #what are these arguments?

$button1->show; #this tells Gtk that our button preps are done. Cool.

$button1 = Gtk2::Button->new("I'm not home"); #NEW POINTER, SAME VARIABLE
$button1->signal_connect(clicked => \&host_remote);
$box1 -> pack_start($button1, TRUE, TRUE, 0);

$button1->show;

$box1->show; #Box is done being composed. Send to higher level to get rendered.

$main->show; #show the window! :D

Gtk2->main;

0; #frig I keep forgetting this



sub delete_event
{
    Gtk2->main_quit;
    return FALSE;
}

sub host_remote
{
    exec ("gksudo cp /home/adam/Scripts/GTK2/hosts.remote /etc/hosts") || die "Cannot change hosts file: $!\n";
    
    
}

sub host_local
{
    exec ("gksudo cp /home/adam/Scripts/GTK2/hosts.local /etc/hosts") || die "Cannot change hosts file: $!\n";
    
    
    
}

```

Not sure if this is totally correct code... but it works the way I wanted :)

To set it up, replace the two lines on the bottom with where your replacement host files are. I bound this script to ALT-H for easy access.

---

