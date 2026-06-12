---
title: "trying to install a metframe presentation client"
date: 2009-08-10
forum: New to Ubuntu
---

### Post by Nick Wynn on 2009-08-10
Hi, very new to ubuntu 904 (endevouring to shake the Gates hold on me) and have moderate computer knowledge.  Learning & stumbling as I go, would love someone's help.  

In order to access work computer from home I have to install a "Metaframe Presentation Client for Linux".  I download the client as a zip, then extract .... and then after that lose my way.  I am looking for a simple 'install' option as I would have in windows.  

I get to either 'run' or 'run in terminal'.  Run won't work, the 'terminal' option loses me. 

Am I trying to be too tricky....? is it:confused: beyond me...? can anyon help.  thx in advance
nick

---

### Post by arky on 2009-08-10
Perhaps you should read the documentation ([http://support.citrix.com/article/CTX120175](http://support.citrix.com/article/CTX120175)) or get support from the citrix people.

---

### Post by zarthon on 2009-08-10
You need to expand the archive and read any instructions inside like a READ ME file to know how to proceed.
It may be possible to do what you need to do from the gnome desktop and you can definitely use the graphic synaptic package manager to add packages instead of my instructions.

What I suggest is that you use the command line. I shiver to mention that it's also very useful in windows. 

Launch a terminal window
Click on Applications menu -> accessories -> Terminal.
In the terminal window install zip tools. You may get a message that they have been installed already. Sudo will give you administrative "root" privileges to execute the install. You then will go to the Desktop and unzip the file. The 'less' command will show the file in the terminal window and allow you to scroll content with the page-up and page-down keys. Press Q to Quit 'less'
```

sudo apt-get unzip zip
cd ~/Desktop
unzip metaframe-whatever.zip

```
The packager should have wrapped the contents of the zip into a folder.
Move to this folder and read the README file, or any useful .txt files.
Follow instructions in this file.

```

cd metaframe-whatever-folder
less README

```

After you get that far if you still are stuck post back.

---

### Post by Nick Wynn on 2009-08-10
wow thanks guys, will have a go - I work by trial and error so no doubt you haven't heard the end of me..... cheers.  thanks again

---

