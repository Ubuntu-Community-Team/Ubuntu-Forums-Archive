---
title: "*BUG* ?(maybe 3)? 1 Lclick on &quot;GNUsound&quot; forces instant log out !"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by Ronok on 2009-02-11
*BUG* ?(maybe)? 
I am still new to Ubuntu 
But I think I found a problem... maybe 3 ?

**#2**
I thought I should try the:
applications > Programing > Bug report tool
but I got "Either --appname or --package arguments are required." message
and 
**#3**
applications > system tools > Report a problem
starts a "title" in the lower panel... then absolutely disappears 
what started this was
**#1**
when I left click on:
applications > sound & Video > "[**GNUsound**]("http://www.gnu.org/software/gnusound/")" 
it forces instant log out ! in less than 1 second it is black screen
then the welcome screen, with drums, log back in, and all open things are closed or gone

I am happy with Ubuntu 8.10 over all
and haven't had any other applications
do the force quit thing
I wanted to cut up some ".wav" files
maybe there is a better program?
ok let me know How can I help?

---

### Post by cariboo on 2009-02-11
You can create a bug report, by going to [Launchpad]("http://bugs.launchpad.net/"), and creating an account, then report your bug.

I see there is a package in the repositories called mhwavedit.

Jim

---

### Post by alfu on 2009-08-27
Not much help, but instant logout happens to me too, on a Toshiba Satellite notebook, simply by starting GNUsound.  

Not sure I have all the dependencies loaded because Update Manager is stuck in a "Not all updates can be installed" loop.  I let UM do its suggested partial install twice, but now I just smack it back down.  Anyhow it seems that GNUsound should not just restart.  I do have 'JACK Control' installed.

Before the restart, I get a black screen for about split second with white text, which I presume is the crash dialog.  The GNUsound readme file has no clue what it is named or where it resides.  I notice on the GNUsound website that the latest rev is July 2008, so it may be a dead project.

Starting GNUsound from the terminal with --help shows a 'disable crash dialog' option which is not currently useful.

A "GNUsound" text document states:

?package(gnusound): needs="X11"\
  section="Applications/Sound" \
  title="GnuSound" \
  command="/usr/bin/gnusound" \
  icon="/usr/share/gnusound/gnusound-icon.xpm"

so perhaps there is a missing X11 component. Installed xmix X11-based interface to the Linux sound driver mixer -- that did not help.

Also, Synaptic shows no application titled 'mhwavedit'.

---

### Post by Ronok on 2010-02-11
I am now using Ubuntu 9.10 (karmic)
and have had overall smooth sailing with 
Ubuntu over the last year

if someone stumbles on this looking for: 
"**edit .wav files**"

go to:
applications> "ubuntu software centre"

Audacity
Rezound
Jokosher
Ardour

I Use & like them all

[SIZE="1"][http://www.gongkuo.com/index.htm]("http://www.gongkuo.com/index.htm")[/SIZE]

---

