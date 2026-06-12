---
title: "how to download a wav file"
date: 2009-08-08
forum: New to Ubuntu
---

### Post by mystmaiden on 2009-08-08
The site help said to play it then right click and save as, but I don't seem to have that option. I think I'm definitely missing something here. Save link as didn't work because it said I needed an html plugin. I just want the little wav not the whole bloomin page :)

myst

---

### Post by Praseodymi on 2009-08-08
Are you sure your clicking the correct link?

---

### Post by mystmaiden on 2009-08-09
yeah, there's no link involved.

---

### Post by credobyte on 2009-08-09
Try downloading it via terminal:
```
wget http://www.domain.com/file.wav
```
[COLOR=Gray]** Replace the url with your wav file location ( download link or smth like that ) ..[/COLOR]

---

### Post by 3rdalbum on 2009-08-09
What site are we talking about? If it's an audio file that is embedded in a web page, you can't right-click it and choose Save As.

Generally you have to right-click the page and choose View Page Information, then click the Media button, to find out the URL of the media file. Then you can use Wget, as shown above, to download it.

---

### Post by mystmaiden on 2009-08-10
Cool, I had no idea about the 'view page info' option. Very handy. I can't remember the link now, I'll do another search and go at it that way. Thanks

mystmaiden

---

