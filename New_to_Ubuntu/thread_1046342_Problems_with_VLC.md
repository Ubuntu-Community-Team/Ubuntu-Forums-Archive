---
title: "Problems with VLC"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by rob42 on 2009-01-21
Hello
I am new to linux as a whole but enjoying the experiance in general. I have used Mandriva for a few weeks and been able to use VLC along with other media players.
was then given access to a new laptop ( toshiba sat pro a100) and other than a problem with the wireless card all is well. 
But I can't get VLC to work . It loads via and the add and remove software interface,but when I go to use it it partly opens and then a window opens asking for a skin. This I downloaded and when asked click on the reliant parts . VLC then crashes.

Any pointers?

---

### Post by ithanium on 2009-01-21
i suggest you using the following commands in terminal to install it:
```
sudo apt-get update
sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc
```

---

### Post by Tek-E on 2009-01-21
I had the same problem for a while.  I then tried downloading the .deb for VLC but installing that way failed to work as well.  You could also download the XP version and run it under wine.  Thats what I did and I havnt had a problem since.

---

### Post by D3M0L1$H3® on 2009-01-21
dis should work. (sorry if already posted, ive had the thread up for a while without refreshing)
```
sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc
```

---

### Post by HavocXphere on 2009-01-21
Does it do the same when you launch it without giving it any file to play? i.e. Not dbl-clicking on a media file, but rather just launching vlc on its own.

---

### Post by rob42 on 2009-01-21
wow that was quick
have tried the terminal load but cant get connected to 91.189.90.142
have tried a number of times to choose  'BETTER SERVER' but this doesnt help.

never thought of using the window version - if it works.... will give it a try .

HavocXphere -  it seems to run in the lower panel, but wont max or open out from there. some times it shows as a small panel ( with a very flickery output ) am unable to do anything with it other than close it .

---

### Post by mc4man on 2009-01-21
Open up a terminal and use this to start and reset vlc
```

vlc --reset-config
```

---

### Post by rob42 on 2009-01-22
Many thanks for the help - followed mc4man just before I removed vlc and then was going to use wine . And as if by magic  it works.
thanks to all who replied.

---

