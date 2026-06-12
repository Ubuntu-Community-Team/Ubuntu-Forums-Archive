---
title: "Quiet Songbird"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by nnjond on 2009-04-16
Hi,

I've downloaded a copy of Songbird to my home folder; a directory of files.
But as i've only used the add/remove app to install programes in the past, I don't know how to install this one. Are there any instructions any where?


Thanks

---

### Post by James_Lochhead on 2009-04-16
This is a little harder. It requires you to execute the songbird script in the directory. You can do this (I believe) in Ubuntu just by double clicking the "songbird" file and selecting run (not run in terminal).

---

### Post by achase79 on 2009-04-16
You should be able to find a .deb file for songbird to download.  Then you would just double click and install.

---

### Post by achase79 on 2009-04-16
The deb is available [HERE]("https://help.ubuntu.com/community/Songbird")

---

### Post by James_Lochhead on 2009-04-16
Obviously leaving it in your download folder leaves a lot to be desired. So I recommend you move it to another directory (such as /usr/lib) and create a launcher for it. Open a terminal and do the following:

```

cd path/to/your/download/directory/
sudo chown -R root:root Songbird/
sudo mv Songbird/ /usr/lib/

```

Now you need a launcher on your desktop. Create one and type this in the command:

```

bash /usr/lib/Songbird/songbird

```

There you go. The launcher will launch Songbird.

---

### Post by James_Lochhead on 2009-04-16
Ah okay. If there is a deb available just use that. It is much easier.

---

### Post by nnjond on 2009-04-16
Thanks Have successfully installed 1.1.1

---

### Post by zero_koop on 2009-05-10
> **James_Lochhead said:**
> 
Now you need a launcher on your desktop. Create one and type this in the command:

```

bash /usr/lib/Songbird/songbird

```

There you go. The launcher will launch Songbird.

Thanks for the info about creating the launcher.  I've been searching all evening and no one has mentioned that "bash" part before in order to get the command to work.  Thanks.

---

### Post by BIGtrouble77 on 2009-05-10
Just a personal preference of mine... If you are installing a precompiled binary (like song bird), I like to copy it to /opt.  That way it's very easy for me to see what non-repo apps I have installed. Putting it in /usr/lib is going to mix it with many other apps.

Btw, songbird kicks ***.

-bt

---

