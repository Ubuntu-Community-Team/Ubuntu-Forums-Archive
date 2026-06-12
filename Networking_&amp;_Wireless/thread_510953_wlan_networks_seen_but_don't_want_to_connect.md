---
title: "wlan networks seen but don't want to connect"
date: 2007-07-27
forum: Networking &amp; Wireless
---

### Post by mulan on 2007-07-27
I had problem with the computer recognising the Atheros AR5007eg wlan card, but after following this it solved that part:
[http://ubuntuforums.org/showthread.php?p=3003336#post3003336](http://ubuntuforums.org/showthread.php?p=3003336#post3003336)

It can now see all wlan networks in the area. Problem is that it doesn't want to connect to them. As i am a newbie i don't really know what to look for...
It can't connect with my network, nor with my neigbours which is unprotected... With Vista both of them are accessible...
Maybe i did sth wrong during the process but i'm pretty sure i didn't...

My router is an Netgear WGR614v6
My computer is an Acer Aspire 3683WXMi

Please help out with this so i can erase my Windows partition!

---

### Post by moore.bryan on 2007-07-27
*have you installed network-manager-gnome or [wicd]("http://www.wicd.org/")?  they are gui's to help "streamline" the connection process...  i'd suggest wicd, but that's just me.  i think it's in the repos.*

---

### Post by mulan on 2007-07-27
i guess the gnome network manager is what i use. it's the one that comes with 7.04.
i'll try out the wcid! thanks

---

### Post by mulan on 2007-07-27
OK if this message enters then wicd is really, making Ubuntu the winner. Then the wlan question is resolved. Now i just have to clear out the problems with my ipod and my speakers, then i can throw out Vista...
thanks moore.bryan

---

### Post by moore.bryan on 2007-07-27
*no problem... just glad to hear you got it working.  maybe i can help with the ipod... my 1stgen nano gave me unbelievable issues until i found-out about [rockbox]("http://www.rockbox.org/").  after the expected learning curve, i'm 100% pure ubuntu...*

---

### Post by GMachine_24 on 2007-07-27
> **mulan said:**
> OK if this message enters then wicd is really, making Ubuntu the winner. Then the wlan question is resolved. Now i just have to clear out the problems with my ipod and my speakers, then i can throw out Vista...
thanks moore.bryan

Ok I must be blind but I don't see anything at wicd.com or wicd.org which looks like a linux network configuration tool..... can someone give me the link to the download link?? thank you

gm

---

### Post by moore.bryan on 2007-07-27
[I]that's my mistake... it's at [wicd.sourceforge.net]("http://wicd.sourceforge.net/") and i think it's in the repos.
[/I]

---

### Post by GMachine_24 on 2007-07-27
thanks. i should have found that myself but with my cursor skipping all over the place and new pages being opened and stuff being submitted before i click 'send' i'm a little wary of the time it will take me to do anything. (i am working on this issue next).

so, for anyone else needing a network manager that actually works enter

<code>

deb [http://wicd.longren.org](http://wicd.longren.org) feisty all

<end code>

[note if the middle part of th  above repository line is highlighted as a url, ignore the highlight and underline and just copy the 
actual text.

as a custom repository in synaptic (will require you to remove gnome network manager if installed --- good riddance) where 'feisty' is whatever version of ubuntu you are running. do the save-reload-search thing, find witc, install it and 'voile,' chances are you will soon be war driving . .  i mean surfing . . . the net wirelessly

thanks.

gm

---

### Post by moore.bryan on 2007-07-27
*yeah, wicd rocks...*

---

### Post by mulan on 2007-07-27
great Gmachine_24 with the spelling out, i haven't really understood most of the stuff i have done since i installed ubuntu, but stuff like that help.
moore.bryan: the ipod is functional now, it was mostly a question about me not thinking about mp3 beeing proprietary so  didn't think the programs would need more installs to handle that.
but if you know what to install to play m4a, then that info would be delcious!
BTW i'm 100% ubuntu since 1 hour!!

---

### Post by moore.bryan on 2007-07-27
*m4a on the ipod?*

---

