---
title: "Where is the desktop image stored, please?"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by Mariane on 2009-11-09
I would like to retrieve the desktop image I had, where is it stored please? 

Mariane

---

### Post by mikewhatever on 2009-11-09
The desktop image you had might be anything you stored anywhere, so how would anyone know? Can you be more specific. Perhaps you are looking for /usr/share/backgrounds, but that's a far fetched guess.

---

### Post by JugglinPhil on 2009-11-09
Do you mean your Desktop background? You can change them by going to System => Preferences => Appearance under the Background tab. The images themselves are usually stored under /usr/share/backgrounds.
Edit: Looks like I was a little late here. ^^ :)

---

### Post by Mariane on 2009-11-10
Yes, this did sound like "Do you know where I stored such a file?". Ooops. 
I was using kde control center when I got this file, I chose it among others to download. So it probably put it in /usr/share/backgrounds if this is the default location. 

I'll go and look (I have to put the old hard disk in for that and nothing says this file is still intact) 

Thank you

Mariane

---

### Post by Mariane on 2009-11-10
No, it was not there. I searched for all jpg files on the old hard disk and went to look at anything even remotely likely. Maybe it got lost when the hard disk failed. 

I tried to redo the same installation process with another file, using the kde control center, but either the name gets modified during download or I don't know what happens, can't find the newly downloaded file either. Is something wrong with my syntax? I do 

```

cd /

```

and then 

```

sudo find ./ -name *.jpg

```

(It I don't search as root I get a lot of "permission denied" lines.) 

Mariane

---

### Post by philinux on 2009-11-10
It was maybe a .png file.

Try using kfind with modified files less than xx days old.

---

### Post by mrboojive on 2009-11-10
You might also try looking in .kde/cache-*your-computer's-name*/plasma-wallpapers/ but substituting the name of your computer for *your-computer's-name*. KDE keeps some kind of a cache of recently used wallpapers there.

---

### Post by Mariane on 2009-11-10
Yeah, you're right! 
/disk/home/<username>/.kde/share/wallpapers/

Thank you very much  :D 

Mariane

---

