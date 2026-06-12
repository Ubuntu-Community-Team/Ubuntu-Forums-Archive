---
title: "Problem installing programs, (.run files)"
date: 2009-10-11
forum: New to Ubuntu
---

### Post by Kieran B. on 2009-10-11
Hello all. It's good to finally be checking out Ubuntu. I've heard a lot of good things, but to be honest, I'm having a bit of trouble.

I downloaded this game: Wolfinstien-Enemy Territory the other day. It came as a .run file...

1. I right clicked on the file, went to properties/permissions and selected "Allow executing as a program" tab.

2. I then double clicked on the file, and picked "Run in terminal." It unpacked a bit, then asked me for my password.

3. I input my password, the terminal spits out some lines then just shuts down! It moves a bit quick, but I did manage to catch the words "Authentication Failure." The program did not install.

Now I assume that whatever I put in as the password must be invalid or something... Its just a bit odd because that IS my password! It's the only one I've ever entered into this thing! It's what I use to log in, access Synaptic etc..

Intrestingly, I can't access the Root terminal through the System Tools in the "Start Menu" (for lack of a better term) by using that password either. 

I'm wondering what the problem could be.

---

### Post by arochester on 2009-10-11
Have you looked at: [https://help.ubuntu.com/community/EnemyTerritory](https://help.ubuntu.com/community/EnemyTerritory)

---

### Post by sandyd on 2009-10-11
can you open up a terminal
(Applications -> Accessories -> Terminal)
or however your version does it.

and run it directly from there?

then we can see the error.

if you saved it to the desktop, you can navigate to the desktop by typing in
```

cd ~/Desktop

```
running
```

dir

```

find the filename of the installer and do
```

sudo ~/Desktop/filename.run

```

---

### Post by Kieran B. on 2009-10-11
Well...

[LEFT]I was looking over the  Enemy territory help page where I found that I needed to install something else before the game would work. (A dependency?)[ ]("https://help.ubuntu.com/community/EnemyTerritory")

Anyway I ran sudo apt-get install libgtk1.2 then went about running sudo ~/Desktop/game.run like you asked and the thing installed fine!

I'm still getting the hang of this thing really, and it's been frustrating at times. Thanks Carlee and Arochester.
[]("https://help.ubuntu.com/community/EnemyTerritory")[/LEFT]

---

### Post by sandyd on 2009-10-11
your welcome.

happy gaming!

---

