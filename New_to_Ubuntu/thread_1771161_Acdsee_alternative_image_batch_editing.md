---
title: "Acdsee alternative image batch editing"
date: 2011-05-30
forum: New to Ubuntu
---

### Post by 007casper on 2011-05-30
Is there an Acdsee/Irfan view/Lightroom alternative on linux?  I need image batch editing where I can rename files, add prefix, postfix to names etc

fspot doesnt have all the bells and whistles

I saw this [http://photodoto.com/free-photo-editors/](http://photodoto.com/free-photo-editors/)  and also checked synaptic. ???

thank you.

---

### Post by jtarin on 2011-05-30
[ImageMagick]("https://help.ubuntu.com/community/ImageMagick") installation.
[Home.]("http://www.imagemagick.org/script/index.php")

---

### Post by 007casper on 2011-05-30
I have it loaded.  How do I launch it through terminal?

I typed imagemagick, I got command not found

thank you

---

### Post by jtarin on 2011-05-30
> **007casper said:**
> I have it loaded.  How do I launch it through terminal?

I typed imagemagick, I got command not found

thank youI gave you a link to their hompage.:P

---

### Post by 007casper on 2011-05-30
nice I really appreciate it.

Is there gui for this?  It says it does.

---

### Post by jtarin on 2011-05-30
[http://www.imagemagick.org/script/api.php](http://www.imagemagick.org/script/api.php)
[http://www.imagemagick.org/Usage/](http://www.imagemagick.org/Usage/)
Plug the term "ImageMagick" into Synaptic package manager.

---

### Post by HermanAB on 2011-05-30
The Imagemagick utility is called 'convert'.

---

### Post by 007casper on 2011-05-30
@jtarin thank you for the links. I really appreciate it.

I also checked out convert on the terminal.

I am really looking for a push button interface.  Maybe it is facing me and I dont see it.

I also tried graphicsmagick.  However, I dont get the same interface as this link
[http://dailypackage.fedorabook.com/uploads/2008-02-19-graphicsmagick.jpg](http://dailypackage.fedorabook.com/uploads/2008-02-19-graphicsmagick.jpg) I guess that is for fedora, I figured it would at least have a similar menu.

I am still trying to figure out how to launch a graphic interface menu driven imagemagick.

---

### Post by 007casper on 2011-05-30
Geeqie is light and extremely fast. 

If there is an alternative where it has a lot of bells and whistles to batch process images, please let me know.

Thank you.

---

### Post by dFlyer on 2011-05-30
Have a look at bibble lab b5 and lightcraft lightzone. Neither of these are free software, but they work very well with linux.

---

### Post by jtarin on 2011-05-30
> **007casper said:**
> @jtarin thank you for the links. I really appreciate it.

I also checked out convert on the terminal.

I am really looking for a push button interface.  Maybe it is facing me and I dont see it.

I also tried graphicsmagick.  However, I dont get the same interface as this link
[http://dailypackage.fedorabook.com/uploads/2008-02-19-graphicsmagick.jpg](http://dailypackage.fedorabook.com/uploads/2008-02-19-graphicsmagick.jpg) I guess that is for fedora, I figured it would at least have a similar menu.

I am still trying to figure out how to launch a graphic interface menu driven imagemagick.From the second paragraph on their main page.> The functionality of ImageMagick is typically utilized from the command line or you can use the features from programs written in your favorite language. **_Choose from these interfaces: _**G2F (Ada), MagickCore (C), MagickWand (C), ChMagick (Ch), ImageMagickObject (COM+), Magick++ (C++), JMagick (Java), L-Magick (Lisp), NMagick (Neko/haXe), MagickNet (.NET), PascalMagick (Pascal), PerlMagick (Perl), MagickWand for PHP (PHP), IMagick (PHP), PythonMagick (Python), RMagick (Ruby), or TclMagick (Tcl/TK). With a language interface, use ImageMagick to modify or create images dynamically and automagically.

---

### Post by 007casper on 2011-06-02
> The functionality of ImageMagick is typically utilized from the command line or you can use the features from programs written in your favorite language. Choose from these interfaces: G2F (Ada), MagickCore (C), MagickWand (C), ChMagick (Ch), ImageMagickObject (COM+), Magick++ (C++), JMagick (Java), L-Magick (Lisp), NMagick (Neko/haXe), MagickNet (.NET), PascalMagick (Pascal), PerlMagick (Perl), MagickWand for PHP (PHP), IMagick (PHP), PythonMagick (Python), RMagick (Ruby), or TclMagick (Tcl/TK). With a language interface, use ImageMagick to modify or create images dynamically and automagically. 

I tried some of those. I checked out magickcore, magickwand, magick++, perlmagick.

I love how powerful imagemagick, it is a bummer that it doesn't have gui.  I had to play around in terminal, and get a list of images, take it to spreadsheet, rename it, and reload it with the convert command and run it through.  Maybe, I will figure out a better way to tackle it later on.  I was surprised that a few of the names came out all weird.  Overall, it is definitely better than doing it manually.

I finally figured graphicsmagick gui.  If you click on the left button menu shows up, and if you click on the right button, you get alternative options.  However, I couldn't find rename option on graphicsmagick.

My biggest desire to add a prefix to image file, and rename it in batch if it is necessary.  In addition to that, find/replace would be awesome. Quick and easy. Nothing complicated.  

Geeqie is fast, agile.  I like it.  Unfortunately, you can't prefix a name.  It seems like you could, however it overwrites the old name.  It doesn't have find/replace option either.  I just want to substitute underscore _ to dash -  Nothing.  You can't even do it.  However, you can rename the file three different ways. You can't batch rename multiple types of files either (those with different extensions).

I am about to check out gThumb.

---

### Post by Jon69 on 2011-08-10
Be careful with gThumb I've just tried it (in Ubuntu 10.04), it seemed to be easy, but in renaming a batch of photos it made all but one of them disappear!!

I am not technical enough to report how and why. I just know that they're no longer there, nor in rubbish bin. So at least to be safe, practice with something you don't mind losing!

---

### Post by mcduck on 2011-08-10
> **007casper said:**
> I tried some of those. I checked out magickcore, magickwand, magick++, perlmagick.

I love how powerful imagemagick, it is a bummer that it doesn't have gui.  I had to play around in terminal, and get a list of images, take it to spreadsheet, rename it, and reload it with the convert command and run it through.  Maybe, I will figure out a better way to tackle it later on.  I was surprised that a few of the names came out all weird.  Overall, it is definitely better than doing it manually.

I finally figured graphicsmagick gui.  If you click on the left button menu shows up, and if you click on the right button, you get alternative options.  However, I couldn't find rename option on graphicsmagick.

My biggest desire to add a prefix to image file, and rename it in batch if it is necessary.  In addition to that, find/replace would be awesome. Quick and easy. Nothing complicated.  

Geeqie is fast, agile.  I like it.  Unfortunately, you can't prefix a name.  It seems like you could, however it overwrites the old name.  It doesn't have find/replace option either.  I just want to substitute underscore _ to dash -  Nothing.  You can't even do it.  However, you can rename the file three different ways. You can't batch rename multiple types of files either (those with different extensions).

I am about to check out gThumb.
If you just want to edit the image *names*, then it makes no sense to use any image editor at all. A simple shell script, or any file renaming utility, will do the trick in less time and without reducing the image quality.

For example the Thunar file manager (used in XFCE desktop, but works fine on any other as well) includes a great bulk renaming tool.

(if you actually need to edit the images as well instead of just renaming them, you might want to try [Phatch]("http://photobatch.stani.be/"), it's the easiest one for the purpose and quite powerful as well. It should be in Ubuntu's repositories.)

---

