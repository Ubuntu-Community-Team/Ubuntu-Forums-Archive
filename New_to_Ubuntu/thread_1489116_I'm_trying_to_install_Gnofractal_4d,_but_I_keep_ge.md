---
title: "I'm trying to install Gnofractal 4d, but I keep getting this"
date: 2010-05-20
forum: New to Ubuntu
---

### Post by Legendary_Bibo on 2010-05-20
What does it mean? This is just the setup, but the setup isn't working so I can't run it. I looked in the file it was talking about for the maps, and there's some with the .cs extension but that doesn't help. I don't know what the second part means. I also looked in synaptic for the libpng, but I have libpng 12.0 and I installled libpng3, but that didn't work.

```
bibo@Bibo:~$ /home/bibo/gnofract4d-3.13/setup.py build
Can't find 'libpng'
Some functionality will be disabled
NO PNG HEADERS FOUND
Can't find 'libpng'
Some functionality will be disabled
NO JPEG HEADERS FOUND
Traceback (most recent call last):
  File "/home/bibo/gnofract4d-3.13/setup.py", line 215, in <module>
    get_files("maps",".cs") +
  File "/home/bibo/gnofract4d-3.13/setup.py", line 192, in get_files
    return [ os.path.join(dir,x) for x in os.listdir(dir) if x.endswith(ext)] 
OSError: [Errno 2] No such file or directory: 'maps'

```

---

### Post by Ocxic on 2010-05-20
try "sudo apt-get install linpng12-dev" to install the libpng development headers, that is what seems to be ewhat it is wanting. 

Welcome to dependency hell.

---

### Post by Legendary_Bibo on 2010-05-20
It's a cold dark place. I skipped the dev one. Alas, it doesn't work. If I had the hard drive space, I would just download every god damn of these dependencies. In the readme it says it needs

o Python version 2.2 or higher - got it
o PyGTK version 1.99 or higher - not exactly named that, but I downloaded it
o GTK+ version 2.0 or higher - I'm pretty sure I have it considering I have other programs using it.
o A C compiler - I got 3 different ones through synaptic.

---

### Post by Legendary_Bibo on 2010-05-20
Oh, out of the kettle into the fire. Well it seems I'm getting a different error...*sigh* first it was looking for PNG headers now JPEG. Make up your damn mind!

```
bibo@Bibo:~$ /home/bibo/Downloads/gnofract4d-3.13/setup.py build
NO JPEG HEADERS FOUND
Traceback (most recent call last):
  File "/home/bibo/Downloads/gnofract4d-3.13/setup.py", line 215, in <module>
    get_files("maps",".cs") +
  File "/home/bibo/Downloads/gnofract4d-3.13/setup.py", line 192, in get_files
    return [ os.path.join(dir,x) for x in os.listdir(dir) if x.endswith(ext)] 
OSError: [Errno 2] No such file or directory: 'maps'

```

So I've reduced the error by getting the jpeglib-dev whatever from synaptic since how that worked for the PNG so now my error is down to this:

```
Traceback (most recent call last):
  File "/home/bibo/Downloads/gnofract4d-3.13/setup.py", line 215, in <module>
    get_files("maps",".cs") +
  File "/home/bibo/Downloads/gnofract4d-3.13/setup.py", line 192, in get_files
    return [ os.path.join(dir,x) for x in os.listdir(dir) if x.endswith(ext)] 
OSError: [Errno 2] No such file or directory: 'maps'

```

---

### Post by Legendary_Bibo on 2010-05-20
Ah ha! I know what I have to do. I have to copy the maps folder to my share folder. Unfortunately it's not letting me do that because it says I don't have permission because I'm not root. How do I do this? I did once on Xubuntu, but I forget how. I'll just do a quick google search.

---

### Post by Sealbhach on 2010-05-20
> **Legendary_Bibo said:**
> Ah ha! I know what I have to do. I have to copy the maps folder to my share folder. Unfortunately it's not letting me do that because it says I don't have permission because I'm not root. How do I do this? I did once on Xubuntu, but I forget how. I'll just do a quick google search.

You can open Nautilus as super user:

```
gksu nautilus

```
.

---

### Post by Legendary_Bibo on 2010-05-20
Oh wow that would've been easier then using the sudo mv command. Unfortunately it didn't work. Blah. I'm going to try creating a 'share' directory in my main filesystem, that might be where it's looking.

---

### Post by Legendary_Bibo on 2010-05-20
Screw it. I give up.

---

