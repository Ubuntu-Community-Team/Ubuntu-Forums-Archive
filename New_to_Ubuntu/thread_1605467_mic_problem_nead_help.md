---
title: "mic problem nead help"
date: 2010-10-25
forum: New to Ubuntu
---

### Post by milankomadina on 2010-10-25
I reacently installd ubuntu 10.10 maverick merchant edition and i have problem with my microphone. At first i tought that the mic dont work becouse i cold not hear anything when i recorded something. But now i know that i nead to speak wrealy loud when i record something and even then i can barely hear what i recorded. My sound card is HDA ATI SB and my sound chip is REALTEK ALC 861. IF YOU HAVE ANY SOLUTION PLEASS HELP. if you nead any other device informationen to solve this problem pleass ask me. I did try to resolve this with Puls audio volume control but nothing hapens. I do not know what else can be done becouse i am beginer with ubuntu.thanks in advance

---

### Post by cariboo on 2010-10-25
Open an Applications->Accessories->Terminal, and type:

```
alsamixer
```

use the arrow keys to navigate to the mic setting and increase or decrease the volume. Once you have the volume level set to where you want them, press esc to exit, and to store the changes, in the same terminal type:

```
sudo alsactl store
```

**Note** In the screen shot the mic control doesn't have a bar graph, because my netbook has a builtin microphone, I use System->Preferences->Sound to set the mic level

---

### Post by milankomadina on 2010-10-26
i followed your instructions and it works untill I restart my computer, after restart the problem is still present. every time i start or restart my computer i nead to go to the alsamixer and to do the following: go to the INPUT SORCE (set to MIC) then i only nead to switch INPUT SORCE to CD and right away back to MIC. after that mic is fully functional. any ideas?????

---

