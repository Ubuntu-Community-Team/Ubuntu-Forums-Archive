---
title: "archive manager and .tar file problem"
date: 2009-04-04
forum: New to Ubuntu
---

### Post by gertrude58 on 2009-04-04
I really need some basic help on extracting files.I downloaded Lifeograph from Launchpad ,which was lifeograph-0.3.8src.tar.gz[md 5,sig]It appeared in archive manager and I didn't have a clue what to do with it so just left it there.Now today I can't find archive manager[which I had never seen before and didn't know existed!] or the file.Please could someone kindly tell me,in words of one syllable,how to deal with this file as I would like to be able to download other stuff like this in future.And will the app appear in applications when extracted?

I am running ubuntu 8.10 
Thanks in advance.

---

### Post by InspiredIndividual on 2009-04-04
I'm afraid I'm not proficient enough in the noble english language to express myself using only monosyllables... if your instruction to do so was british humor, please educate me ;-) That being said, I'll try to address your question. I'm not sure what your experience level is, so I'll just try to be as complete as possible. Let me know if anything's still unclear afterwards, so I can elaborate if necessary.

When you click a .tar.gz file in your browser, choose 'Open with Archive Manager'. Afterwards, click 'Extract' and navigate to the directory where you want the files to be saved. This is a generic way to download and extract files from archives in Ubuntu.

When you open an archive with Archive Manager in this way, the archive is downloaded as a temporary file. As those files are, well, temporary, you probably have to download lifeograph-0.3.8src.tar.gz again. If you prefer you store the archive permanently on your hard disk as well (instead of only the unpacked files), choose 'Save file' instead of 'Open with Archive Manager' when clicking the .tar.gz file.

Regarding the particular download, it looks like you downloaded the source code of the Lifeograph software. This means you don't have an installed application yet after you've downloaded and extracted the files. It's like having a recipe and the ingredients for cake, but you still have to bake it yourself. An 'easy' howto can be found here:
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)
It's not very concise in my humble opinion, and I can certainly help you translate unclear parts into less technical language. However, if you plan to download other software from source in the future, it's worthwhile to go through the howto. Frankly, upon seeing the HowTo for the first time after coming to Ubuntu, I thought it didn't look very easy. Luckily, in practice it will get easy very soon, just like baking cakes... :-D

I don't think the application will appear in 'Applications' automatically. Luckily, it's very easy to add yourself if it doesn't. Right click 'Applications', 'Edit Menus', 'New Item' and fill the necessary information. I think that's intuitive enough that you won't have any trouble with it. Of course, it's possible I'm biased, so feel free to ask for clarification if anything is unclear.

---

### Post by gertrude58 on 2009-04-05
Thanks for your concise instructions on archive manager and how to get apps on the applications list.I have bookmarked the page you sent me to,It scared me half to death! Maybe when I have a bit more confidence in my abilities, I might have another go,but as a complete novice[one month] with linux,I think I will do as advised and wait until someone packages lifeograph.It's not an essential after all.Just one more[dim] question-did you mean that your instructions work for a normal .tar file?I mean if it doesn't need to be 'baked' like a cake,as you put it.i hope you see what I mean!

---

