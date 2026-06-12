---
title: "Remote Control (LIRC) use in Amarok 2"
date: 2010-06-02
forum: New to Ubuntu
---

### Post by El Conquistador on 2010-06-02
Im trying to figure out how to use my mceusb remote to control amarok 2. I tried using my previous config files from amarok 1.4 but apparently amarok 2 now using mpris/dbus type configuration instead of the dcop previously used in amarok 1.4. Ive been searching the web for a simple solution on how to get this to work but it seems like for as long as amarok 2 has been out nobody has documented a simple easy to follow "how-to" on setting this up. (that i have been able to find anyway)

I did find this on the ArchWiki

##amarok2

begin
button = Play
prog   = irexec
repeat = 0
config = qdbus org.mpris.amarok /Player Play
end

begin
button = Pause
prog   = irexec
repeat = 0
config = qdbus org.mpris.amarok /Player Pause
end

begin
button = Stop
prog   = irexec
repeat = 0
config = qdbus org.mpris.amarok /Player Stop
end

begin
button = Skip
prog   = irexec
repeat = 0
config = qdbus org.mpris.amarok /Player Next
end

begin
button = Replay
prog   = irexec
repeat = 0
config = qdbus org.mpris.amarok /Player Prev
end

but it seems that all of my other .lirc config files use "prog = *insert program name here* e.g. rhythmbox/mplayer/vlc" and not irexec. So to me this means that maybe i set up my lirc incorrectly. But if that is the case then why was it so darn easy to set up? and why does it work with everything else i use EXCEPT amarok?

If anyone could provide me with their working .lirc config file for amarok 2, or a link that i can follow, or some kind of "set-up guide" i would appreciate it. 

If it turns out i have to script everything myself as is shown in the mpris wiki. then i guess i will have to do that. But i just cant imagine why it would be so hard to set up such a simple task. Even more so why it would be so hard for those new to linux, who may have no scripting/text editing config file experience.

Any help would be appreciated Thanks!

---

