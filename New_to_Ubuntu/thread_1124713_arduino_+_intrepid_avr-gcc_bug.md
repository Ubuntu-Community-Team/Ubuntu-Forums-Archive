---
title: "arduino + intrepid avr-gcc bug???"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by letapjar on 2009-04-13
Can someone please point me in the right direction.  The arduino website says that intrepid has a major bug in the avr-gcc pacakge.  Has this been fixed/patched?  if so how can i make sure I have the latest patch/bugfix.  If not, how do I install another version of the avr-gcc package (i.e. from Jaunty) so that the arduino IDE will work right?

Thanks in advance for helping a total noob.

---

### Post by letapjar on 2009-04-13
OK, so here's the solution I found myself - in case anyone else is trying to do this.  Also, if this is totally the wrong way - I'd appreciate a heads up.

I found a list of sources for jaunty [[COLOR="Blue"]_here_[/COLOR]]("http://ubuntuforums.org/archive/index.php/t-997890.html")

I opened my terminal, sudo gedit /etc/apt/sources.list

First thing was to do a save as and save a version e.g. sources.list.old in case I screwed everything up.

next I copied the jaunty source repo listings from the link above into my sources.list

Then under synaptic I reloaded the repos so it would recognize the new repos.

now I was able to select avr-gcc and then in the package menu I selected "force version" and it had options for both jaunty and intrepid so I just selected the jaunty versions.
[http://ubuntuforums.org/archive/index.php/t-997890.html](http://ubuntuforums.org/archive/index.php/t-997890.html)
I did the same for the other packages that arduino's IDE requires.  when I do a avr-gcc --version in my terminal it reads 4.3.2.something [i forghet exactly].

I haven't tried to check whether or not longint multiplication bug is there, but it should be fine.

Arduino was up and running in a snap after these changes.

I just hope I haven't broken my system in other places since gcc and libc6 are used everywhere.

Hope this helps someone else who is a linux noob itching to play around with an arduino.

---

### Post by tona70 on 2010-05-03
Hi,are you Raj Patel friend.

---

