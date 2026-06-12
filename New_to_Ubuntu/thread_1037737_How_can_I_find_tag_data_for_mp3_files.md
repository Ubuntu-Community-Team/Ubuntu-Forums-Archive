---
title: "How can I find tag data for mp3 files?"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by curiousnoob on 2009-01-12
I am currently transferring my parents music library to their hard drive now that they have an mp3 player but I have come across several CDs that were burned for them by friends.  These do not have any tag data so it just comes up as unknown.  Is there anyway to make Rythmbox automatically find and download the appropriate tags?

---

### Post by mcduck on 2009-01-12
You could try Cowbell, very nice and simple-to-use tagging program for MP3-files.

---

### Post by mag_dex on 2009-01-12
I recommand great tool EasyTAG.

sudo apt-get install easytag

[http://easytag.sourceforge.net/](http://easytag.sourceforge.net/)

---

### Post by 3rdalbum on 2009-01-12
You're probably looking for Easytag. Despite the name, it's very powerful and it apparently can do exactly what you're looking to do.

---

### Post by curiousnoob on 2009-01-12
Is there an install guide for easytag?  I have downloaded the tar.gz file and extracted it but when I double click on the install-sh file and choose to run nothing happens.  
I also tried cowbell but when it attempts to connect to the amazon server it says to check my internet connection and try again.

---

### Post by curiousnoob on 2009-01-12
> **curiousnoob said:**
> Is there an install guide for easytag?  I have downloaded the tar.gz file and extracted it but when I double click on the install-sh file and choose to run nothing happens.  
I also tried cowbell but when it attempts to connect to the amazon server it says to check my internet connection and try again.

Nevermind.  I was able to find it in the add/remove menu.  I have not been able to make it work with my files however.  Using the CDDB I get a list of many options for each file but they don't match and nothing comes up when I try to find the album by including all the files.  
I believe this must mean that there are different files from different sources but I don't know why checking the individual files don't work.  
Is there any way I use this or another program to locate the source and tags for an orphan file or do a more comprehensive search?:confused:

---

### Post by hyper_ch on 2009-01-12
or use KID3... it can also check online.

---

### Post by curiousnoob on 2009-01-12
> **hyper_ch said:**
> or use KID3... it can also check online.

Thank you for the suggestion but I was unable to make this work as well.  Are there any other type of databases I could search manually?

---

### Post by ChildOfMana on 2009-01-12
I use [Banshee]("http://banshee-project.org/") as my music player. It automatically connects to the CDDB to search for metadata and album artwork.

However, on the rare occasion Banshee can't find any metadata I usually just go to [Amazon]("www.amazon.co.uk") and look up the CD I'm importing and manually enter the metadata.

[Last.fm]("http://www.last.fm/") is also a good place to look for Artist/Track metadata.

---

### Post by hyper_ch on 2009-01-12
I normally use the musicbrainz db to auto-get id tags... kid3 has that option to use that.

---

### Post by stchman on 2009-01-12
> **curiousnoob said:**
> I am currently transferring my parents music library to their hard drive now that they have an mp3 player but I have come across several CDs that were burned for them by friends.  These do not have any tag data so it just comes up as unknown.  Is there anyway to make Rythmbox automatically find and download the appropriate tags?

No, if the MP3 has no tag then creating a proper tag is not going to be possible.

If you know the song, you can install tagtool and manually install an ID3 tag.

```
sudo apt-get install tagtool
```

---

### Post by mjheagle8 on 2009-01-12
you can also just view the tag by right click>properties>audio

---

