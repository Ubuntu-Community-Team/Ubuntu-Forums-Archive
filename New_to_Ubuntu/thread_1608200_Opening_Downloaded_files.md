---
title: "Opening Downloaded files"
date: 2010-10-28
forum: New to Ubuntu
---

### Post by franzferdinand on 2010-10-28
I am new to Ubuntu. I have apparently successfully downloaded some .zip and .rar files but I cannot open them. I have added 7zip and p7zip apps but if I try and open the files they do nothing. If I right click and try and choose an application the 7zip and p7zip do not appear on the application list. 
What am I doing wrong/missing?

---

### Post by Ubuntiac on 2010-10-28
Try installing the package "unrar" from the Software Center (or in Kpackagekit if you're on Kubuntu) and see if that helps.

---

### Post by franzferdinand on 2010-10-28
UNRAR does not appear on my list. I have accessed the full list.

---

### Post by Der Ritter on 2010-10-28
> **franzferdinand said:**
> I am new to Ubuntu. I have apparently successfully downloaded some .zip and .rar files but I cannot open them. I have added 7zip and p7zip apps but if I try and open the files they do nothing. If I right click and try and choose an application the 7zip and p7zip do not appear on the application list. 
What am I doing wrong/missing?

Right-click the file, click "Open With", and select "Archive Manager".

I dunno how you installed 7zip, there is not a version of 7zip for linux. p7zip, as far as I know, is an unofficial port that is only endorsed by the 7zip developers.

That aside, if you want to use p7zip, open a terminal (Applications -> Accessories -> Terminal) and type
```
p7zip -d /path/to/the/file.zip
```
but file-roller (the "Archive Manager" previously mentioned) should be fine for your needs.

---

### Post by franzferdinand on 2010-10-28
Ok, so using Archive Manager on the RAR file gets a 'Archive Type Not Supported' message. 

This seems much more complicated than I thought it would be. The 7zip and p7zip are all on the list of apps to download so why dont they work?

---

### Post by Der Ritter on 2010-10-28
> **franzferdinand said:**
> Ok, so using Archive Manager on the RAR file gets a 'Archive Type Not Supported' message. 

This seems much more complicated than I thought it would be. The 7zip and p7zip are all on the list of apps to download so why dont they work?

What do you mean by "the list of apps to download"?

---

### Post by franzferdinand on 2010-10-28
So when I go to Add/Remove files it does not appear even though I access the whole list.

Surely it should be easy to open a RAR or ZIP file?

---

### Post by Der Ritter on 2010-10-28
> **franzferdinand said:**
> So when I go to Add/Remove files it does not appear even though I access the whole list.

Surely it should be easy to open a RAR or ZIP file?

Terribly sorry, I assumed you had already done the step in post 2 of this thread.

Open a terminal and do

```
sudo apt-get install unrar
```

Then try it with "Archive Manager" and it should work.

---

### Post by franzferdinand on 2010-10-28
Superb. It works. Thank you so much.

---

### Post by beew on 2010-10-28
[http://peazip.sourceforge.net/](http://peazip.sourceforge.net/)[URL="http://peazip.sourceforge.net/"]
[/URL]

---

### Post by mister_playboy on 2010-10-28
> **beew said:**
> [http://peazip.sourceforge.net/](http://peazip.sourceforge.net/)[URL="http://peazip.sourceforge.net/"]
[/URL]

I was just trying PeaZip out yesterday and I can't recommend it.  The UI is quite slow, and entering a directory with hundreds of files caused the program to lock up with 100% CPU on one core... I assume this is related to the CRC hash generation or something.

Sounded promising, but was near unusable for me.

---

### Post by beew on 2010-10-28
> **mister_playboy said:**
> I was just trying PeaZip out yesterday and I can't recommend it.  The UI is quite slow, and entering a directory with hundreds of files caused the program to lock up with 100% CPU on one core... I assume this is related to the CRC hash generation or something.

Sounded promising, but was near unusable for me.

You may want to try p7zip (install p7zip-full p7zip-rar) and get the gui Q7Z from SourceForge. PeaZip works for me but P7Zip is much faster. File-roller is a complete piece of junk.

---

### Post by SeijiSensei on 2010-10-28
RAR is [not an open format]("http://en.wikipedia.org/wiki/RAR") so Ubuntu can't include free tools to handle rar archives.  That's why you need to install unrar separately after installing Ubuntu.

---

