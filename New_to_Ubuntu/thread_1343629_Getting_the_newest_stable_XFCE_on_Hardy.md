---
title: "Getting the newest stable XFCE on Hardy"
date: 2009-12-02
forum: New to Ubuntu
---

### Post by longtom on 2009-12-02
Hi,

I'd like to test the newest stable XFCE on Hardy in a virtual machine.What would be the easiest way to do so?

Any suggestions welcome.

---

### Post by byStanderone on 2009-12-02
...perhaps you can find something from here:

[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=xfce](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=xfce)

---

### Post by longtom on 2009-12-02
> **byStanderone said:**
> ...perhaps you can find something from here:

[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=xfce](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=xfce)

Thanks.

But for Hardy they still have only 4.4.2.  I am hoping for something closer to 4.6.1...  

A PPA would be ideal, of course....

---

### Post by jbrown96 on 2009-12-02
I recommend Virtualbox. It's got a really good interface, and installs much easier. If you just want to try XFCE 4.6, then just use the open source edition. ```
sudo apt-get install virtualbox-ose
``` After that installs, then run ```
sudo usermod -aG vboxusers $USER
``` then reboot. You can now open virtualbox from the Applications menu.

[Here]("http://blog.xfce.org/2009/03/04/") are some instructions on how to install XFCE 4.6 on Hardy.


Edit: I saw the previous post. This page only mentions 4.6 in the article, but the repository has probably been updated since.

Just a future tip. When you want newer editions of programs, you usually need to add a PPA. Try searching the version of ubuntu you use, ppa, and the program name.

---

### Post by longtom on 2009-12-02
Thank you, jbrown96.

Been there, done that.  This person doesn't exist any more and so doesn't his PPA.

I was hoping somebody found something I missed.

Yes, I am using VirtualBox and it works like a charm....

---

### Post by Julita on 2009-12-02
longtom, when I used Hardy Heron, I have compiled new Xfce version from the source. Naturally, it works a lot better. In order to do that, go to [www.xfce.org](www.xfce.org) and download the source.

---

### Post by longtom on 2009-12-02
> **Julita said:**
> longtom, when I used Hardy Heron, I have compiled new Xfce version from the source. Naturally, it works a lot better. In order to do that, go to [www.xfce.org](www.xfce.org) and download the source.

Yes...I was thinking of that.  However, I won't be able to do that just like that.

You know of any guidelines I could follow?

---

### Post by Julita on 2009-12-02
Of course! Before compiling, make sure that you have build-essential package installed.
Go to [http://sourceforge.net/projects/xfce/files/xfce-4.6/4.6.1/xfce-4.6.1-src.tar.bz2/download](http://sourceforge.net/projects/xfce/files/xfce-4.6/4.6.1/xfce-4.6.1-src.tar.bz2/download) Save the file, unpack until you have all necessary directories. Open terminal, type
```
cd /path/to/directory
./configure
``` During the configuration, you will see in the end the error (if there are any) which packages you have to install additionally. After you install it, run ./configure again and again, until you have all the required development files. When you see
```
creating.config
``` or something-like-that string, wait until it ends, and then you can type
```
make
``` In total, it can take several hours to compile. I have a very slow machine, though. Then, when it is finished, type
```
sudo make install
``` When you are done with all the directories, you can reboot.

---

### Post by longtom on 2009-12-02
Thank you Julita, I'll try that.

---

### Post by jbrown96 on 2009-12-02
Be sure not to delete these the source folders or else there won't be a way to uninstall it.

---

