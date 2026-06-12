---
title: "Problems with wireless on my Compaq C700"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by brianslater on 2008-05-02
Alright so I just installed a fresh install of hardy heron on my C700 and I have no idea how to get my wireless working. I have been reading on the forums, and I cant seem to be able to fix it. besides that everything else is working, any help would be greatly appractiated, I am ready to drop windows permanetly

---

### Post by MattBD on 2008-05-02
If wireless doesn't work, then you can use ndiswrapper to enable you to install the Windows wireless drivers. Although it's a command-line thing, there's a graphical front end for it called ndisgtk which should make it easier. Just enter the following to install it:
```
sudo apt-get install ndisgtk
```
And it should install ndisgtk and ndiswrapper for you.

You didn't mention whether it the device was detected or not, if it was you'll need to blacklist the existing driver if it doesn't work.

---

### Post by agim on 2008-05-02
I have a similar computer. Do you have your windows drivers for your wireless card?

---

### Post by brianslater on 2008-05-02
Ok, so I download the UI for ndiswrapper, and install it and everything goes well, I go to compaq.com download the exe and install it to a directory on my windows pc, then use my thumbdrive to move the file to ubuntu, and now I am stuck because it says invalid driver any idea's anyone? the they doesnt even recongize a wifi adapter exist, I think.

any idea's?

---

### Post by agim on 2008-05-02
This is the how-to that I have used. Its not as easy as the gui, but you just cut and paste the commands, so its not so much hard as it is tedious.
Anyway, here is the link.

There is an extra hoop at the end to jump through for gutsy and this post includes it.

[http://ubuntuforums.org/showthread.php?t=766560&highlight=ndiswrapper+hardy](http://ubuntuforums.org/showthread.php?t=766560&highlight=ndiswrapper+hardy)

---

