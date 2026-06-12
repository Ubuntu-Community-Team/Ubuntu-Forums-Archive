---
title: "How do I hide album art in music folder?"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by gobberpooper on 2009-09-15
In my music phone, a quarter of the files are the album art. Why does it show in Ubuntu but not in Windows? I don't mind the fact that I have to scroll down more, but it takes a while to load the folder because of the album pictures. How can I hide it without individually placing a period in front of each one?

---

### Post by dj-toonz on 2009-09-15
> **gobberpooper said:**
> In my music phone, a quarter of the files are the album art. Why does it show in Ubuntu but not in Windows? I don't mind the fact that I have to scroll down more, but it takes a while to load the folder because of the album pictures. How can I hide it without individually placing a period in front of each one?

Hi there's 2 ways you can do this what I know off the top of my head the first one is put a txt file in the folder called .hidden & put all the folders in there without a . before it i.e in my home folder I have .hidden & then in that Desktop,Templates & so on & on (it doesn't remove it completely as where the file system can't find it, Just hides it 

Or the second way is by going to edit , Preferences , Previews , Going down to Show Thumbnails & having never in the box Then clicking on close

---

### Post by gobberpooper on 2009-09-15
i don't mean just move them to another folder but just hide them like in windows

---

### Post by sunchiqua on 2009-09-15
[LIST=1]
[*]Create a new file: .hidden
[*] Add file names you want to hide
[/LIST]

---

### Post by gobberpooper on 2009-09-15
> **sunchiqua said:**
> [LIST=1]
[*]Create a new file: .hidden
[*] Add file names you want to hide
[/LIST]

That's weird it doesn't work.
> 
/home/shridhar/Desktop/music/AlbumArt_{0A0B70F4-AA3C-48FF-B440-70925C53A4A0}_Large.jpg
/home/shridhar/Desktop/music/AlbumArt_{0A0B70F4-AA3C-48FF-B440-70925C53A4A0}_Small.jpg
/home/shridhar/Desktop/music/AlbumArt_{0ABE881C-29CC-418A-AE13-F99109B4F43C}_Large.jpg
/home/shridhar/Desktop/music/AlbumArt_{0ABE881C-29CC-418A-AE13-F99109B4F43C}_Small.jpg


I also tried it without the path but that didn't work either.

---

### Post by gn2 on 2009-09-15
As an example, right-click on then select rename and change ```
/home/shridhar/Desktop/music/AlbumArt_{0A0B70F4-AA3C-48FF-B440-70925C53A4A0}_Large.jpg
```

to ```
/home/shridhar/Desktop/music/.AlbumArt_{0A0B70F4-AA3C-48FF-B440-70925C53A4A0}_Large.jpg
```

By putting a . in front of the file name, it will not be shown.

If you want to hide the music folder, do: /home/shridhar/Desktop/.music

You can toggle between showing and hiding by pressing Ctrl+h

---

### Post by mcduck on 2009-09-16
> **gobberpooper said:**
> That's weird it doesn't work.


I also tried it without the path but that didn't work either.

the hidden file must be in the same directory as the files you wish to hide. And because of that, you don't need (and can't) use full paths, just the file names.

Also note that the .hidden file doesn't affect terminal listings, and not even every file manager respects it. For example nautilus does, PcManFM doesn't.

(renaming the files by changing their file names will probably just stop the player from recognizing them completely. Not a good idea, if you don't want it t o use the files you can just as well delete the files completely instead ;))

edit: You usually also have to move to some other directory and back again before the files disappear, Nautilus doen't constantly poll for the .hidden file but only reads it at the moment you enter a directory..

---

### Post by sunchiqua on 2009-09-16
> **gobberpooper said:**
> That's weird it doesn't work.


I also tried it without the path but that didn't work either.

.hidden file works within the given directory only. If you want to hide a file from /home/user/Music, you need to add file names ( yes, only file name, not path ) to the .hidden file, located at /home/user/Music, not somewhere else.

---

### Post by misfitpierce on 2009-09-16
If your talking about in file browser aka nautilus why not just turn off thumbnails in the nautilus settings?

---

### Post by specd822 on 2010-12-21
Hello there,

I know this reply is like really really late, but I was facing the same problem today, anyways I decided to write a basic script that will handle the "hiding" of the album art files, basically all I had to do is rename all the Albumart* files to .Albumart. The script is pretty straightforward. I am not sure whether you are familiar with shell scripts or not but if you would like, I can post my script for you.

Hope this helps :)

---

