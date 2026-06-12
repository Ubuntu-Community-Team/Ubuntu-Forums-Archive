---
title: "Netatalk 2.0.5 install/upgrade Karmic"
date: 2009-11-30
forum: New to Ubuntu
---

### Post by k()()zmi4 on 2009-11-30
Hi!

I'm having problems with netatalk-2.0.5 installation. 
I've tried 2.0.4 using [_this_]("http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/") method described and all went fine, I suppose...(got my afp shares configures flawlessly, etc.)
With 2.0.5 I've downloaded the .bz2 package and tried the "./configure - make - make install" way.
The installation as far as I'm aware went ok, but in the end I figured it installed to /usr/local (?). So I couldn't configure it to my needs and upon removing I end up with a message saying the package could not be removed since it couldn't be found.
As I understand it installs some other way compared to 2.0.4 and doesn't actually integrate into OS (?). To my understanding I probably have to run ./configure with some options (maybe directing the paths(?), but I know *very* little 'bout which ones I should choose and how to properly add 'em((
On the other hand I may as well be wrong (I'm only a Linux starter and this whole thing makes me very excited when somethin' starts to work)).. 

So any suggestions would be greatly appreciated 'bout fresh install of 2.0.5 or upgrade over a working 2.0.4 on Karmic .15 kernel since I'm quite interested 'bout *a* feature added to .5 release;)

Thx in advance!
Steven

_***EDIT:***_ The solution was found at a Debian site. I've found a netatalk-2.0.5-1 files which were downloadable *and* linked to a corresponding repository. 

Since I was pretty much sure I had nothing showing up upon 'netatalk' search in Synapse, except for 2.0.4rc3 version, I gave it a try... After I added the rep and updated, I got a message, tellin' me I didn't have a ppa key for that rep (that's another thing to consider gettin', anyone know where, maybe and how???:rolleyes:) But.. the 'netatalk-2.0.5-1' *did* show up in Synapse, so I installed it the 'easy' way)))

Then I configured it and now am enjoying my afp shares, including that 'feature added to .5 release' (allready did a 6Gb backup to a time machine shared volume over wireless to a fat:o formatted volume (only one available for testin') - fingers crossed;)

***_UPDATE:_*** For those of you having problems, regarding 'avahi .local domain' (message at startup), making you  restart the daemon manually to get Bonjour-like service running - [_*here's a place to go!*_]("http://www.ubuntu.com/getubuntu/releasenotes/904#Avahi%20will%20not%20start%20if%20a%20.local%20domain%20is%20present") Strange... the solution was so close, but I searched for it for 2 days:lol: Well at least now it's working after reboots, and no annoying messages poppin' up:D

Thanx 4 not answerin' - I got a full orgasm resolving this thing myself:P
ubuntu's getting more fun each day!
cheers!

---

### Post by Ryan Gardner on 2009-12-01
What was the URL / PPA you used to get Netatalk 2.0.5 installed? Did you have to rebuild from source to get the encrypted passwords working like you have to with 2.0.4?

---

### Post by k()()zmi4 on 2009-12-01
> **Ryan Gardner said:**
> What was the URL / PPA you used to get Netatalk 2.0.5 installed? Did you have to rebuild from source to get the encrypted passwords working like you have to with 2.0.4?

'deb [http://ftp.de.debian.org/debian](http://ftp.de.debian.org/debian) sid main'  - added to '/etc/apt/sources.list'

You'll find netatalk [_here_]("http://packages.debian.org/sid/netatalk") - bottom of the page - select appropriate architecture, following the link you'll find a page with  the above ftp address, as well as the option to go easy and get a .deb package (double-click install) straight off the ftp server close to you (I found 'bout that a little later :redface:)

the only thing 'bout this debian source is that they (netatalk 2.0.5-) are in "sid" section marked "unstable", so bear that in mind!

---

### Post by k()()zmi4 on 2009-12-02
> **k()()zmi4 said:**
> as well as the option to go easy and get a .deb package (double-click install) straight off the ftp server close to you (I found 'bout that a little later :redface:)


**Don't** use the standalone package, unless you're experienced (unlike me) and know what you're doin'!!! For noobs like me, Synaptic is the way to go, as the standalone .deb package has several dependencies on installed software etc.

I tried it and ended up with the broken netatalk installation which wouldn't uninstall. 
Synaptic quit straight after reporting problems regarding netatalk package, so became unusable, though gave instructions on reinstalling 'ubuntu-desktop', which I did and ended up well.
'Remove' command returned with a 'not found -1' error (actually you'll get this error straight after netatalk configuration upon running netatalk restart command). And you're not able to use afp with a broken netatalk I got a 'server not found'-type messages.

---

### Post by tdiaz on 2009-12-13
If I've manually compiled 2.0.4 to enable FakeSSL, etc. One of these tutorials for fixing login problems. If use Synaptic to update to 2.0.5 will any of that change or should I just build it from source the same way I did before, using the 2.0.5 source instead?

---

### Post by aleem on 2010-03-18
I used .deb packages to install Netatalk 2.0.5.  I documented it on my blog.. [here]("http://sidikahawa.blogspot.com/2010/03/setting-up-time-machine-server-on-my.html"):

Hope it helps someone.

cheers,

---

