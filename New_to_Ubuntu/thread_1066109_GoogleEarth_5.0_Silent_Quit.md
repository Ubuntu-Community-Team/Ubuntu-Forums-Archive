---
title: "GoogleEarth 5.0 Silent Quit"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by ftabor on 2009-02-10
I have installed GE 5 twice.  Once by this method:

```
cd ~/Desktop
chmod +x GoogleEarthLinux.bin
sudo ./GoogleEarthLinux.bin

```

And by this method:

```
cd /path/to/GEbinFile/
sh GoogleEarthLinux.bin

```
After starting GE from Applications-->Internet-->GE. While the Daily Tips screen is showing, GE silently quits.  No error messages.  Nothing.

A thread search didn't reveal any similar problems.  Thanks for any help.

---

### Post by taurus on 2009-02-10
Try running it from a terminal to see if there is any error message when it shuts down on it own.

```
googleearth
```

---

### Post by ftabor on 2009-02-10
It's still installed by the second method to ~/ and not root.

```
bash: googleearth: command not found

```

---

### Post by taurus on 2009-02-10
If it's not in your path, then you need to include the whole path.  I assume you probably installed it to ~/googleearth.

```
ls -la ~/googleearth
```

---

### Post by ftabor on 2009-02-10
> **taurus said:**
> If it's not in your path, then you need to include the whole path.  I assume you probably installed it to ~/googleearth.

```
ls -la ~/googleearth
```

It started and ran.  I'm going to post the whole output, I'm a little confused.

```
frank@SeniorChief:~$ ls -la ~/googleearth
lrwxrwxrwx 1 frank frank 37 2009-02-10 16:00 /home/frank/googleearth -> /home/frank/google-earth//googleearth
frank@SeniorChief:~$ ~/googleearth
Warning: Unable to create prefs directory '/home/frank/.googleearth'. File exists.
```

/google-earth as well as .googleearth exists.  Despite the warning about the prefs directory, GE started and ran.  It also starts and runs from the Application Menu.  So I guess I should leave it alone and enjoy it?

Thanks.

Edit: I'll mark it solved as soon as I can find how.  It's not showing in Thread Tools.

---

### Post by johnjohn2 on 2009-02-10
same problem her 
64 bit it that helps

---

