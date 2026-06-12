---
title: "spotify problem"
date: 2009-10-04
forum: New to Ubuntu
---

### Post by johncee on 2009-10-04
I have ubuntu 9.0.4 with latest version of Wine. Installation of Spotify goes OK, but I can only launch it once. After running Spotify, then exiting, if I try to run it again I get the error message:
"The program spotify.exe has encountered a serious problem and needs to close....."
The only way I can then get spotify to run again is to uninstall it from the .wine folder, then reinstall. It then works for one time only, and I have to go through the whole process again.......
Any ideas, anyone?

---

### Post by Kulgan on 2009-10-04
Did you follow the instructions from the Spotify website with the audio driver changes?

Heard someone had random problems related to that.

---

### Post by vastus on 2009-10-04
I've got same problem. Which version of wine u tried it? I tried it with 1.0.1 which is the latest stable release, dunno if it works with latest beta release.

---

### Post by Kulgan on 2009-10-04
Works for me with version in Jaunty repos, whatever that may be (not home at the moment)

---

### Post by johncee on 2009-10-04
> **vastus said:**
> I've got same problem. Which version of wine u tried it? I tried it with 1.0.1 which is the latest stable release, dunno if it works with latest beta release.

Tried both 1.0.1 and the latest beta. Same problem.

---

### Post by johncee on 2009-10-04
> **Kulgan said:**
> Did you follow the instructions from the Spotify website with the audio driver changes?

Heard someone had random problems related to that.


Yes, I changed the audio settings as specified. Didn't make any difference.

---

### Post by vastus on 2009-10-04
That's latest stable version. With 1.0.1 spotify worked fine for me too @ my other pc, but cant get it working in this one.

---

### Post by guriinii on 2009-10-07
I am also have the same problem running spotify with wine 1.1.30. I purged wine and reinstalled and the problem repeats. Please help, I'm still quite the noob.

---

### Post by vicshrike on 2009-10-09
Problem here too, says that I am off line. Which I am not. But when I leave the program open it connects after a couple of minutes. Same thing happens on my dear old aunt too (xp).

---

### Post by guriinii on 2009-10-20
I've got it working after uninstalling wine 1.1.30 and spotify. Then reinstalling wine 1.0.1 and spotify.

Voilá! I wish you all good luck.

---

### Post by edhornby on 2010-01-30
I found that spotify couldn't run from one track to the next and also the attenuation on the 

I switched my audio from ALSA to the eSound drivers and all works fine for me now, thanks for the advice (a fujitsu Esprimo on Karmic with wine 101 and whatever spotify install was on my old windoze partition if that helps...)

---

