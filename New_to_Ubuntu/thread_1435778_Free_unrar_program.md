---
title: "Free unrar program?"
date: 2010-03-21
forum: New to Ubuntu
---

### Post by razorseal on 2010-03-21
I found the one on synaptic, but it says 'read only' and it will not let me extract the files! I tried xarchiver, and that didn't work either...

FYI, this is what i'm trying to download - 

[http://woolfier.deviantart.com/art/Xions-Icon-template-88810804](http://woolfier.deviantart.com/art/Xions-Icon-template-88810804)

---

### Post by mkvnmtr on 2010-03-21
From you link I could not tell what you are trying to extract. But if you have a rar file you should have no trouble working with it with the apps in the repositories. In fact you should be able to double click on it or right click on it. Maybae it is not a rar archieve. 
What I normally do on a new install is open a search in synaptic for rar, zip and compression and install all the apps that look like they will be of benifit to me. Then I have no trouble with anything.

---

### Post by Ozymandias_117 on 2010-03-21
Archive Manager which your computer comes with can open it. Just download and double click. (If it tries to open it with something else, right-click and select open with another application and select Archive Manager)

---

### Post by razorseal on 2010-03-21
Archive manager will not open it... 

it says "Archive type not supported"

---

### Post by Ozymandias_117 on 2010-03-21
> **mkvnmtr said:**
> From you link I could not tell what you are trying to extract. But if you have a rar file you should have no trouble working with it with the apps in the repositories. In fact you should be able to double click on it or right click on it. Maybae it is not a rar archieve. 
What I normally do on a new install is open a search in synaptic for rar, zip and compression and install all the apps that look like they will be of benifit to me. Then I have no trouble with anything.

There is a download button in the top left, I downloaded and Archive Manager was able to open it.

BTW, to the OP: If you're somewhat comfortable with the command line, you can use 7zip (But it only has a CLI in Linux) by using ```
sudo apt-get install p7zip-full
```

---

### Post by ndefontenay on 2010-03-21
I've downloaded a rar'ed file saturday and I was happily surprised that Ubuntu could unrar it no problem.

---

### Post by razorseal on 2010-03-21
> **mkvnmtr said:**
> From you link I could not tell what you are trying to extract. But if you have a rar file you should have no trouble working with it with the apps in the repositories. In fact you should be able to double click on it or right click on it. Maybae it is not a rar archieve. 
What I normally do on a new install is open a search in synaptic for rar, zip and compression and install all the apps that look like they will be of benifit to me. Then I have no trouble with anything.

this is what I'm trying to download... its a set of icons that I'm trying to make work with conky

[http://www.deviantart.com/download/88810804/Xions_Icon_template_by_woolfier.rar](http://www.deviantart.com/download/88810804/Xions_Icon_template_by_woolfier.rar)

---

### Post by Ozymandias_117 on 2010-03-21
> **razorseal said:**
> Archive manager will not open it... 

it says "Archive type not supported"

Hmm... when I downloaded, I got a file named "Xions_Icon_template_by_woolfier.rar" Did I download the wrong thing?

---

### Post by razorseal on 2010-03-21
> **Ozymandias_117 said:**
> There is a download button in the top left, I downloaded and Archive Manager was able to open it.


I don't get it... it's not opening it for me i'm specifally using archive manager by clicking and selecting it

---

### Post by Ozymandias_117 on 2010-03-21
> **razorseal said:**
> I don't get it... it's not opening it for me i'm specifally using archive manager by clicking and selecting it

Sorry, I'm not sure what it could be...

---

### Post by razorseal on 2010-03-21
here is proof that I can't open it... no clue what's going on =/

anyone help?

---

### Post by mkvnmtr on 2010-03-21
It took me a while because I was on XP ina virtual box when I answered you. I was able to download and open the file with no problem when I got back on nUbuntu. It was a rar file and archive manager just extracted it. Can not think what your problem might be.
By the way the icons look kind of ugly.

---

### Post by razorseal on 2010-03-21
I really dont know why it won't open it with mine... just making me mad now grrrr

the icons are for a conky setup actually lol

---

### Post by ikt on 2010-03-21
> **razorseal said:**
> I really dont know why it won't open it with mine... just making me mad now grrrr

the icons are for a conky setup actually lol

if you install unrar:

```
sudo apt-get install unrar
```

does it work?

---

### Post by razorseal on 2010-03-21
> **ikt said:**
> if you install unrar:

```
sudo apt-get install unrar
```does it work?

when I used that it was 'read only' I was able to see the files in the folder, but it would not let me extract them

---

### Post by jrusso2 on 2010-03-21
unrar is a free program but rar is shareware.

---

### Post by ikt on 2010-03-21
> **razorseal said:**
> when I used that it was 'read only' I was able to see the files in the folder, but it would not let me extract them

select all the files in the archive, then choose extract.

working fine for me here.

---

### Post by asmoore82 on 2010-03-21
I was able to just right-click the archive and "Extract Here" ...
**_But_** you have to have the "unrar" package first!!
```
sudo apt-get install unrar
```

Just for fun, after it's extracted, if you right-click and "Compress" it many ways:
```
du -sb Xions* | sort -n
174291	Xions.7z
174324	Xions.tar.lzma
178079	Xions.zip
178309	Xions.tar.gz
178439	Xions_Icon_template_by_woolfier.rar
178569	Xions.tar.bz2
185512	Xions
```
^^7zip and even plain old zip and tar.gz out perform rar here.
rar is non-free Shovelware :popcorn:

Ooo - multi-part archives - w0w...```
man split
```

---

### Post by Roger Allott on 2010-03-21
Download the rar file again. It sounds to me as if you only got part of the file, which is why Archive Manager can't unwrap it.

---

### Post by razorseal on 2010-03-21
I just tried it on my desktop and it didn't work either... I also tried it with unrar and that lets me open it, but it says 'read only'

I'm just real confused how it works for you guys, and on both my desktop and laptop it will not work... 

would this have anything to do with that fact that I used wubi to install linux on these computers?

---

### Post by Roger Allott on 2010-03-21
Check the file size of your downloaded rar archive. If it's not "174.3 KB (178439 bytes)", you haven't got the full file.

---

### Post by ikt on 2010-03-21
> **razorseal said:**
> I just tried it on my desktop and it didn't work either... I also tried it with unrar and that lets me open it, but it says 'read only'

can you print screen the error message you get when selecting all the files and choosing extract?

---

### Post by razorseal on 2010-03-21
> **ikt said:**
> can you print screen the error message you get when selecting all the files and choosing extract?

ok... with unrar app it let me 'drag' them out of the window to the desktop, but extract button didn't work. No error comes up when I try to extract, it acts as if it extracted, but it really didn't

oh well, dragging will work... lol

---

