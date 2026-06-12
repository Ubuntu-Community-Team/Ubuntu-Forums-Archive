---
title: "weird picture in banshee"
date: 2010-08-11
forum: New to Ubuntu
---

### Post by philipballew on 2010-08-11
in my banshee music player the all albums picture is of a hannah montanah album no matter what album or artest i play. i dont want that there.

---

### Post by jtarin on 2010-08-11
Wow! Ididn't realize she was that popular.:p
[http://old.nabble.com/change-cover-art-with-banshee-td21127279.html](http://old.nabble.com/change-cover-art-with-banshee-td21127279.html)

It's actually a little complicated if there's one of these two problems:

1 - The album name has characters in it that are irregular, like [ , ], etc...
2 - Banshee misreads the album ID3 tag.

What you have to do if you don't have album art immediately pop up is navigate to your home folder and then press ctrl+H to reveal the hidden folders. Then navigate to /.cache/album-art.

You'll find a list of picture named in the following convention: artist-album.cover AND artist-album.jpg.

If Banshee is just having a problem reading your embedded album art (typically because of irregular characters) then you'll find a .cover file for your album and just need to rename it to a .jpg. If you do not see a picture that relates to your album, simply put a picture into that folder and name it with the artist-album.jpg convention. It has to be a JPG

The Folder.jpg/Cover.jpg trick might work, but I have not found it to.

---

### Post by ronnielsen1 on 2010-08-11
That's weird. You're not running Hannah Montana Linux or you? ;)

[http://hannahmontana.sourceforge.net/Site/Home.html](http://hannahmontana.sourceforge.net/Site/Home.html)

---

### Post by teh603 on 2010-08-11
> **ronnielsen1 said:**
> That's weird. You're not running Hannah Montana Linux or you? ;)

[http://hannahmontana.sourceforge.net/Site/Home.html](http://hannahmontana.sourceforge.net/Site/Home.html)

O.O

What has been seen cannot be unseen...

---

### Post by philipballew on 2010-08-11
actually i dont even have this album that shown on my comp making it even that much weirder

---

### Post by philipballew on 2010-08-13
so i am a little unsure what im soupossed to do there i think i tried it and nothing changed. any ideas?

---

### Post by jtarin on 2010-08-13
Exactly what have you done?

---

### Post by philipballew on 2010-08-13
i went to my home folder, revealed my hidden files then went to the album file and deleated every album picture of this albnum and restarted banshee. its still there.

---

### Post by jtarin on 2010-08-13
I don't use Banshee any longer so its difficult for me to help past this point.

---

