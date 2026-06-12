---
title: "Install Vista fonts into Ubuntu"
date: 2010-05-19
forum: New to Ubuntu
---

### Post by belochkka on 2010-05-19
Okay, so I'm running a dual-boot system, with Ubuntu Lucid and Windows XP happily coexisting on two separate partitions.
I also have MS Office 2007, and Vista fonts installed on Windows. Everything fully licensed and paid for, so I'm not doing anything illegal here!
**How do I copy the Vista fonts to my Ubuntu installation???**
While I'd *like* to copy all of them, preferably, I desperately need Cambria, since my thesis has to be written in it.
How do I do this???

Note
I've tried the "hack" where you download MS PPT viewer, and copy the fonts. Doesn't work.

Thanks in advance!

---

### Post by 3rdalbum on 2010-05-19
You need to copy your fonts from C:\Windows\Fonts\, to /usr/share/fonts/truetype.

Note that you'll need to open a root file browser in order to copy files to that location. You can open a root file browser by hitting Alt-F2 and typing:

```
gksudo nautilus
```

---

### Post by Paqman on 2010-05-19
It's not something I really do, but IIRC you'll have to rebuild the font cache after copying over all the fonts. I believe you can do that with the command:
```
sudo fc-cache -f -v
```

---

### Post by pmlxuser on 2010-05-19
copy your fonts into ~/.fonts

ie creat a .fonts  folder in your home director ```
mkdir .fonts 
```
copy as much windows fonts into this folder log out then in you have all the fonts available to you....

---

### Post by 3rdalbum on 2010-05-19
> **Paqman said:**
> It's not something I really do, but IIRC you'll have to rebuild the font cache after copying over all the fonts. I believe you can do that with the command:
```
sudo fc-cache -f -v
```

Ahh, I've learnt something new today.

---

### Post by -humanaut- on 2010-05-19
sudo apt-get install ubuntu-restricted-extras will install Windows fonts.

---

### Post by belochkka on 2010-05-19
> It's not something I really do, but IIRC you'll have to rebuild the font cache after copying over all the fonts. I believe you can do that with the command:Copied Cambria over manually to /.fonts
rebuilt the tree and IT WORKS. Thank you!

> sudo apt-get install ubuntu-restricted-extras will install Windows fonts.Not Vista fonts like Cambria and Calibri, no, it won't! They're proprietary and licensed by Microsoft.

---

### Post by mrboojive on 2010-05-19
If your Windows drive is mounted in Ubuntu, instead of copying, you could just make a link from your Windows fonts folder to your .fonts folder. Assuming you are in your home directory, the command would be something like

```
ln -s /path/to/your/windows/fonts/folder .fonts/windows
```

Then rebuild the font cache.

---

### Post by Teddykhil on 2010-06-16
G'day, I'm understanding on how to install Windows fonts to Ubuntu, but how to you "Rebuild my font's List" ???

Thanks, Teddy

---

### Post by mrboojive on 2010-06-16
To rebuild the font cache, open a terminal and enter the command:
```
sudo fc-cache -fv
```

---

### Post by cpcpcp on 2010-08-31
> **mrboojive said:**
> If your Windows drive is mounted in Ubuntu, instead of copying, you could just make a link from your Windows fonts folder to your .fonts folder. Assuming you are in your home directory, the command would be something like

```
ln -s /path/to/your/windows/fonts/folder .fonts/windows
```Then rebuild the font cache.

I did as you suggest but as you can see I had an error and so used a slightly different version:-

```
ln -s /media/0AC8F325C8F30DA7/Windows/Fonts .fonts/window
ln: creating symbolic link `.fonts/window': No such file or directory
 ln -s /media/0AC8F325C8F30DA7/Windows/Fonts .fonts

cjp@cjp-desktop:~$ sudo fc-cache -fv

```it did something :o :-
```
/usr/share/fonts: caching, new cache contents: 0 fonts, 3 dirs
/usr/share/fonts/X11: caching, new cache contents: 0 fonts, 6 dirs
/usr/share/fonts/X11/100dpi: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/75dpi: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/Type1: caching, new cache contents: 9 fonts, 0 dirs
/usr/share/fonts/X11/encodings: caching, new cache contents: 0 fonts, 1 dirs
/usr/share/fonts/X11/encodings/large: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/misc: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/util: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/truetype: caching, new cache contents: 1 fonts, 15 dirs
/usr/share/fonts/truetype/freefont: caching, new cache contents: 12 fonts, 0 dirs
/usr/share/fonts/truetype/msttcorefonts: caching, new cache contents: 60 fonts, 0 dirs
/usr/share/fonts/truetype/openoffice: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/takao: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/thai: caching, new cache contents: 54 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-dejavu: caching, new cache contents: 6 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-indic-fonts-core: caching, new cache contents: 17 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-kacst-one: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-khmeros-core: caching, new cache contents: 2 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-lao: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-liberation: caching, new cache contents: 12 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-punjabi-fonts: caching, new cache contents: 2 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-symbol-replacement: caching, new cache contents: 0 fonts, 1 dirs
/usr/share/fonts/truetype/ttf-symbol-replacement/symbol-replacement.ttf: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/unfonts: caching, new cache contents: 4 fonts, 0 dirs
/usr/share/fonts/truetype/wqy: caching, new cache contents: 2 fonts, 0 dirs
/usr/share/fonts/type1: caching, new cache contents: 0 fonts, 2 dirs
/usr/share/fonts/type1/gsfonts: caching, new cache contents: 35 fonts, 0 dirs
/usr/share/fonts/type1/mathml: caching, new cache contents: 1 fonts, 0 dirs
/usr/X11R6/lib/X11/fonts: skipping, no such directory
/usr/local/share/fonts: caching, new cache contents: 0 fonts, 0 dirs
/home/cjp/.fonts: caching, new cache contents: 208 fonts, 0 dirs
/var/cache/fontconfig: cleaning cache directory
/home/cjp/.fontconfig: cleaning cache directory
fc-cache: succeeded

```but all the TT fonts did not seem to make to Office's drop down list of fonts

Is it me?:confused:  Do I need to copy them across rather than linking?

Chris

---

### Post by mrboojive on 2010-08-31
Yeah, if you want to do it the same way I suggested, you would need to create a .fonts folder in your home directory first before you can place a symbolic link inside it, e.g.:```
mkdir .fonts
```

What you did is just link your Windows fonts folder straight to .fonts, which should work just fine, too (unless you want to put other fonts in .fonts in the future, because then you'll be putting them in a folder on your Windows drive). Anyways, based on this line from the output, it looks like the fonts cached properly because it says there are 208 fonts cached from your .fonts directory:```
/home/cjp/.fonts: caching, new cache contents: 208 fonts, 0 dirs
```

So you are talking about OpenOffice, right? Try closing it and opening it again. That will refresh its list of fonts. Or look at the list of fonts in another program to see if they are showing up there. You can also verify that your Windows fonts are linked to .fonts by using the file browser to look in your .fonts directory (show hidden files/folders to get to it), or by doing this (should give a big list of .TTF files):```
ls .fonts
```

---

### Post by cpcpcp on 2010-09-01
> **mrboojive said:**
> So you are talking about OpenOffice, right? Try closing it and opening it again. That will refresh its list of fonts. Or look at the list of fonts in another program to see if they are showing up there. You can also verify that your Windows fonts are linked to .fonts by using the file browser to look in your .fonts directory (show hidden files/folders to get to it), or by doing this (should give a big list of .TTF files):```
ls .fonts
```

Office's fonts is sorted thanks.

A couple of  things though if you have the time or patience?

I seem to have** font** folders all over the place, is that normal or have things got out of hand and need sorting out?
/etc/fonts
/etc/X11/fonts
/usr/local/share/fonts
/usr/share/fonts

the ones below seem to relate to programmes only so do not bother me really but the first four?

/usr/lib/firefox-3.68/res/fonts
/usr/lib/openoffice.basis3.2/fonts
/usr/lib/xulrunner-1.9.2.8/res/fonts
/usr/share/feh/fonts
/usr/share/cups/fonts
/usr/share/ghostscript/8.71/Resorce/Font
/usr/share/wine/fonts

the other thing relates to symbolic link thingies (ls -s and all that)

Browsing through questions and answers I came across the suggestion that such links are all placed in one folder so they can be located, amended, deleted quite easily. It seemed to make sense to me (as I have no idea where the one I created only yesterday might be:P) but what do you think ?

Chris

---

### Post by mrboojive on 2010-09-01
It is normal to have all of those font folders. If you look at the output of the font config cache command you did, you will see that most of the fonts that were cached were from /usr/share/fonts/. Many of those other font folders, like the X11 one and the Firefox one, don't have fonts in them. They just have configuration files in them that configure how those programs use fonts.

I'm not sure I understand your symlinks question, but I'll try to explain. You made a symlink from ".fonts" in your home directory to the Windows fonts folder on your Windows drive. The ".fonts" folder located in your home directory is the symlink. A symlink is kind of like opening up a wormhole from one file or folder to another. Now, if you use the file manager and open up ".fonts" in your home directory, it will show everything that is in the fonts folder on your Windows drive. Linux knows to look in ".fonts" in your home directory to see if you have any fonts there, so all we did was redirect it to the fonts folder on your Windows drive. So now your OS thinks it's looking in your ".fonts" folder for fonts, but actually it's checking your Windows fonts folder.

There are symlinks like that all over the place on Linux. The only potential issue with what you did will come up if you plan to put more of your own fonts in your ".fonts" folder in the future (like if you found some cool TTF file and want to be able to use that font in all of your applications). That's going to be kind of awkward since your ".fonts" isn't an actual folder, just a link. In that case, you could make a real ".fonts" folder and place the symlink inside the folder along with whatever other additional fonts you wanted to put in there. The way you would do that is go to your home folder and delete the symlink you already made using the file manager or by doing:```
rm .fonts
```Then make an actual ".fonts" folder and put the symlink inside that folder:```
mkdir .fonts
ln -s /path/to/your/windows/fonts/folder .fonts/windows
```Then the "windows" folder inside your ".fonts" folder would be the link.

---

### Post by Miyavix3 on 2010-09-01
Can't you just double click the font files (from your ntfs partition) and have it install through fonty python?

Of course, this is only if you want to install a few, or a few at a time.

---

### Post by mrboojive on 2010-09-02
> **Miyavix3 said:**
> Can't you just double click the font files (from your ntfs partition) and have it install through fonty python?

Of course, this is only if you want to install a few, or a few at a time.

You also need to have Fonty Python installed. If you do that with the Gnome Font Viewer, all it's going to do is just copy it to your .fonts directory anyways.

---

