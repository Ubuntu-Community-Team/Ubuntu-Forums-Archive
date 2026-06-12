---
title: "movie player need to update"
date: 2010-06-13
forum: New to Ubuntu
---

### Post by chandrav23 on 2010-06-13
Dear Devopers Team,

Here I have suggeston for you guys:

In ubnutu 9.04 you have been provided movie player

Applicaitons>Sound & Video>Movie Player.

The above movie player is not woring properly moreover its closing automatically with out user knowledge.

I dont know about ubutntu fetured versions but whats my advise is try to rectify and please proved perfect player to play audio files as well for videos.

If we can provide good one, ubuntu users will not go for other players also there are chances to increse ubuntu lovers.



Thanks

---

### Post by Locke_99GS on 2010-06-13
Run the player from the command-line

```

totem
```

and play a movie which results in it crashing. It should provide some output in the terminal which would be helpful in determining why the player is crashing.

Post the output here, please.

---

### Post by anewguy on 2010-06-13
And, remember there are other movie players in Ubuntu as well - VLC is used by a lot of users.

In addition, it's possible you may be having problems from trying to play a protected (ie, commercially produced) DVD.

Besides the instructions posted by Locke_99GS, I would suggest you do the following as well:

Open Synaptics Package Manager

Search for "gstreamer" and set the good, bad and ugly plugins for installation.

Search for "ubuntu-restricted-extras" and set it for installation.

Search for "libdvdcss" (I *think* that's the first part of the name - it will have more in the name following that).  Set it for installation.

Click "Apply" and wait for it all to finish, then close the package manager and try your movie again.

Dave ;)

---

