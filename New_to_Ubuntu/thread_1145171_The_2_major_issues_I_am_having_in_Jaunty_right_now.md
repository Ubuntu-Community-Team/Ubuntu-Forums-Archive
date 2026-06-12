---
title: "The 2 major issues I am having in Jaunty right now."
date: 2009-05-01
forum: New to Ubuntu
---

### Post by cptrohn on 2009-05-01
Of course I am using Kubuntu 9.04... The first one is getting connected to my HP WiFi printer... I could set it up from the printer to connect to my network, but could not for th life of me get the printer and the computer to talk... pinged the printer and nothing, it's not recognized wirelessly at all, it does work fine via USB though.. Got in touch with the developers at hplip and they said that this is a known issue that they are working on right now. (whether it is specific to my my printer model or not I don't know)


The 2nd one is the one that is the real killer though,  I had all of my music collection backed up on an external HD from my days with windows and about half of my collection got mixed up from being seperated from th artist/album art folders where they belonged so I am having to manually take a listen to each song in Amarok create a new folder for the artist and then the CD and move the singl song file from the external HD to the appropriate artist/CD folder on my computer..  I can move 4 or 5 tracks where they are supposed to go and then the system just freezes up and can't do anything.... I also can't do a contol/alt/backspace to unlock the system and have to manually reboot every single time it hangs... I REALLY don't like doing that at all...

Is anybody else having an issue with the system freezing up?

---

### Post by Dark Aspect on 2009-05-01
> **cptrohn said:**
> Of course I am using Kubuntu 9.04... T

There is a [kubuntu forums]("http://kubuntuforums.net/forums/index.php"), however most people will probably help you here. Just thought you might be interested to know. 


> **cptrohn said:**
> The 2nd one is the one that is the real killer though,  I had all of my music collection backed up on an external HD from my days with windows and about half of my collection got mixed up from being seperated from th artist/album art folders where they belonged so I am having to manually take a listen to each song in Amarok create a new folder for the artist and then the CD and move the singl song file from the external HD to the appropriate artist/CD folder on my computer..  I can move 4 or 5 tracks where they are supposed to go and then the system just freezes up and can't do anything.... I also can't do a contol/alt/backspace to unlock the system and have to manually reboot every single time it hangs... I REALLY don't like doing that at all...

Have you tried another music player? What format is the music in and have you installed kubuntu-restricted-extras for mp3 support?

---

### Post by cariboo on 2009-05-01
You can manually edit /etc/X11/xorg.conf to enable Ctrl-Alt-Backspace, or install and run dontzap to enable it. Dontzap is in the repositories.

```
Section "ServerFlags"
	Option	"DontZap"	"False"
EndSection
```

---

### Post by cptrohn on 2009-05-01
> **cariboo907 said:**
> You can manually edit /etc/X11/xorg.conf to enable Ctrl-Alt-Backspace, or install and run dontzap to enable it. Dontzap is in the repositories.

```
Section "ServerFlags"
	Option	"DontZap"	"False"
EndSection
```

Ahh thank you very much!

---

### Post by cptrohn on 2009-05-01
> **Dark Aspect said:**
> There is a [kubuntu forums]("http://kubuntuforums.net/forums/index.php"), however most people will probably help you here. Just thought you might be interested to know. 




Have you tried another music player? What format is the music in and have you installed kubuntu-restricted-extras for mp3 support?

Oh yes, I know about Kubuntu forums, and it is very good as well, I use both forums for Maximum effect... ;)

---

