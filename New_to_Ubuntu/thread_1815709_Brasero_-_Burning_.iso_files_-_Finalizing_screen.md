---
title: "Brasero - Burning .iso files - Finalizing screen"
date: 2011-07-31
forum: New to Ubuntu
---

### Post by avnd on 2011-07-31
Hello there!

I downloaded an image for Kubuntu and wanted to burn it to a CD.

I tried burning with Brasero.

The 'burning data' part went fine. I was able to see the speed and progress and all. It got to 100% and then it got stuck at a screen called 'Finalizing'. The title bar says 'Burning CD 100% done'. There's 'Burning image' below that and 'Finalizing' below that. Sorry it didn't strike me to take a screenshot then.

This has actually happened 3 or 4 times with different data and different discs. It stops at exactly that same stage with that same message 'Finalizing'. By 'stuck' I don't mean a hanging screen. The bar is actually going left and right the whole time (like it's doing something). It just stays that way for over an hour. 

Any suggestions?

Cheers!

---

### Post by scorchgeek on 2011-07-31
According to [this thread]("http://forums.fedoraforum.org/showthread.php?t=243318") (it's Fedora, but about the same program), the problem is likely with Brasero. There are several CD burning applications in the repository--try installing one of them:

```
sudo apt-get install gnomebaker
```
or
```
sudo apt-get install k3b
```

If that doesn't work, you may have a more serious problem with your drive (or with its drivers or interface with the operating system).

---

### Post by fdrake on 2011-07-31
i had the same problem. My solution was to change both cd and program. I always had problem with brasero. Gnomebaker or k3b work fine. Also my cd- used to get corrupted very easily..

---

### Post by DaveClark on 2011-07-31
I am a total novice with Ubuntu, having only installed it today! How do I use the code, where and how do I enter it?:confused:
sudo apt-get install gnomebaker

---

### Post by fdrake on 2011-07-31
> **DaveClark said:**
> I am a total novice with Ubuntu, having only installed it today! How do I use the code, where and how do I enter it?:confused:
sudo apt-get install gnomebaker

from menubar > applications --> accessories --> terminal;
copy and paste. it will prompt you for a pass. your user pass.

---

### Post by DaveClark on 2011-07-31
Thanks very much for the help. I feel sure that i'll be back.

---

### Post by sidzen on 2011-07-31
Now that scorchgeek and fdrake have shown how to get to the terminal and how to install, I would suggest the following

Since your OS is Kubuntu, why not use a KDE app like K3b and take advantage of its inherent compatibility?  Gnome is gtk while KDE is qt4, so for efficiency (and I agree brasero is best not to be considered)  --

[PHP]sudo apt-get update[/PHP]

[PHP]sudo apt-get remove gnomebaker && sudo apt-get remove brasero --purge[/PHP]

[PHP]sudo apt-get -f install k3b[/PHP]

While you are at it, why not install k9copy, too

[PHP]sudo apt-get install k9copy[/PHP]
then
[PHP]sudo apt-get autoremove[/PHP]
to clean things up a bit

Have fun and enjoy!

---

### Post by hreichgott on 2011-07-31
Oh, I sometimes have that happen when burning discs with brasero.
Did you manually eject the drive and check the CD anyway?
My experience is that most of the time this happens, it still produces a perfectly fine CD. It's like the program hangs right after finishing the CD.

---

### Post by avnd on 2011-08-01
Thanks for the replies fellas!

---

