---
title: "Sound not coming and driver installation instructions sound greek to me"
date: 2009-09-06
forum: New to Ubuntu
---

### Post by Soul_Fly on 2009-09-06
Noob Here,
Ok am a newbie. After checking the awesome awesomeness of ubuntu in the net i decided to migrate to it and ordered the live CD. I got it. over joyed I installed it. then behold I installed it. Got the cool special effects running. Installed restricted extras...etc. NOW comes the bummer. **NO Sound**.:confused: ***absolutely* no sound**. I checked out the forums and they advised various checks (*refer Comprehensive sound issues*). I did all that modprobe and stuff and found out that sound card is detected all right but no sound. I have a r**ealtek sound card which is onboard on my MSI mobo (ALC883)**. Got the sound card linux drivers from realtek site. Now comes the pain in (u kno where). **The installation notes are absolute G(R)EEK to me**. Being a windows user the first thing i did was hit install. (dont blame me typical windows habit). Then as if reading french the first thing** i realised was i was supposed to manual install that thing. then how am i to revert it?** I dont suppose there is a control panel in ubuntu. and then how am i to carry out the manual install?.....total greek plz help me PLEASE. Or I'll have to revert back to a peice of **** called VISTA.
-----
Installation Notes:
[http://tinypaste.com/2cc06](http://tinypaste.com/2cc06)
_
please, _step by step instructions will be appreciated_. Complete noob.
Other solutions will also be appreciated.

---

### Post by Bradtek on 2009-09-06
On board realtek card should work without download/install drivers
Most basic hardware has drivers already in the kernel, but anyway

Open a terminal and type
```
alsamixer
```

Check to see if something is turned off (or down to 0)
use the arrow keys to move and turn up/down and the M key to turn on/off

---

### Post by Soul_Fly on 2009-09-06
Here check it out....
Ya they SHOULD work...thats the prob...they aren't :X

---

### Post by Soul_Fly on 2009-09-06
any help...please!!!

---

### Post by Soul_Fly on 2009-09-07
Ok....got that stuff to work..... don't ask me how took me 3 hrs...but finally sound coming through...thank you for yor co-operation

---

