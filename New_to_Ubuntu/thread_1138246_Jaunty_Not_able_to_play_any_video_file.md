---
title: "Jaunty: Not able to play any video file"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by luckydeveloper on 2009-04-26
Hi,

I just installed jaunty in my system now. I installed various codecs and vlc player as well.

I can play audio files... but i am not able to play any video file. If i try to play them (.avi etc) the software closes.. totem closed this way, vlc also closed this way. 

what will be the problem... how can i rectify it

---

### Post by jmmL on 2009-04-26
It sounds like you might not have the relevant codecs installed.

This is a bit of a brute-force solution, but this command will install all the common codecs:

```
sudo apt-get install libdvdcss2 non-free-codecs gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad
```

You'll need the medibuntu repos enabled first.

Also, if you're interested i've written a little script to help with the setup process after a new install. It's customised for myself, but well commented and easily modifiable for your own needs. Just download it to your home directory, make it executable:

```
sudo chmod +x ~/ubuntusetup.sh
```

and then run it with
```
~/ubuntusetup.sh
```

It takes care of adding the medibuntu repos and that sort of stuff. Feedback welcome!

---

### Post by coldReactive on 2009-04-26
Next time, just link:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by fooman on 2009-04-26
> **jmmL said:**
>  Feedback welcome!

jmmL,  just curious....i don't know much about your script,  but i took a little look at it and....is there any specific reason why you left the "ubuntu-restricted-extras" out of the mix? thanks.



* to the original poster, in addition to adding the medibuntu repos as suggested above,  try this:

open a terminal and type or copy/paste the following:

```
 sudo apt-get install ubuntu-restricted-extras
```that should help you play some formats.  :P

---

### Post by jmmL on 2009-04-26
> **fooman said:**
> jmmL,  just curious....i don't know much about your script,  but i took a little look at it and....is there any specific reason why you left the "ubuntu-restricted-extras" out of the mix? thanks.


The main reason I left that out is that I really don't like msttcorefonts. They look really terrible compared to even the default fonts on ubuntu (in my opinion at least). Also, the package currently conflicts with some bleeding edge mplayer / vlc packages I have (I forget which).

It's certainly an easier solution for a lot of people though.

---

### Post by raymondh on 2009-04-26
> **coldReactive said:**
> Next time, just link:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

this link is great .... use it a lot even for non-9.04 installs :)

---

