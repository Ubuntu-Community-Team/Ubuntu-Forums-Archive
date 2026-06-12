---
title: "VoIP applications in UBUNTU 10.04 for Messagenet VoIP account"
date: 2011-01-09
forum: New to Ubuntu
---

### Post by Kirom on 2011-01-09
Hi,
i'm new in forum and in UBUNTU, the first problem I'm having since the installation of UBUNTU it's the setting of my **_Messagenet account for VoIP_**. I tried to use **Ekiga**, and **Kphone**. and also **Twinkle**, but the result didn't go beyond "hearing the voice, but can't speaking, microphone mute..."

So I'd like to know how to install "**Xlite**" (it works fine in win) in **UBUNTU** **10.04**, or how to set well one of the other VoIP application.

Thanks for help,

Kirom

---

### Post by cariboo on 2011-01-09
Open a terminal and type:

```
alsamixer
```

use the arrow keys to navigate and adjust the volume. Make sure your microphone isn't muted and the volume is turned up. On my netbook the volume is set to low by default.

Once you have made the changes needed press esc to close alsmixer, then in the same terminal type:

```
sudo alsactl store
```

the above command will store the changes you have made.

---

### Post by tumutanzi on 2011-03-09
I made an article to show how to set up nonoh etc. in Ekiga.
[http://www.tumutanzi.com/2011/03/how-set-up-sip-in-linux-operating_06.html](http://www.tumutanzi.com/2011/03/how-set-up-sip-in-linux-operating_06.html)

---

### Post by tumutanzi.com on 2011-09-29
> **tumutanzi said:**
> I made an article to show how to set up nonoh etc. in Ekiga.
[http://www.tumutanzi.com/2011/03/how-set-up-sip-in-linux-operating_06.html](http://www.tumutanzi.com/2011/03/how-set-up-sip-in-linux-operating_06.html)

Sorry, the right link of "How to set up Nonoh in Ekiga of Linux operating system to use VOIP" is: 
[http://tumutanzi.com/archives/92](http://tumutanzi.com/archives/92)

---

