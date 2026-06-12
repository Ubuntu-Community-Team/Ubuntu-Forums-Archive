---
title: "Missing files on a gnome software install"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by Lostin60's on 2009-02-02
I am attempting to install gnome-color-chooser-0.2.4. I downloaded it as a tar.gz file. I found a nice how-to in Ubuntu Documentation. Since I am trying to learn as much as I can I figured this would be a great learning experience.
This went off without a hitch
```
 sudo apt-get install build-essential checkinstall
```
This almost did.
```
daniel@mypos:~$ sudo apt-get install cvs subversion  git-core hg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package hg
```
From what little I know, I think hg helps in file downloads, or keeps up with files that may have been moved in the repositories. But I decided to continue in case it wasn't necessary for my install.

> You should then build a common directory for yourself where you'll be building these packages. We recommend creating /usr/local/src, but really you can put it anywhere you want. Make sure this directory is writable by your primary user account I took ownership and permissions of this folder. Nothing recursive, just the one directory.
I moved my package into the directory I just made and ran
```
tar xzvf gnome-color-chooser-0.2.4.tar.gz
```
I also installed auto-apt, but for the experience, I am trying to do all this manually. 
```
daniel@mypos:/usr/local/src/gnome-color-chooser-0.2.4$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for DEPS... configure: error: Package requirements (gtkmm-2.4 >= 2.8.0 libglademm-2.4 >= 2.6.0 libgnome-2.0 >= 2.16.0  libgnomeui-2.0 >= 2.14.0 libxml-2.0 >= 2.6.0 ) were not met:

No package 'gtkmm-2.4' found
No package 'libglademm-2.4' found
No package 'libgnome-2.0' found
No package 'libgnomeui-2.0' found
No package 'libxml-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables DEPS_CFLAGS
and DEPS_LIBS to avoid the need to call pkg-config.

```
so I ran
```
apt-file search gtkmm-2.4
```
and the return ran off the page, but this is an example.
```
libgtkmm-2.4-doc: /usr/share/doc/libgtkmm-2.4-doc/docs/reference/html/structAtk_1_1AttributeTraits-members.html
libgtkmm-2.4-doc: /usr/share/doc/libgtkmm-2.4-doc/docs/reference/html/structAtk_1_1AttributeTraits.html
libgtkmm-2.4-doc: /usr/share/doc/libgtkmm-2.4-doc/docs/reference/html/structGtk_1_1Box__Helpers_1_1EndElem-members.html
libgtkmm-2.4-doc: /usr/share/doc/libgtkmm-2.4-doc/docs/reference/html/structGtk_1_1Box__Helpers_1_1EndElem.html
libgtkmm-2.4-doc: /usr/share/doc/libgtkmm-2.4-doc/docs/reference/html/structGtk_1_1Box__Helpers_1_1EndElem__inherit__graph.png
libgtkmm-2.4-doc: /usr/share/doc/libgtkmm-2.4-doc/docs/reference/html/structGtk_1_1BuiltinStockID-members.html
libgtkmm-2.4-doc: /usr/share/doc/libgtkmm-2.4-doc/docs/reference/html/structGtk_1_1BuiltinStockID.html
libgtkmm-2.4-doc: /usr/share/doc/libgtkmm-2.4-doc/docs/reference/html/structGtk_1_1Notebook__Helpers_1_1MenuElem-members.html
libgtkmm-2.4-doc: /usr/share/doc/libgtkmm-2.4-doc/docs/reference/html/structGtk_1_1Notebook__Helpers_1_1MenuElem.html
libgtkmm-2.4-doc: /usr/share/doc/libgtkmm-2.4-doc/docs/reference/html/structGtk_1_1Notebook__Helpers_1_1MenuElem__inherit__graph.png
libgtkmm-2.4-doc: /usr/share/doc/libgtkmm-2.4-doc/docs/reference/html/structGtk_1_1Notebook__Helpers_1_1TabElem-members.html
libgtkmm-2.4-doc: /usr/share/doc/libgtkmm-2.4-doc/docs/reference/html/structGtk_1_1Notebook__Helpers_1_1TabElem.html
libgtkmm-2.4-doc: /usr/share/doc/libgtkmm-2.4-doc/docs/reference/html/structGtk_1_1Notebook__Helpers_1_1TabElem__inherit__graph.png
libgtkmm-2.4-doc: /usr/share/doc/libgtkmm-2.4-doc/docs/reference/html/style_8h.html
libgtkmm-2.4-doc: /usr/share/doc/libgtkmm-2.4-doc/docs/reference/html/table1.png
libgtkmm-2.4-doc: /usr/share/doc/libgtkmm-2.4-doc/docs/reference/html/tabs.css
libgtkmm-2.4-doc: /usr/share/doc/libgtkmm-2.4-doc/docs/reference/html/targetentry_8h.html
libgtkmm-2.4-doc: /usr/share/doc/libgtkmm-2.4-doc/docs/reference/html/targetlist_8h.html

```
The rest of the files gave roughly the same return, except for libxml, which returned
```
libxml2-dev: /usr/lib/pkgconfig/libxml-2.0.pc
lsb-build-desktop3: /usr/lib/lsb3/pkgconfig/libxml-2.0.pc
valac: /usr/share/vala/vapi/libxml-2.0.vapi

```
So I know the files are there, but "./configure" can't find them. Any ideas on  where to go from here? Could I use a command like
```
apt-file search install filename
```
I don't think "apt-get" will help, since all the files were found on my hdd.
Any and all help will be appreciated.
[COLOR="White"]aa[/COLOR]

---

### Post by oldos2er on 2009-02-02
Usually when you see a dependency error e.g. "No package 'gtkmm-2.4' found," it's looking for the -dev package of the same name.

---

### Post by Lostin60's on 2009-02-02
> **oldos2er said:**
> Usually when you see a dependency error e.g. "No package 'gtkmm-2.4' found," it's looking for the -dev package of the same name.

Maybe I am misunderstanding something.If this
```
daniel@mypos:/usr/local/src/gnome-color-chooser-0.2.4$ ./configure

```
returned this
```
No package 'libxml-2.0' found

```                                                 that probably means it was looking for the -dev file, but this
```
apt-file search libxml-2.0
```
returned this
```
libxml2-dev: /usr/lib/pkgconfig/libxml-2.0.pc
lsb-build-desktop3: /usr/lib/lsb3/pkgconfig/libxml-2.0.pc
valac: /usr/share/vala/vapi/libxml-2.0.vapi

```
doesn't that mean the -dev file was there to find.
This is not meant to argue against what you said. I am just trying to understand. Isn't libxml2-dev the -dev file? 
The how-to said, in reference to the "./configure" that
> But right above that it will list a filename that it cannot find (often a filename ending in [COLOR="Red"]".pc"[/COLOR], for instance)
But there was no file extention indicated in the "./configure" output. But the "apt-file search" had this
"libxml2-dev: /usr/lib/pkgconfig/libxml-2.0.pc". So if I use
```
sudo apt-get install requiredpackage
```
do I use just "/usr/lib/pkgconfig/libxml-2.0.pc"  for requiredpackage or do I use "libxml2-dev: /usr/lib/pkgconfig/libxml-2.0." Or will that even work? I am totally new to all this. Some things I am getting a pretty good handle on, but lots of things still stump me. If you have any comments, they will be greatly appreciated, and thank you for your previous post.

While trying to figure this all out, I found this.
> This file contains any messages produced by compilers while
running configure, to aid debugging if configure makes a mistake.

It was created by GNOME Color Chooser configure 0.2.4, which was
generated by GNU Autoconf 2.61.  Invocation command line was

  $ /home/daniel/.wine/dosdevices/z:/usr/local/src/gnome-color-chooser-0.2.4/configure
Why would wine be involved? I haven't even configured wine yet. And the pkg I am installing isn't an .exe file.
[COLOR="White"]aa[/COLOR]

---

### Post by oldos2er on 2009-02-04
" /home/daniel/.wine/dosdevices/z:/usr/local/src/gnome-color-chooser-0.2.4/configure" looks like you untarred that archive inside your Wine directory.

 I usually use Synaptic to search for dependencies. Searching on "libxml" shows, among others, a package called "libxml2-dev," which contains the *.h files (as well as the *.pc file) needed to compile gnome-color-chooser. 

 When you use the apt-get command, all you need to give it is the name of the package, "sudo apt-get install requiredpackage" not "sudo apt-get install /some/path/requiredpackage". And if you are having trouble compiling, run "sudo apt-get gnome-color-chooser"

---

### Post by Lostin60's on 2009-02-04
> **oldos2er said:**
> " /home/daniel/.wine/dosdevices/z:/usr/local/src/gnome-color-chooser-0.2.4/configure" looks like you untarred that archive inside your Wine directory.

 I usually use Synaptic to search for dependencies. Searching on "libxml" shows, among others, a package called "libxml2-dev," which contains the *.h files (as well as the *.pc file) needed to compile gnome-color-chooser. 

 When you use the apt-get command, all you need to give it is the name of the package, "sudo apt-get install requiredpackage" not "sudo apt-get install /some/path/requiredpackage". And if you are having trouble compiling, run "sudo apt-get gnome-color-chooser"



I saw color chooser on a post in these forums. Since the post had a link to the softwares website, I assumed it wasn't in the repositories. I see I was wrong. 
I created a folder named src in /usr/local and untarred the archive in there, which is why the wine thing confused me. It still does.
> Searching on "libxml" shows, among others, a package called "libxml2-dev,"

Yes, I saw that, and that was what I was trying to get.

> But there was no file extention indicated in the "./configure" output. But the "apt-file search" had this
"libxml2-dev: /usr/lib/pkgconfig/libxml-2.0.pc". So if I use
```
[COLOR="Red"]sudo apt-get[/COLOR] install requiredpackage
```

The above was a mistake. I meant to ask if an "aptitude", not an "apt-get" would work. I knew what I wanted was on my comp, so "apt-get" wouldn't work.
Anyway, since I now know it is in the repositories, install is no issue. I still gotta figure out the wine thing. Thanks for your input, it was helpful.

> This file contains any messages produced by compilers while
running configure, to aid debugging if configure makes a mistake.

It was created by GNOME Color Chooser configure 0.2.4, which was
generated by GNU Autoconf 2.61. Invocation command line was

$ [COLOR="Red"]/home/daniel/.wine/dosdevices/z[/COLOR]:/usr/local/src/gnome-color-chooser-0.2.4/configure 
This directory/path doesn't exist, nor is there a .wine folder. At least I can't find them with "file-browser"
[COLOR="White"]aa[/COLOR]

---

### Post by oldos2er on 2009-02-05
"The above was a mistake. I meant to ask if an "aptitude", not an "apt-get" would work. I knew what I wanted was on my comp, so "apt-get" wouldn't work."

 No, aptitude and apt-get work similarly.

---

