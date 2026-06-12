---
title: "Games Crashing out with a &quot;Segmentation Fault&quot; on load"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by beastrace91 on 2009-03-19
I have a few games installed and they all crash out with various "segmentation faults" when I try to load them... here is the output from three of them: ```
jeff@jeff-ubuntu:~/Desktop/SDL-1.2.13$ opencity
Welcome to opencity version 0.0.5stable
Copyright (C) by Duong-Khang NGUYEN. All rights reserved.
   web  : http://www.opencity.info
   email: neoneurone @ users sf net

This program is released under the terms of
GNU General Public License (See the COPYING file for more details)

Starting OpenCity standalone/client application...

<INFO> Failed to initialized BinReloc routines to search for the datadir. The error was: 4
<INFO> Failed to initialized BinReloc routines to search for the confdir. The error was: 4
<INFO> Detected data directory   : /usr/share/games/opencity/
<INFO> Detected config directory : /etc/opencity/
<INFO> Detected save directory   : /home/jeff/.opencity/
<INFO> Reading XML config file: "/etc/opencity/config/opencity.xml"
<INFO> Checking video doublebuffer: OK !
Segmentation fault

```

Trying to run the Game "smc" from consoles gives a whole slew of these image errors before it crashes:

```
Error loading image : /usr/share/games/smc/pixmaps/menu/items/save.png
Reason : Unsupported image format
Error loading image : /usr/share/games/smc/pixmaps/menu/save.png
Reason : Unsupported image format
Error loading image : /usr/share/games/smc/pixmaps/menu/quit.png
Reason : Unsupported image format
Error loading image : /usr/share/games/smc/pixmaps/menu/logo_sdl.png
Reason : Unsupported image format
Segmentation fault

```

```
jeff@jeff-ubuntu:~/Desktop/SDL-1.2.13$ frozen-bubble
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

Any input on fixes would be wonderful.

~Jeff

---

