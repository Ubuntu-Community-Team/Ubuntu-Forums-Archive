---
title: "How to play an .arf file"
date: 2010-01-13
forum: New to Ubuntu
---

### Post by A_M_S on 2010-01-13
Hello

Anyone know how to play an .arf file in ubuntu?

Tnx

---

### Post by Daveth on 2010-01-13
there seem to be at least 7 different .arf file extensions around - do you mean for WebEx advanced recording, or Active Tutor data file, or something else?

---

### Post by A_M_S on 2010-01-13
> **Daveth said:**
> there seem to be at least 7 different .arf file extensions around - do you mean for WebEx advanced recording, or Active Tutor data file, or something else?

WebEx advanced recording

---

### Post by A_M_S on 2010-01-14
The following link has a way to install webex player in ubuntu.

[http://www.johnoriordan.ie/index.php/2008/03/10/webex-player-on-linux/](http://www.johnoriordan.ie/index.php/2008/03/10/webex-player-on-linux/)

---

### Post by mciverza on 2011-07-14
> **A_M_S said:**
> The following link has a way to install webex player in ubuntu.

[http://www.johnoriordan.ie/index.php/2008/03/10/webex-player-on-linux/](http://www.johnoriordan.ie/index.php/2008/03/10/webex-player-on-linux/)

Thanks. However, this is only for the old webex version not the .arf files.

---

### Post by T_W on 2012-10-19
How to play ARF files has been added as a comment to: [http://www.johnoriordan.ie/index.php/2008/03/10/webex-player-on-linux/](http://www.johnoriordan.ie/index.php/2008/03/10/webex-player-on-linux/)

Basically:
> 
1. Play any publicly available webex video.
Ex: Open this URL [http://goo.gl/keFJh](http://goo.gl/keFJh) and click ‘Playback’ button. **[COLOR="DarkOliveGreen"]<-- NOTE THIS EXAMPLE IS NOT PRESENT ANYMORE.  YOU NEED THE URL OF A RECORDING[/COLOR]**
2. It will open this ‘Network Recording Player’ to play that webex video.
3. And It will create ~/.webex directory in your linux home directory which contains all dependent libraries and webex Network Recording player.
4. Then close all webex windows
5. Run this command : ‘~/.webex/500/nbrplay’ or ‘~/.webex/500/nbr_play’ which will open the Network Recording Player
6. Click ‘File->Open’ and select your ‘*.arf’ or ‘*.wrf’ file to play.
7. That’s it!…

I have confirmed that this works.

---

