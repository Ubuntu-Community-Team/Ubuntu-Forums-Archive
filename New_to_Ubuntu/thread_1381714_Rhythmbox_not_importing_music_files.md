---
title: "Rhythmbox not importing music files"
date: 2010-01-15
forum: New to Ubuntu
---

### Post by lotuscarsltd52 on 2010-01-15
I recently reinstalled Ubuntu after using Wubi and losing it because it got screwed-up. I successfully copied all of my Windows files off of my external and onto my Ubuntu partition.

The problem? Rhythmbox won't play *any* of my music files. I cannot import them and it won't read them from the music folder. It even gives me some sort of error message I can't decipher.

What can I do about this problem?

---

### Post by arubislander on 2010-01-15
You already did something by posting here :). Now, if you could post the error message and them maybe someone here could decipher it. In any case, it would really help in diagnosing the problem.

---

### Post by Kobalt on 2010-01-15
Did you install restriceted formats such as MP3) support?

---

### Post by elliotbeken on 2010-01-15
This might sound silly, but i had the same problem in 8.10. you say you have the music in the music folder, is that on the main file system?

because i moved my music folder to a second (slave) drive and mine would not import but when i moved the music files back to the main file system it worked file]

although i am not sure why it might of been something to do with the permissions.

---

### Post by ajgreeny on 2010-01-15
Right click on one of the music file that will not play or import, go to Properties and on the permissions tab check that you are the owner, and have read/write permission.  If not, you will need to change the owner with the chown command, eg ```
sudo chown -R username:username /home/username/music
```Of course you will need to put your own pathway to your music folder and your own username where I used "username"

---

### Post by lotuscarsltd52 on 2010-01-15
> **arubislander said:**
> You already did something by posting here :). Now, if you could post the error message and them maybe someone here could decipher it. In any case, it would really help in diagnosing the problem.

When I try opening, say, a single song it takes me to the Movie Player, not Rhythmbox. I also get the following message:

*Search for suitable plugin? The required software to play this file is not installed. You need to install suitable plugins to play media files. Do you want to search for a plugin that supports the selected file? The search will also include software which is not officially supported.*

After clicking "search" I get something that says the following:

*Please select the packages for installation to provide the following plugins: MPEG-1 Layer 3 (MP3) decoder*

which is followed by a pop-up which says:

*No packages with the requested plugins found*

What does this mean?

---

### Post by ajgreeny on 2010-01-15
I think it means you do not have the right repositories enabled.  I suggest you make sure you have the universe and multiverse repos and also would advise you add the medibuntu repos; they are extremely useful, particularly for the libs needed for commercial DVD playback (libdvdcss2)
[http://www.medibuntu.org/](http://www.medibuntu.org/)

---

### Post by lotuscarsltd52 on 2010-01-15
> **ajgreeny said:**
> I think it means you do not have the right repositories enabled.  I suggest you make sure you have the universe and multiverse repos and also would advise you add the medibuntu repos; they are extremely useful, particularly for the libs needed for commercial DVD playback (libdvdcss2)
[http://www.medibuntu.org/](http://www.medibuntu.org/)

I'm not familiar with Linux so I'm not sure what you're asking.

Could you clarify?

---

