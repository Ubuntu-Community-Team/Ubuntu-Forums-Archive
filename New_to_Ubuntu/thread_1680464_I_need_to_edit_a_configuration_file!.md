---
title: "I need to edit a configuration file!?"
date: 2011-02-02
forum: New to Ubuntu
---

### Post by waltherg on 2011-02-02
I need to edit a configuration file to fix a synaptics bug. It is seriously one line that I need to put into the file. I just cant figure out how to edit it! I tried "gedit" in terminal... but once I edit it it says it can't find the file. If i find it manually in the file system, there is no way for me  to edit the file. Please help, I really need a step by step!

Greg

---

### Post by rcayea on 2011-02-02
What file?

And, try sudo gedit /path/to/document.txt

---

### Post by xoomer.ap on 2011-02-02
And, by the way, read this - [http://en.wikipedia.org/wiki/Sudo](http://en.wikipedia.org/wiki/Sudo) ;)

---

### Post by JRV on 2011-02-02
Open a terminal.

Type: sudo nautilus

(This will bring up the file manager with root access, be careful.)

Navigate to your file, and double click it.

---

### Post by mcduck on 2011-02-02
by the way, use *gksudo*, not *sudo*.

Sudo should never be used for anything else than command-line applications. For any graphical tool you should always use gksudo  instead.

Sudo is made for CLI tools only, and doesn't load the user's environment correctly for GUI applications. While some programs may work without problems, launching others with sudo can have really nasty effects, like changing the ownership of your user's configuration files or home directory to root, preventing you from logging in or changing some (or any) settings any more.

Since it's pretty much impossible to find out & remember what graphical programs work fine with sudo and what don't, it's definitely a good idea to simply learn the habit of always using gksudo with GUI apps and sudo with CLI apps.

(there's similar kind of issue with using "sudo su" or "sudo -s" to open a root session in terminal, if you want to do that you should use "sudo -i" instead.)

---

### Post by sisco311 on 2011-02-02
> **waltherg said:**
> I need to edit a configuration file to fix a synaptics bug. It is seriously one line that I need to put into the file. I just cant figure out how to edit it! I tried "gedit" in terminal... but once I edit it it says it can't find the file. If i find it manually in the file system, there is no way for me  to edit the file. Please help, I really need a step by step!

Greg

Hi,

First of all check out: [uhelp]community/RootSudo[/uhelp].

You have to edit the file as the super user: root.

If you don't want to mess with the terminal, then open the Software Center and install the package *nautilus-gksu*. This package provides an *Open as administrator* right click menu item in the file manager. After installing it you have to log out and log back in. Then simply right click on the file and select *Open as administrator*.

Another method is to open your favorite text editor as root. The default GUI one is gedit. The command to run a GUI application as root is gksudo. So, you can press Alt+F2 or open a terminal and run:
```
gksudo gedit
```
then simply drag the file in the text editor or use the File-> Open... menu to open it.

If you know the exact path to the file, you can specify it in the CLI. For example:
```
gksudo gedit /etc/fstab
```
will open the /etc/fsatab file.

You can do the same thing with a CLI text editor. IMHO, nano is the easiest to use. For CLI apps you have to use sudo:
```
sudo nano /path/to/file
```
To save the file and exit press: Ctrl+x, y, then Enter.

---

### Post by waltherg on 2011-02-02
Thank you everyone. I didn't think this would be solved in 45 minutes... I had to edit 50-synaptics.conf to add [Option "ClickFinger3" "1"] to prevent left-click from mistakenly triggering a center-click. As you can imagine, this is incredibly annoying when using tabs in a web-browser. (It closes the tab you click on approximately 80% of the time). Hopefully adding that fixes everything. There's a bug thing already submitted for it.

Thanks again!

Greg W

---

### Post by JRV on 2011-02-02
> **mcduck said:**
> by the way, use *gksudo*, not *sudo*.

Sudo should never be used for anything else than command-line applications. For any graphical tool you should always use gksudo  instead.

Sudo is made for CLI tools only, and doesn't load the user's environment correctly for GUI applications. While some programs may work without problems, launching others with sudo can have really nasty effects, like changing the ownership of your user's configuration files or home directory to root, preventing you from logging in or changing some (or any) settings any more.

Since it's pretty much impossible to find out & remember what graphical programs work fine with sudo and what don't, it's definitely a good idea to simply learn the habit of always using gksudo with GUI apps and sudo with CLI apps.

(there's similar kind of issue with using "sudo su" or "sudo -s" to open a root session in terminal, if you want to do that you should use "sudo -i" instead.)

Thanks for pointing this out.
I was not aware of this.

---

