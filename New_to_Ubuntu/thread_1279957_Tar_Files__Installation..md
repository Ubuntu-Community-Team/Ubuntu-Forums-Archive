---
title: "Tar Files_ Installation."
date: 2009-10-01
forum: New to Ubuntu
---

### Post by Narendra on 2009-10-01
Hello,

Please advise how do I install .tar.gz and .tar.bz2 files,xplain them with an example.
I am a newbe  for this, aged 60 and disabled,been using windows but have switched to ubuntu (9-04).
And I have searched the sites but can not get/find proper workouts.

Thank you.
Narendra

---

### Post by Bachstelze on 2009-10-01
Tar files are archives, just like ZIP or RAR files in Windows, so they can contain anything. If you say you want to "install" them, they probably contain some application. Most likely, that application is available in the repositories, which will make it easier to install..

[http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)

---

### Post by arochester on 2009-10-01
Also see "How to install ANYTHING in Ubuntu!" at [http://amitech.50webs.com/installing/index.php.html](http://amitech.50webs.com/installing/index.php.html)

---

### Post by letank on 2009-10-01
I unsdertand your pain..... even those links do not even get into the details... of what and how.... I will try to find a good link... but I am currently trying to duplicate my HD, so my references are burried...

---

### Post by pedro3005 on 2009-10-01
If an application you downloaded came in .tar.gz or .tar.bz2, it most likely will be one of two:
. A pre-compiled application (Easy!)
. A source for compiling (A bit hard).

If the first, you will probably just run a file inside the extracted directory. See the README file.
If the second, it could vary, but generally this is how it is done: Let's imagine the application A is inside directory B. You'd open a terminal and type:
```

cd /path/to/B
./configure
make
sudo make install

```
But please, check the README file. ALWAYS CHECK THE README FILE! IT'S RIGHT IN THE NAME! READ - ME! :D

---

### Post by arochester on 2009-10-01
Hi Narendra

When you are also posting to the Linux Format forum about .tar for Kompozer I must say again that it is available from Repository and does not need to be unpacked or compiled.

Connect to the Internet, open a Terminal and issue the command: > sudo apt-get install kompozer Job done!

---

### Post by Narendra on 2009-10-02
[COLOR="DarkSlateBlue"][FONT="Tahoma"]Thank you very much for your reply, Arochester.
We meet again!

I have downloaded like you have instructed from the terminal but it crashes.

What I have done, downloaded the new version in the Home Folder, have extracted it, and click on the 'Kompozer-bin ' icon and it works that way.

I'll wait till the final version comes out.

Regards.[/FONT][/COLOR]

---

