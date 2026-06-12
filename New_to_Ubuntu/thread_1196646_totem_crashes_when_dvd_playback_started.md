---
title: "totem crashes when dvd playback started"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by mayoban on 2009-06-25
Hi All,

In order to enable dvd playback in Ubuntu 9.04, I installed the restricted packages and the medibuntu repositories following the instructions on "https://help.ubuntu.com/community/Medibuntu"

Now, when trying to playback a dvd, totem crashes. Vlc player also does not work for dvd playback in my case.

Does anyone have an idea what the problem may be?

Cheers, mayoban

---
I am using Ubuntu 9.04, 64-bit version
on a Lenovo Thinkpad R400, Type 7439-A85
Gnome Desktop with Compiz Window Manager and Gnome-Do Docky

---

### Post by ubudog on 2009-06-25
I got it working with some other directions that I found online.  Try searching google.

---

### Post by ubudog on 2009-06-25
Do you mean it stopped playing or the window shut?

---

### Post by mayoban on 2009-06-26
Hi ubudog,

Thanks for your reply. The window **shut** after selection of the source.

Do you remember the webadress, where you found the instructions, which worked for you? There are so many different posts and it is hard to discern, which comment may be suitable.

Cheers, mayoban

---

### Post by ubudog on 2009-06-30
I don't remember. Search on google.

---

### Post by undecisive on 2010-02-14
Probably the naffest lack of response to an issue I've ever seen. You should all be ashamed. First things first, look here: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")

From the sounds of things, you've probably manage to install the gstreamer plugins and libdvdread. All that's missing is you need to open a terminal (Applications => Accessories => Terminal) and type: 

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

After this, I tried it and Movie Player froze on me. It was closable, but certainly wasn't going to play a dvd for me. I ran the commands towards the bottom (although it should read: 

```
sudo chmod 660 /dev/sr0; sudo chgrp cdrom /dev/sr0
```

I'm not sure it's necessary. But I then rebooted the machine, and tried again, and it seemed to work lovely-like!

Hope it works!

---

### Post by ubudog on 2010-02-14
> **ubudog said:**
> I don't remember. Search on google.

Yeah, sorry about that.  I was tired.  Try installing ubuntu restricted extras.  ```
sudo apt-get install ubuntu-restricted-extras
```

Hope that helps! ;)

---

### Post by Tangentabacus on 2010-03-29
I'm having the exact same problem. 10.04 beta, instead. At first I thought it was something wrong with CSS, then I read this post and realized, "Oh, hey, why didn't I think of the 'restricted extras'?" Needless to say, problem fixed. Thanks.

P.S. Also, it did a lot of work for me that I had to do later.

---

### Post by ubudog on 2010-03-29
> **Tangentabacus said:**
> I'm having the exact same problem. 10.04 beta, instead. At first I thought it was something wrong with CSS, then I read this post and realized, "Oh, hey, why didn't I think of the 'restricted extras'?" Needless to say, problem fixed. Thanks.

P.S. Also, it did a lot of work for me that I had to do later.

Yeah, it is nice to have :)

---

