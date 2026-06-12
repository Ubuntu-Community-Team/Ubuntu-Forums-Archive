---
title: "Dynamic Hosts file?"
date: 2008-09-04
forum: Networking &amp; Wireless
---

### Post by pi_31415926535898 on 2008-09-04
Hello,

[I apologize if this is posted elsewhere -- I searched, but saw nothing matching my issue.]

My problem is this:

I have my own domain and my own mail server, which both work fine, and for which I have edited my Hosts file to accommodate "friendly" URLs for each. That being said, I just got a new laptop for school, and (obviously) my Hosts file entries are invalid when I am on campus, or in any Hotspot other than my own network at home.

I tried writing a shell script to edit the Hosts file for this particular line, but a) I'm new to Linux of all flavors, and b) scripts are understandably restricted from running as root (unless wrapped).

Does anyone have a reasonably simple solution, which will allow me to dynamically edit my Hosts file based on my IP address (or act as a switch regardless of my IP address)? I managed to write a batch file in Windows Vista which functions quite well (and is a testament to how easily malicious code could gain access to the Hosts file, really), but my Linux knowledge is weak and pitiful, so I defer to the experience and wisdom in this forum.

Thanks in advance,

--
Stan

---

### Post by pi_31415926535898 on 2008-09-04
<bump>

Nobody? Somebody? Please?

--
Stan

---

### Post by Windsurfer619 on 2008-09-04
Hi! I've created a program just to fix this. The thread I originally posted it in is [here .]("http://ubuntuforums.org/showpost.php?p=5661181&postcount=2")
To use it, first install libgtk2-perl by finding it in synaptic or typing the following in a terminal: [php]sudo apt-get install libgtk2-perl[/php]Following that, copy my program into a text file on your hard drive, preferably calling it something that ends in a .pl. Make sure you make it executable (This can be done by right-clicking and going to properties)
My program:
[php]&#65279;
#copy after this line... those numbers shouldn't be here. Glitch with ubuntuforums, I guess

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
#THIS IS THE FIRST LINE YOU NEED TO CHANGE
    
    
}

sub host_local
{
    exec ("gksudo cp /home/adam/Scripts/GTK2/hosts.local /etc/hosts") || die "Cannot change hosts file: $!\n";
    # THIS IS THE SECOND LINE YOU NEED TO CHANGE
    
    
}[/php]The brunt of the program happens in the last few lines. It executes a simple bash command copying a file onto the current hosts file using sudo privileges. To fix it for your uses, create the two seperate hosts files you wish to use, and replace /home/adam/Scripts/GTK2/hosts.remote with the path to the one you want to use when away from home, and /home/adam/Scripts/GTK2/hosts.local to the path to the hosts file you wish to use when you are at home.

Now, for security reasons, you shouldn't keep any of these files in your home folder or writable by anyone except root. If you need help with that... let me know.

---

### Post by pi_31415926535898 on 2008-11-01
I realize it's been a while, and perhaps no one has even cared to look at this thread, but I discovered the built-in and ridiculously simple solution...

In "Manual Configuration" for the network, I merely configured my laptop for my home (secure) wireless connection, and saved it as a "Location". Following this, I manually edited the Hosts file (using gedit -- not using the GUI Hosts file editor in Network) to have the appropriate entries for this location.

Then, I went back to "Manual Configuration" and configured my wireless settings for roaming, and again saved this configuration as a "Location". Again, I manually edited the Hosts file to have the appropriate entries (which I commented out, in this case) using gedit.

Problem solved! Now I need only to unlock "Manual Configuration" and then select and apply the appropriate location. No more editing Hosts every time I go anywhere!

If anybody is as new as I am, this should help. For all you experienced jerks who are laughing at me already, I quote Han:

[INDENT]*Laugh it up, fuzzball.*[/INDENT]

I'll get there...

:)

--
Stan

---

