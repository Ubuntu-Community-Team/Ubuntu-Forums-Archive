---
title: "Gimp not starting"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by strangelymade on 2009-01-07
Last night I installed security updates for Umbuntu and afterwards had problems starting up Amarock. Solved that problem by re-installing it, how ever, today I tried to open up GIMP and it wouldn't open, I got the message "Starting GIMP" but then nothing, I tried to re-install it but that hasn't solved the problem.

I am using Unbuntu 8.4, anything else need to know to help me sort this out?

BTW I am Really not computer savvy so please try and explain stuff in a way an idiot can understand.

---

### Post by fooman on 2009-01-07
have you tried to start it via the terminal?  ....that way if there is an error,  it will show in the output of the terminal.

just open a terminal window (applications > accessories > terminal),  and type:
```
gimp
```

please post back with any errors that pop up after you run the command (just copy/paste the output).

---

### Post by strangelymade on 2009-01-07
Thanks for the reply, I used Terminal and managed to open Gimp that way, however I did get this message in Terminal

> strangelymade@strangelymade-desktop:~$ gimp
/usr/local/lib/gimp/2.0/plug-ins/print: error while loading shared libraries: libgimpprint.so.1: cannot open shared object file: No such file or directory

(gimp:6580): LibGimpBase-WARNING **: gimp: wire_read(): error
strangelymade@strangelymade-desktop:~$ 
strangelymade@strangelymade-desktop:~$ 

Just found out, that when I close Terminal then Gimp closes as well. Does this mean something serious is wrong?

---

### Post by donkyhotay on 2009-01-07
If you close terminal any programs you launched with it will close automatically as well, thats normal. With the error message it looks like you have a dependency problem, most likely libgimp wasn't updated when gimp was updated. Did you recieve any message stating something like "some packages could not be downloaded..." during the update? If you ever get that you always want to hit 'no' and then try the update again. It means that only some of the updates were downloaded and sometimes 'some of the updates' means 'only half the program gets updated' which breaks things. I would try updating your system again to make certain *everything* is updated correctly.

//edit: if I remember right the specific error message I'm thinking of is "some packages could not be downloaded, do you want to continue anyways?"

---

### Post by fooman on 2009-01-07
here are a few threads with similar errors...if you have "gimpshop" installed....try uninstalling that first,  otherwise check these:

[http://ubuntuforums.org/showthread.php?t=825345](http://ubuntuforums.org/showthread.php?t=825345)

[http://ubuntuforums.org/showthread.php?t=978501](http://ubuntuforums.org/showthread.php?t=978501)

hope something there helps.

---

### Post by unutbu on 2009-01-07
When you run gimp from the terminal, notice that the output mentions> 
/usr/local/lib/gimp/2.0/plug-ins/print

This implies you have gimp installed in /usr/local/lib.

The standard Ubuntu gimp package installs itself in /usr/lib and /usr/bin.

If you are not trying to run a special version of gimp and would be happy with the regular Ubuntu version, then the first thing to do is remove all vestiges of the /usr/local installation of gimp from your system, turn off any third-party software repositories, and then reinstall:
```

sudo apt-get install gimp
```

If you run into any trouble, please post the output of this command:
```

dpkg --get-selections | awk '/gimp/{print $1}' | xargs apt-cache policy
```

---

### Post by strangelymade on 2009-01-07
Many thanks for the help guys, ended up getting rid of GIMPShop and now GIMP works fine.

Dunno why, but at least I can use it now.

---

### Post by donkyhotay on 2009-01-08
If it works don't forget to mark the thread as solved.

---

