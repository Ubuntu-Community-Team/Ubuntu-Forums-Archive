---
title: "Firefox 5 and PDFs in Natty"
date: 2011-07-30
forum: New to Ubuntu
---

### Post by donssword on 2011-07-30
Long time Mac user (1989). Bought my kids a couple of HP Mini 110s in the spring, slapped 2GB of RAM in them and installed Ubuntu Natty from a thumb drive. Love, love, love Ubuntu. Jealous that I don't have my own netbook with Natty to play with. 

As they are on Netbooks, I run into the typical screen size issues. A lot of these I can figure out how to get around, but I am stuck on one particular issue.

Firefox 5 is our default browser (please don't suggest I change) and Acrobat Reader is configured as our default PDF reader. The problem I want to work around is that **Acrobat Reader's print interface does not fit on Netbooks.**** I would prefer to migrate to another Ubuntu friendly PDF app, like Evince, but when I go to the Helper App configuration screen, and it asks me to select another app, I have absolutely no idea how to find/select another app.** I also do not want to ask my kids to go to the command line--we can argue all day about how cool that would be for my kids to learn how to do, but I need then to have basic functionality via the Ubuntu GUI, especially since I am usually giving them tech support from my office 30 minutes away from home.

**Where do apps live in Ubuntu? Do they all sit in one DIR like Mac OS X? Or are they hidden in the structure somewhere?**

I am familiar with viewing invisible file with periods before them because my son plays a lot of Minecraft, and we need to access his .minecraft directory for his mods, but the Firefox interface does not let me access other apps with "." before the file name (unles sI am overlooking this.

On my Mac, I point Firefox to the Preview App to render PDFs because it is smaller and faster than Acrobat.

Thanks in advance.

---

### Post by mikewhatever on 2011-07-30
What you probably need is where the executable is, for example - /usr/bin/evince. Most of the executables are in /usr/bin, and you can easily find out by running **which program-name**, for example - **which evince**.
You can also use alt+drag (drag the window while holding an alt key) to move any window beyond upper screen bounds, if needed.

---

### Post by donssword on 2011-07-30
> **mikewhatever said:**
> What you probably need is where the executable is, for example - /usr/bin/evince. Most of the executables are in /usr/bin, and you can easily find out by running **which program-name**, for example - **which evince**.
You can also use alt+drag (drag the window while holding an alt key) to move any window beyond upper screen bounds, if needed.

Super. I'll give both of those a try. Thanks!

---

### Post by walt.smith1960 on 2011-07-30
Another option is Foxit.  I didn't install it in the usual manner, just copied the files to a directory and double-click the executable.  What with Adobe Acrobat's reputation for bloat and security issues,  Evince or Foxit work for me.

---

### Post by lovinglinux on 2011-07-31
Another option is to install mozplugger plugin, so you can open the PDF files inside the browser, using Evince.

```
sudo apt-get install mozplugger
```

I prefer to use [gPDF]("https://addons.mozilla.org/en-US/firefox/addon/gpdf/") extension, which opens the files through Google Docs.

---

