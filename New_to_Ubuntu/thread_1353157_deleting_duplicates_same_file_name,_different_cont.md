---
title: "deleting duplicates: same file name, different contents"
date: 2009-12-12
forum: New to Ubuntu
---

### Post by jmcgovern on 2009-12-12
I'm trying to sort through my music collection. Due to adventures trying to get the music off my iPod, I've ended up with multiple files which have duplicate names, but they may not be exact copies.  Due to errors importing, some of the duplicate files are the whole song, some are only partials (playback stops midsong).  I've found fdupes and fslint via searching, but I want to be able to tell which are the bad imports and delete those, while keeping the goods, and the files appear to be the same size.  any advice, or am i just gonna have to listen to the songs?

---

### Post by NCLI on 2009-12-13
> **jmcgovern said:**
> I'm trying to sort through my music collection. Due to adventures trying to get the music off my iPod, I've ended up with multiple files which have duplicate names, but they may not be exact copies.  Due to errors importing, some of the duplicate files are the whole song, some are only partials (playback stops midsong).  I've found fdupes and fslint via searching, but I want to be able to tell which are the bad imports and delete those, while keeping the goods, and the files appear to be the same size.  any advice, or am i just gonna have to listen to the songs?

Are you sure they all have the EXACT same filename?

---

### Post by ankspo71 on 2009-12-13
I don't think I have a real answer to your question, but to make it a little easier....


There might be a program that will detect broken mp3's or other media types though.
Go to synaptic package manager, and search for checkmp3, as that could be a program of use to you. There may be other programs for other filetypes too.

If you imported your songs and it imported them into multiple directories (example: my music 1, my music 2, my music 3, etc, you can open two or more instances of nautilus windows for comparing the songs, then delete each bad song one by one, the finally merge all of the folders into one.

maybe it would be easier to compare the file creation dates (assuming the newer ones are the best). 

maybe it would be easier to compare the file size (assuming the bigger ones are the best). 

If you open each song in a program such as audacity, you can visually see where a song cuts off and not have to listen to it. This could take forever though.


hope I somehow gave you some useful ideas,
James

---

