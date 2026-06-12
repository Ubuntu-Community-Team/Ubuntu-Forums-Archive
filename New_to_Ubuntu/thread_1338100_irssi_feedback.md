---
title: "irssi feedback?"
date: 2009-11-26
forum: New to Ubuntu
---

### Post by TironN on 2009-11-26
Hey guys,
Is there anyway to get some form of feedback (beep, ding, text on desktop?) when using irssi. Its annoying having to always look at the terminal while i do other things. So is there any way?
Thanks!

---

### Post by VCoolio on 2009-11-26
Yes, on the irssi scripts page look for alert or notify. I recommend [trigger]("http://wouter.coekaerts.be/site/irssi/trigger") though; you can use a trigger like this:

/trigger add -joins -channels '#ubuntu' -command 'exec notify-send -i blam.png "Ubuntu - $\N says:" "$\M";exec aplay -q ~/sound.wav >/dev/null 2>&1' 

This would show a popup and play a wav file every time someone enters #ubuntu (so this would be a very annoying trigger). Instead of aplay you could also use mplayer. Find sounds in /usr/share/sounds and search for dream sound theme on the internet, it has some nice ones to use.
For notify-send: the -i defines the icon, the first part between quotes the title and the second part the message, so: notify-send -i icon "Title" "Message here". Without a path the icon name is searched in your icon theme.

---

### Post by Soul-Sing on 2009-11-26
maybe this?: ```
/set bell_beeps ON /set beep_msg_level MSGS NOTICES DCC DCCMSGS HILIGHT
```

---

### Post by ilil on 2009-11-26
irssi can call Perl scripts when events occur. Here is one I use:

```

##
## Put me in ~/.irssi/scripts, and then execute the following in irssi:
##
##       /load perl
##       /script load notify
##

use strict;
use Irssi;
use vars qw($VERSION %IRSSI);

$VERSION = "0.01";
%IRSSI = (
    authors     => 'Luke Macken',
    contact     => 'lewk@csh.rit.edu',
    name        => 'notify.pl',
    description => 'TODO',
    license     => 'GNU General Public License',
    url         => 'http://www.csh.rit.edu/~lewk/code/irssi-notify',
);

sub notify {
    my ($dest, $text, $stripped) = @_;
    my $server = $dest->{server};
    # hilight or private
    return if (!$server || !($dest->{level} & (MSGLEVEL_HILIGHT|MSGLEVEL_MSGS)));

    #$stripped =~ s/[^a-zA-Z0-9 .,!?\@:\>]//g;
    my $target = $dest->{target};
    $stripped =~ s/[^a-zA-Z0-9 .,!?\@:\>]//g;
    # dont compare strings with == ! Use eq and ne !
    if( $target eq "NickServ" ) {
        $stripped = "Identifing with NickServ"; # dont want to see password as notice!
    }
    system("notify-send -t 10000 '$target' '$stripped'");
}

Irssi::signal_add('print text', 'notify');

```

This code shows yellow tooltips (due to 'notify-send' command) on desktop when message is sent to you. You can ajdust the command to play sound etc.

---

### Post by TironN on 2009-11-27
> **VCoolio said:**
> Yes, on the irssi scripts page look for alert or notify. I recommend [trigger]("http://wouter.coekaerts.be/site/irssi/trigger") though; you can use a trigger like this:

/trigger add -joins -channels '#ubuntu' -command 'exec notify-send -i blam.png "Ubuntu - $\N says:" "$\M";exec aplay -q ~/sound.wav >/dev/null 2>&1' 

This would show a popup and play a wav file every time someone enters #ubuntu (so this would be a very annoying trigger). Instead of aplay you could also use mplayer. Find sounds in /usr/share/sounds and search for dream sound theme on the internet, it has some nice ones to use.
For notify-send: the -i defines the icon, the first part between quotes the title and the second part the message, so: notify-send -i icon "Title" "Message here". Without a path the icon name is searched in your icon theme.

so if I did this:
/trigger add -all -command 'exec notify-send -i home/fergus/Pictures/pac.png "Hey!" "A message"

It should work? Because it gives me a syntax error..

---

### Post by VCoolio on 2009-11-27
> **TironN said:**
> so if I did this:
/trigger add -all -command 'exec notify-send -i home/fergus/Pictures/pac.png "Hey!" "A message"

It should work? Because it gives me a syntax error..

you forgot at least a / before home, so /home/fergus etc. and at the end you need an ending single quote. Try like this:

/trigger add -all -command 'exec notify-send -i /home/fergus/Pictures/pac.png "Hey!" "A message"'

---

### Post by andrew.46 on 2010-01-26
Hi TironM,

> **TironN said:**
> Is there anyway to get some form of feedback (beep, ding, text on desktop?) when using irssi.

I realise I am resurrecting an older thread here but you may be interested in the following post which describes and illustrates an easy solution to this problem:

[http://ubuntuforums.org/showpost.php?p=8720989&postcount=4](http://ubuntuforums.org/showpost.php?p=8720989&postcount=4)

All the best,

Andrew

---

