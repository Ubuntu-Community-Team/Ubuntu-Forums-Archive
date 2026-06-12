---
title: "Trying to Play a DVD with Movie Player"
date: 2011-05-16
forum: New to Ubuntu
---

### Post by ndex477 on 2011-05-16
This is the situation. I'm using Movie Player to try to watch a DVD but when i start the movie I get a message:  Totem cannot play this type of media(DVD) because it does not have the appropriate plugins to be able to read from the disk. 

So how do I install the plugins?

Thanks in advance for any help.

---

### Post by zealibib slaughter on 2011-05-16
You need this. [https://help.ubuntu.com/community/Medibuntu#Playing%20Encrypted%20DVDs](https://help.ubuntu.com/community/Medibuntu#Playing%20Encrypted%20DVDs)

---

### Post by norville05 on 2011-05-16
You will need to install the restricted extras for Ubuntu.  It does not naturally come with these.

Open up terminal and type 
[INDENT]sudo apt-get install ubuntu-restricted-extras

[/INDENT]This will get you the restricted extras

Now you will want to also get the dvd css

[INDENT]sudo /usr/share/doc/libdvdread4/install-css.sh
[/INDENT]If you need help with this there is an excellent guide here.

[https://help.ubuntu.com/community/RestrictedFormats/](https://help.ubuntu.com/community/RestrictedFormats/)

---

### Post by 3rdalbum on 2011-05-16
Even with the DVD decryption libraries and codecs, you might not be able to play DVDs in Movie Player. I'd recommend VLC Media Player for playing DVDs (you'll still need the decryption libraries as mentioned above).

---

### Post by ndex477 on 2011-05-19
After entering the first sudo command I got to the EULA and then I closed the screen. Was that the end of that install? I clicked on ok @ the EULA and nothing happened.

When i tried to execute the second command I got an error message.

---

### Post by wildmanne39 on 2011-05-19
> **ndex477 said:**
> After entering the first sudo command I got to the EULA and then I closed the screen. Was that the end of that install? I clicked on ok @ the EULA and nothing happened.

When i tried to execute the second command I got an error message.

Hi, no that was an agreement that you had to agree too.Move the curser to it by hitting the down arrow I think, but so all your needs are meet for mp3 play back, flash video go here and install according to which version of ubuntu you are using. Read the whole page. [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by ndex477 on 2011-05-22
Downloaded VLC and now how do i install it? it's a .tar file. Also, according to the link you listed, do i need to install Medibuntu? and the rest of those lines of instructions?
 
I have two media players installed on my system now and can't use either. This has become very frustrating. Please tell me(line by line) the instructions you used to install VLC.
 
Thanks very much.

---

### Post by andrew.46 on 2011-05-23
Use the following single command, just copy it and paste it into a terminal window:

```

sudo apt-get install vlc && \
sudo apt-get install libdvdread4 && \
sudo /usr/share/doc/libdvdread4/install-css.sh

```

and hopefully vlc will now play your dvd :).

---

### Post by wildmanne39 on 2011-05-23
> **ndex477 said:**
> Downloaded VLC and now how do i install it? it's a .tar file. Also, according to the link you listed, do i need to install Medibuntu? and the rest of those lines of instructions?
 
I have two media players installed on my system now and can't use either. This has become very frustrating. Please tell me(line by line) the instructions you used to install VLC.
 
Thanks very much.
Hi, if you use the link in post 6 it will make all your media stuff work.

---

### Post by ndex477 on 2011-05-23
O.K. Thank you all very much. Will try.

---

### Post by ndex477 on 2011-05-23
DVDs are playing now! THANK YOU VERY MUCH!

---

### Post by wildmanne39 on 2011-05-23
> **ndex477 said:**
> DVDs are playing now! THANK YOU VERY MUCH!
Hi, your welcome enjoy. would you please go to the top of the page and mark this thread solved be clicking on forum tools. Thank you so much.:)

---

