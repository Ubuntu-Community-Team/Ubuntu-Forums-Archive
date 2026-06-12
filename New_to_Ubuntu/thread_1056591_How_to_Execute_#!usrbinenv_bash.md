---
title: "How to Execute: #!/usr/bin/env bash"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by Gias Kay on 2009-01-31
I am trying to install nautilussvn and in its "[Manual installation]("http://code.google.com/p/nautilussvn/wiki/Installation")" section it simply shows me some kind of script with no explanation:

```
#!/usr/bin/env bash

# Nautilus extensions live in ~/.nautilus/python-extensions - make sure that this directory exists.
mkdir -p ~/.nautilus/python-extensions/

# Next checkout NautilusSvn into ~/.nautilus/python-extensions/NautilusSvn
cd ~/.nautilus/python-extensions/
svn checkout http://nautilussvn.googlecode.com/svn/branches/stable NautilusSvn

# Setup the emblems
mkdir -p ~/.icons/hicolor/scalable
ln -s ~/.nautilus/python-extensions/NautilusSvn/icons ~/.icons/hicolor/scalable/emblems # The current emblems folder
ln -s ~/.nautilus/python-extensions/NautilusSvn/icons ~/.icons/hicolor/scalable/icons # The old emblems folder

# Finally we need to set up a symlink so that Nautilus finds the correct startup script. 
ln -s NautilusSvn/NautilusSvn.py NautilusSvn.py

# Now just restart Nautilus, and you should see the new Subversion menu items.
# 1) nautilus -q && nautilus
# 2) killall nautilus
# 3) log out and back in again

nautilus -q && nautilus
```

What does it expect me to do with these command lines? It seems like I have to save it as a certain type of execution file then run it, but I don't know how. Any helps?

---

### Post by taurus on 2009-01-31
I believe you have to create a file

```
gedit myscript
```
and add those lines to it.

```

#!/usr/bin/env bash

# Nautilus extensions live in ~/.nautilus/python-extensions - make sure that this directory exists.
mkdir -p ~/.nautilus/python-extensions/

# Next checkout NautilusSvn into ~/.nautilus/python-extensions/NautilusSvn
cd ~/.nautilus/python-extensions/
svn checkout http://nautilussvn.googlecode.com/svn/branches/stable NautilusSvn

# Setup the emblems
mkdir -p ~/.icons/hicolor/scalable
ln -s ~/.nautilus/python-extensions/NautilusSvn/icons ~/.icons/hicolor/scalable/emblems # The current emblems folder
ln -s ~/.nautilus/python-extensions/NautilusSvn/icons ~/.icons/hicolor/scalable/icons # The old emblems folder

# Finally we need to set up a symlink so that Nautilus finds the correct startup script. 
ln -s NautilusSvn/NautilusSvn.py NautilusSvn.py

# Now just restart Nautilus, and you should see the new Subversion menu items.
# 1) nautilus -q && nautilus
# 2) killall nautilus
# 3) log out and back in again

nautilus -q && nautilus

```
Save it and exit gedit.  Then, change the permission so you can execute/run it.

```
chmod +x myscript
./myscript
```

---

### Post by handydan918 on 2009-01-31
I think an important question is:
Why do you want this installed? This is development (pre-beta!) software and if you don't know how to run a script, perhaps you should reconsider this move.

---

### Post by Gias Kay on 2009-02-01
@taurus: Thanks, that did it! =)

@handydan918: Hey, that's a stable branch I was installing, and you really don't have the right to have a say on what I'd like to learn, right?

---

