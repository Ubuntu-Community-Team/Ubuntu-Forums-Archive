---
title: "Can't open .deb file"
date: 2010-08-09
forum: New to Ubuntu
---

### Post by gandalf2000 on 2010-08-09
Trying to install Ubuntu Control Center but when I click the Gdebi installer I get the following message:-
/tmp/ucc_051_i386-6.deb could not be opened, because the associated helper application does not exist. Change the association in your preferences

What do I do?

---

### Post by themusicalduck on 2010-08-09
First off it might be a good idea to copy it to your Desktop if it isn't already (since the error says it's in /tmp/)

Next, right click on the file, go to Properties and the Open With tab. Make sure that GDebi Package Installer is selected.

(I'm assuming you are on Ubuntu and not Kubuntu or something as it might be different otherwise)

---

### Post by jtarin on 2010-08-09
Make your way to the directory containinng the file in the terminal. To install a .deb file use the command:

    ```
sudo dpkg -i filename.deb
```

---

### Post by ajgreeny on 2010-08-09
Just out of interest, how different is the UCC from the gnome control centre, which I always enable in my menu after installing the OS?

Not necessary, I know, but useful.

---

### Post by gandalf2000 on 2010-08-12
I have tried all of the above to no avail.  Gdebi is already marked as the helper application and I know that that is installed.  The second suggestion looked promising but threw up a list of unsatisfied dependencies one of which was font-manager that also has the same problem.  When I tried to us synaptic to install the dependencies synaptic didn't get past the first screen before graying out.  At that point I decided to reinstall the system as I have been having other problems as well.  Once I have the system back to the way I want I'll have another run at it.  Keep you informed.

---

### Post by Zeike on 2010-08-12
This has happened to me when I've downloaded a file in firefox (and chose 'open' rather than 'save'), and then subsequently closed firefox.

When you choose 'open' when downloading a file firefox stores it in the /tmp directory.  But firefox's temp files are deleted when you close firefox.

---

### Post by Frogs Hair on 2010-08-12
Read this post : [http://www.webupd8.org/2010/06/ubuntu-control-center-brings-simplicity.html](http://www.webupd8.org/2010/06/ubuntu-control-center-brings-simplicity.html)  I like the UCC , it has  dependent programs that are listed in the post.

Edit: I had to install Deja Dup and System Benchmark and Profiler . The Font manager came as deb per the Web Upd8 instructions.

---

