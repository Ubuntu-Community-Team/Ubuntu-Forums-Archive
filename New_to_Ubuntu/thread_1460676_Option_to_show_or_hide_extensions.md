---
title: "Option to show or hide extensions?"
date: 2010-04-23
forum: New to Ubuntu
---

### Post by lovets on 2010-04-23
In Windows, you have the option of showing or hiding extensions. A jpeg file of one's passport photograph, for example will appear as "mugshot.jpeg" if you opt for "Show extensions" and "mugshot" if you choose "Hide extensions." Does Ubuntu offer the same choice? If so, where do I go to exercise it. If not, could one simply include the extension in the filename, or would that throw a spanner in the works?

---

### Post by mechro on 2010-04-23
Linux generally doesn't use file extensions to identify and process the file so a jpeg will be opened by your photo/picture application regardless of whether it's called **Photo.jpg**, **Photojpg**, or just **Photo**.

---

### Post by HermanAB on 2010-04-23
The file type is figured out by a program called, wait for it, drum roll... 'file'.

The 'dot three letter' idea comes from CP/M and is not really used much in Linux.

---

### Post by mcduck on 2010-04-23
While what other people have said about Linux not using extensons is true, it's not the whole truth.

Linux itself, and the command-line, generally doesn't care about extensions. Why would it, it has better ways to find out a file's type, and most of the time when you open a file from command-line you'll tell the program to use in the same command anyway.

On the other hand, the graphical desktops *do* use file name extensions. While desktop environments like Gnome do some magic number checking on files the file name extension is most of then the one that tells how a file should be handled when you click it in your file manager.

If you want to try this, just rename a .jpg image to .txt and click it, most likely Gnome will try to open it in Gedit and then complains that it can't detect the character encoding...

---

### Post by 3rdalbum on 2010-04-23
I believe for security and usability reasons you do not get the option of hiding filename extensions. They have little use on Linux, and are notorious on Windows.

On Windows, trojans tend to call themselves things like "MILEY CYRUS NUDE!!!.jpg.exe", and Windows hides the ".exe" extension and so the victims think that they're opening a simple picture file. Hence the security concern.

The only extension that the Gnome desktop hides is ".desktop", but it only hides it for files that have been explicitly approved by the user or created by Gnome itself.

---

### Post by mechro on 2010-04-23
> **mcduck said:**
> 

If you want to try this, just rename a .jpg image to .txt and click it, most likely Gnome will try to open it in Gedit and then complains that it can't detect the character encoding...

:oops: Oh, Bugger! That's just blown apart my **Photo.jpg/Photo** example. :)

---

### Post by coffeecat on 2010-04-23
> **mechro said:**
> :oops: Oh, Bugger! That's just blown apart my **Photo.jpg/Photo** example. :)

Actually, it's only half blown it apart. :p Rename Photo.jpg to Photo.txt and gedit will, indeed, try to open it. But rename it to Photo (no extension) and it will be opened by Eye-of-Gnome (or whatever default app you have set for JPEGs).

If I understand correctly what is going on, if a filename has an extension this will over-ride the magic number and Gnome will rely on the extension. But with no extension to the filename, the magic number is used. Whether that's true for KDE, I don't know, but I imagine it would be. Perhaps a Kubuntu user could chip in here.

---

### Post by mcduck on 2010-04-23
> **coffeecat said:**
> Actually, it's only half blown it apart. :p Rename Photo.jpg to Photo.txt and gedit will, indeed, try to open it. But rename it to Photo (no extension) and it will be opened by Eye-of-Gnome (or whatever default app you have set for JPEGs).

If I understand correctly what is going on, if a filename has an extension this will over-ride the magic number and Gnome will rely on the extension. But with no extension to the filename, the magic number is used. Whether that's true for KDE, I don't know, but I imagine it would be. Perhaps a Kubuntu user could chip in here.

Something like that.

Also in some cases Gnome will check both the extension and the magic number, for example a .html file that doesn't have a correct document type declaration on the first line will give you an warning about document's file name extension and actual contents not matching when you try to open the file (At least it used to, some versions ago, I haven't tried that lately so it might have changed).

---

### Post by Nocturnmidnight on 2011-02-08
The option has been in the Mac OS at least since I started using in 2004 without any problems. It is rather handy as some devices such as my DVD player requires extensions for my video files etc... I can hide the extension because for the most part I don't need them either. Yet when working with several versions of a document I can turn them on to see which file is .rtf, .pdf. or .txt. which are all set to open with Preview and without extensions all have the same preview icon. I have to give my admin password for any rogue application to do anything significant on my computer. I can see how anything on a Windows box could be considered a security risk. I can't see it being a problem on Linux or Mac. There is a need for this type of functionality in order for Linux to be user friendly to the general public. I have converted several novice users to Ubuntu. Usually, so I won't have to keep fixing their virus ridden boxes. Having to explain file extensions to some people is like pulling teeth. Having to fix the file extensions they deleted while renaming their movies so that their DVD player will load the is like having a root canal.

---

### Post by Old *ix Geek on 2011-02-08
> **Nocturnmidnight said:**
> There is a need for this type of functionality in order for Linux to be user friendly to the general public.I disagree. File extensions are a DOS thing, not UNIX.

Unlike the idiotic DOS/windows model, *nix didn't start out using extensions. A file could be named anything [as long as it consisted of allowed characters], with or without dots in its name, and with any number of characters after a dot, because the part after the dot WASN'T an extension, it was just part of the name. Like **fstab.original** or **.profile**.

UNIX, being the intelligent OS that it was/is, didn't rely on "extensions" to figure out what kind of file a file was. So why include something that's a reflection of a different operating system? It's like saying my 5-speed stick shift Toyota should come with an owner's manual for an automatic Ford. Makes no sense!

---

