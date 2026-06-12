---
title: "Problem with compiling gtoaster from source."
date: 2009-09-17
forum: New to Ubuntu
---

### Post by ankspo71 on 2009-09-17
Hi Everyone,

First, let me say that I am new to compiling anything, but I know the basics. I am having a problem trying to compile gtoaster from source. I am using the ubuntu mini cd 9.04 with a gnome 2.26.1 desktop environment. The mini cd I am referring to is here: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD) . If you are new to ubuntu don't try this unless you know your way around the terminal at least with apt-get (there is no desktop installed).

I wanted to find a application similar to kiso (without having to install any KDE dependencies), so I can modify a few ISO files. Technically I am trying to insert readme.txt files inside of them. So I came across gtoaster (Gnome Toaster) and wanted to give it a try because I like the sounds of it. gtoaster is found here at [http://gnometoaster.rulez.org/](http://gnometoaster.rulez.org/) and the exact source file I downloaded is gtoaster1.0Beta6.tgz

I made sure I had at least had [ binutils cmake dpkg-dev g++ gcc ] installed just to get the ball rolling, but then I realized I didn't have GTK+ installed after using ./configure . So I went to look for that in synaptic, but no luck. Next I tried installing [ gtk-sharp2 ] thinking it would help, but it just installed a ton of things I didn't need (like mono). So I see there is a GTK+ website at [http://www.gtk.org/](http://www.gtk.org/) But I would have to install GTK+ 2.16 GLib 2.20 and Pango 1.24 (including any of their dependencies I don't already have). 

So being that I am trying to keep this a minimal Ubuntu install, my questions are... Is there a different application to modify ISO's in the ubuntu 9.04 repos (besides kiso)? Has anybody successfully compiled gtoaster from source in Ubuntu 9.04? I see there is a git URL for GTK+ too, but I have no idea how to use them, or whether it would be compatible with Ubuntu since this seems to be a debian only kind of thing. I am including my ./configure error in the attachment.

My other thought was to find a cd burner app that would extract ISO from CD, and then later convert folders to ISOs, but I don't remember seeing those feature in Brasero or gnomebaker though. Or maybe an advanced archive manager?   

Thanks in advance,
James.

---

### Post by Bachstelze on 2009-09-17
You probably need [font=monospace]libgtk2.0-dev[/font].

(And please post your output in your message, not as an attachment.)

---

### Post by ankspo71 on 2009-09-17
Thanks Bachstelze,

First, sorry about using the attachment. I'll use the code button from now on. Second, I installed libgtk2.0-dev, rebooted, then tried to use ./configure but I ended up with the same error.

I'll post the code here for those that don't want to open any attachments for safety reasons.

```
james@ubuntu:~$ cd Desktop/gtoaster
james@ubuntu:~/Desktop/gtoaster$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal-1.4... missing
checking for working autoconf... missing
checking for working automake-1.4... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for strerror in -lcposix... no
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking for unistd.h... (cached) yes
checking linux/ucdrom.h usability... no
checking linux/ucdrom.h presence... no
checking for linux/ucdrom.h... no
checking for gcc option to accept ANSI C... none needed
checking for an ANSI C-conforming const... yes
checking for mkdir... yes
checking for rmdir... yes
checking for strstr... yes
checking for gtk-config... no
checking for GTK - version >= 1.2.0... no
*** The gtk-config script installed by GTK could not be found
*** If GTK was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GTK_CONFIG environment variable to the
*** full path to gtk-config.
configure: error: Cannot find Gtk+
james@ubuntu:~/Desktop/gtoaster$ 

```

Thanks,
James

---

### Post by Bachstelze on 2009-09-17
Oh, then you need GTK 1.2

```
sudo apt-get install libgtk1.2-dev
```

---

### Post by ankspo71 on 2009-09-17
Hi Again,

Thanks for helping with the
```
sudo apt-get install libgtk1.2-dev 
```
because that got me through the the missing GTK+ part, but then ./configure said I needed to configure a "configure --host". So I tried to figure that out, but didn't have any success because I couldn't find documentation on their sites or on google about it. I couldn't even find any usable info about gtoaster in jaunty. Up until then everything was fine though, so that wasn't the bad part.

So eventually I went and downloaded GTK+ 2.16 GLib 2.20 and Pango 1.24 (the dependencies of gtoaster) and started to compile those. Glib took forever to compile and install, and Pango wasn't so bad, but when I started compiling GTK+2.16, "make" told me there was no make file in the directory I was working from. So I looked at the instructions inside the source package again and it said there was, but there actually wasn't. I was just about ready to give up for the night, but then I noticed that I wasn't able to open my "my computer" icon. "Nautilus could not display computer: Nautilus can not handle computer locations" a popup error message said. So then I went to look in my /media directory, and it isn't even there anymore. Somehow I really messed things up this time lol. From now on I am only going to compile something if all dependencies are in Ubuntu repos, or already installed. 

There is a happy ending to this though.... because I backed up my system yesterday, and I can restore where I left off in only a few minutes. :lolflag: 

PS. I don't recommend anyone trying to install gtoaster in Ubuntu 9.04 or the downloadable dependencies for that matter.

James

---

