---
title: "how do i get to run 3.6 firefox"
date: 2010-01-21
forum: New to Ubuntu
---

### Post by blake7 on 2010-01-21
i have just dowm loadedit from there main site 

thank you 

or if there is a simpler way then that would be helpful

cheers

---

### Post by _H3MLOCK on 2010-01-21
There is a firefox executable in the folder you downloaded (Uncompress it first). You can start firefox 3.6 using that... To replace your existing firefox with 3.6 I would advise wating for ubuntu to officially support it. Else you can always modify the shortcut router.

---

### Post by Mze on 2010-01-21
Ubuntu Geek has a tutorial up.

[How to install Firefox 3.6 in Ubuntu Karmic/Jaunty/Intrepid/Hardy]("http://www.ubuntugeek.com/how-to-install-firefox-3-6-in-ubuntu-karmicjauntyintrepidhardy.html")

---

### Post by nanotube on 2010-01-21
a more integrated (and easier) way is to use the ubuntuzilla repository, which has the latest firefox:
[http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)

---

### Post by oldsoundguy on 2010-01-21
> **nanotube said:**
> a more integrated (and easier) way is to use the ubuntuzilla repository, which has the latest firefox:
[http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)

Don't spoil their fun.  Many people like to do things the hard way and feel that others should experience the thrill! LOL
I see lots of answers to questions here and way too many of them are geek answers that scare the crud out of the newbies .. when there is an EASIER method built into the build!

---

### Post by Stigmata13 on 2010-01-21
I myself would reccomend sticking to 3..57 until it gets out of Beta... I gave it a try and it seemed to work ok but there are a few things that bugged me, like for example when you download something and right click it in the download manager and try to run it or open location it just tells you that it doesn't know what program to open.

---

### Post by ratcheer on 2010-01-21
> **Stigmata13 said:**
> I myself would reccomend sticking to 3..57 until it gets out of Beta... 

3.6 is out of beta as of today.

Tim

---

### Post by 416inversed on 2010-01-21
I used the Ubuntu Geek method, but it installed the Namakoro build of 3.6. So I removed it. Then I used the Ubuntuzilla method. It created a concurrent installation from 3.57 of 3.6. I removed 3.57, but then 3.6 ceased to work, neither from clicking the icon or from the terminal. So I removed & reinstalled, still no good, even after rebooting. 

So I removed 3.6 and reinstalled 3.57 for the time being.

---

### Post by tacantara on 2010-01-21
I ran my Ubuntuzilla script, and managed a successful download of 3.6, which totally replaced my 3.5.7.  Had it installed and running in a matter of minutes.

---

### Post by bluelamp999 on 2010-01-21
> **tacantara said:**
> I ran my Ubuntuzilla script, and managed a successful download of 3.6, which totally replaced my 3.5.7.  Had it installed and running in a matter of minutes.

Same here, very easy...

*However*, it screwed up the font rendering in my particular case. Any sequence of vertical line characters in a word (e.g. Moz-*ill*-a would show an unpleasant coloured smudge around the 'ill'.)

I reverted to 3.5.7 but has anybody else had this problem? I tried a few of the suggested fixes for 3.5 when it apparently had this problem but no joy...

---

### Post by lovinglinux on 2010-01-21
See the [COLOR="Sienna"]**Install Other Versions section**[/COLOR] of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by mikewhatever on 2010-01-21
The simplest way to run 3.6 is to download a taz from firefox.com, unpack it somewhere and run the executable included.

---

### Post by nanotube on 2010-01-21
> **416inversed said:**
> I used the Ubuntu Geek method, but it installed the Namakoro build of 3.6. So I removed it. Then I used the Ubuntuzilla method. It created a concurrent installation from 3.57 of 3.6. I removed 3.57, but then 3.6 ceased to work, neither from clicking the icon or from the terminal. So I removed & reinstalled, still no good, even after rebooting. 

So I removed 3.6 and reinstalled 3.57 for the time being.

uninstalling the 3.5.7 from the repos probably took out some dependencies. just leave 3.5.7 be (don't uninstall), and use 3.6 that comes from ubuntuzilla, if you want 3.6.

---

### Post by 416inversed on 2010-01-22
> **nanotube said:**
> uninstalling the 3.5.7 from the repos probably took out some dependencies. just leave 3.5.7 be (don't uninstall), and use 3.6 that comes from ubuntuzilla, if you want 3.6.

Thanks. I actually came to that same conclusion as I was writing my post last night.

So I retried the Ubuntuzilla method and it seamlessly replaced 3.57. What was different this time around? I don't know, but it worked.

---

