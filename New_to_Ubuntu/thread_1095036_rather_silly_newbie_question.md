---
title: "rather silly newbie question?"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by cairnzi on 2009-03-13
hi people, ive just downloaded the new songbird player 1.1a to my desktop, now as there is no .deb yet is an .tar.gz file, i have never had to install anything from my desktop as yet, so if anybody could tell me how to do this i would be very gratefull, many thanks from a rather embarassed newbie;)

---

### Post by Cheesemill on 2009-03-13
You can find a .deb for SongBird at [GetDeb]("http://www.getdeb.net/").

Cheesemill

---

### Post by cairnzi on 2009-03-13
@cheesemill, i no but the new 1.1a version can watch multiple folders where as the first release cannot, thanks.

---

### Post by roccivic on 2009-03-13
First open a terminal and type in:
```
sudo apt-get install build-essential
```

Then extract your tarball somewhere. Navigate to that folder in terminal using the **cd** command. Once there run the configure script and hope that there won't be any errors:

```
./configure
```

if that went well, type in:

```
make
```and```
sudo make install
```

if configure returned some errors, then you are probably missing some packages. You can try searching for then using "Synaptic".

Hope this helps ;)

---

### Post by cairnzi on 2009-03-13
@roccivic, many thanks mate, working like a dream, will take a note of those commands for future reference, cheers again.

---

### Post by solian2002 on 2009-03-13
[http://www.getdeb.net/app/Songbird](http://www.getdeb.net/app/Songbird)

There is the deb file if you prefer. Hope that helps. :)

---

### Post by cairnzi on 2009-03-13
@roccivic, many thanks mate, working like a dream, will take a note of those commands for future reference, cheers again.

---

### Post by rburkartjo on 2009-03-13
cair, i usually always use a deb file for installation ( if avail) think it is the easiest. just my two cents

---

