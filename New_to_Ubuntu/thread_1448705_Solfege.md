---
title: "Solfege"
date: 2010-04-07
forum: New to Ubuntu
---

### Post by itsvan on 2010-04-07
HI im trying to use this Music Program called SOLFEGE,, but it wont let me hear anything this is what i get when i start it up:

                 No module named _solfege_c_midi
You should configure sound from the preferences window, and try to use an external midi player. Or try to recompile the program and check for error messages to see why the module is not built.

Any ideas what i can do???

---

### Post by candtalan on 2010-04-07
> **itsvan said:**
> HI im trying to use this Music Program called SOLFEGE,, but it wont let me hear anything this is what i get when i start it up:

                 No module named _solfege_c_midi
You should configure sound from the preferences window, and try to use an external midi player. Or try to recompile the program and check for error messages to see why the module is not built.

Any ideas what i can do???

not sure however, a comment  on the page
[http://www.solfege.org/Solfege/InstallingSolfege](http://www.solfege.org/Solfege/InstallingSolfege)

includes:
==========
If you can start the program, but there is no sound
            sudo apt-get install timidity 
might help 
(if timidity is set as midi file player in the sound setup of Solfege). 
==========

good luck

---

