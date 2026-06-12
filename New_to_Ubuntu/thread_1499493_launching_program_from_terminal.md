---
title: "launching program from terminal"
date: 2010-06-02
forum: New to Ubuntu
---

### Post by trailofdead on 2010-06-02
I was trying to install calibre, but I'm using Jaunty and the newest version that works without GLIBC 2.10 is 0.6.29.  
Following the instructions at [http://calibre-ebook.com/download_linux](http://calibre-ebook.com/download_linux), i downloaded and extracted the tar.bz2 into /opt/calibre

How do I launch the script from any path in the terminal?  i.e. i dont want to have to go into the /opt/calibre path and type ./calibre, i just want to type "calibre" from the terminal have it launch the scrpt.  

Thanks

---

### Post by BoneKracker on 2010-06-02
There are several ways you can accomplish that.

_1. One way_ is to create an alias in the shell, so that when you type "calibre", the shell automatically expands that to the full name of the executable, including the path.  You didn't mention it, so let's pretend that it's "/opt/calibre/bin/calibre".  (Please keep in mind throughout all the examples in this post that you would substitute the correct path and filename where I have used "/opt/calibre/bin/calibre".) What you would do is edit your shell startup file to establish the alias when you login.  The best place to do this at the bottom of your ~/.bashrc file (this is an example; substitute _your_ information):
```
alias calibre="/opt/calibre/bin/calibre"
```
If you want other users of your computer to also be able to do this, then you could make this same addition to the system-wide bash startup file located in /etc (it might be "bashrc", but I don't know since I don't use Ubuntu), or you could add this to /etc/skel/.bashrc in which case it would automatically be in the ~/.bashrc files of new users.


_2. A second way_ is to modify your PATH variable.  A user's PATH variable contains a list of directories on the system that will automatically be searched for an executable when only the basename is given.  If you add "/opt/calibre/bin" to your PATH, then you would be able to simply type "calibre" and it would find it there and execute it.  You do this also in a shell startup file; the best place to do this is in your ~/.bash_profile file (this is an example; substitute _your_ information):```

export PATH="/opt/calibre/bin:${PATH}"
```
If you choose this second method and you want other users of your computer to also be able to do this, then you could make this same addition to the system-wide bash startup file located in /etc (it might be "bash_profile" or simply "profile", but I don't know since I don't use Ubuntu), or you could add this to /etc/skel/.bash_profile in which case it would automatically be in the ~/.bashrc files of new users.


_3. A third way_ to do this is create a symbolic link (symlink) to the calibre executable, locate in another directory that is already in your PATH.  You can see what your PATH variable currently contains like this:
```
echo $PATH
```
Let's say, for the sake of argument that "/usr/local/bin" is already in your PATH.  That's a good place for user-installed executables to be.  You could create a symlink there, pointing to the calibre executable like so (this is an example; substitute _your_ information):```

ln -s /opt/calibre/bin/calibre /usr/local/bin/calibre
```

_4. A fourth way_ to do this is applicable only if you use a graphical environment (e.g. Gnome, KDE, or a window manager).  You would create a menu item that starts the program when you select it.  Exactly how you do this depends upon the graphical environment you are using and whether calibre is a graphical program or runs in a terminal.  You can combine this with any of the other three methods above (so you only have to type the shorter command into the menu item or icon, and so you can have the option of executing the command manually.

---

### Post by trailofdead on 2010-06-02
> **BoneKracker said:**
> There are several ways you can accomplish that.



Very informative reply, thank you sir.

Is there a preferred method or "proper" way?  I used a symlink.

---

### Post by BoneKracker on 2010-06-02
> **trailofdead said:**
> Very informative reply, thank you sir.

Is there a preferred method or "proper" way?  I used a symlink.

I think that or modifying your PATH are both good ways.

Trivial but possibly interesting:

You want to be careful not to pollute your system with dead symlinks (e.g., you remove this program and forget to remove the symlink).  You an create a little "find" script to search for and clean dead symlinks up though, and theres a nice little utility called (strangely enough) "symlinks", which will do that and more.  I use it in a weekly cron job, but I don't want to go so far as to recommend it to an Ubuntu user, because I don't know what kind of unorthodox symlink practices the Ubuntu packagers might have engaged in (some developers like to create dead symlinks as lockfiles).

The downside to creating a huge PATH variable is that it gets searched every time you run an executable.  While we're talking fractions of a second, simple is better than complex.  So if you're anal, you might prune your PATH variable and also put them order of frequency of use (or time-sensitivity).

---

