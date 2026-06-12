---
title: "gksu nautilus usr/share/..... gets an error that it's cannot be found"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by Ubunser on 2009-05-21
I need to acces a folder as a root to be able to write to a folder. What's wrong here  gksu nautilus usr/share/games/flightgear/aircraft

---

### Post by apjone on 2009-05-21
gksu nautilus usr/share/games/flightgear/aircraft
should be 
gksu nautilus /usr/share/games/flightgear/aircraft

also I unless you have set your root password use gksudo istead of gksu

---

### Post by Ubunser on 2009-05-21
I typed:

gksu nautilus /usr/share/games/flightgear/aircraft

It yielded:

Could not find "/usr/share/games/flightgear/aircraft".
Please check the spelling and try again.

As for gksudo, is this the same as sudo? I heard it's better not to use sudo. 
What else can I do?

---

### Post by apjone on 2009-05-21
open a terminal and type 
```

cd /usr/share/games/flightgear/

```
then 
```
ls 
```

And post the output

---

### Post by Ubunser on 2009-05-21
It says, no such file or directory, I still then type ls and it shows some of my folders in three rows.

---

### Post by apjone on 2009-05-21
try
```

whereis flightgear

```

---

### Post by Ubunser on 2009-05-21
whereis flightgear

It shows

flightgear:

---

### Post by apjone on 2009-05-21
Ok a quick google suggest it is 

/usr/share/games/FlightGear/Aircraft

not

/usr/share/games/flightgear/aircraft

try that with the original command

---

### Post by Ubunser on 2009-05-21
Yes, after that I pasted the file I wanted.

But check is this normal output from terminal? Also do I have to exit root rights now or is this granted for one folder and until I close it?

Initializing nautilus-share extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:6947): WARNING **: Unable to add monitor: Operation not supported

--- Hash table keys for warning below:
--> file:///usr/share/games/FlightGear
--> file:///usr/share/games/FlightGear/Aircraft

(nautilus:6947): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 2 elements at quit time (keys above)

(nautilus:6947): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 2 elements at quit time
seahorse nautilus module shutdown

---

### Post by mcduck on 2009-05-21
> **Ubunser said:**
> 
As for gksudo, is this the same as sudo? I heard it's better not to use sudo. 


Gksudo has same purpose as sudo has, allowing you to run programs as different user than the one you are currently logged in. Both are usually used in Ubuntu for administration tasks.

"sudo" is intended to be used with command-line programs. It doesn't load root user's environment correctly for graphical applications so you should never run them with sudo.

"gksudo" is like sudo, only made specifically to run graphical applications. It also provides you with a graphical dialog for entering your password so it can be used for menu& desktop launchers.

The rule is simple, use sudo for command-line applications, and gksudo for graphical applications.


For the original problem, most likely you have just mistyped the location. Also remember that Linux is case sensitive, so Flightgear and flightgear would be two separate things.

---

### Post by mcduck on 2009-05-21
> **Ubunser said:**
> Yes, after that I pasted the file I wanted.

But check is this normal output from terminal? Also do I have to exit root rights now or is this granted for one folder and until I close it?

Initializing nautilus-share extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:6947): WARNING **: Unable to add monitor: Operation not supported

--- Hash table keys for warning below:
--> file:///usr/share/games/FlightGear
--> file:///usr/share/games/FlightGear/Aircraft

(nautilus:6947): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 2 elements at quit time (keys above)

(nautilus:6947): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 2 elements at quit time
seahorse nautilus module shutdown

Don't worry about the errors.

If you open the file manager as root, it will run as root until you close it. Also if you open any files from that file manager window the programs used to open the files will run as root as well. So, make sure you close the root nautilus as soon as you don't need it any more.

I always set the background of the root nautilus to bright red, just to make sure I'll never accidentally forget that it's running with full root privileges..

---

### Post by Ubunser on 2009-05-21
Thank you! If it is not too hard for you you may tell how to set the background to red color. I'm not that busy with "roots", but still...

---

### Post by mcduck on 2009-05-21
> **Ubunser said:**
> Thank you! If it is not too hard for you you may tell how to set the background to red color. I'm not that busy with "roots", but still...

You can change the file manager's background color/pattern by selecting Edit/Backgrounds and Emblems. Just pick the color or pattern you like and drag&drop it into the file manager to use it.

If you use the spatial mode of Nautilus you can even set different background for each directory.

---

### Post by Ubunser on 2009-05-21
Cool:p

---

