---
title: "update problems"
date: 2009-06-01
forum: New to Ubuntu
---

### Post by cybuss on 2009-06-01
when i try to update it brings up.

          [IMG]http://ubuntuforums.org/picture.php?albumid=1143&pictureid=4087[/IMG]http:/



any help will be greatly appreciated!
more screenshots will be up

this is another problem that happens when i check in update manager (UM) [http://ubuntuforums.org/picture.php?albumid=1143&pictureid=4088](http://ubuntuforums.org/picture.php?albumid=1143&pictureid=4088)

---

### Post by lindsay7 on 2009-06-01
Try this first, replace the numbers in my post with the number that you need.

gpg --keyserver subkeys.pgp.net --recv 6AF0E1940624A220


gpg --export --armor 6AF0E1940624A220 | sudo apt-key add -

sudo apt-get update


type these commands in the terminal


Then type alt + F2 and type update-manager -d

---

### Post by cybuss on 2009-06-01
> **lindsay7 said:**
> Try this first, replace the numbers in my post with the number that you need.

gpg --keyserver subkeys.pgp.net --recv 6AF0E1940624A220


gpg --export --armor 6AF0E1940624A220 | sudo apt-key add -

sudo apt-get update


type these commands in the terminal


Then type alt + F2 and type update-manager -d

how do i tell what numbers i need?

---

### Post by lindsay7 on 2009-06-01
It was in the screen shot that you gave in the link you had in your post, the NO-PUB KEY number.

---

### Post by cybuss on 2009-06-01
> **lindsay7 said:**
> It was in the screen shot that you gave in the link you had in your post, the NO-PUB KEY number.

i think it fixed it this is what it says,
[IMG]http://ubuntuforums.org/picture.php?albumid=1143&pictureid=4090[/IMG]

one last question, is there anyway to update hardy to jaunty without uninstalling my games and etc? if not is there a possible way to transfer my games?

---

### Post by SunnyRabbiera on 2009-06-01
Personally I say keep Hardy, Jaunty might be newer but its very buggy in my opinion.

---

### Post by lindsay7 on 2009-06-01
I do not believe you can jump upgrade on line only go form one release to the next. You would have to install for a cd or dvd.

As far as games, it would depend  where they were on the drive partition. If you have s separate home directory on its own partition, when  you do the install from the cd you can tell the installer not to format the home directory and everything there will remain untouched.

---

### Post by SunnyRabbiera on 2009-06-01
Still I say stick with Hardy, its old yes but its STABLE.
Cant say the same about Jaunty.

---

### Post by cybuss on 2009-06-01
ok thanks i got ANOTHER PROBLEM! they coming faster then they going
im trying to burn a cd for my sister a hardy heron cd and it wont let me any ideas? screen shot be up soon

---

### Post by Jazzy_Jeff on 2009-06-01
> **SunnyRabbiera said:**
> Still I say stick with Hardy, its old yes but its STABLE.
Cant say the same about Jaunty.

Jaunty has been very stable for me. I have not seen any issues on my desktop or laptop computers.

---

### Post by SunnyRabbiera on 2009-06-01
> **Jazzy_Jeff said:**
> Jaunty has been very stable for me. I have not seen any issues on my desktop or laptop computers.

For you maybe, but I cant use it because its too slow.
Even with effects turned off.

---

