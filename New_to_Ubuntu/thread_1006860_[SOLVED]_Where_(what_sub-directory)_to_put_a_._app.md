---
title: "[SOLVED] Where (what sub-directory) to put a ./ app into"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2008-12-09
jUploadr ([http://juploadr.org/screenshots.html](http://juploadr.org/screenshots.html)) is a application (program) for sending photos to a website.

It's download is named:

jUploadr-1.1.2-linuxGTK-i386.tar.gz

and Ubuntu asks me whether I want to open it with Archive Manager, when I right click on the folder I've downloaded & saved to my Desktop.

What I don't understand is where to "install" this software. Should in go in 

/usr/bin

or

/home/mark     (mark is my username)

or where?

Is there a 'best' place to install this program?

---

### Post by ibutho on 2008-12-09
According to the [FHS]("http://www.pathname.com/fhs"), there should be no subdirectories in the various */bin directories. This means that you should not place your programs in /usr/bin. The correct place is /opt if you are installing globally or anywhere in your home directory (e.g. /home/mark/programs) if you are the only one that is going to use it.

---

### Post by spiderbatdad on 2008-12-09
did you extract the tar and read the readme? Is there a bin file? According to the FAQ, as long as java is in your path, you run the file...like any bin file...after making it executable.

---

### Post by Bölvaður on 2008-12-09
> **ibutho said:**
> The correct place is /opt if you are installing globally or anywhere in your home directory (e.g. /home/mark/programs) if you are the only one that is going to use it.

I support having it in your home directory and never running that (or any program) with super user rights (other than system critical programs).

I have some games and demos here:

/home/bolvadur/games/prey-demo/

and some others that I share with other distros

/data/games/ETQW/

I also have few programs and they should be dealt with similarly.

---

