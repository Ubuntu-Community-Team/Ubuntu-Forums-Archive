---
title: "Skype or similar program for Ubuntu 8.04 64-bit"
date: 2011-01-11
forum: New to Ubuntu
---

### Post by alemariscal on 2011-01-11
[SIZE=3]**Is it possible to install Skype for Ubuntu 8.04 64-bit?? or a similar program??? if so, can someone please explain to me how to do it...thank you!:confused:**[/SIZE]

---

### Post by squaregoldfish on 2011-01-11
You can get Skype from the Skype website.

---

### Post by sriramrangan on 2011-01-11
Yes,it is. Go to this link: [http://goo.gl/Ogj1B](http://goo.gl/Ogj1B), Then download skype. Then,go to the folder you downloaded the file to and double click on the file.

---

### Post by alemariscal on 2011-01-11
the download button takes me to the option of downloading skype for 64bit or 32bit **BUT FOR VERSION 8.10 **and i have version **8.04**

---

### Post by squaregoldfish on 2011-01-11
So it does. In that case, you can download and install the Static version (the last link in the group). This will contain Skype along with all the libraries it requires.

It looks like the package is a bzip2 file. Download it, uncompress it and move the extracted directory into /usr/local.

You'll have to make sure the skype executable is in the system path - the easiest way is to create a symbolic link in /usr/local/bin.

(Note that you'll need sudo access to do stuff in /usr/local)

HTH
Steve.

---

### Post by alemariscal on 2011-01-11
steve thank you so much, but i'm new to ubuntu so you kinda lost me where i have to make a symbolic link????

---

### Post by squaregoldfish on 2011-01-13
Symbolic links are roughly equivalent to shortcuts in Windows.

By default, Linux will only run programs in certain pre-specified directories, and your newly installed Skype won't be one of them. So, to make Skype runnable, the easiest thing to do is create a symbolic link in one of the runnable locations.

Now, you need to find out what the executable for Skype is called. It's probably just called skype. Assuming you put the Skype directory in /usr/local, we want to create the symbolic link in /usr/local/bin. To do this, change to the directory where you want the link (in this case, /usr/local/bin), and enter the command:

sudo ln -s /usr/local/<skype dir>/skype .

This creates a link to the skype executable in the current location (i.e. /usr/local/bin). Because it's a directory owned by root, you have to run sudo to get permission to create the link.

That should be it!

Steve.

---

### Post by dFlyer on 2011-01-13
Is there any reason why you don't update to a more recent version of Ubuntu??

---

