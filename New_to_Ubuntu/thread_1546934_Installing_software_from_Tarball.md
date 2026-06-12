---
title: "Installing software from Tarball"
date: 2010-08-06
forum: New to Ubuntu
---

### Post by Moriarty123456 on 2010-08-06
Morning Ubuntu Pals,

And what a lovely morning it is too. I'm slowly getting used to Ubuntu, the majority of times in a positive way, but still loads to learn of course. 

I'm stuck on loading software from tarballs, I know, I know, there's some great software on the repositories and software centre, but the programs I lust after aren't on there. Anyway even if they were I'd still like to know how to install from places like sourceforge.

For example there's one called Wyneken I've downloaded that looks to be right "up my Strasse". I extracted the tarball and the folder is now sitting in my /home/robert folder - what now? Something about apt-get? Something about make? Something about make-install? 

Whaaaa?

Any help appreciated.

Thanks.

---

### Post by Moriarty123456 on 2010-08-06
Hey I did it! \\:D/Wyneken now up and running!

For other idiots like me: when I went to the extracted folder there was a file called 'install.py' (duh!) then in the terminal type:

sudo install.py

and away ye go.

---

### Post by isoscelesrectangle on 2010-08-06
Dug a bit around for you. Try doing this first. 
> Installation Instructions

Meet the following dependencies: (Install these from the Repositories)

python-2.5 or higher
tetex or texlive installed
python-imaging-1.1.6 or higher
qt-4.3 or higher
PyQt4-4.3 or higher


To install Wyneken 0.5.2, do the following:

(As root):
```
python setup.py install
texhash
wyn --auto-config

```
Once you have completed this, you can launch wyneken by typing: ```
wyneken
```


EDIT: Woops, I came a bit late. Sorry!

---

### Post by Moriarty123456 on 2010-08-06
Hey thanks for that. Very kind.

I'm still having a little trouble actually. The wyneken logo is there in office, but it hangs after the first time use menu. Your extra code will probably do the trick.

Do I need to 'cd' to the directory before entering it?

Thanks for your help.

---

